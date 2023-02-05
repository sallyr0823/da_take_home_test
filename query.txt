1.Which brand saw the most dollars spent in the month of June?







```

SELECT b.BRAND_CODE, b.NAME, SUM(it.TOTAL_FINAL_PRICE) AS `TOTAL_SALE`

FROM receipts re JOIN receipt_items it ON (re.ID = it.REWARDS_RECEIPT_ID) join brands b USING brand_code

WHERE MONTH(re.PURCHASE_DATE) = 6

GROUP BY b.BRAND_CODE




ORDER BY `TOTAL_SALE` DESC

LIMIT 1;

```

2.Which user spent the most money in the month of August?




```

SELECT u.ID, u.BIRTH_DATE,u.GENDER, u.STATE, SUM(re.TOTAL_SPENT) AS `TOTAL_PURCHASE`

FROM users u JOIN receipts re on u.ID = re.USER_ID




WHERE MONTH(re.PURCHASE_DATE) = 8

GROUP BY u.ID

ORDER BY TOTAL_PURCHASE DESC 

LIMIT 1;

```

3.What user bought the most expensive item?

```

SELECT u.ID, it.TOTAL_FINAL_PRICE / it.QUANTITY_PURCHASED AS SINGLE_PRICE,it.ITEM_INDEX, it.DESCRIPTION

FROM users u JOIN receipts re ON u.ID = re.USER_ID JOIN receipt_items as it ON re.ID =it.REWARDS_RECEIPT_ID




ORDER BY SINGE_PRICE DESC

LIMIT 1;

```

4.What is the name of the most expensive item purchased?




```

SELECT DESCRIPTION,TOTAL_FINAL_PRICE/QUANTITY_PURCHASED AS `SINGLE_PRICE`

FROM receipt_items 

ORDER BY SINGE_PRICE DESC 

LIMIT 1;

```







5.How many users scanned in each month?

```

SELECT YEAR(PURCHASE_DATE) AS `Year`, MONTH(PURCHASE_DATE) AS `MONTH`, COUNT(r.USER_ID) AS `TOTAL_USERS`, COUNT(DISTINCT r.USER_ID) AS `DISTINCT_TOTAL_USERS`

FROM receipts r

GROUP BY YEAR(DATE_SCANNED),MONTH(DATE_SCANNED)




```
