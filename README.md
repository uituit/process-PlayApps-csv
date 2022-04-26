# Processing Google Play Earning Report (PlayApps_yyyymm.csv) with Pandas

A sample of the PlayApps_yyyymm.csv is displayed below:

| Description | Transaction Date | Transaction Time | Tax Type | Transaction Type | Refund Type | Product Title | Product id | Product Type | Sku Id | Hardware | Buyer Country | Buyer State | Buyer Postal Code | Buyer Currency | Amount (Buyer Currency) | Currency Conversion Rate | Merchant Currency | Amount (Merchant Currency) | Base Plan ID | Offer ID |
| ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- | ----------- |
| GPA.0000-0000-0000-00000| Mar 1, 2022 | 3:11:51 AM PST |  | Charge |  | Your product title 1 | your.product.id1 | 1 | sku_id1 |  | HK | - |  | HKD | 8.00 | 1.000000 | HKD | 8.00 |  | 
| GPA.0000-0000-0000-00000 | Mar 1, 2022 | 3:11:51 AM PST |  | Google fee |  | Your product title 1| your.product.id1 | 1 | sku_id1 |  | HK | - |  | HKD | -2.4 | 1.000000 | HKD | -2.4 |  | 
| GPA.0000-0000-0000-00001..0 | Mar 1, 2022 | 5:12:55 PM PST |  | Charge |  | Your subscription product | your.subscription.product.id | 1 | subscriptionProduct.sku |  | TH |  | 00000 | THB | 38 | 0.238720 | HKD | 9.07 |  | 
| GPA.0000-0000-0000-00001..0 | Mar 1, 2022 | 5:12:55 PM PST |  | Google fee |  | Your subscription product | your.subscription.product.id | 1 | subscriptionProduct.sku |  | TH |  | 00000 | THB | -5.7 | 0.238720 | HKD | -1.36 |  | 
| GPA.0000-0000-0000-00002..2 | Mar 2, 2022 | 11:51:15 AM PST |  | Charge |  | Your subscription product | your.subscription.product.id | 1 | subscriptionProduct.sku |  | US | CA | 00000 | USD | 1 | 7.813400 | HKD | 7.813 |  | 
| GPA.0000-0000-0000-00002..2 | Mar 2, 2022 | 11:51:15 AM PST |  | Google fee |  | Your subscription product | your.subscription.product.id | 1 | subscriptionProduct.sku |  | US | CA | 00000 | USD | -0.15 | 7.813400 | HKD | -1.17 |  | 
| GPA.0000-0000-0000-00007 | Mar 4, 2022 | 9:57:29 AM PST |  | Charge |  | Your product title 2 | your.product.id2 | 1 | sku_id2 | a71x | HK | 九龍 |  | HKD | 58.00 | 1.000000 | HKD | 58.00 |  | 
| GPA.0000-0000-0000-00007 | Mar 4, 2022 | 9:57:29 AM PST |  | Google fee |  | Your product title 2 | your.product.id2 | 1 | sku_id2 | a71x | HK | 九龍 |  | HKD | -17.40 | 1.000000 | HKD | -74.40 |  | 
| GPA.0000-0000-0000-00007 | Mar 7, 2022 | 10:26:46 PM PST |  | Charge refund | Full | Your product title 2 | your.product.id2 | 1 | sku_id2 | a71x | HK | 九龍 |  | HKD | -248.00 | 1.000000 | HKD | -58.00 |  | 
| GPA.0000-0000-0000-00007 | Mar 7, 2022 | 10:26:46 PM PST |  | Google fee refund | Full | Your product title 2 | your.product.id2 | 1 | sku_id2 | a71x | HK | 九龍 |  | HKD | 74.40 | 1.000000 | HKD | 17.40 |  | 

## Observations
1. The table lists all transaction records, it is hard to quickly find out how many units were sold in a month;
2. For Subscription product, a prefix "..0", "..1", "..2", ... can be observed; It shows how many times the subscription was renewed; It is an important indicator to deduce the "Retention Rate" of the app, but it's not easy to read from the table;

## Aims
1. Insert number of units at the end of the table
2. Update the 'sku_id' to indicate subscriptions being renewed after 1-year
3. Export the table

*Note: If sales report from Apple and Google need to be processed together, the SKU needs to be standardize.*
