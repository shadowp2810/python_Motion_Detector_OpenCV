# python_Motion_Detector_OpenCV
Python script to detect objects in motion using OpenCV, storing the detected times in csv using Pandas,  and visualizing the csv on a graph using Bokeh
<br><br> 
![python_GUI_BookShelf_DB_OOPv](demo/demo.gif)
<img width="1280" alt="bokeh_plot" src="https://user-images.githubusercontent.com/66818159/125201232-cd710600-e28b-11eb-96b7-a18219c31b76.png">
<br>
### To run Motion Detector and generate graph at end of session:
$`python3 plotting.py` <br>
Press `q` to end session <br><br>
### To run just the Motion Detector:
$`python3 app.py` <br>
Press `q` to end session <br><br>

#### In directory cv2 visionScripts is script to batch identify faces in a folder of images using haarcascade

## Notes:
Objects in motion<br>
Motion Detector<br>

- Script first needs a static image or baseline image. <br>
- Objects in motion are the objects, <br>
that when subtracted with baseline image, still remain.  <br>

- The first frame when webcam is started, <br>
must be the static image. <br>
- Static image is first greyscaled, <br>
and all other frames in loop are greyscaled. <br>
- Difference or `Delta frame` is made.  <br>
In difference the object in motion will have <br>
light behind it from the first static photo. <br>
All else in photo will be blackened.  <br>

- `Threshold Frame` turns the intensity to max , <br>
which shows just white or black contracting objects in frame. <br>
- Below Threshold areas are black.  <br>
- A contour is made arround the objects in white ,  <br>
and if they are over 500 px then they are considred moving.  <br>

1) Python captures first frame. <br>
2) Converts it to greyscaled. <br>
3) Blurs it. <br>
4) And stores the first frame.  <br>
5) Then calculates difference between <br>
everyframe proceeding it and first frame.  <br>
6) Finds contours. <br>
7) And if contours is greater than a value , <br>
status is 1 so moving object detected. <br>
8) Status list is appended. <br>
9) Status list starts with 0 from first frame. <br>
10) And everytime there is a change from 0 to 1 ,  <br>
or 1 to 0 in status list , then the date time <br>
is recorded into a csv file using pandas. <br>

11) The csv file is loaded as a dataframe using pandas. <br>
12) Bokeh using this dataframe, <br>
graphs the start and end times of the moving detected objects, <br>
and makes a html file to visualize the data using a graph. <br> <br>

