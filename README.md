# Superstore Sales & Profitability Analysis

**Tools:** Power BI · Power Query · DAX · SQL · Python (Pandas, Matplotlib, scikit-learn)

## Project overview

An end-to-end educational analytics project exploring historical Superstore sales, profitability, customer and regional performance, discounts, and loss-making products. The Power BI report includes a separate page on linear-regression estimates of historical profit. **The estimates are not a forecast of future sales or profit.**

## Questions explored

- How do sales and profit vary by region, product sub-category, and customer segment?
- Which products and sub-categories generate losses?
- How are discount levels associated with profitability?
- How well can a simple linear-regression baseline estimate transaction profit using Sales, Discount, and Quantity?

## Deliverables

- `Superstore_Sales_Profitability_Final.pbix` — interactive multi-page Power BI report
- `Final_Project_Python.ipynb` — exploratory analysis and baseline linear regression

Screenshots of selected report pages will be added to this repository separately.

## Selected findings

The dashboard snapshot shows approximately **$741.7K in sales**, **$18.5K in profit**, **1,764 orders**, and **707 customers** for the report's current filters. On the discount and profitability page, **68 loss-making sales** appear in the 100%-loss-rate product selection, with approximately **$7,710 in aggregate loss**. These are descriptive findings from the report, not causal claims.

The notebook reports a correlation of approximately **−0.484** between Discount and Profit, indicating a moderate negative association in the analyzed sample. Correlation does not by itself establish causation.

## Baseline model

- Algorithm: `sklearn.linear_model.LinearRegression`
- Target: `Profit`
- Features: `Sales`, `Discount`, `Quantity`
- Evaluation: random 80/20 train/test split (`random_state=42`)
- **Test R²:** ~0.188
- **Test MAE:** ~67.07 (in the same units as Profit)

**Limitations:** The model explains only a modest share of test-set profit variation. The monthly chart in Power BI aggregates predictions computed for *historical observations*, including observations used for training; it should not be interpreted as independent out-of-sample forecasting or future-period prediction. A time-based validation design would be required for a genuine forward-looking forecasting claim.

## How to explore

Open the `.pbix` file in Power BI Desktop. Open the notebook in Jupyter or Google Colab. The notebook expects an input CSV named **`final_orders.csv.csv`** (as written in the original notebook); the raw dataset is **not included** in this repository. To reproduce all notebook results, supply an appropriately licensed, non-sensitive version of that file or update the input path in the notebook.

## Data privacy and reproducibility

This repository should only include public or appropriately anonymized source data. The notebook copy has had saved row-level preview outputs removed; please review the PBIX data model and its source paths before publishing.

## Next improvements

- Publish selected dashboard screenshots and a data dictionary.
- Add documented SQL queries and cleaning steps, if original SQL scripts are available.
- Evaluate a stronger model with time-aware validation and error diagnostics.
