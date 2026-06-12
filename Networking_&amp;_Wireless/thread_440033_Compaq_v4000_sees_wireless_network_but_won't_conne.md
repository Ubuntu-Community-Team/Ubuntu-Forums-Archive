---
title: "Compaq v4000 sees wireless network but won't connect"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by Aloir on 2007-05-11
Hi there

I've managed to get my Broadcom 4318 card's light on, and Network Manager is detecting wireless networks in range. However, when attempting to actually connect to the network, it fails, with no IP address assigned. 

i cannot access the internet on the computer itself, so I just have another computer to transfer files over.

I've installed wl_apsta.o and fwcutter. This is what got the light working.

Network is detected (unsecured) with iwlist:

alister@alister-laptop:~$ iwlist eth1 scanning
eth1 Scan completed :
Cell 01 - Address: 00:05:5D:F1:70:CA
ESSID:"WLANGCHX"
Protocol:IEEE 802.11b
Mode:Master
Channel:11
Encryption keyff
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
Quality=70/100 Signal level=-80 dBm Noise level=-73 dBm
Extra: Last beacon: 48ms ago


iwconfig reveals this:

alister@alister-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSID:"WLANGCHX" Nickname:"Broadcom 4318"
Mode:Managed Frequency=2.462 GHz Access Point: 00:05:5D:F1:70:CA 
Bit Rate=11 Mb/s Tx-Power=18 dBm 
RTS thrff Fragment thrff
Link Quality=41/100 Signal level=-80 dBm Noise level=-73 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


ifup:

alister@alister-laptop:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:14:a5:6c:6e:b3
Sending on LPF/eth1/00:14:a5:6c:6e:b3
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


and when I do dhclient:

alister@alister-laptop:~$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0a:e4:df:e4:e0
Sending on LPF/eth0/00:0a:e4:df:e4:e0
Listening on LPF/eth1/00:14:a5:6c:6e:b3
Sending on LPF/eth1/00:14:a5:6c:6e:b3
Sending on Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


My interface file looks like this:


auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid WLANGCHX



auto eth1



I used fwcutter to get the bcm43xx driver to work, which has got me to this point. Can't seem to get an IP address assigned.

Can anyone help please?

---

### Post by Kobalt on 2007-05-11
Apparently the bcm43xx drivers get you a 11Mb/s network and not a 54Mb/s : > 
eth1 IEEE 802.11b/g ESSID:"WLANGCHX" Nickname:"Broadcom 4318"
Mode:Managed Frequency=2.462 GHz Access Point: 00:05:5D:F1:70:CA
**Bit Rate=11 Mb/s** Tx-Power=18 dBm
RTS thrff Fragment thrff
Link Quality=41/100 Signal level=-80 dBm Noise level=-73 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
Is this normal ?
I have a similar card and I never go it working properly with those drivers... I'd suggest you to use the windows drivers and ndiswrapper, following this guide : [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

