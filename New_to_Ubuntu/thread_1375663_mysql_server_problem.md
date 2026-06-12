---
title: "mysql server problem"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by Ashishkhandelwal on 2010-01-08
When i am running rcmysql start command it is giving me error that 

Starting service MySQL warning: /var/lib/mysql/mysql.sock didn't appear within 30 seconds

and it is not starting sql services.Is there any solution for this problem as i am not able to create new sql users accounts also.

---

### Post by ukripper on 2010-01-08
Check more info in logs:
```
cat /var/log/mysql/mysql.log
```

---

### Post by mistaguy on 2010-09-30
-the problem could that mysql server is not started....you can work  around it using the following options:
(1)use
root@wazzabanga:/home/mistaguy# mysqld -u root
the server should start and so u can now access mysql using
root@wazzabanga:/home/mistaguy# mysql u root p
(2)incase this fails; use the option
mysqld --verbose --help
this will give u options that u can use to start the server. u can use  the following but its risky in that any one can access your server
root@wazzabanga:/home/mistaguy# mysqld --skip-grant-tables
punch in the following to access the mysql
root@wazzabanga:/home/mistaguy# mysql
once mysql is okay by using any of the options above, u can access  phpmysqladmin from your browser as usual provided u provide the okay user  details

---

