---
title: "Requests on eth1 is not working, eht0 is working ok"
date: 2016-06-29
forum: Networking &amp; Wireless
---

### Post by texsas on 2016-06-29
Hi,

I have a Ubuntu 14.04 computer with two ethernet cards. Eth0 is default and eth1 is on another subnet, both static.

Eth0 (default):
ip 192.168.2.245
subnet mask: 255.255.255.0
Default route 192.168.2.1
Primary DNS 192.168.2.1

Eth1:
ip 192.168.1.246
subnet mask: 255.255.255.0
Default route 192.168.1.1
Primary DNS 192.168.1.1

My problem is that internet on eth0 works as it should, but on eth1 i need communication on two ports, 13555 and 13556. 
I can't reach theese two ports on eth1, but I can on eth0.

How can I priority these two to eth1?

Regars
texsas

---

### Post by jeremy31 on 2016-06-29
Moved to networking

---

### Post by Fire_Chief on 2016-06-30
This link may shed some insight on how to accomplish this. Normally it's a very bad idea to have two default gateways on a single system. But by adding multiple route tables with a bit of conditional logic, this can be done.
[https://www.thomas-krenn.com/en/wiki/Two_Default_Gateways_on_One_System]("https://www.thomas-krenn.com/en/wiki/Two_Default_Gateways_on_One_System")

Cheers!

---

