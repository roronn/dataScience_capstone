RFM Customer Segmentation Analysis
Introduction
This project performs an RFM (Recency, Frequency, Monetary) analysis to segment customers based on their purchasing behavior. The goal is to identify distinct customer groups and provide targeted marketing recommendations to maximize customer lifetime value (CLV) and optimize campaign effectiveness.
Data Sources
The analysis utilized the following datasets:
* orders_dataset.csv
* order_payments_dataset.csv
* order_items_dataset.csv
Methodology
1. Data Pre-processing and Preparation
* Data Loading & Cleaning: Loaded orders_dataset.csv. All date/timestamp columns were converted to datetime format. Data was filtered to include only orders with an order_status of 'delivered'.
* Monetary Value Calculation: Used order_payments_dataset.csv to calculate the total payment_value for each order_id.
* Data Merging: Merged cleaned orders data with total payment values and order items data to create a consolidated dataset for RFM calculation.
* Missing Value Handling: Rows with any remaining missing values (approx. 24 rows) were dropped, as they were deemed small and did not significantly affect the mean payment value.
* Data Transformation: The Monetary value was normalized using a log transformation (np.log) to handle skewness and prepare the data for better scoring.
2. RFM Calculation and Scoring
The RFM metrics were calculated for each customer using a reference date of 2018-10-18. Each metric was scored from 1 (lowest/worst) to 5 (highest/best) using custom bins.
MetricDefinitionScore LogicBins (Lower/Worse to Higher/Better)Recency (R)Days since last purchase.Lower days = Higher Score (5)[0, 50, 100, 200, 365, inf] with labels [5, 4, 3, 2, 1]Frequency (F)Total number of orders.Higher count = Higher Score (5)[0, 1, 3, 6, 10, inf] with labels [1, 2, 3, 4, 5]Monetary (M)Total value spent.Higher value = Higher Score (5)[0, 1000, 3000, 6000, 10000, inf] with labels [1, 2, 3, 4, 5]3. Customer Segmentation
The combined RFM scores were used to assign customers to distinct segments, including: Champions, Loyal Customers, New Customers, Needs Attention, At Risk, and Lost.
Key Findings & Results
Customer Segment Distribution
The segmentation revealed that the majority of customers fall into the Lost segment.
Segment LabelCustomer CountPercentageLost67,465$\approx 68.7\%$Needs Attention18,441$\approx 18.8\%$New Customers9,875$\approx 10.1\%$At Risk656$\approx 0.7\%$Loyal Customers17$\approx 0.02\%$Average Order Value (AOV) by Segment
* Loyal Customers have the highest average order value (AOV) at R$ 710.45.
* At Risk customers also show a high AOV at R$ 473.67, indicating a significant potential loss if not re-engaged.
* The Needs Attention, New Customers, and Lost segments have comparable AOV values, hovering around R$ 155 to R$ 167.
Marketing Strategy Recommendations
Based on the customer segmentation, the following targeted strategies are recommended:
SegmentInsight/StatusRecommended ActionChampionsOur best, highest-spending customers.Reward: Provide VIP treatment, priority support, and exclusive rewards.Loyal CustomersHigher AOV than the previous year, showing strong engagement.Retention: Implement loyalty rewards and offer exclusive benefits/discounts.Needs AttentionLarge segment of customers not yet high-value.Activation: Use limited-time offers to increase activity and repeat purchase promotions/vouchers.New CustomersLow customer acquisition rate.Acquisition: Develop new promotions specifically designed to attract first-time buyers and increase the customer base.At RiskUsed to buy frequently/high value but haven't purchased recently.Re-engagement: Implement re-engagement strategies like exclusive discounts or early access to sales.LostLargest segment of inactive customers.Win-Back: Launch win-back campaigns and "we miss you" vouchers.
