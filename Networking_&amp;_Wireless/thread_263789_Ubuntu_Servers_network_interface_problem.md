---
title: "Ubuntu Servers network interface problem"
date: 2006-09-23
forum: Networking &amp; Wireless
---

### Post by terrrorr on 2006-09-23
I have a mysterious problem and it needs to be fixed. I have installed Ubuntu server to my old Fujitsu-siemems computer. The idea is to use this computer as a DHCP-server. Well... everything works fine untill the network interace stops listening any connection from outside (SSH, DHCP, Telnet). If I ping from the server for example [www.google.com](www.google.com) everything seems to be in order :confused: 

Solution. i'll have to restart the network interface manually by usin /etc/init.d/networking restart command (Well... crontab makes this nowdays). After that everything is in order

Question. What is wrong my servers network !?!?

Specification: Ubuntu 6.06 Server, ISC DHCP3 Server, Static IP-address (naturally) 

P.S. I deeply regret my bad english

---

