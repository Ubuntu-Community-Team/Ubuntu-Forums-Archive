---
title: "Internet connection help please"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by indrakeerthi on 2006-09-21
i installed ubuntu then configured network to DHCP but it still didn't work,then i change the about:config ipv6 to false in fire fox still it didn't work i tried ping on ip adresses it didn't work
it shows my network card though.........what i can do

please help

---

### Post by tomdevries on 2006-09-21
Have you tried dhclient already?
Typ in your terminal:

  sudo dhclient

This will configure your networkdevice via DHCP. Often helps me when I'm not having a networkconnection. Hope it works for you aswell.

---

### Post by indrakeerthi on 2006-09-22
when i use this command it gave this results

sudo dhclient

poojitha@poojitha-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:d3:ce:e5:99
Sending on   LPF/eth0/00:13:d3:ce:e5:99
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
poojitha@poojitha-desktop:~$

---

