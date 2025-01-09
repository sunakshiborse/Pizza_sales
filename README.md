# Pizza Sales Analysis Project 🍕

## Overview
A comprehensive data analytics project analyzing pizza sales patterns using SQL and Power BI. This project demonstrates the use of advanced SQL queries for data analysis and Power BI for creating interactive visualizations to derive business insights.

## 🎯 Business Problem
To analyze pizza sales data to understand:
- Sales performance and revenue patterns
- Customer ordering behavior
- Product performance metrics
- Temporal trends in orders
- Category and size-based performance analysis

## 🔧 Tools Used
- SQL Server (for data analysis)
- Power BI (for visualization)
- Excel (data storage)

## 📊 Analysis Performed

### Key Performance Indicators (KPIs)
- Total Revenue
- Average Order Value
- Total Pizzas Sold
- Total Orders
- Average Pizzas Per Order

### Sales Analysis
- Daily trend analysis for total orders
- Monthly trend analysis
- Sales percentage by pizza category
- Sales percentage by pizza size
- Best sellers analysis by:
  - Revenue
  - Total Quantity
  - Total Orders

## 💻 SQL Queries

### Revenue Analysis
```sql
SELECT SUM(total_price) AS Total_revenue 
FROM pizza_sales;

SELECT SUM(total_price) / COUNT(DISTINCT order_id) AS avg_order_value 
FROM pizza_sales;
```

### Order Analysis
```sql
SELECT DATENAME(DW, order_date) as order_day, 
       COUNT(DISTINCT order_id) as total_orders
FROM pizza_sales
GROUP BY DATENAME(DW, order_date);

SELECT DATENAME(MONTH, order_date) as Month_Name, 
       COUNT(DISTINCT order_id) as total_orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, order_date) 
ORDER BY total_orders DESC;
```

### Category Performance
```sql
SELECT pizza_category, 
       SUM(total_price) as total_sales, 
       SUM(total_price) * 100 / (SELECT sum(total_price) from pizza_sales) AS PCT
FROM pizza_sales
GROUP BY pizza_category;
```

## 📈 Visualizations
The Power BI dashboard includes:
- Daily and monthly trends charts
- Pizza category distribution
- Size-wise sales analysis
- Top performers analysis
- KPI cards for key metrics

## 🚀 Key Insights
1. Sales Performance Metrics
   - Tracked total revenue and average order value
   - Analyzed total pizza sales and order volumes
   - Calculated average pizzas per order

2. Temporal Patterns
   - Identified peak ordering days
   - Analyzed monthly sales patterns
   - Tracked seasonal trends

3. Product Analysis
   - Evaluated category-wise performance
   - Analyzed size preferences
   - Identified top-performing products

## 📁 Repository Structure
```
└── pizza_sales_analysis/
    ├── data/
    │   └── pizza_sales.xlsx
    ├── sql_queries/
    │   └── analysis_queries.sql
    ├── powerbi/
    │   └── pizza_sales_dashboard.pbix
    └── documentation/
        └── analysis_documentation.md
```

## 🛠️ Setup and Usage
1. Clone the repository
2. Import the pizza sales data into SQL Server
3. Run the SQL queries from `analysis_queries.sql`
4. Open the Power BI dashboard file
5. Refresh the data connections if needed

## 🤝 Contributing
Feel free to fork this project and add your own analyses or improvements. Pull requests are welcome!

## 📝 License
This project is open source and available under the [MIT License](LICENSE).
