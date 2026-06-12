---
title: "Cannot Connect Internet Ubuntu 8.10 with NETGEAR usb"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by chickenpatty878 on 2008-11-24
Im fairly new to linux and especialy ubuntu. Im running 8.10 on a Dell GX260 desktop. I used ndiswrapper to install a Netgear WPN111 usb adapter. Network Connections still did not let me use wlan0, so i downloaded wifi Radar and after awhile, it connect with my wireless router. It connected, but i still dont have a connection to the internet and Network Connections still says "no connection". I did  sudo dhclient  
and the results were 
```
hooper@gerald-desktop:~$ sudo dhclient
[sudo] password for hooper: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/pan0/16:ad:87:09:28:6a
Sending on   LPF/pan0/16:ad:87:09:28:6a
Listening on LPF/eth0/00:0b:db:45:83:46
Sending on   LPF/eth0/00:0b:db:45:83:46
Listening on LPF/wlan0/00:1f:33:e1:61:8d
Sending on   LPF/wlan0/00:1f:33:e1:61:8d
Sending on   Socket/fallback
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
:confused:
I have tried some methods after this but none worked, so If anyone knows the steps that are needed after this it would be gretaly appreciated.

---

