---
title: "problem connection DSL dhcp"
date: 2008-03-20
forum: Networking &amp; Wireless
---

### Post by Portu Maxx on 2008-03-20
Hi well i`m a new user of xubuntu.. yesteday mi internet connection was ok, my computer is connected to a starbrigde 305eu modem, to a ethernet controller ( D-LINK  DFE-530TX) but i have to give my connection to my brother because he needs it for a work... well when i´m going to connect it again, xubuntu doesn´t recognize the dhcp (it configures by itself the first time i was connected) and now the nm-applet only give me the modem configuration... srry for my bad english .... well here is the /etc/network/interfaces file

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0

iface eth0 inet dhcp
when I put this command sudo /etc/init.d/networking restart this what console says 
Reconfiguring network interfaces... eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

lspci command 
01:0d.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 86)

---

