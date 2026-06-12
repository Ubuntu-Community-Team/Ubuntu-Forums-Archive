---
title: "creating a MySQL database?"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by master5o1 on 2006-09-06
How do i do this...please tell me :)

---

### Post by az on 2006-09-06
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

You have a choice:

mysql -u root -p

and then enter your mysql root password.  At the mysql prompt enter:

CREATE DATABASE mydatabase;


or use the command line mysqladmin tool:

mysqladmin -u root -p create mydababase

---

### Post by master5o1 on 2006-09-06
thanks

---

