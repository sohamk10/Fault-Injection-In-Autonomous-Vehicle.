# Fault-Injection-In-Autonomous-Vehicle.
Identifying failure modes of vehicle cameras in the domain of autonomous driving (ADAS) and, designing a Fault Injection Module (FIM) to inject these faults through image processing into the autonomous vehicle system.  

This task consists of identifying various failure modes associated with vehicle cameras. The following faults were selected for further study based on literature review and research: Pixel manipulation faults, image superimposition faults, and new filters to simulate rainy weather. As a result, the following faults have been implemented:

1. Contrast  
2. Brightness  
3. Blur Colour  
4. Sharpness  
5. Raindrop  
6. Blur  
7. Salt and Pepper noise  
8. Snow  
9. Dust  
10. Rain  
11. Dense fog  
12. Light fog  
13. Mud splash  
14. Glass crack  
15. Shattered glass  
16. Smog  
17. Dust  


# Fault Implementation

1. Pixel manipulation Filters  
Digitally, images are saved as a matrix of pixels. The pixel is the fundamental element of
an image. The way colours are specified is known as the colour space, and each pixel has a
distinct colour.
The RGB colour space is the most used. Three values, one each for red, green, and blue,
are used in this paradigm to define each colour. The term "colour depth" refers to the fact
that these values are typically 8-bit unsigned integers with a range of 0 to 255. Black and
white are the colours (255, 255, 255) and (0, 0, 0) respectively.
Filters are mathematical functions which perform mathematical computations of the pixel
values of the input image to produce a new image.The filters to manipulate the Brightness,
Sharpness, Colour and Contrast were created using the PIL module ImageEnhance using
separate functions.

![blur](https://user-images.githubusercontent.com/117833435/205360989-bc7267d7-5e16-429f-b789-162212ea0dbb.png)  

2. Image superimposition filters  
Image superimposition is a image processing technique for coping the image data from
one image over the other. This technique is used to implement faults related to changes
in weather and damage to the camera glass protecting the lens. The image frames from
the camera are superimposed with a mask of the fault to be injected. These masks are
transparent images collected from public domain images on Google. Transparent images
of dirt, snow, fog, glass crack, rain are used as masking images. These transparent images
contain opaque regions representing the faults. Only the opaque regions of the transparent
images are overlayed on the camera image frames. Python Imaging Library (PIL) is a python package used for implementing these faults.

3. Rain Drop Blur  
Drops of water during the rainy season create a blurring effect on the surface of the glass.
This blurring effect is caused only on the portion where the drop lies on the glass surface.
Such an effect is created using the pillow library in python.  


■ An image is created in the ’L’ (luminous) mode with the same size as that of the
camera frame image.  
■ Small white circles are drawn on the luminous image at random using the draw.ellipse
method.  
■ This luminous image is converted into an array.  
■ The image frame from the camera is blurred and then converted into an array.  
■ The blurred camera image is stacked on the luminous image to get the blurred effect
at random locations.  
■ The function is created which allows the user to set the number of blurred circles
depending on the desired effect to be generated. If the desired effect is slight rainfall,
the number of blurred circles to be drawn is small and for heavy rainfall the number
is large.  


![rain](https://user-images.githubusercontent.com/117833435/205361754-0d0af39f-102c-446a-8532-f08a65a03850.png)  


# Fault Injection Module (FIM)

Now faults are injected into camera image frames to simulate real-time errors in autonomous cars. As an input to the AI model of the autonomous car, the camera on the autonomous car provides image frames at a rate of 30 frames per second. We therefore need a Fault Injection Module (FIM) in order to inject the camera-based faults into the image frames. The Fault Injection Module (FIM) is a Python interface that allows selecting single or multiple faults to be injected, as well as selecting the intensity of the fault to be injected.  

![FIM](https://user-images.githubusercontent.com/117833435/205360071-800a1b06-1a23-4ed7-b978-d95d9474409b.jpg)  






