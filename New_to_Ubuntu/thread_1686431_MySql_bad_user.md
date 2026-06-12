---
title: "MySql bad user"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by linuxsyst on 2011-02-12
Please Help when i try to make a database in terminal it writes bad user.
could you write a comand or help me pleasw i really need it

---

### Post by linuxsyst on 2011-02-12
Please i need some help

---

### Post by Joeb454 on 2011-02-12
What command are you running in the terminal that gives you the error?

---

### Post by SavageWolf on 2011-02-12
I'm not too skilled in MySql, but maybe you need to be in a specific group?

---

### Post by le_phoceen on 2011-02-12
Hi,

when you connect to the MySQL server, you have to specify the server *host* (for example [FONT=Courier New]localhost[/FONT] if the server has been installed on your computer) and the user (in the MySQL sense) you use to connect. For example if you have installed MySQL yourself on your computer, you should have been asked at some point to choose a *root* password. Then you would connect typing : ```
mysql -h localhost -u root -p
``` The server will ask you to enter the password of the MySQL *root* user.

Here you have a comprehensive and very clear tutorial :
[http://dev.mysql.com/doc/refman/5.5/en/connecting-disconnecting.html](http://dev.mysql.com/doc/refman/5.5/en/connecting-disconnecting.html)

---

### Post by linuxsyst on 2011-02-13
```
root@comps:~# mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

```

---

### Post by linuxsyst on 2011-02-13
No sorry it now works thank you le_phoceen

---

### Post by Joeb454 on 2011-02-13
It's worth noting that if you don't specify a host, it will automatically assume localhost, which means you could just run ```
mysql -u root -p
``` if you're working on the same machine.

---

### Post by linuxsyst on 2011-02-13
Thank you for helping it now works

---

### Post by linuxsyst on 2011-03-19
```
justin@comps:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
```

---

