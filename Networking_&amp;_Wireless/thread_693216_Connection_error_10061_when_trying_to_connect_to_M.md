---
title: "Connection error 10061 when trying to connect to MySQL from WinXP MySQL administrator"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by paul.hectors on 2008-02-10
When trying to connect with MySQL Administrator from a WinXP computer to a Ubuntu Server 7.10 I get the following error:

"Could not connect to the specified instance.

MySQL Error Number 2003
Can't connect to MySQL server on '192.168.1.124'(100061)

If you want to check the network connection, please click the Ping button"

Status:
[INDENT]I can ping the server.
I can use phpMyAdmin to administrate MySQL
I have a user with permission to connect from any ip address
Entry in iptables for port 3306
I have opened port 3306 on the firewall of the WinXP client
[/INDENT]

I do not know what else to do (I am new to Linux)?

Thank you for your time.

Best regards,

Paul

---

### Post by SteveCT on 2008-02-19
Hi Paul 

I have the same problem, also a new to Linux and using MySQL.
Did you manage to fix your problem.

Thanks
Steve - Cape Town

---

### Post by paul.hectors on 2008-02-21
Hi Steve,

Sorry about the slow reply.

Yes I did get it working by commenting out the 'bind-address' parameter in the MySQL configuration file (/etc/mysql/my.conf).

Best regards,

Paul

---

### Post by SteveCT on 2008-02-21
Thanks Paul.
Got it working thanks got the access to the MySQL service but then had a Password and Username denied. I managed to fix that with a SQL GRANT commant:

Add the sever host you want to connect from in my case my PC name: mypcname.ct
mysql>  GRANT ALL PRIVILEGES ON *.* TO ‘root’@’mypcname.ct’ 

Could use % if you want to connect from any host computer.

Regards
Steve

---

