
# LicensePlateDetector
Detects license plate of car from image/video and recognizes its characters.
<br> 
<b>
>Created by Harsh Gupta.<b>
## Steps

1. Detect License Plate
2. Perform segmentation of characters
3. Train a ML model to predict characters
4. Prediction of characters in License Plate

## Procedure

The approach used to segment the images is Connected Component Analysis. Connected regions wil imply that all the connected pixels belong
to the same object. A pixel is said to be connected to another if they both have the same value and are adjacent to each other.

Car Image -> Grayscale Image -> Binary Image -> Applying CCA to get connected regions -> Detect license plate out of all connected regions
(Assumptions made : width of the license plate region to the full image ranges between 15% and 40% and height of the license plate region
to the full image is between 8% & 20%)

Output of first step is a license plate image detected in a car image. This is provided as input to step2 and CCA is applied on this image
to bound the characters in plate. Each character identified is appended into a list.

Model is trained using SVC (4 cross fold validation) with dataset present in directory train20X20. The model is saved as finalized_model.sav
which is then loaded to predict each character.

Once the characters of plate is obtained and model is trained, the model is loaded in order to predict each character.


## Setup

Clone the repository.

Change the path of the image/video file in DetectPlate.py

Create virtual env. On windows you could do something like: py -m venv env

Activate the virtual environment env

Install the needed modules using: pip install -r requirements.txt

Run PredictCharacters.py. This will load the trained model (finalized_model.sav) which is added to repo for reference. Your own model can also be trained using the dataset attached in repo.

Running PredictCharacters.py first gives grayscale and binary image. Then produces gray image with license plate bounded inside a rectangle.Each characters are also segmented and shown within boxes.Finally the model predicts the license plate.


## Screenshots

1. Car Video 

>Original frame of video

<img src = "D:\project on number plate recognition\output 1.png">


>License Plate Detected

<img src = "D:\project on number plate recognition\output 2.png">

>Segmented Characters

<img src = "D:\project on number plate recognition\output 3.png">

>Predicted Value

<img src = "D:\project on number plate recognition\output 4.png">

2. Car Image


>Original Image



>License Plate Detected



>Segmented characters



>Predicted characters

