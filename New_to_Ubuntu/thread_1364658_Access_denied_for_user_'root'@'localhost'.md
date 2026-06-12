---
title: "Access denied for user 'root'@'localhost'"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by sukhon on 2009-12-26
I just installed ubuntu on a different partition along with Vista

when ever I give this command 
mysql -u root
i get this message
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

---

### Post by albandy on 2009-12-26
mysql -u root -p
then type the password you assigned to mysql root user

---

### Post by sukhon on 2009-12-27
Thank you

> **albandy said:**
> mysql -u root -p
then type the password you assigned to mysql root user

---

