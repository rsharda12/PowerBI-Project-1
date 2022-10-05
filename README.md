# PowerBI-Project-1

This report shows an interactive view of overall sales for a Global Super Store across different demographies which can be further drilled-down based on *year, segment, market*. The dashboard can be viewed by downloading the .pbix file above.

The report uses three tables namely **Orders, People, Returns** imported using a .xlsx file.

## Steps involved in creating the dashboard:

**1) Importing data from Excel**

```
Get Data > Excel > Select the file > Transform
```

> Used the Raw Data file mentioned above to get the data, did transformations on and then loaded to the data model.

**2) Creating custom columns**

- Created "Delivery Days" column under Orders Table (*used to identify avg. delivery days for a product*)

```
Steps: 
 Under Add Column Menu > General > Custom Column
 Named the column as "Delivery Days"
 Formula = [Ship Date] - [Order Date]
```

![image](https://user-images.githubusercontent.com/111697358/194138087-9b8828e2-f1d1-4716-a9a0-7fed25912e23.png)

> Changed the type to Whole Number to show the number of days more correctly

- Created "Year" under Orders Table (used to filter out data in the dashboard using a slicer)

```
Steps: 
 Under Add Column Menu > General > Custom Column
 Named the column as "Year"
 Formula = Date.Year([Ship Date])
```

![image](https://user-images.githubusercontent.com/111697358/194138300-5e56c23c-e63b-4a2b-bcb3-5d64708950da.png)

- Created "Returned Orders" under Returns Table (used to get a count of returned orders)

```
Steps: 
 Under Add Column Menu >  General > Conditional Column
 Named the column as "Returned Orders"
 Formula = If "Returned" = "Yes" then 1 else 0
```

![image](https://user-images.githubusercontent.com/111697358/194137731-69dee71e-658b-423d-8b15-50cfee774f24.png)

**3) Creating relationship between Tables under Model view**

- From Orders(OrderID) To Returns(OrderID)
- Returns(Region) To People(Region)

![TableRelationships - DataModel](https://user-images.githubusercontent.com/111697358/194138705-02db5498-df06-4683-88a9-05b089356a61.png)

**4) Creating visuals for the dashboard**

![Dashboard](https://user-images.githubusercontent.com/111697358/194139004-9cdbe6fe-61e4-43b5-9d06-dc58576292d8.png)

- Year

```
Used a Slicer to display data using Year column under Order Table.
```

> Changed the orientation from Vertical to Horizontal `Format Visual > Slicer Settings > Orientation`.

- Sales by Region

```
Used a Map visual to display Bubble Size (Sales) by Location (Region).
```

- Total Sales, Quantity Sold, Avg. Delivery Days, Returned Orders

```
Used a Card to show above mentioned values based on [Sum]Sales, [Sum]Quantity, [Average]Delivery Days, [Count]Returned Orders.
```

- Sales by Segment, Sales by Market

```
Used a Pie Chart and Donut Chart to visualize Sales based on Segment and Market to help the organisation make better decisions.
```

- Top 10 Customers

```
A stacked column chart showing Top 10 customers by Profit.

Uses a filter on the Customer Name:
Filter Type = Top N, Show Items = Top 10, By Value = Profit.
```

> A company can use this to drive sales by providing these customers special discounts.

- Top 5 Profit Generating Products

```
A Clustered Bar chart showing Top 5 performing products.

Uses a filter on the Product Name:
Filter Type = Top N, Show Items = Top 5, By Value = Profit.
```

> Organisation could decide to increase the sales of these products.

- Top 5 Loss Generating Products

```
A Clustered Bar chart showing Top 5 performing products.

Uses a filter on the Product Name:
Filter Type = Top N, Show Items = Bottom 5, By Value = Profit.
```

> Organisation could reduce the volume of these products.
