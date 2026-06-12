---
title: "ERROR 1045 (28000): Access denied for user 'harsha'@'localhost' (using password: NO)"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by rejuvenate on 2010-05-21
hi, i have installed mysql in ubuntu 9.10 
i think i made some error while installing bcoz it is giving error:
ERROR 1045 (28000): Access denied for user 'harsha'@'localhost' (using password: NO)

when i am trying to run mysql as
shell> mysql

---

### Post by cariboo on 2010-05-21
Use the user name and password you set when you installed mysql, the at the prompt type:

```
mysql -u <user> -p
```

If you didn't set a user name and password type:

```
sudo dpkg-reconfigure mysql-server-5.1
```

substitute your server version for the one in the example above.

---

