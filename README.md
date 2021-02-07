# SQLdatasets
SQL datasets for SQL query practice and safe keeping



### important notes and trade terminology



\
\
\

## SQL Query-formation Quick Reference

---

#### Clause precedence hierarchy:

Precedence | Clause | function
---------- | ------- | -------
1 | FROM | Choose and join tables to get base data
2 | WHERE | Filters base data
3 | GROUP BY | Aggregates base data
4 | HAVING | Filters aggregated data
5 | SELECT | Returns final data
6 | ORDER BY | Sorts the final data
7 | LIMIT | Limits returned data to a row count


### SELECT statements


#### Terminology
- The output of a SELECT statement is called results or **a result set** as it’s a set of data that results from a query.
- SELECT * - referred to as a  'select star statement'



#### The following is prudent way structuring a select query
Case insensitive so caps is not necessary but multiple lines helps to avoid errors and provide query clarity through conventional and consistent formatting

```
SELECT 
    lastname, 
    firstname, 
    jobtitle
FROM
    employees;
```

Below is an example for a way to create a special column that is the sum result of the multiplication of two other columns
```
SELECT 
    orderNumber, 
    orderlinenumber, 
    quantityOrdered * priceEach
FROM
    orderdetails
ORDER BY 
   quantityOrdered * priceEach DESC;
```

### AS keyword

The below query creates synonyms for SELECT arguments using the AS keyword

```
SELECT
    employeenumber AS id,
    lastname AS last,
    firstname AS first
FROM
    employees
ORDER BY
    last ASC,
    first ASC;
```

### WHERE keyword

WHERE clause in the SELECT statement filters rows from the result set. Besides the SELECT statement, you can use the WHERE clause in the UPDATE or DELETE statement to specify which rows to update or delete. In the SELECT statement, the WHERE clause is evaluated after the FROM clause and before the SELECT clause.

```
SELECT 
    lastname AS last, 
    firstname, 
    jobtitle
FROM
    employees
WHERE
    jobtitle = 'Sales Rep'
ORDER BY
    last ASC;
    
```
WHERE statements can employ the logical operators: 
- AND
- OR
- NOT


Note: in the below query that since WHERE is evaluated before before SELECT using code as a synonym defined in the SELECT statement will return an error as the SELECT statement has not yet been evaluated by the time the WHERE statement is evaluated and so the synonym doesn't yet exist.
```
SELECT
    firstname,
    employeenumber AS id,
    officecode AS code
FROM
    employees
WHERE
    jobtitle = 'sales rep' AND officecode = 1 
ORDER BY 
    id ASC;
```


### ORDER BY - keyword

The below query returns a result set that orders col1 in ascending order and col2 in descending order
Example:
```
SELECT 
col1, col2
FROM
example_table
ORDER BY
col1 asc,
col2 desc;

```
Note: What it's specifically doing is tell the result set to be sorted in terms of ascending order in col1 first and then descending order of col2 afterwards.
In ORDERY BY, the order of which columns are ordered first matters. Note also that the ORDER BY clause is always evaluated after the FROM and SELECT clause.

Example from sample data set 'classicmodels' customer table:
```
SELECT
contactlastname, 
contactfirstname 
FROM 
customers 
ORDER BY 
contactlastname asc, 
contactfirstname desc;

```










