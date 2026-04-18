Project Title: Retail Customer Behavior & Revenue Optimization Analytics
Tech Stack: Python (Pandas), Google Colab, Google BigQuery (Standard SQL), Power BI.

1. Executive Summary
The objective of this project was to analyze a dataset of 3,900+ retail transactions to uncover trends in consumer shopping behavior, evaluate the effectiveness of promotional campaigns, and identify the demographic segments driving the highest revenue. The insights generated aim to optimize marketing strategies, logistics, and customer retention programs.

2. Phase 1: Data Engineering & Preprocessing (Python / Google Colab)
To ensure a robust and scalable ETL (Extract, Transform, Load) pipeline, the raw dataset was ingested via Google Drive into a cloud-based Google Colab environment. Comprehensive data validation and transformation were executed using the Pandas library:

Data Profiling: Conducted initial exploratory analysis (df.info(), df.describe(), isnull()) to evaluate data types and assess statistical distributions.

Advanced Data Imputation: Identified 37 missing values within the review_rating field. Innovated the cleaning process by applying category-specific median imputation, preserving the statistical integrity of localized product evaluations.

Schema Normalization: Standardized all column headers into a programmatic snake_case format to ensure seamless schema compatibility during downstream SQL migration.

Feature Engineering:

Segmented continuous age data into structured, categorical age groups to facilitate demographic trend analysis.

Transformed qualitative textual data (frequency_of_purchase) into a structured numeric format (days) using dictionary mapping, enabling accurate time-based aggregations.

Dimensionality Reduction: Conducted redundancy checks across promotional fields, identified a near-perfect correlation between the discount and promo code columns, and dropped the redundant feature to optimize storage.

The fully transformed DataFrame was authenticated and loaded directly into Google BigQuery.

3. Phase 2: Exploratory Data Analysis (SQL via Google BigQuery)
Advanced SQL querying techniques (including Window Functions, CTEs, and conditional aggregations) were deployed to solve unstructured business problems, specifically extracting:

Revenue & Demographics: Calculated total revenue contributions across different age groups and compared revenue generation between male and female customers.

Promotional ROI: Analyzed purchasing patterns to isolate highly profitable customers who utilized discounts but still maintained a higher-than-average overall spend.

Product & Logistics Performance: Ranked the top 5 products by highest average review rating. Utilized Window Functions (ROW_NUMBER() OVER(PARTITION BY...)) to extract the top 3 most purchased products within every overarching category. Evaluated the commercial impact of delivery speed by comparing average purchase amounts between standard and express shipping.

Customer Retention & Loyalty: Segmented the consumer base into "New," "Returning," and "Loyal" cohorts based on historical purchase counts. Cross-referenced repeat buyers (>5 previous purchases) against active subscription statuses to evaluate the conversion rate of the existing subscription model.

4. Phase 3: Business Intelligence & Visualization (Power BI)
The structured BigQuery tables were connected to Power BI to assemble an interactive dashboard for executive stakeholders. The visual report allows end-users to dynamically filter KPIs (Total Sales, Revenue, Average Rating) across different geographic locations, shipping types, and product categories to instantly spot operational bottlenecks and opportunities.

5. Strategic Business Recommendations

Logistics Investment: Data indicates that express shipping options consistently correlate with higher average purchase amounts, suggesting that subsidizing or promoting faster delivery could unlock higher overall revenue.

Subscription Optimization: SQL analysis revealed a high volume of repeat buyers (>5 purchases) who remain unsubscribed. This highlights a critical opportunity to deploy targeted loyalty marketing (e.g., offering the first month free to users crossing the 5-purchase threshold) to convert active shoppers into recurring revenue streams.
