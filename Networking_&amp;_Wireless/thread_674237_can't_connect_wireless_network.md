---
title: "can't connect wireless network"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by Pulka on 2008-01-21
hello everyone!

Again, connecting to internet is always a nightmare in Linux.

Have an active wireless connection, but can't seem to be able to connect it. Here's some configuration:

iwconfig

lo no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:"xxxx"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Retry min limit:7 RTS thrff Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

iwlist wlan0 scanning
wlan0 No scan results


sudo ifdown wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5278
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1b:11:bf:63:b6
Sending on LPF/wlan0/00:1b:11:bf:63:b6
Sending on Socket/fallback
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.
cxxx@cxxxx-desktop:~$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)


/etc/network/interfaces
auto lo
iface lo inet loopback


iface wlan0 inet dhcp
wireless-essid xxxx

auto wlan0


does anyone has a clue why i can't connect?

---

