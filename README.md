# 🏋️ Gym Customer Churn Prediction
---

## 📌 Overview

This project uses **predictive analytics** to identify gym members likely to cancel their memberships. Three Decision Tree models — **CHAID**, **CRT**, and **QUEST** — were built in IBM SPSS Statistics on a dataset of **4,000 gym customer records** to predict churn and derive actionable customer retention strategies.

---

## 📂 Dataset

| Field | Description |
|-------|-------------|
| `Churn` | Target variable — 1 if membership cancelled, 0 if retained |
| `Gender` | Customer gender |
| `Near_Location` | Whether customer lives/works near the gym |
| `Partner` | Whether customer is an employee of an associated company |
| `Promo_friends` | Whether customer joined via a friend's referral |
| `Age` | Customer age |
| `Contract_period` | Membership contract duration (1, 6, or 12 months) |
| `Avg_additional_charges_total` | Average additional charges paid |

**Dataset Size:** 4,000 records | **Churn Rate:** 26.5% (1,061 churned out of 4,000)

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| **IBM SPSS Statistics** | Decision tree modeling |
| **CHAID** | Chi-squared Automatic Interaction Detector |
| **CRT** | Classification and Regression Trees |
| **QUEST** | Quick, Unbiased, Efficient Statistical Tree |

---

## 🌳 Models Built

### Model 1 — CHAID (Chi-Squared Automatic Interaction Detector)

```
Path: Analyze → Classify → Tree → Select Dependent & Independent Variables → Method: CHAID
```

| Setting | Value |
|---------|-------|
| Dependent Variable | Churn |
| Independent Variables | Age, Promo_friends, Near_Location, Partner, Gender |
| Max Tree Depth | 3 |
| Min Parent Node Cases | 100 |
| Min Child Node Cases | 50 |
| Total Nodes | 37 |
| Terminal Nodes | 22 |

**Classification Results:**

| Class | Accuracy |
|-------|----------|
| Non-Churners | 90.0% |
| Churners | 42.4% |
| **Overall** | **77.4%** |

**Key Finding:** Age splits first at Node 0, confirming it as the strongest churn predictor. Promo_friends and Near_Location are next significant splits.

---

### Model 2 — CRT (Classification and Regression Trees)

```
Path: Analyze → Classify → Tree → Method: CRT
```

| Setting | Value |
|---------|-------|
| Dependent Variable | Churn |
| Independent Variables | Gender, Near_Location, Partner, Promo_friends, Age, Contract_period, Avg_additional_charges_total |
| Max Tree Depth | 5 |
| Total Nodes | 7 |
| Terminal Nodes | 4 |

**Classification Results:**

| Class | Accuracy |
|-------|----------|
| Non-Churners | 92.9% |
| Churners | 48.8% |
| **Overall** | **81.2%** ✅ Best Model |

**Variable Importance (Normalized):**

| Rank | Variable | Importance |
|------|----------|-----------|
| 1 | Age | 100 (highest) |
| 2 | Contract_period | ~75 |
| 3 | Avg_additional_charges_total | ~20 |
| 4 | Promo_friends | ~15 |
| 5 | Partner | ~10 |

---

### Model 3 — QUEST (Quick, Unbiased, Efficient Statistical Tree)

```
Path: Analyze → Classify → Tree → Method: QUEST
```

| Setting | Value |
|---------|-------|
| Total Nodes | 11 |
| Terminal Nodes | 6 |
| Depth | 4 |

**Classification Results:**

| Class | Accuracy |
|-------|----------|
| Non-Churners | 87.6% |
| Churners | 61.3% |
| **Overall** | **80.6%** |

---

## 📊 Model Comparison

| Model | Overall Accuracy | Non-Churn Accuracy | Churn Accuracy | Risk Estimate |
|-------|-----------------|-------------------|----------------|---------------|
| CHAID | 77.4% | 90.0% | 42.4% | 22.6% |
| CRT | **81.2%** ✅ | **92.9%** | 48.8% | 18.8% |
| QUEST | 80.6% | 87.6% | **61.3%** | 19.4% |

> **Winner: CRT** — Highest overall accuracy (81.2%) and best non-churn prediction (92.9%).  
> **Note:** QUEST performs best at identifying actual churners (61.3%) if churn recall is prioritized.

---

## 🔍 Key Findings

1. **Age** — Strongest predictor. Customers ≤25 years churn significantly more.
2. **Contract Period** — Longer contracts (6–12 months) are strongly linked to retention.
3. **Avg Additional Charges** — Higher extra fees push customers towards cancellation.
4. **Promo_friends** — Referral-joined members are less likely to churn.
5. **Partner** — Corporate-affiliated members show lower churn rates.
6. **Gender** — Least significant but still a valid predictor.

---

## 💡 Retention Strategies (Data-Driven)

### 1. Age-Specific Offers
- **Under 25:** High-energy classes (HIIT, dance, sports)
- **25–33:** Flexible schedules, career-friendly timings
- **Over 33:** Low-impact activities (yoga, pilates, wellness)

### 2. Contract Incentives
- Offer **discounts for 6 or 12-month sign-ups**
- Introduce loyalty rewards for long-term members

### 3. Referral Programs
- Members who join via friends churn less → **reward referrers with free classes or discounts**

### 4. Location Strategy
- Members near the gym churn less → consider **satellite locations** or **transport benefits**

### 5. Additional Charges Management
- High additional charges correlate with churn → **bundle services** or offer predictable pricing plans

---

## 📁 Project Structure

```
gym-churn-prediction/
│
├── data/
│   └── gym_members.csv          # Original dataset
│
├── models/
│   ├── chaid_model.spv          # SPSS output — CHAID tree
│   ├── crt_model.spv            # SPSS output — CRT tree
│   └── quest_model.spv          # SPSS output — QUEST tree
│
├── reports/
│   └── CA2_Churn_Analysis.pdf   # Full analysis report
│
└── README.md
```

---

## 📊 Frequency Distribution Summary

| Variable | Category | Count | % |
|----------|----------|-------|---|
| Churn | Did Not Churn (0) | 2,939 | 73.5% |
| Churn | Churned (1) | 1,061 | 26.5% |
| Gender | Male (0) | 1,959 | 49.0% |
| Gender | Female (1) | 2,041 | 51.0% |
| Promo_friends | No Referral (0) | 2,766 | 69.2% |
| Promo_friends | Referral (1) | 1,234 | 30.9% |
| Contract_period | 1 Month | 2,207 | 55.2% |
| Contract_period | 6 Months | 833 | 20.8% |
| Contract_period | 12 Months | 960 | 24.0% |



---

## 📬 Contact

**Samiksha Barnwal**  
📧 [099samiksha@gmail.com](mailto:099samiksha@gmail.com)  
🐙 [github.com/wildtigress](https://github.com/wildtigress)  
💼 [linkedin.com/in/samiksha4](https://linkedin.com/in/samiksha4)

---

*Built with IBM SPSS Statistics using CHAID, CRT, and QUEST Decision Tree methods*
