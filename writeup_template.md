# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of several steps: 

* First, I converted the images to grayscale, then I applied Gaussian blur and extract eages using Canny.
* I specifies a rather complex region of interest to reduce the area where lines should be found.
* In the basic version (Video 1 with `process_image()`) I used all line segments from Hough line transformation and plot that on the original image. Here I did not modify draw_lines.

* For Video 2 (`process_image2()`) I added a lot of new funtions (I did not put it in draw_lines() but just after the hough function.)
* I seperated left and right lines and only took those with a meaninful slope. 
* I save them in a buffer of 20 lines for each side. Since there are problems with some images in between, I make sure that there are always enough lines available for the next processing steps. 
* I took the left x and y points and fit a line (`np.polyfit`). 
* For the final printed line I made sure that the line start at the bottom of the image and reaches up to the most right point in the buffer. 
* It did the same for the right points.



### 2. Identify potential shortcomings with your current pipeline


* One potential shortcoming would be what would happen when the street is very curvy and the lane lines are not in the handmade region of interest. 
* Another shortcoming is that parameters for Hough Lines are "tuned" on those few images and videos. It does not generalize well.


### 3. Suggest possible improvements to your pipeline

* Make lines more robust for curves using 2 to 3 lines.
* In general there are a lot of parameters involed which need to be tested with other videos (days, night, etc.).
