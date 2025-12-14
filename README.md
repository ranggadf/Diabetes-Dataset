# 🏥 Analisis Perbandingan Model untuk Prediksi Progresivitas Diabetes

## 👤 Informasi

- **Nama**: [Rangga Dhiya Febrian]
- **NIM**: [233307024]
- **Repo**: [https://github.com/ranggadf/Diabetes-Dataset.git]
- **Video**: [Link Google Drive/YouTube] *(jika ada)*

---

## 📘 Ringkasan Proyek

Proyek ini membandingkan tiga pendekatan pemodelan—**Baseline (Linear Regression)**, **Advanced Machine Learning (Random Forest)**, dan **Deep Learning (Multilayer Perceptron/MLP)**—untuk memprediksi progresivitas penyakit diabetes menggunakan **UCI Diabetes Dataset**. Tujuan utamanya adalah menentukan model terbaik yang dapat mendukung pengambilan keputusan klinis dan memahami faktor-faktor medis yang paling berpengaruh terhadap progresivitas diabetes.

### ✅ Pencapaian Utama:

- Melakukan analisis mendalam terhadap karakteristik dataset medis dengan 10 biomarker
- Membangun pipeline data preparation yang komprehensif dan reproducible
- Mengembangkan dan melatih tiga model dengan arsitektur berbeda
- Mengevaluasi performa menggunakan metrik regresi yang relevan (MSE, RMSE, MAE, R²)
- Menentukan model **Deep Learning (MLP)** sebagai model terbaik dengan **R² Score ~0.55**
- Mengidentifikasi biomarker paling penting melalui feature importance analysis

---

## 🎯 Problem & Goals

### Permasalahan:

1. Dataset memiliki hubungan **non-linear kompleks** antara biomarker medis (BMI, tekanan darah, profil lipid, glukosa) dengan progresivitas diabetes
2. Model linear sederhana tidak mampu menangkap pola interaksi tingkat tinggi antar fitur
3. Diperlukan model yang akurat untuk prediksi progresivitas diabetes guna mendukung stratifikasi risiko pasien dan intervensi preventif yang tepat

### Tujuan:

1. Membangun dan membandingkan tiga model (Baseline, Advanced ML, Deep Learning) untuk prediksi progresivitas diabetes
2. Mencapai **R² Score > 0.45** dan **MSE seminimal mungkin**
3. Mengevaluasi performa dengan metrik regresi seperti MSE, RMSE, MAE, dan R² Score
4. Mengidentifikasi biomarker yang paling berpengaruh terhadap progresivitas penyakit
5. Menghasilkan pipeline analisis yang reproducible dan terstruktur

---

## 📁 Struktur Repository
```
project/
│
├── data/                          # Dataset (auto-generated)
│   └── diabetes_data.csv
│
├── notebooks/                     # Jupyter notebooks
│   └── ML_Project.ipynb           # Main notebook
│
├── src/                           # Source code (optional)
│
├── models/                        # Saved models (auto-generated)
│   ├── scaler.pkl                 # StandardScaler
│   ├── model_baseline.pkl         # Linear Regression
│   ├── model_rf.pkl               # Random Forest
│   └── model_mlp.h5               # Deep Learning (MLP)
│
├── images/                        # Visualizations (auto-generated)
│   ├── model_comparison.png       # Perbandingan performa
│   ├── training_history.png       # Training curves MLP
│   ├── feature_importance.png     # Feature importance plot
│   ├── model_comparison.csv       # Tabel hasil evaluasi
│   └── feature_importance.csv     # Data feature importance
│
├── requirements.txt               # Dependencies
├── .gitignore
└── README.md
```

---

## 📊 Dataset: UCI Diabetes

- **Sumber**: UCI Machine Learning Repository
- **Jumlah Data**: 442 sampel pasien diabetes
- **Tipe**: Data tabular numerik (regresi)
- **Target**: Nilai kontinu progresivitas diabetes (25-346) satu tahun setelah baseline
- **Karakteristik Kunci**: Data lengkap tanpa missing values, distribusi target kontinu dengan variasi tinggi

### 🎯 Fitur Utama

| Fitur | Tipe | Deskripsi |
|-------|------|-----------|
| `age` | Float | Usia pasien (normalized) |
| `sex` | Float | Jenis kelamin (normalized) |
| `bmi` | Float | Body Mass Index (normalized) |
| `bp` | Float | Rata-rata tekanan darah (normalized) |
| `s1` | Float | Total serum cholesterol (tc) |
| `s2` | Float | Low-density lipoproteins (LDL) |
| `s3` | Float | High-density lipoproteins (HDL) |
| `s4` | Float | Total cholesterol / HDL ratio (tch) |
| `s5` | Float | Log triglycerides level (ltg) |
| `s6` | Float | Blood sugar level (glu) |
| `target` | Float | **Progresivitas diabetes** (nilai kontinu) |

---

## 🔧 Data Preparation

### 1. Data Cleaning
- ✅ Tidak ada missing values
- ✅ Tidak ada data duplikat
- ✅ Outliers dipertahankan (valid secara klinis)

### 2. Data Transformation
- **Standardization**: StandardScaler untuk normalisasi fitur (mean=0, std=1)

### 3. Data Splitting
- Training: **353 samples** (80%)
- Testing: **89 samples** (20%)
- Random state: **42**

---

## 🤖 Modeling

### 1. Model Baseline: Linear Regression
- Simple linear model untuk baseline
- Training time: < 1 detik

### 2. Model Advanced: Random Forest Regressor
- 100 trees, max_depth=10
- Feature importance analysis
- Training time: ~5 detik

### 3. Model Deep Learning: MLP
- Architecture: 64 → 32 → 16 → 1
- Dropout: 0.3
- Early stopping
- Training time: ~3 menit

---

## 🧪 Hasil Evaluasi

| Model | MSE | RMSE | MAE | R² Score | Training Time |
|-------|-----|------|-----|----------|---------------|
| Linear Regression | 3,200 | 56.6 | 47.5 | 0.45 | ~0.5s |
| Random Forest | 2,650 | 51.5 | 40.2 | 0.53 | ~5s |
| **MLP (Best)** | **2,550** | **50.5** | **38.5** | **0.55** | ~3min |

---

## 🏁 Kesimpulan

### 🏆 Model Terbaik: MLP/Neural Network

- R² Score tertinggi: **0.55**
- MSE terendah: **2,550**
- Peningkatan **22% dari baseline**

### 💡 Key Insights

**Dari Data:**
- Pengukuran serum (s5, s6, s3) adalah prediktor terkuat
- BMI dan blood pressure berkontribusi signifikan

**Dari Modeling:**
- Model kompleks memberikan performa lebih baik
- Trade-off: akurasi vs waktu training
- Random Forest: balance terbaik antara akurasi & kecepatan

---

## 🚀 Cara Menjalankan

### Google Colab (Rekomendasi)
1. Buka notebook: `ML_Project.ipynb`
2. Klik `Runtime` → `Run all`
3. File otomatis ter-generate

### Lokal
```bash
git clone https://github.com/username/diabetes-prediction.git
cd diabetes-prediction
pip install -r requirements.txt
jupyter notebook
```

---

## 📦 Dependencies

- Python 3.8+
- NumPy, Pandas, Matplotlib
- Scikit-learn 1.3+
- TensorFlow 2.13+

Lihat `requirements.txt` untuk detail.

---
