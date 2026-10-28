# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

print("OpenCV Version:", cv2.__version__)
print("Libraries imported successfully!")

gray = cv2.imread("virat_kohli.jpg", cv2.IMREAD_GRAYSCALE)

if gray is None:
    raise FileNotFoundError(
        "Image not found. Check the filename and notebook folder."
    )

print("Image dimensions:", gray.shape)

plt.figure(figsize=(6, 6))
plt.imshow(gray, cmap="gray")
plt.title("Virat Kohli - Grayscale Image")
plt.axis("off")
plt.show()

import os

print("Current folder:", os.getcwd())
print("Files in folder:", os.listdir())

import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\Pictures\virat_kohli.jpg"

gray = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)

if gray is None:
    print("Image not found. Check the filename in your Pictures folder.")
else:
    print("Image loaded successfully!")
    print("Image dimensions:", gray.shape)

    plt.imshow(gray, cmap="gray")
    plt.title("Virat Kohli - Grayscale Image")
    plt.axis("off")
    plt.show()

import cv2
import matplotlib.pyplot as plt

image_path = r"C:\Users\acer\OneDrive\Pictures\Camera Roll\Virat Kohli.jpg"

gray = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)

if gray is None:
    print("Image could not be loaded.")
else:
    print("Image loaded successfully!")
    print("Image dimensions:", gray.shape)

    plt.figure(figsize=(6, 6))
    plt.imshow(gray, cmap="gray")
    plt.title("Virat Kohli - Grayscale Image")
    plt.axis("off")
    plt.show()

plt.figure(figsize=(8, 4))
plt.hist(gray.ravel(), bins=256, range=(0, 256))
plt.title("Histogram of Virat Kohli Grayscale Image")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")
plt.show()

equalized = cv2.equalizeHist(gray)

plt.figure(figsize=(6, 6))
plt.imshow(equalized, cmap="gray")
plt.title("Histogram Equalized Image")
plt.axis("off")
plt.show()

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(gray, cmap="gray")
plt.title("Original Grayscale Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(gray.ravel(), bins=256, range=(0, 256))
plt.title("Original Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.imshow(equalized, cmap="gray")
plt.title("Histogram Equalized Image")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.hist(equalized.ravel(), bins=256, range=(0, 256))
plt.title("Equalized Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()

color = cv2.imread(
    r"C:\Users\acer\OneDrive\Pictures\Camera Roll\Virat Kohli.jpg"
)

rgb = cv2.cvtColor(color, cv2.COLOR_BGR2RGB)
b, g, r = cv2.split(color)

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(b.ravel(), bins=256, range=(0, 256))
plt.title("Blue Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.hist(g.ravel(), bins=256, range=(0, 256))
plt.title("Green Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 4)
plt.hist(r.ravel(), bins=256, range=(0, 256))
plt.title("Red Channel Histogram")
plt.xlabel("Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()

b, g, r = cv2.split(color)

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(b.ravel(), bins=256, range=(0, 256))
plt.title("Blue Channel Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.hist(g.ravel(), bins=256, range=(0, 256))
plt.title("Green Channel Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 4)
plt.hist(r.ravel(), bins=256, range=(0, 256))
plt.title("Red Channel Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()

hsv = cv2.cvtColor(color, cv2.COLOR_BGR2HSV)

h, s, v = cv2.split(hsv)

plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(h, cmap="gray")
plt.title("Hue Channel")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(s, cmap="gray")
plt.title("Saturation Channel")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(v, cmap="gray")
plt.title("Value Channel")
plt.axis("off")

plt.tight_layout()
plt.show()

v_equalized = cv2.equalizeHist(v)

plt.figure(figsize=(10, 4))

plt.subplot(1, 2, 1)
plt.imshow(v, cmap="gray")
plt.title("Original V Channel")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(v_equalized, cmap="gray")
plt.title("Equalized V Channel")
plt.axis("off")

plt.tight_layout()
plt.show()

hsv_enhanced = cv2.merge([h, s, v_equalized])

enhanced_bgr = cv2.cvtColor(
    hsv_enhanced,
    cv2.COLOR_HSV2BGR
)

enhanced_rgb = cv2.cvtColor(
    enhanced_bgr,
    cv2.COLOR_BGR2RGB
)

plt.figure(figsize=(6, 6))
plt.imshow(enhanced_rgb)
plt.title("Virat Kohli - HSV Enhanced Image")
plt.axis("off")
plt.show()

plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(rgb)
plt.title("Original Color Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.hist(color.ravel(), bins=256, range=(0, 256))
plt.title("Original Color Image Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.subplot(2, 2, 3)
plt.imshow(enhanced_rgb)
plt.title("HSV Histogram Equalized Image")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.hist(enhanced_bgr.ravel(), bins=256, range=(0, 256))
plt.title("Enhanced Image Histogram")
plt.xlabel("Pixel Intensity")
plt.ylabel("Frequency")

plt.tight_layout()
plt.show()
```

### Developed By:
**Name:** PON SARAVANA PANDIAN B

### Register No:212225230207

---

##  Output
<img width="648" height="413" alt="image" src="https://github.com/user-attachments/assets/2b24858d-f1c6-4f80-85f6-8dad747a2638" />

<img width="887" height="502" alt="image" src="https://github.com/user-attachments/assets/89eb04b0-d782-42f9-b90a-8f92b527e107" />

<img width="600" height="377" alt="image" src="https://github.com/user-attachments/assets/b0eeec99-2095-4bd1-9179-1d7f54a2747e" />

<img width="1307" height="853" alt="image" src="https://github.com/user-attachments/assets/e7078837-47f0-47e0-ba5b-27c0ecfff93c" />

<img width="1300" height="872" alt="image" src="https://github.com/user-attachments/assets/624819ae-a14a-4029-8d64-c2c85f638051" />

<img width="1317" height="301" alt="image" src="https://github.com/user-attachments/assets/9d143a57-37c9-444d-be1c-0bea1ba9b5de" />

<img width="1253" height="410" alt="image" src="https://github.com/user-attachments/assets/0bd2556a-4f9a-478f-9bde-35a158a17521" />

<img width="1306" height="890" alt="image" src="https://github.com/user-attachments/assets/1ab6e2e7-e405-499e-9a5f-d4d1f990a826" />

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
