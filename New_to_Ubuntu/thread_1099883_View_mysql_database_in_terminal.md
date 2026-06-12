---
title: "View mysql database in terminal ?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by garyed on 2009-03-18
I've finally got a mysql database working but viewing it in the terminal is a problem if the columns are wider than the page. 

```
SELECT * from table; 
```
 
brings up the table contents but it gets so tangled that it's virtually unreadable. 
Is there any way around this other than opening up phmyadmin every time to view the database table?

---

### Post by unutbu on 2009-03-19
```
SELECT * from table \G
```
For each record in the table:
  For each field in the record: 
     The field and its value will be printed on its own line.

---

