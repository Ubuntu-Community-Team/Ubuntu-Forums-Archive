---
title: "Can't connect...MySQL"
date: 2008-05-29
forum: Networking &amp; Wireless
---

### Post by gharabed on 2008-05-29
I just set up 8.0 and installed mysql.  I can ping the Ubuntu box from my XP system no problem, but can't log in to mysql, nor can I telnet to my Ubuntu box.  I tried telneting to port 22,23,3306(Mysql) but nothing...it just hangs.  Does Ubuntu have some sort of built in firewall or port mapper that blocks off port communications?

---

### Post by superprash2003 on 2008-05-29
well to access mysql from another pc you need to set permissions.. its normally available in phpmyadmin where you enter the ip of the xp machine to allow access to mysql

---

### Post by gharabed on 2008-05-29
Right...the MySQL side I understand fine...I am actually a database administrator.  It's the networking/Ubuntu side I think I'm having problems with.  I say that because I can ping the Ubuntu box but when I try to log in it just hangs.  If it were a permission problem I would receive an error message.

---

### Post by Monicker on 2008-05-30
> **gharabed said:**
> I just set up 8.0 and installed mysql.  I can ping the Ubuntu box from my XP system no problem, but can't log in to mysql, nor can I telnet to my Ubuntu box.  I tried telneting to port 22,23,3306(Mysql) but nothing...it just hangs.  Does Ubuntu have some sort of built in firewall or port mapper that blocks off port communications?

Ubuntu does not block any ports by default.  Unless you installed something to restrict network access, it will be open.  One thing though, by default mysql only listens for connections from localhost when it is installed, and  will not be able to accept external connections.  If you want to change that, you will need to change the bind-address in /etc/mysql/my.cnf; you can either comment it out, or set it to the actual ip address of the server. Afterwards, restart the mysql service.

---

