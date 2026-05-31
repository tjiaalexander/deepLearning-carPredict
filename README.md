# 🚗 Car Classification Using CNN (MobileNetV2)

## 📌 Project Overview

Proyek ini merupakan sistem klasifikasi gambar mobil menggunakan **Convolutional Neural Network (CNN)** dengan metode **Transfer Learning**. Model yang digunakan adalah **MobileNetV2** yang telah dilatih sebelumnya pada dataset ImageNet.

Tujuan proyek ini adalah mengidentifikasi jenis mobil berdasarkan gambar yang diunggah oleh pengguna.

---

## 🎯 Objectives

* Mengembangkan model klasifikasi gambar mobil menggunakan CNN.
* Menerapkan teknik Transfer Learning untuk meningkatkan performa model.
* Melakukan preprocessing dan augmentasi data gambar.
* Menyediakan antarmuka prediksi menggunakan Gradio.

---

## 📂 Dataset

Dataset terdiri dari gambar berbagai jenis mobil yang dikelompokkan ke dalam beberapa kelas.

### Dataset Processing

* Image Size: **224 × 224 pixels**
* Training Split: **80%**
* Validation Split: **20%**
* Batch Size: **32**

---

## 🔄 Data Preprocessing

Sebelum proses pelatihan, data diproses menggunakan `ImageDataGenerator`:

### Normalization

```python
rescale = 1./255
```

Mengubah nilai pixel dari rentang 0–255 menjadi 0–1.

### Data Augmentation

```python
rotation_range = 20
horizontal_flip = True
```

Teknik ini digunakan untuk:

* Menambah variasi data
* Mengurangi overfitting
* Meningkatkan kemampuan generalisasi model

---

## 🧠 Model Architecture

Model menggunakan **MobileNetV2** sebagai feature extractor.

### Architecture Flow

```text
Input Image (224x224x3)
        │
        ▼
MobileNetV2 (Pretrained ImageNet)
        │
        ▼
GlobalAveragePooling2D
        │
        ▼
Dense(128, ReLU)
        │
        ▼
Dense(Number_of_Classes, Softmax)
```

### Transfer Learning

```python
for layer in base_model.layers:
    layer.trainable = False
```

Semua layer MobileNetV2 dibekukan (freeze) sehingga hanya layer klasifikasi yang dilatih.

---

## ⚙️ Model Training

Model dikompilasi menggunakan:

```python
optimizer='adam'
loss='categorical_crossentropy'
metrics=['accuracy']
```

Training dilakukan selama:

```python
epochs = 10
```

---

## 📊 Model Evaluation

Evaluasi dilakukan menggunakan:

### Training Accuracy

Mengukur performa model pada data training.

### Validation Accuracy

Mengukur performa model pada data yang belum pernah dilihat sebelumnya.

### Visualization

Grafik yang ditampilkan:

* Training Accuracy
* Validation Accuracy
* Training Loss
* Validation Loss

---

## 🔍 Prediction Example

Model melakukan prediksi terhadap gambar validasi dan menampilkan:

```text
True Label: Sedan
Predicted Label: Sedan
```

Visualisasi ini digunakan untuk melihat hasil prediksi secara langsung.

---

## 🌐 Gradio Interface

Proyek ini menyediakan antarmuka berbasis Gradio sehingga pengguna dapat mengunggah gambar mobil dan mendapatkan hasil klasifikasi secara real-time.

### Features

* Upload image
* Predict vehicle class
* Display prediction probabilities
* Easy-to-use interface

---

## 📈 Results

Model berhasil mencapai:

```text
Training Accuracy  ≈ 90%
Validation Accuracy ≈ 87%
```

Hasil ini menunjukkan bahwa model memiliki kemampuan yang baik dalam mengklasifikasikan gambar mobil dan mampu melakukan generalisasi terhadap data baru.

---

## 🛠 Technologies Used

* Python
* TensorFlow
* Keras
* MobileNetV2
* NumPy
* Matplotlib
* Gradio

---

## 🚀 Future Improvements

* Fine-tuning MobileNetV2 layers
* Early Stopping Callback
* Learning Rate Scheduler
* Larger and more diverse dataset
* Deployment to Hugging Face Spaces or Streamlit

---

## 👨‍💻 Author

**Alexander Tjia**

Project: **Car Classification Using CNN with MobileNetV2 Transfer Learning**
Year: **2026**
