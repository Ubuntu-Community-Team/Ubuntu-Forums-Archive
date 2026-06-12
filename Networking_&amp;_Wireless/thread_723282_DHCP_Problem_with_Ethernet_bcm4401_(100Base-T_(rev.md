---
title: "DHCP Problem with Ethernet bcm4401 (100Base-T (rev01)) with Dell Inspiron 5100"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by aka_student on 2008-03-13
Hi,

I am having Dell Inspiron 5100 laptop. After hearing good words about Ubuntu from a friend, I installed Ubuntu 7.10 on the laptop. However I am having problem in configuring the Ethernet card using DHCP. The details are as follows.

Ethernet card
---------------------
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

Its using b44 and mii drivers.

Card is recognized as follows.
------------------------------------------------------------------------
ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:0D:56:B6:B4:EE
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:7
----------------------------------------------------------------------------
ethtool -i eth0
driver: b44
version: 1.01
firmware-version:
bus-info: 0000:02:01.0
--------------------------------------------------
ethtool eth0

Settings for eth0:
Supported ports: [ MII ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
Advertised auto-negotiation: Yes
Speed: 10Mb/s (why ?????????)
Duplex: Half (why ?????????)
Port: Twisted Pair
PHYAD: 1
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: g
Wake-on: d
Current message level: 0x000000ff (255)
Link detected: no
-------------------------------------------------------------------------------------------
dhclient eth0

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0d:56:b6:b4:ee
Sending on LPF/eth0/00:0d:56:b6:b4:ee
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
-------------------------------------------------------------------------------------------
dmesg output ((curtailed only for eth0))
[ 28.536898] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b6:b4:ee
[ 147.321243] ADDRCONF(NETDEV_UP): eth0: link is not ready
---------------------------------------------------------------------------------------
cat /var/log/messages (curtailed only for eth0)

Mar 13 13:58:49 aspen kernel: [ 2615.092553] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 14:02:26 aspen kernel: [ 20.986830] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b6:b4:ee
Mar 13 14:02:31 aspen kernel: [ 152.633663] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 14:08:31 aspen kernel: [ 511.368865] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 14:30:57 aspen kernel: [ 1855.268657] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 14:35:15 aspen kernel: [ 28.243333] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b6:b4:ee
Mar 13 14:35:15 aspen kernel: [ 136.404090] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 18:21:25 aspen kernel: [13687.642206] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 18:32:37 aspen kernel: [ 20.952394] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b6:b4:ee
Mar 13 18:32:37 aspen kernel: [ 130.327786] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 22:43:44 aspen kernel: [ 19.728563] eth0: Broadcom 4400 10/100BaseT Ethernet 00:0d:56:b6:b4:ee
Mar 13 22:43:44 aspen kernel: [ 135.125546] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 13 22:43:55 aspen kernel: [ 155.016780] b44: eth0: Link is up at 100 Mbps, full duplex.
Mar 13 22:43:55 aspen kernel: [ 155.016785] b44: eth0: Flow control is off for TX and off for RX.
Mar 13 22:43:55 aspen kernel: [ 155.017236] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar 13 22:43:57 aspen kernel: [ 157.011556] b44: eth0: Link is down.
Mar 13 22:44:12 aspen kernel: [ 171.973090] b44: eth0: Link is up at 100 Mbps, full duplex.
Mar 13 22:44:12 aspen kernel: [ 171.973096] b44: eth0: Flow control is off for TX and off for RX.
Mar 13 22:44:17 aspen kernel: [ 176.960159] b44: eth0: Link is down.
Mar 13 22:45:06 aspen kernel: [ 225.834305] b44: eth0: Link is up at 100 Mbps, full duplex.
Mar 13 22:45:06 aspen kernel: [ 225.834311] b44: eth0: Flow control is off for TX and off for RX.
Mar 13 22:45:08 aspen kernel: [ 227.829090] b44: eth0: Link is down.
Mar 13 22:45:14 aspen kernel: [ 233.813747] b44: eth0: Link is up at 100 Mbps, full duplex.
Mar 13 22:45:14 aspen kernel: [ 233.813753] b44: eth0: Flow control is off for TX and off for RX.
Mar 13 22:45:16 aspen kernel: [ 235.808529] b44: eth0: Link is down.
------------------------------------------------------------------------------------------
So the problem is that the card is not getting the IP address through DHCP. And i do not know why the ethtool output shows Speed: 10Mb/s, Duplex: Half.

However, during installation of Ubuntu 7.10 using Live CD, the ethernet card got the IP addresse correctly. But after full, install, the ethernet card does not get the IP address at all. Even when i try the Live CD now, the card does not get the IP address. I am sure that this problem is not related to DHCP server since I am using other machines on the network and those machines are getting their IP addresses correctly.

I would really appreciate if somebody can help in this regard. I would be happy to provide any other information if needed.

Thanks
Aka

---

### Post by superprash2003 on 2008-03-13
check this [http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html](http://prash-babu.blogspot.com/2008/03/internet-connection-problems-in-ubuntu.html)
  the part where you need to change from roaming mode to DHCP mode may help

---

### Post by aka_student on 2008-03-13
Thanks for your response. However, I had already enabled dhcp option, and set the dns correctly. Still the same problem is occuring.

---

