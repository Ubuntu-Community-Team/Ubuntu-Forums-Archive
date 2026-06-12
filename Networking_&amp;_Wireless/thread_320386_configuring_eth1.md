---
title: "configuring eth1"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by Panzerknacker on 2006-12-17
I have been playing with NDISwrapper and after uninstalling the thing, my eth1 which by default I think is used for internet connection sharing is not accessible anymore. When doing ifup I get the following:

> There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.


I believe the eth1 needs to be connected to the eth0 for the wired internet connection sharing, but I have no idea how to configure this and Ubuntu doesn't have a neat way of going back to the defaults as it seems.

This is the info for my local connection, can anyone tell me how to configure this, I can't seem to find a proper guide for doing this.

> eth0      Link encap:Ethernet  HWaddr 00:14:22:B8:AA:CE  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feb8:aace/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21770638 (20.7 MiB)  TX bytes:2452252 (2.3 MiB)
          Interrupt:11 


Thanks for the help

---

### Post by Panzerknacker on 2006-12-17
Anyone that can help me?

---

### Post by scrooge_74 on 2006-12-17
I am no expert here, but ndiswrapper function is to let you use your Windoze drivers for your wireless card in Linux if you can't find Linux driver for it

It seems eth1 is your wireless card and eth0 is your wire lan card.  You should check for the drivers for your wireless.

---

