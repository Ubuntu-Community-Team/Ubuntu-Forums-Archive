---
title: "Help me about install MySQL SERVER"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by zoran035 on 2009-06-02
This is my frst in OS ubuntu. I want to install MySQL and tools for manipulatig databases in server. Help me

---

### Post by Celauran on 2009-06-02
```
sudo aptitude install mysql-server
```

---

### Post by zoran035 on 2009-06-02
Thanks a lot Celauran,  my English not so good, Zoran

---

### Post by zoran035 on 2009-06-02
Next question, name of server, where is it,  how to open in 'emma' ,... MySQL is my first too, but  I have expiriance with SQL SERVER 2005 Thanks again

---

### Post by Celauran on 2009-06-02
I'm not sure what 'emma' is, so I can't help you there. You can use localhost as the server name.

---

### Post by cariboo on 2009-06-02
The name of the server is what you named it during installation, to find the name at the prompt type:

```
hostname
```

I would suggest you install phpmyadmin to administrate mysql, as there is no gui installed. PnpMyadmin is in the repositories. It might ber a good idea to install the mysql documentation which is also in the repositories.

---

### Post by zoran035 on 2009-06-02
Once again, Thanks a lot Celauran, forgot 'emma' , I found another manager  MYSQL Administrator, and I create my first database and firs table and first sproc. 
My INSTANCE conn            = (  User=root, Host = localhst, Socked = /var/run/mysqld.sock )
My SERVER INFORMATION = (  Network Name = localhst, IP = 127.0.0.1 )
My CLIENT  INFORMATION = (  Network Name = ububtu  , IP = 127.0.1.1 ,                                                  OS = Linux 2.6.28-11-generic    ) 
I am VB6 + SQL Express 2oo5 in WIN and want to use Gambas in Linux with MySQL. Is it good idea ?

---

### Post by zoran035 on 2009-06-02
Ops!!!  Cariboo907 Thanks . I did not see another nik

---

