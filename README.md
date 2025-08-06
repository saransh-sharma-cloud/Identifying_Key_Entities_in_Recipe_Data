# 🧠 CRF Model for Entity Recognition in Recipe Data

This project demonstrates how to build and evaluate a Conditional Random Field (CRF) model to identify key entities in recipe ingredient texts — such as **quantity**, **unit**, and **ingredient** — using structured feature engineering and sequence modeling.

---

## 📌 Objective

The objective is to extract structured data from unstructured ingredient strings by labeling each token as:
- `B-QUANTITY` / `I-QUANTITY`
- `B-UNIT` / `I-UNIT`
- `B-INGREDIENT` / `I-INGREDIENT`
- `O` (other)

---

## 📊 Dataset

- Format: JSON
- Each entry contains:
  - `input`: raw ingredient phrase
  - `pos`: corresponding label for each token
- Total entries: ~250+

---

## 🛠️ Steps Performed

### 1. Data Preprocessing
- Tokenized input and aligned with corresponding labels
- Validated each token-label pair for consistency

### 2. Train-Validation Split
- Split data into 70% training and 30% validation
- Printed sample training rows and label statistics

### 3. Exploratory Data Analysis (EDA)
- Visualized label frequency using bar plots
- Identified dominant classes and imbalance

### 4. Feature Engineering
- Designed `word2features()` using:
  - Lowercase form, digit check
  - Quantity regex match
  - Unit/cooking method keyword match
  - Contextual tokens (±1 window)
  - BOS/EOS markers

### 5. CRF Model Training
- Used `sklearn-crfsuite` with:
  - `algorithm='lbfgs'`
  - `c1=0.1`, `c2=0.1`
  - `max_iterations=100`
- Trained without class weights (not supported)

### 6. Model Evaluation
- Evaluated using:
  - `flat_classification_report`
  - Confusion matrix
- Visualized predictions vs ground truth

### 7. Error Analysis
- Analyzed incorrect predictions
- Summarized label-level misclassifications

---

## 📷 Visual Outputs (in report)

- First 5 rows of training data  
- Label distribution bar plot  
- Model training logs  
- Classification report + confusion matrix

All visuals are included in the **PDF report**.

---

## 📄 Final Deliverables

- `CRF_Recipe_Entity_Extraction.ipynb` – full notebook  
- `CRF_Recipe_Entity_Visual_Report.pdf` – final PDF report  
- `ingredient_and_quantity.json` – dataset  


---

## 📚 Dependencies

- Python 3.x
- pandas, numpy, matplotlib, seaborn
- scikit-learn
- sklearn-crfsuite

---

## 📬 Contact

For questions or collaboration, feel free to open an issue or connect via GitHub!
