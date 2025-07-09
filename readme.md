# 🧠 TumorNet-Classifier-Segmenter: Model Training  
*Created by: Waleed Haroon*

This project demonstrates the training of two deep learning models for **brain tumor analysis using MRI images**:

1. **CNN Classifier:** Determines whether an MRI image contains a tumor.
2. **U-Net Segmenter:** Segments the tumor region within the MRI image (if a tumor is present).

---

## 📂 Dataset

The following publicly available datasets from **Kaggle** were used:

- **🧪 Classification Dataset**:  
  *[Brain MRI Images for Brain Tumor Detection](https://www.kaggle.com/navoneel/brain-mri-images-for-brain-tumor-detection)* by Navoneel  
  → Used to train the CNN classifier  
  → **253 images** (`yes` = tumor, `no` = no tumor)

- **🧬 Segmentation Dataset**:  
  *[LGG MRI Segmentation](https://www.kaggle.com/mateuszbuda/lgg-mri-segmentation)* by Mateusz Buda et al.  
  → Used to train the U-Net model  
  → **500 images** and corresponding tumor masks

---

## 🔍 How It Works

1. **Data Loading & Preprocessing**  
   - MRI images are resized and normalized  
   - Segmentation masks are converted to grayscale and normalized

2. **CNN Training (Classifier)**  
   - Learns to classify MRI images into *Tumor* or *No Tumor*

3. **U-Net Training (Segmenter)**  
   - Learns to predict pixel-wise segmentation masks for tumor regions

4. **Inference Pipeline**  
   - Given an MRI image:
     - It is first passed through the **CNN Classifier**
     - If a tumor is predicted, the image is passed through the **U-Net Segmenter**
     - The predicted mask is **overlaid** on the original image for visualization

---

## 🛠️ Training Details

| Model            | Optimizer | Loss Function         | Epochs | Validation Split |
|------------------|-----------|------------------------|--------|------------------|
| CNN Classifier   | Adam      | Binary Crossentropy    | 10     | 20%              |
| U-Net Segmenter  | Adam      | Binary Crossentropy    | 3      | 20%              |

---

## 🧠 Model Architectures

### ✅ CNN Classifier
- Uses multiple `Conv2D`, `MaxPooling`, and `Dense` layers
- Learns abstract features from the MRI scans to classify tumor presence

### ✅ U-Net Segmenter
- U-shaped architecture with:
  - **Encoder**: Downsampling via convolution and pooling
  - **Decoder**: Upsampling and reconstructing segmentation
  - **Skip connections** for preserving spatial details

---

## 📌 Results

- Classifier achieves high accuracy on tumor detection
- Segmenter produces accurate masks, visually overlaid on original images
- The complete pipeline provides **automated tumor detection and localization**

---

## 🚀 Future Work

- Enhance segmentation using Dice loss / Jaccard index
- Train on a larger dataset for robustness
- Deploy as a web app using **Streamlit** or **Flask**

