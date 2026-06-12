---
title: "Wifi on Ubuntu Edgy"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by xabierurra on 2007-03-10
I need some help, because I don't have more ideas on how to get it. I've tried to install a wifi pci card for the last days but it is not working. The problem is I don't have internet access appart from the wifi. 
It is an Asus WL-138G v2, with a Broadcom 4318 chipset. 
I first tried to make it work with ndiswrapper but it was imposible, I tried different versions and I tried to install it from the cd-live with synaptic, but there where incompatibility uses when trying to "make" and "make install". Anyway, I think I got to fix it, I don't remember exactly hoy. 
The problem is that when I try to configure the wifi, I always get this error message: "No DHCPOFFERS received. No working leases in persistent database - sleeping."

I do not know if the problem is with the driver, but I thouhgt that it that was the case the system wouldn't recognize it... Please, tell me what you think the problem is. This is my last console session:

[COLOR="Blue"]xxx-desktop:~$ sudo iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"Jazztel Wireless" Nickname:"Broadcom 4318"
Mode:Master Frequency=2.462 GHz Access Point: 00:03:C9:EA:3A:CE
Bit Rate=11 Mb/s Tx-Power=15 dBm
RTS thr:off Fragment thr:off
Encryption key:off
Link Quality=58/100 Signal level=-57 dBm Noise level=-51 dBm
Rx invalid nwid:0 Rx invalid crypt:36 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.

xxx-desktop:~$ sudo iwlist scan
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

eth1 Scan completed :
Cell 01 - Address: 00:03:C9:EA:3A:CE
ESSID:"Jazztel Wireless"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption key:off
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=100/100 Signal level=-51 dBm
Extra: Last beacon: 472ms ago
Cell 02 - Address: 00:A0:C5:83:EB:4C
ESSID:"cortinaw"
Protocol:IEEE 802.11b
Mode:Master
Channel:11
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Quality=100/100 Signal level=-48 dBm
Extra: Last beacon: 972ms ago
Cell 03 - Address: 00:14:BF:CC:85:08
ESSID:"gn/gb"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=100/100 Signal level=-57 dBm
Extra: Last beacon: 12ms ago
Cell 04 - Address: 00:12:17:6B:22:26
ESSID:"pn/pb"
Protocol:IEEE 802.11bg
Mode:Master
Channel:11
Encryption key:on
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
48 Mb/s; 54 Mb/s
Quality=100/100 Signal level=-56 dBm
Extra: Last beacon: 656ms ago

sit0 Interface doesn't support scanning.

xxx-desktop:~$ sudo iwconfig eth1 channel 11
xxx-desktop:~$ sudo iwconfig eth1 essid "Jazztel Wireless"
xxx-desktop:~$ sudo iwconfig eth1 ap 00:03:C9:EA:3A:CE
xxx-desktop:~$ dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5393
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted
xxx-desktop:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 5393
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:18:f3:e4:51:4a
Sending on LPF/eth1/00:18:f3:e4:51:4a
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
xxx-desktop:~$[/I][/I][/COLOR]

Thank you for your help.

---

### Post by chili555 on 2007-03-10
Please try another command: sudo iwconfig eth1 mode managed followed by sudo dhclient eth1.

This part here: ```
xxx-desktop:~$ sudo iwconfig

eth1 IEEE 802.11b/g ESSID:"Jazztel Wireless" Nickname:"Broadcom 4318"
Mode:**Master** Frequency=2.462 GHz Access Point: 00:03:C9:EA:3A:CE
Bit Rate=11 Mb/s Tx-Power=15 dBm
``` means your card wants to be the access point. You want managed, meaning you will *connect* to an access point.

---

### Post by xabierurra on 2007-03-10
Thank you. I tried with your commands, but the result is the same. I don't know, Im not even sure that the driver is correct. But I think it might be because it is recognised, isn't it?

xabi

---

