## README--Object Detection on the Raspberry Pi with Multiple Movidius NCSs  
-------------
#### Software and Hardware Used  
|Software|Hardware|
|:---:|:---:|  
|Python 3.7|Raspberry Pi 3 Model B+|  
|NCSDK v2.0| NCS 1(at least two)|
|Caffe(When we need to build our own model)|Pi camera(XC9020 5MP Camera)|

#### Instructions
* This project combines the Intel Neural Compute Stick (NCS) and Raspberry Pi 3 Model B+, at least two sticks are needed.   
* There are two different scenarios, 'On The Road' and 'Off the Road', with different usage of models.
* The first device is using MobileNet to judge which scenario it is; The rest devices are used for further processing.  
* 'On The Road': only Tiny YOLO will be used to do object detection.
* 'Off the Road': both Tiny YOLO and GoogLeNet will be used to do object detection, where the GoogLeNet will predict on filtered objects from Tiny YOLO.  

-------------
#### Operation while running
* There are two operation modes: Manual and Automatic.
1. Manual: press '2' to toggle GoogLeNet classification.
2. Automatic: It will automatically decide which scenario and do related operation.
* Method to change operation modes:  
E/D mean Enable/Disable keyboard interruption.
* All the running infomation will be printed on the screen first including handling keys:  
```
print('Running program')
print('Keys:')
print("  'Q'/'q' to Quit")
print("  'B'/'b' to inc/dec the Tiny Yolo box probability threshold")
print("  'I'/'i' to inc/dec the Tiny Yolo box intersection-over-union threshold")
print("  'G'/'g' to inc/dec the GoogLeNet probability threshold")
print("  '2'     to toggle GoogLeNet classification")
print("  'E/D'   to Enable/Disable Keyboard Interruption")
```
-------------
#### Acceleration ability of NCS when only using MobileNet(easier and faster)

|Configuration|Time(s)|FPS|SpeedUp|
|:---:|:---:|:---:|:---:|
|Pi CPU|318.37|0.49|1.0x|
|Pi CPU+NCS * 1|46.45|3.37|6.87x|
|Pi CPU+NCS * 2|23.58|6.62|13.50x|
-------------
#### Results


-------------
**Created by Yucong on 2018/05/30**
