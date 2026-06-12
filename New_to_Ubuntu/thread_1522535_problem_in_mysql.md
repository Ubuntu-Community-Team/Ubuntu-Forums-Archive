---
title: "problem in mysql"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by adityagoel123 on 2010-07-02
Hi,

I had installed mysql-server on ubuntu 9.04.

when i tried to run mysqld command in sheell, i am getting the message as :

aditya@aditya-desktop:~$ mysqld
100702 18:43:34 [ERROR] Can't find messagefile '/usr/share/mysql/english/errmsg.sys'
100702 18:43:34 [ERROR] Aborting


Please help:-k

---

### Post by cariboo on 2010-07-02
Does the file exist on your system? If it doesn't, open a terminal and type:

```
sudo dpkg-reconfigure mysql-server-5.1
```

to see if that solves the problem.

---

