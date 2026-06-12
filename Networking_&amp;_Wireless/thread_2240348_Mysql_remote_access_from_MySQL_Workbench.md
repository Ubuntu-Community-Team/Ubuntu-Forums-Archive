---
title: "Mysql remote access from MySQL Workbench"
date: 2014-08-19
forum: Networking &amp; Wireless
---

### Post by goodseller2 on 2014-08-19
I have a newly install ubuntu installed the mysql server.

After the basic config, 

I changed the my.cnf file and commented the bind_address

I can start the server and added iptable for 3306.

I also add the privileges to mysql server as follow:

GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'
IDENTIFIED BY 'P@ssw0rd' WITH GRANT OPTION;
FLUSH PRIVILEGES;
exit


However after connected from the mysql workbench, it shows no database. But it seems that have login.

Anyone have faced that or can help me?

Thx!

---

### Post by SeijiSensei on 2014-08-19
What happens if you try to connect with the [native command-line mysql client]("http://dev.mysql.com/doc/refman/5.6/en/connecting.html")?"

---

