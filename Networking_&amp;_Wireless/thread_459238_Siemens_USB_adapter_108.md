---
title: "Siemens USB adapter 108"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by liberalist on 2007-05-30
I have a question concerning WiFi, she has a Siemens Gigaset USB adapter 108. It connects to a KPN/Telefonica Experia (European brand) access point. Would MadWifi be good or are there any other Linux/Ubuntu drivers?

---

### Post by liberalist on 2007-06-01
This is what I got after running *sudo dhclient*:

```
danielle@DaniellesUbuntu:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:0f:20:28:08:9c
Sending on   LPF/eth0/00:0f:20:28:08:9c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
danielle@DaniellesUbuntu:~$
```

---

