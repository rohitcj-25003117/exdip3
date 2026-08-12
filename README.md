Histogram Equalization Using OpenCV (Grayscale & Color Images)
Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

Read and display a grayscale image
Plot histogram of the grayscale image
Apply histogram equalization on grayscale image
Read and display a color image
Plot histogram of B, G, R channels
Convert image to HSV color space
Apply histogram equalization on the Value (V) channel
Convert the enhanced image back to BGR format
Display original and enhanced images with histograms
Software Used
Anaconda – Python 3.7
Jupyter Notebook / VS Code
OpenCV (cv2)
NumPy
Matplotlib
Algorithm
Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:

Read the image saveetha.jpg in grayscale format.

Step 3:

Display the grayscale image and plot its histogram.

Step 4:

Apply histogram equalization using cv2.equalizeHist() to enhance contrast.

Step 5:

Display the original grayscale image, its histogram, enhanced image, and its histogram separately.

Step 6:

Read the same image in color format.

Step 7:

Split the image into B, G, R channels and plot their histograms.

Step 8:

Convert the image from BGR to HSV color space.

Step 9:

Apply histogram equalization on the V (Value) channel.

Step 10:

Merge the channels and convert the image back to BGR format.

Step 11:

Display the original color image, histogram, enhanced image, and enhanced histogram separately.

Developed By:

Name: CJ ROHIT

Register No: 212224243005

Program :
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# =========================================================
# 1. Load the Image
# =========================================================

image = cv2.imread('saveetha.jpg')

# =========================================================
# 2. Convert the Image to Grayscale
# =========================================================

gray_image = cv2.cvtColor(
    image,
    cv2.COLOR_BGR2GRAY
)

# Display Original Grayscale Image

plt.figure(figsize=(6, 5))

plt.imshow(
    gray_image,
    cmap='gray'
)

plt.title('Original Grayscale Image')
plt.axis('off')
plt.show()


# =========================================================
# 3. Original Grayscale Histogram
# =========================================================

hist_original = cv2.calcHist(
    [gray_image],
    [0],
    None,
    [256],
    [0, 256]
)

plt.figure(figsize=(7, 5))

plt.plot(
    hist_original,
    color='black'
)

plt.title('Original Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])
plt.show()


# =========================================================
# 4. Apply Histogram Equalization
# =========================================================

equalized_image = cv2.equalizeHist(
    gray_image
)


# =========================================================
# 5. Display Equalized Image
# =========================================================

plt.figure(figsize=(6, 5))

plt.imshow(
    equalized_image,
    cmap='gray'
)

plt.title('Equalized Image')
plt.axis('off')
plt.show()


# =========================================================
# 6. Equalized Histogram
# =========================================================

hist_equalized = cv2.calcHist(
    [equalized_image],
    [0],
    None,
    [256],
    [0, 256]
)

plt.figure(figsize=(7, 5))

plt.plot(
    hist_equalized,
    color='black'
)

plt.title('Equalized Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])
plt.show()


# =========================================================
# 7. Read Color Image
# =========================================================

color_image = cv2.imread(
    'saveetha.jpg',
    cv2.IMREAD_COLOR
)


# =========================================================
# 8. Display Original Color Image
# =========================================================

plt.figure(figsize=(6, 5))

plt.imshow(
    cv2.cvtColor(
        color_image,
        cv2.COLOR_BGR2RGB
    )
)

plt.title('Original Color Image')
plt.axis('off')
plt.show()


# =========================================================
# 9. B, G, R Channel Histograms
# =========================================================

blue, green, red = cv2.split(
    color_image
)

plt.figure(figsize=(8, 5))

plt.hist(
    blue.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Blue'
)

plt.hist(
    green.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Green'
)

plt.hist(
    red.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Red'
)

plt.title('B, G, R Channel Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])
plt.legend()
plt.show()


# =========================================================
# 10. Convert BGR Image to HSV
# =========================================================

image_hsv = cv2.cvtColor(
    color_image,
    cv2.COLOR_BGR2HSV
)


# =========================================================
# 11. Apply Histogram Equalization to V Channel
# =========================================================

image_hsv[:, :, 2] = cv2.equalizeHist(
    image_hsv[:, :, 2]
)


# =========================================================
# 12. Convert HSV Back to BGR
# =========================================================

enhanced_image = cv2.cvtColor(
    image_hsv,
    cv2.COLOR_HSV2BGR
)


# =========================================================
# 13. Display Enhanced Color Image
# =========================================================

plt.figure(figsize=(6, 5))

plt.imshow(
    cv2.cvtColor(
        enhanced_image,
        cv2.COLOR_BGR2RGB
    )
)

plt.title('Enhanced Color Image')
plt.axis('off')
plt.show()


# =========================================================
# 14. Enhanced Color Histogram
# =========================================================

blue_enhanced, green_enhanced, red_enhanced = cv2.split(
    enhanced_image
)

plt.figure(figsize=(8, 5))

plt.hist(
    blue_enhanced.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Blue'
)

plt.hist(
    green_enhanced.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Green'
)

plt.hist(
    red_enhanced.ravel(),
    256,
    range=[0, 256],
    alpha=0.5,
    label='Red'
)

plt.title('Enhanced Color Histogram')
plt.xlabel('Pixel Intensity')
plt.ylabel('Frequency')
plt.xlim([0, 256])
plt.legend()
plt.show()
Grayscale Histogram Equalization
Original grayscale image is displayed
Histogram of original grayscale image is plotted
Enhanced image after histogram equalization is displayed
Histogram of enhanced grayscale image shows improved contrast
```

OUTPUT:

1. Original Grayscale Image

2. Original Histogram

3. Equalized Grayscale Image

4. Equalized Histogram

Color Image Histogram Equalization
Original color image is displayed
Histogram of B, G, R channels is plotted
Image is converted from BGR to HSV
Histogram equalization is applied to the V channel
Enhanced color image is displayed
Enhanced color histogram is displayed
OUTPUT:

5. Original Color Image

6. B, G, R Channel Histogram

7. Enhanced Color Image

8. Enhanced Color Histogram
<img width="557" height="599" alt="image" src="https://github.com/user-attachments/assets/ccefb649-fcb7-44f7-8485-650d4f6c022b" />
<img width="521" height="416" alt="image" src="https://github.com/user-attachments/assets/a037ab4f-8e25-4344-9fb5-994d2a1a5057" />
<img width="392" height="535" alt="image" src="https://github.com/user-attachments/assets/9679f750-66df-47f0-ab37-f919c479298d" />




Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the saveetha.jpg image are improved, enhancing visual quality and feature visibility.
