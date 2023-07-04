# Depth estimation and distance to collision using a stereo camera

This project focuses on applying stereo depth estimation techniques to a driving scenario in order to calculate the distance to a collision. By leveraging stereo vision and depth estimation algorithms, provide a solution for estimating the distance to collisions using stereo-depth estimation. By utilizing two cameras, we can capture the scene from slightly different perspectives, mimicking human binocular vision. This allows us to estimate the depth of objects in the captured images.

For the given stereo image pair, assuming a proper alignment performed a stereo matching to compute the disparity map. The disparity map contains information about the pixel-wise disparity between the two images, which can be used to estimate the depth, and using the estimated depth, we can determine the distance to potential collisions in the driving scenario.

## Approach

## 1 - Getting Set-up

- [numpy](www.numpy.org) 
- [matplotlib](http://matplotlib.org)
- [cv2] (https://opencv.org) 
- The `files_management` package contains pre-developed functions for importing data.

- Rectify the stereo image pair to ensure proper alignment.
- Convert the rectified images to grayscale if necessary.

## 2 - Estimating Depth

1. Perform stereo matching on the rectified image pair to calculate the disparity map.



#### Disparity map 
![image](https://github.com/satyapalsinh10/Stereo_Depth/assets/125583562/2807c210-9d43-4eae-8bfc-d64cf4671fcf)

  
3. Decompose the projection matrices into the camera intrinsic matrix $K$, and extrinsics $R$, $t$.
4. Generate the depth map and Use the estimated depth information to determine the distance to potential collisions in the driving scenario.



#### Depth estimation heatmap 
![image](https://github.com/satyapalsinh10/Stereo_Depth/assets/125583562/b8be320d-2e9a-4e9b-927a-430376356481)


## 3 - Finding the distance to collision

We have a map of the depths of each pixel in the scene and use the trained object detector to select a rectangular section containing the object of interest or a potential obstacle (like a motorcycle) to find the object. Our system automatically determines where this obstacle is in the scene using a cross-correlation algorithm for each pixel in the image and generated the associative heat map using OpenCV.

#### Cross-correlation heatmap 
![image](https://github.com/satyapalsinh10/Stereo_Depth/assets/125583562/a6be9e95-1200-42e9-82eb-f10e00fd9456)


### Result : Bounding box and the depth of the nearest point visualization

![image](https://github.com/satyapalsinh10/Stereo_Depth/assets/125583562/baa3040e-7a9a-45f2-9fc4-cbe083266dad)


