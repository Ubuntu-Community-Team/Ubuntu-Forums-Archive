---
title: "Internet connection still in trouble"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by indrakeerthi on 2006-09-22
i installed ubuntu then configured network to DHCP but it 

still didn't work,then i change the about:config ipv6 to false 

in fire fox still it didn't work i tried ping on ip adresses 

it didn't work
it shows my network card though,my network card is nvidia 

nforce

when i use this command it gave this results

sudo dhclient

poojitha@poojitha-desktop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:13:d3:ce:e5:99
Sending on LPF/eth0/00:13:d3:ce:e5:99
Sending on Socket/fallback
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

### Post by kidders on 2006-09-22
You don't appear to have a DHCP server. Are there any other computers on your network? (I'm wondering how they are configured.)

---

