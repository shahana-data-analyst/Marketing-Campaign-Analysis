# 🛒 NourishMart: Marketing Campaign Performance & Customer Behaviour Analysis (Python + Google Colab)

## 📌 1. Project Overview / Executive Summary
This project analyzes the customer dataset of **NourishMart**, a retail store, to understand buyer behavior and measure marketing campaign success. Using Python in Google Colab, I built an automated workflow to clean raw customer records, engineer targeted spending groups, track business metrics, and display visual summaries to help managers make data-driven marketing choices.

---

## 🎯 2. Business Problems
Through this analysis, I focused on solving three core business questions for NourishMart:
*   **Campaign Performance:** Which historical marketing campaigns successfully converted customers, and where was the budget wasted?
*   **Customer Spending Value:** How do household income levels directly affect overall sales, and who are our highest-value buyers?
*   **Product Portfolio Dominance:** Which specific product categories generate the highest wallet share and revenue for the store?

---

## 🗄️ 3. Tech Stack & Data Pipeline
*   **Environment:** Google Colab IDE
*   **Libraries:** Pandas (Data manipulation), NumPy (Mathematical logic)
*   **Visualization Tools:** Matplotlib & Seaborn (Statistical charts)
*   **Languages:** Python 3.x

---

## 💻 4. Data Engineering & Python Snippets
To demonstrate my core coding structure, here is the automated custom pipeline I engineered to handle missing records, filter out extreme values, and build a rule-based customer grouping system:

```python
# Advanced Data Cleaning & Imputation Engine
def cleaned_data(df):
    median_income = df["Income"].median()
    df["Income"] = df["Income"].fillna(median_income)
    
    # Removing extreme high income outliers (> 300k) to protect data averages
    df = df[df['Income'] < 300000].reset_index(drop=True)
    return df

# Rule-Based Customer Segmentation Engine
def create_features(df):
    df["Total_Spend"] = (df['MntWines'] + df['MntMeatProducts'] + df['MntFishProducts'] + 
                         df['MntFruits'] + df['MntSweetProducts'] + df['MntGoldProds'])
    
    def find_segment(spend):
        if spend < 500: return 'Low Spender'
        elif spend < 2000: return 'Medium Spender'
        else: return 'High Spender'
        
    df['Customer_Segment'] = df['Total_Spend'].apply(find_segment)
    return df
```

---

## 📊 5. Automated Metrics Dashboard (KPIs)
When my pipeline script runs the executive summary block, it outputs the following baseline health metrics for NourishMart:

| Business Metric | Performance Value | Strategic Meaning |
| :--- | :--- | :--- |
| **Overall Response Rate** | **14.92%** | The baseline conversion success across marketing touches. |
| **Average Customer Spend** | **\$605.74** | The standard monetary value generated per customer profile. |
| **Customer Complaint Rate** | **0.95%** | Exceptionally low friction level, proving high service quality. |


---

## 💡 7. Actionable Business Recommendations
Based on my findings, I proposed these three data-backed actions for NourishMart management:
1.  **Optimize Ad Budget Shifting:** Cut ad budgets from historical campaigns that yielded poor conversion rates and shift resources to replicate the highest-converting campaign setups.
2.  **Launch VIP Reward Schemes:** Build premium retention campaigns specifically for the engineered `High Spender` and `Medium Spender` cohorts, as they represent the highest financial value.
3.  **Cross-Product Incentive Bundling:** Leverage the mass popularity of **Wines and Meats** by creating special bundle discounts that include slower-moving products like Fruits and Sweets.

---

## 🚀 8. How to Run the Project
You can easily replicate this data pipeline in two quick steps:
1.  Upload the dataset file `ifood_df.csv` into your Google Colab runtime storage disk.
2.  Open my notebook file (`.ipynb`), clear all previous inputs, and click **Runtime -> Run All** from the top menu toolbar.
