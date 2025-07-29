Tools Used:
- SQL (MySQL workbench)
- Power BI
- ETL (Extract, Transform, Load)
- Excel / CSV Data

# Project Description:
This project involves analyzing a retail sales dataset using SQL and Power BI. The process includes:
- Cleaning raw data with SQL scripts
- Performing data modeling and transformation
- Loading cleaned data into Power BI
- Creating dynamic dashboards with charts and KPIs

#Features:
- Revenue & profit tracking
- Product/customer performance
- year-month trend analysis
- Region-wise sales metrics

- SQL Query
-  Show total number of customers

    `SELECT count(*) FROM customers;`

1. Show transactions for Chennai market  Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

1. Show distrinct product 

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

1. Show transactions where currency USD

    `SELECT * from transactions where currency="USD"`

1. Show transactions in year

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

1. Show total revenue

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
1. Show total revenue 

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date
   where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

   POWER BI

   = Source{[Schema="sales",Item="customers"]}[Data]
   = Source{[Schema="sales",Item="date"]}[Data]
   = Table.SelectRows(sales_markets, each ([zone] <> ""))
   = Table.AddColumn(#"Filtered Rows1", "norm_sales_currency", each if [currency] = "USD#(cr)" then [sales_amount]*86.72 else [sales_amount])
   = Table.TransformColumnTypes(Source,{{"Column1", type text}})
