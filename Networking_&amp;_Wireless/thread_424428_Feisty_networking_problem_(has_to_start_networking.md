---
title: "Feisty networking problem (has to start networking manually)"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by teleforce on 2007-04-26
Hi all,

I'm using wifi at home and the my last version of Drapper Ubuntu (6.04) have no networking problem.  Unfortunately when I've installed the latest Feisty Ubuntu (7.04) my networking does not start when the system boot.  I've to manually run the '/etc/init.d/networking restart' in order to enable the network.

The 'dmesg' output for the networking looks like the following:

[   18.404000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   18.404000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   18.404000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   20.352000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   86.248000] ADDRCONF(NETDEV_UP): eth1: link is not ready

When I run the script '/etc/init.d/networking restart',  I've failed notices but somehow it works.  The error messages:

* Reconfiguring network interfaces...                                         
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 4354
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:de:89:01
Sending on   LPF/eth1/00:13:02:de:89:01
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:13:02:de:89:01
Sending on   LPF/eth1/00:13:02:de:89:01
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.2 -- renewal in 42727 seconds.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]

My networking interface file '/etc/network/interface' (generated automatically) and the key is concealed for security reason:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid wimax101
wireless-key XXXXXXXXXXXXXXXXXXXXXXXX

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by kooldino on 2007-11-20
Bump - having a similar issue here.  The OS was installed without the network cable plugged in.

---

### Post by Paul41 on 2007-11-20
Mine was installed with the network cable plugged in so I am not sure that that would be your problem.  I never got this fixed in Feisty but when I upgraded to Gutsy it was fixed.

---

### Post by kooldino on 2007-11-20
I'm not sure if that was the issue either, but I figured I'd mention it.

It did seem to cause other issues, such as the online repositories were all disabled by default, and had to be "checked".

---

