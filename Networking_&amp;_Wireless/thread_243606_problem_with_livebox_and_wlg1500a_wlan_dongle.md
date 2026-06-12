---
title: "problem with livebox and wlg1500a wlan dongle"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by xace on 2006-08-25
Hi,
i have a problem with my ubuntu 6.06 system. i have a wlg 1500 dongle and a "inventel livebox" wireless router. 
so i have installed the windoze drivers with ndiswrapper. The router appears on wifi radar but i can't connect. Some things that i tried to do :

conrad@conrad-desktop:~$ sudo ifconfig wlan0
wlan0     Lien encap:Ethernet  HWaddr 00:03:2F:47:EC:09
          adr inet6: fe80::203:2fff:fe47:ec09/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 b) Octets transmis:13108 (12.8 KiB)

conrad@conrad-desktop:~$ ifconfig eth0 192.168.1.1 net mask 255 255 255
255.0 broadcast 192.196.1.255 up
SIOCSIFADDR: Permission non accordée
SIOCSIFFLAGS: Permission non accordée
net: Erreur de repérage du nom de l'hôte cible
ifconfig : `--help' donne des informations concernant son utilisation.
conrad@conrad-desktop:~$


conrad@conrad-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:03:2f:47:ec:09
Sending on   LPF/wlan0/00:03:2f:47:ec:09
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
conrad@conrad-desktop:~$

...
What can i do ?

Thanks,
Xace

---

### Post by xace on 2006-08-26
essai

---

### Post by xace on 2006-08-26
up

---

### Post by xace on 2006-08-27
up

---

### Post by xace on 2006-08-28
up

---

### Post by xace on 2006-08-29
up

---

