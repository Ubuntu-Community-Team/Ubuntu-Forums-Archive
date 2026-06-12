---
title: "TCP Listener"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by rbarr2007 on 2007-11-27
Hi

Coming from a .Net background I have a Multi-threaded TCP listener that monitors TCP traffic from GPS devices that connect via GPRS and puts the position data into a SQL Server Database.

I am now trying to figure out which direction I need to go in order to do the whole thing with with Linux instead.

The devices connect to an IP address and port on TCP and then pass positions. These positions need to be stored in a database for later analysis.

I have used the tcpreen and tcplisten utilities to test, but what is the best way to monitor the ports I select and take the data forwarded to those ports into a MySQL database for example.

I tried figuring this out myself but I feel that I need a push in the right direction. Especially in terms of security, encryption etc.

Any help with which direction I should be looking at would be appreciated.

---

