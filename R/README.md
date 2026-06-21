# Online Retail Recommendation System

## Project Overview

This project implements a product recommendation system using the Online Retail dataset. The goal is to analyze customer purchase behavior and generate product recommendations using two different approaches:

1. **Item-Based Collaborative Filtering (Cosine Similarity)**
2. **Association Rule Mining (Apriori Algorithm)**

The project also includes data cleaning, exploratory data analysis (EDA), and visualization of recommendation results.

---

## Dataset

**Dataset:** Online Retail Dataset

**Sources:**
- UCI Machine Learning Repository
- Kaggle

The dataset contains transactions from a UK-based online retail store between December 2010 and December 2011.

### Features

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

---
### Note on Data Files

Due to file size limitations, the raw and cleaned transaction data are not included in this repository. To run this project:
1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/carrie1/ecommerce-data) 
2. Place the file in the `data/` folder as `data.csv`.
3. Run the notebook — the cleaning steps will generate `clean_data.csv` automatically.

## Data Cleaning

The following preprocessing steps were applied:

- Removed rows with missing CustomerID values
- Removed rows with missing product descriptions
- Removed returned orders (`Quantity <= 0`)
- Removed transactions with invalid prices (`UnitPrice <= 0`)

### Dataset Size

| Stage | Number of Transactions |
|---------|---------|
| Original Dataset | 541,909 |
| Cleaned Dataset | 397,884 |

---

## Exploratory Data Analysis (EDA)

The analysis included:

- Top-selling products
- Most active customers
- Revenue analysis
- Transaction statistics

### Example Insights

- **WHITE HANGING HEART T-LIGHT HOLDER** was among the most frequently purchased products.
- **12748** was one of the most active customers with more than 200 transactions.
- Revenue was concentrated among a relatively small group of highly popular products.

---

## Method 1: Item-Based Collaborative Filtering

A customer-product interaction matrix was created using purchase quantities.

Cosine Similarity was then used to measure similarity between products based on customer purchasing behavior.

### Example Recommendation

**Input Product**

```text
WHITE HANGING HEART T-LIGHT HOLDER
```

**Recommended Products**

- GIN + TONIC DIET METAL SIGN
- RED HANGING HEART T-LIGHT HOLDER
- WASHROOM METAL SIGN
- LAUNDRY 15C METAL SIGN
- GREEN VINTAGE SPOT BEAKER

These recommendations are generated based on similarity scores calculated from customer purchase patterns.

---

## Method 2: Association Rule Mining

The Apriori algorithm was used to identify frequently co-purchased products.

Because the full dataset contains approximately 4,000 unique products, running Apriori on the entire catalog was computationally expensive for a standard laptop. To make the analysis practical, the algorithm was applied to the **Top 50 best-selling products**.

Association rules were evaluated using:

- Support
- Confidence
- Lift

### Example Rule

**If customer buys**

```text
ALARM CLOCK BAKELIKE GREEN
```

**Then recommend**

```text
ALARM CLOCK BAKELIKE RED
```

| Metric | Value |
|----------|----------|
| Confidence | 0.67 |
| Lift | 10.40 |

A lift value significantly greater than 1 indicates a strong positive association between products. The strongest discovered rule achieved a lift score above 10, suggesting a highly meaningful purchasing relationship.

---

## Visualization

The project includes visualizations for:

- Top-selling products
- Customer activity
- Association rules ranked by Lift score

Example:

- Top 10 Association Rules by Lift

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-Learn
- Mlxtend
- Matplotlib
- Jupyter Notebook

---

## Project Structure

```text
Online-Retail-Recommendation-System/
│
├── data/
│   └── clean_data.csv
│
├── notebooks/
│   └── Online_Retail_Recommendation_System.ipynb
│
├── images/
│   ├── association_rules.png
│   ├── top_products.png
│   └── top_customers.png
│
├── requirements.txt
│
└── README.md
```

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/sugrzcore/Online-Retail-Recommendation-System.git
cd Online-Retail-Recommendation-System
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Open the notebook

Open:

```text
Online_Retail_Recommendation_System.ipynb
```

using Jupyter Notebook, JupyterLab, or VS Code.

### 4. Run all cells

Execute all notebook cells in order.

---

## Key Results

- Cleaned and processed **397,884 retail transactions**.
- Built an Item-Based Collaborative Filtering recommendation engine using Cosine Similarity.
- Generated product recommendations based on customer purchase behavior.
- Applied Apriori algorithm to discover frequent itemsets and association rules.
- Identified strong product relationships with Lift values exceeding **10**.
- Visualized recommendation insights and purchasing patterns.

---

## Results

This project demonstrates two complementary recommendation approaches:

### Collaborative Filtering

Finds products that are frequently purchased by similar groups of customers.

### Market Basket Analysis

Discovers products that are commonly purchased together within the same transaction.

The strongest association rule achieved a Lift score greater than 10, indicating a highly significant relationship between products compared with random co-occurrence.

---

## Future Improvements

- User-Based Collaborative Filtering
- Matrix Factorization (SVD)
- Hybrid Recommendation Systems
- Interactive Web Application using Streamlit
- Recommendation Evaluation Metrics (Precision@K, Recall@K)

---

## Author

**Shirin Abdolahzadeh**

B.Sc. Student in Computer Science  
Islamic Azad University, Tehran Central Branch

GitHub: https://github.com/sugrzcore

[def]: images/association_rules.png