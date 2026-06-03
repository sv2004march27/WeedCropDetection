# 🌾 Crop and Weed Detection System using YOLOv8

![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-blue)
![Python](https://img.shields.io/badge/Python-3.10-green)
![Computer Vision](https://img.shields.io/badge/Computer_Vision-Object_Detection-orange)

## 📌 Overview
This project implements a custom deep learning object detection model to distinguish between sesame crops and unwanted weeds. The primary aim of this system is to enable smart agriculture by identifying weeds accurately, which allows for targeted pesticide spraying. This reduces pesticide waste, prevents crop contamination, and lowers environmental impact.

## 📊 Dataset 
The custom dataset consists of **1,300 images** containing sesame crops and various weed types.
* **Original Capture:** 546 high-resolution (4000x3000) images.
* **Preprocessing:** Images were resized to 512x512 pixels to optimize training time without losing critical feature details.
* **Augmentation:** Data augmentation techniques were applied to increase the dataset size to 1,300 images, improving model robustness.
* **Format:** Bounding boxes were manually annotated and formatted in standard YOLO `.txt` format.

## 🧠 Model Architecture & Training
The system utilizes **YOLOv8 Nano (`yolov8n.pt`)**, chosen for its excellent balance of speed and accuracy, making it ideal for real-time agricultural edge devices.

* **Epochs:** 50
* **Batch Size:** 16
* **Image Size:** 512x512
* **Hardware:** Trained on NVIDIA RTX 4060 GPU
* **Validation Split:** 80% Training / 20% Validation

### 📈 Performance Results
The model achieved highly accurate detection metrics on the validation set:
* **Weed Detection (mAP50):** `0.893` (89.3% accuracy)
* **Crop Detection (mAP50):** `0.854` (85.4% accuracy)

## 🚀 Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/sv2004march27/](https://github.com/sv2004march27/)<YOUR_REPO_NAME>.git
   cd <YOUR_REPO_NAME>

2. **Install dependencies:**
Ensure you have Python 3.8+ installed, then run:
```bash
pip install ultralytics opencv-python pandas

```



## 💻 Usage

### Training the Model

You can train the model using either the provided Jupyter Notebook or the Python script:

**Option 1: Jupyter Notebook**
Open `crop_weed_training.ipynb` and run the cells to organize the dataset and initiate the YOLOv8 training sequence.

**Option 2: Python Script**
Run the training script directly from your terminal:

```bash
python train.py

```

### Running Inference (Testing)

To test the trained weights on a new image, use the `best.pt` file generated in your runs folder:

```python
from ultralytics import YOLO

# Load the trained custom model
model = YOLO("runs/detect/train/weights/best.pt")

# Run prediction
results = model.predict(source="path_to_your_test_image.jpg", save=True, show=True)

```

## 📂 Repository Structure

```text
📦 Repository Root
 ┣ 📂 Project5_Ag_Crop and weed detection  # Nested dataset directories and images
 ┣ 📂 runs                                 # YOLOv8 generated charts, weights, and results
 ┃ ┗ 📂 detect                             # Contains training logs and best.pt
 ┣ 📜 crop_weed_training.ipynb             # Interactive notebook for data prep & training
 ┣ 📜 train.py                             # Python script for model training
 ┣ 📜 dataset.yaml                         # YOLO dataset configuration file
 ┣ 📜 yolov8n.pt                           # Pre-trained YOLOv8 Nano base weights
 ┗ 📜 yolo26n.pt                           # Additional model weights

```

## 🔮 Future Enhancements

* **Live Video Inference:** Implementing real-time detection via webcam or drone footage.
* **Interactive HUD:** Adding OpenCV overlays to physically count the total number of crops vs. weeds on screen.
* **Web UI:** Deploying the model to a Streamlit web application for easy user upload and processing.

## 🤝 Acknowledgments

* Dataset and problem statement inspired by upSkill Campus, UCT, and The IoT Academy.
* Framework powered by [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics).
