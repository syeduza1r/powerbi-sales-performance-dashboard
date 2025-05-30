# Sales Performance Dashboard using Power BI

## 📌 Project Overview

This Power BI project delivers an interactive dashboard and actionable KPI insights based on cleaned and refined transactional sales data. It covers the full analytics cycle—from data preparation to DAX measures and visual storytelling—to drive smarter business decisions.

---

## 📁 Files Included
- `Dashboard.pbix` – Full Power BI file

## 🛠️ 1. Data Cleaning & Preparation (Power Query Editor)

### ✅ Step 1: Remove Blank Records  
- Removed rows with missing `CustomerID` or `InvoiceNo`.  
- **Why:** These fields are critical identifiers and necessary for accurate analysis.

### ✅ Step 2: Remove Duplicates  
- Removed duplicate rows based on `InvoiceNo` and `StockCode`.  
- **Why:** Ensures accurate line item and sales count.

### ✅ Step 3: Filter Quantity  
- Kept only rows where `Quantity > 0`.  
- **Why:** Focus on valid sales; negative/zero often indicates returns.

### ✅ Step 4: Handle Invoice Date Errors  
- Replaced error values in `InvoiceDate` with nulls.  
- **Why:** Prevents issues in time-based calculations.

### ✅ Step 5: Filter Country  
- Removed rows with missing/unspecified `Country`.  
- **Why:** Ensures accuracy in regional insights.

---

## 📊 2. DAX Measures & Calculations

- **Total Sales**  
  `Total Sales = SUMX('SalesData', 'SalesData'[Quantity] * 'SalesData'[UnitPrice])`

- **Sales per Customer**  
  `Sales per Customer = DIVIDE([Total Sales], DISTINCTCOUNT(SalesData[CustomerID]), 0)`

- **Total Quantity**  
  `Total Quantity = SUM('SalesData'[Quantity])`

- **Total Orders**  
  `Total Orders = DISTINCTCOUNT('SalesData'[InvoiceNo])`

- **Total Customers**  
  `Total Customers = DISTINCTCOUNT('SalesData'[CustomerID])`

- **Monthly Sales**  
  `Monthly Sales = CALCULATE([Total Sales], DATESMTD('Date'[Date]))`

- **Average Order Value**  
  `Average Order Value = DIVIDE([Total Sales], [Total Orders])`

---

## 🧩 3. Data Model Structure

Assuming a **star schema**:

- **Fact Table:** `SalesData` (InvoiceNo, CustomerID, Quantity, UnitPrice, InvoiceDate, etc.)
- **Dimension Tables:**
  - `Date`
  - `Customer` (optional)
  - `Product` (optional via StockCode)

---

## 📈 4. Dashboard Design

### ✅ KPI Cards  
- Total Sales  
- Total Orders  
- Total Customers  
- Average Order Value  

### ✅ Time-Based Visuals  
- Line/Area Chart: Monthly Sales Trends  
- Bar Chart: Sales/Quantity by Month or Country  

### ✅ Category-Based Charts  
- Donut/Pie Chart: Sales by Country or Product Category  
- Stacked Bar Chart: Sales by Product or Customer Segment  

### ✅ Filters & Slicers  
- Country  
- Date Range  
- Customer ID  
- Product Code (StockCode)

---

## 💡 5. Business Insights & Recommendations

### 📌 Marketing Insights  
- UK dominates sales and customer count  
- Seasonal sales spikes suggest campaign-based trends  
- **Recommendations:**
  - Expand to Germany, France, and Japan  
  - Launch loyalty programs  
  - Study and replicate successful marketing periods  
  - Promote in low-activity countries

### 📌 Product Insights  
- Few SKUs drive most revenue  
- **Recommendations:**
  - Bundle bestsellers  
  - Phase out underperformers  
  - Add variants to popular products  
  - Use top SKUs in cross-sell strategies

### 📌 Customer Analytics  
- High-value customers concentrated in UK  
- **Recommendations:**
  - Reward top spenders  
  - Target low-engagement regions  
  - Customize regional promotions

### 📌 Order & Invoice Analysis  
- Q3 shows peak order activity  
- Average order value: 199.95  
- **Recommendations:**
  - Launch promotions in Q3  
  - Encourage bulk purchases  
  - Balance monthly sales via consistent outreach

---
