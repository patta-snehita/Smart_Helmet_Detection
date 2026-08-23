# 🪖 Smart Helmet Detection using YOLOv8 and CNN

## 📌 Overview

This project implements a **hybrid deep learning system for real-time helmet detection**. It combines **YOLOv8** for object detection with a **Convolutional Neural Network (CNN)** for classifying detected regions as **Helmet** or **No Helmet**.

The system is designed to process real-time video input and display bounding boxes with the predicted helmet status.

---

## 🚀 Features

* Real-time object detection using **YOLOv8**
* Helmet and no-helmet classification using a **CNN**
* Automatic extraction of detected image regions for CNN training
* Binary classification of:

  * 🪖 Helmet
  * ❌ No Helmet
* Real-time webcam inference using **OpenCV**
* Visual output with bounding boxes and predicted labels

---

## 🏗️ System Architecture

```text
Input Image / Webcam
         │
         ▼
   YOLOv8 Detection
         │
         ▼
  Extract Detected Region
         │
         ▼
    CNN Classifier
         │
         ▼
 ┌───────────────────┐
 │ Helmet            │
 │ or                │
 │ No Helmet         │
 └───────────────────┘
```

---

## 🛠️ Tech Stack

* **Python**
* **YOLOv8 / Ultralytics**
* **TensorFlow / Keras**
* **OpenCV**
* **NumPy**
* **Google Colab**
* **Kaggle Dataset**

---

## 📂 Project Workflow

### 1. Dataset Preparation

The traffic surveillance dataset is downloaded and organized into training and validation sets.

YOLO-format annotations are processed to extract relevant object regions and create a separate CNN dataset.

### 2. YOLOv8 Training

A YOLOv8 model is trained for object detection using:

* Image Size: `640`
* Batch Size: `16`
* Epochs: `50`

### 3. CNN Dataset Generation

Detected regions are cropped from the images and categorized into:

```text
cnn_dataset/
├── train/
│   ├── helmet/
│   └── no_helmet/
│
└── val/
    ├── helmet/
    └── no_helmet/
```

### 4. CNN Training

A CNN model is trained using multiple convolutional and pooling layers followed by dense layers for binary classification.

**Configuration:**

* Image Size: `128 × 128`
* Batch Size: `32`
* Optimizer: `Adam`
* Loss Function: `Binary Crossentropy`
* Epochs: `20`

---

## 🧠 CNN Architecture

```text
Input Image (128 × 128 × 3)
          │
          ▼
Conv2D (32) + MaxPooling
          │
          ▼
Conv2D (64) + MaxPooling
          │
          ▼
Conv2D (128) + MaxPooling
          │
          ▼
Flatten
          │
          ▼
Dense (128)
          │
          ▼
Dropout (0.5)
          │
          ▼
Sigmoid Output
          │
          ▼
Helmet / No Helmet
```

---

## ⚡ Real-Time Detection

During inference:

1. Webcam frames are captured using OpenCV.
2. YOLOv8 detects the relevant object regions.
3. Each detected region is cropped and resized.
4. The CNN predicts whether a helmet is present.
5. The result is displayed with a bounding box and label.

Press **`q`** to stop the real-time detection.

---

## 📦 Installation

Clone the repository:

```bash
git clone <your-repository-url>
cd smart-helmet-detection
```

Install the required dependencies:

```bash
pip install ultralytics
pip install tensorflow
pip install opencv-python
pip install numpy
pip install opendatasets
```

---

## ▶️ Running the Project

### Train YOLOv8

```python
from ultralytics import YOLO

model = YOLO("yolov8n.pt")

model.train(
    data="data.yaml",
    epochs=50,
    imgsz=640,
    batch=16
)
```

### Train CNN

Prepare the cropped dataset and train the CNN classifier.

The trained model is saved as:

```text
helmet_cnn.h5
```

### Run Real-Time Detection

```bash
python helmet_cnn.py
```

The webcam window will display the predicted result as:

```text
Helmet
```

or

```text
No Helmet
```

---

## 🎯 Key Learning Outcomes

* Deep Learning and Computer Vision
* Object Detection using YOLOv8
* CNN-based Image Classification
* Dataset Preprocessing and Image Cropping
* Model Training and Validation
* Real-Time Video Processing
* Integration of Multiple Deep Learning Models

---

## 🔮 Future Improvements

* Deploy the application using **Flask or FastAPI**
* Develop a web-based monitoring dashboard
* Add vehicle number plate recognition
* Improve model performance using data augmentation
* Deploy the system on edge devices for real-time traffic surveillance

---

## 👩‍💻 Author

**Patta Snehita**

B.Tech Electrical Engineering
NIT Durgapur
