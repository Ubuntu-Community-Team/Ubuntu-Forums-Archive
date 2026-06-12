---
title: "Intel NIC card issues"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by _-_Goldfinger_-_ on 2007-12-01
I installed ubuntu 7.10 on a compaq laptop(n400c). When I put the install CD in, i was able to log into my network and browse the internet. After installing the OS, when the computer comes on the first time, i can see that my router assigned the computer an ip number. but then the signal drops. now I can not get on the internet anymore. The intel card is

$lspci
00:09.0 Ethernet controller: Intel Corporation 82557/8/9 Ethernet Pro 100 (rev 09)

When it tries to connect the syslog has the following.

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Registering new address record for fe80::2d0:59ff:fe80:77bd on eth0.*.
DHCPOFFER from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPNAK from 192.168.2.1
etc.....

I have tried the NACPI option on startup but no luck. Any help would be appreciated. Thanks.

---

### Post by _-_Goldfinger_-_ on 2007-12-01
Fixed it.

Problem is that i have the Microsoft MN-700 router. There is a bug if your computer name is longer than 15 characters
[http://support.microsoft.com/kb/836514](http://support.microsoft.com/kb/836514)

renamed the computer and it is working now.

---

