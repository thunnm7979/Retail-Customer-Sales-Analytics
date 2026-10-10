# Online Retail II: Data Cleaning & Exploratory Analysis

Cleaning and exploratory analysis of **1,067,371 transactions** from a UK-based online gift retailer, covering **Dec 2009 to Dec 2011**. The goal was to turn raw, messy transaction logs into analysis-ready product- and customer-level tables, and to understand sales seasonality.

> 📊 Dashboard: *coming soon*

## Key findings
- **Strong Q4 seasonality.** November and October are the busiest months by invoice count (Nov 2010: 3,669 invoices). Christmas decorations, such as paper chain kits and T-light holders, dominate revenue in those months.
- **Dec 2011 is a partial month.** The data stops on Dec 9, 2011, so the drop in that month is not a real decline.
- **Many rows are not real sales.** Cancellations (`C` invoices), bad-debt adjustments (`A` invoices), Amazon fees, bank charges, manual entries (`M`), postage, and stock write-offs ("damaged", "missing", "thrown away") all distort revenue if they are left in.
- **About 23% of rows are missing a `CustomerID`.** These rows were profiled by country, month, and cancellation rate before deciding how to handle them.

## Cleaning steps
1. Combined the two yearly files (2009–10 and 2010–11).
2. Removed bad-debt adjustments (`StockCode = B`) and Amazon fees.
3. Removed rows with no description and a zero unit price (stock adjustments, not sales).
4. Standardized descriptions to upper case and removed non-product descriptions (damages, test products, vouchers, carriage, etc.).
5. Dropped exact duplicate rows.
6. Built a **product-level table** (1,026,259 rows) and a **customer-level table** (5,878 customers).

## Repository structure
```
├── online_retail_09_10.csv.gz       # data: Dec 2009 – Dec 2010
├── online_retail_10_11.csv.gz       # data: Dec 2010 – Dec 2011
├── online_retail_analysis.ipynb     # analysis notebook
├── requirements.txt
└── README.md
```

## How to run
```bash
pip install -r requirements.txt
jupyter notebook online_retail_analysis.ipynb
```
pandas reads the `.csv.gz` files directly, so there is no need to unzip them.

## Tools
Python · pandas · NumPy · Matplotlib · seaborn · SciPy

## Data source
[Online Retail II](https://archive.ics.uci.edu/dataset/502/online+retail+ii), UCI Machine Learning Repository (Daqing Chen, 2019), licensed CC BY 4.0.
