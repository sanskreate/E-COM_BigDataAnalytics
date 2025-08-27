# E-commerce Behavior Analysis

A Data Analyst project exploring user behavior across a multi‑category online store during October 2019. The work spans large‑scale data cleaning, scalable processing, exploratory analysis, insight generation, and business recommendations. The dataset contains millions of user interactions, including product views, cart additions, purchases, and more, collected during October 2019.

---

## 📦 Dataset

* **Source:** Kaggle — [Ecommerce behavior data from multi-category store](https://www.kaggle.com/datasets/mkechinov/ecommerce-behavior-data-from-multi-category-store?select=2019-Oct.csv)
* **File Used:** `2019-Oct.csv`
* **Raw Size:** \~5.3 GB (CSV)

> ⚠️ The dataset contains **\~42 million rows**, so scalable processing is essential.

---

## 🗂️ Project Structure

```
.
├── 2019-Oct.csv                     # Raw data (download from Kaggle)
├── combined_data_oct.parquet        # Combined & processed data (Parquet)
├── cleaned_data_oct.parquet/        # Partitioned, cleaned Parquet dataset
├── Ecombehaviour.ipynb              # Jupyter notebook: cleaning, EDA, insights
├── EcomBehaviour.pdf                # PDF form of the ppt
├── EcomBehaviour.pptx               # PPT containing analysis insights and business recommendations
└── README.md                        # This file
```

---

## 🧭 Objectives & Approach

**Objective:** Clean the data, analyze user behavior, extract useful insights, and present findings concisely **with visualizations**.

**Approach:**

1. **Scale with Dask (Pandas‑like API):**

   * Leveraged **lazy evaluation** to defer expensive computations until explicitly executed.
   * Enabled parallel, out‑of‑core processing for the \~42M‑row dataset.
   * 
2. **Efficient Storage with Parquet:**

   * Cleaned data with **Dask**, then saved to **Parquet** (columnar, binary) for faster IO and queries.
   * **Size reduction:** from **\~5.3 GB (CSV)** → **\~2.1 GB (Parquet)**.
   * 
3. **Exploratory Data Analysis (EDA):**

   * Used **Matplotlib** for visual exploration of traffic, engagement, and conversion patterns.
   * Computed revenue, repeat‑purchase metrics, category/brand concentrations, and daily trends.

---

## ⚙️ Environment & Setup

**Requirements:**

* Python 3.x
* Jupyter Notebook
* `pandas`, `numpy`, `pyarrow`
* **`dask[dataframe]`** (for scalable processing)
* `matplotlib` (for charts)

**Install:**

```bash
pip install pandas numpy pyarrow dask[dataframe] matplotlib
```

**Getting Started:**

1. Download `2019-Oct.csv` from Kaggle into the project root.
2. Open `Ecombehaviour.ipynb` and run cells in order.
3. Intermediate/cleaned outputs are written to Parquet for re‑use.

---

## 🧼 Data Cleaning (with Dask)

* Parsed timestamps, normalized categorical fields, and handled missing/invalid values.
* Removed obvious duplicates and invalid events.
* Persisted cleaned data as **partitioned Parquet** for fast, selective reads.

**Why Dask + Parquet?**

* Works on datasets larger than memory.
* Columnar storage improves read performance for analytics workloads.
* Substantial **storage and compute savings** (CSV → Parquet shrink to \~2.1 GB).

---

## 🔎 Exploratory Analysis (EDA)

Key analytical dimensions:

* **Daily revenue** trends and volatility
* **Customer engagement:** events per user, conversion, repeat vs one‑time buyers
* **Category & brand** contributions to revenue
* **Temporal patterns:** mid‑month peaks, late‑month slowdowns

Visualizations (Matplotlib): line charts for daily revenue, bar charts for category/brand revenue, and share plots for buyer segments.

---

## 📈 Key Insights

### Revenue Volatility

* **Daily revenue range:** **\~\$6.0M → \~\$9.7M**
* **Peak window:** **Oct 14–16**, revenues **> \$9.5M**
* **Late‑month dip:** final week declines toward **\$6.0–\$6.5M**

### Buyer Mix & Engagement

* **Repeat purchase rate:** **\~37.9%**
* **One‑time purchasers:** **\~62%** (≈2 out of 3)
* **Average events per user:** **\~14.0**, indicating **moderate‑to‑low** engagement depth per user.

### Category Concentration

* **Electronics & Smartphones** dominate with **\$150M+** revenue.
* **Second‑tier category:** (Unknown/uncategorized) at **\~\$24M**.
* **Market concentration:** Top **2 categories ≈ 70–75%** of total revenue.

### Brand Concentration

* **Apple** leads with **\$100M+** revenue; **Samsung** follows at **\~\$50M**.
* **Top 2 brands ≈ 70–75%** of total revenue → high concentration risk.

> Notes: Figures rounded; derived from October 2019 slice.

---

## 💡 Business Recommendations

### 1) Diversify Revenue Streams

* **Category expansion:** Invest in underperformers (e.g., computers, TVs, clocks, etc.).
* **Reduce dependency:** Target **50–55%** revenue share from Electronics/Smartphones (down from \~70%+).
* **Brand diversification:** Grow partnerships with emerging brands to reduce single‑brand exposure.

### 2) Strengthen Customer Retention

* **Target the \~62% one‑time buyers** with lifecycle journeys and triggered campaigns.
* **Loyalty & rewards:** Aim to lift repeat rate from **\~38% → 45–50%**.
* **Behavioral targeting:** Leverage **\~14 events/user** to score intent and personalize outreach.
* **Road‑map discipline:** Treat retention as **high‑priority** with a clear timeline and ownership.

### 3) Operate to the Calendar

* **Mid‑month peaks:** Align promos and inventory to **Oct 14–16‑style** surges.
* **Late‑month softness:** Counter with price incentives, bundles, or remarketing.

---

## 📓 Usage

* Open `Ecombehaviour.ipynb` for the end‑to‑end workflow.
* Reuse `combined_data_oct.parquet` and `cleaned_data_oct.parquet/` for downstream analytics or ML.

---

## 🧾 License & Attribution

* Data © respective Kaggle contributors; used for analysis and learning purposes.
* Analysis © **Sanskriti Rai**.
