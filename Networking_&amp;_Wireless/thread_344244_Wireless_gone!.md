---
title: "Wireless gone!"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by pinkpanther_bc on 2007-01-22
[FONT="Tahoma"][/FONT]
[COLOR="Navy"][/COLOR]
suddenly to day, i lost my wireless! No wireless shows up in Networking...
I currently get internet with my ethernet cable but nothing in wireless....
When i do ndiswrapper -l i get hardware present and driver installed
did uninstall and reinstall ndiswrapper... same problem

Iwconfig

lo        no wireless extensions
etho    no wireless extensions
sit0     no wireless extensions

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:C8:17:0B  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fec8:170b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20515809 (19.5 MiB)  TX bytes:1094050 (1.0 MiB)
          Interrupt:209 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)


BCM43xx is blacklisted
frank@frank-laptop:~$  sudo ifdown wlan0
ifdown: interface wlan0 not configured

frank@frank-laptop:~$ sudo ifup wlan0
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


Need some help to get  wireless back working:confused:

---

### Post by pinkpanther_bc on 2007-01-23
Found the problem, changed the  /etc/network/interfaces
gedit  /etc/network/interfaces
and installed new ndiswrapper
back on wireless connection..

---

### Post by katu on 2007-01-25
What was the problem? I'm trying to install ndiswrapper and I get the same error all the time. What version of ndiswrapper did You use?

---

