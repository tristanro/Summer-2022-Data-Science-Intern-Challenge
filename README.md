# Summer-2022-Data-Science-Intern-Challenge
Data Science Challenge for Shopify
By: Tristan Ro

Question 1 
is included in the ipynb file

Question 2

A) There were 54 orders that were shipped by Speedy Express

Query

SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
WHERE Shippers.ShipperName = 'Speedy Express'

B) The last name of the employee with the most orders was Peacock

Query

SELECT Employees.LastName, MAX(count) AS MaxOrdersByEmployee
FROM (SELECT EmployeeID, COUNT(EmployeeID) AS count FROM Orders GROUP BY EmployeeID)
Orders INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID;

C) The most ordered item from Germany was Gorgonzola Telino

Query 

SELECT p.ProductName, COUNT(p.ProductName) AS `Orders` 
FROM Products AS p 
   INNER JOIN OrderDetails AS d ON p.ProductID = d.ProductID
   INNER JOIN Orders AS s ON d.OrderID = s.OrderID
   INNER JOIN Customers as c ON s.CustomerID = c.CustomerID
WHERE c.Country = 'Germany'
GROUP BY p.ProductName
ORDER BY `Orders` DESC
LIMIT 1;






