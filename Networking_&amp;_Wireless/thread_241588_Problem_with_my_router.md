---
title: "Problem with my router"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by xace on 2006-08-22
hello ! I cannot connect my inventel livebox wireless router  with my ubuntu.O6. 
heure is the result of dh client:
  conrad@conrad-desktop:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:03:2f:47:ec:09
Sending on   LPF/wlan0/00:03:2f:47:ec:09
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
conrad@conrad-desktop:~$ sudo ifconfig wlan0
wlan0     Lien encap:Ethernet  HWaddr 00:03:2F:47:EC:09
          adr inet6: fe80::203:2fff:fe47:ec09/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:2520 (2.4 KiB)

conrad@conrad-desktop:~$ ping 192.168.1.1.
ping: unknown host 192.168.1.1.
conrad@conrad-desktop:~$
conrad@conrad-desktop:~$ ping 192.168.1.1
connect: Network is unreachabLE                                  i
tHANK YOU; i WAIT yOUR ANSWERS AT MY EMAIL / [email]conrad.michel@wanadoo.fr[/email]

---

