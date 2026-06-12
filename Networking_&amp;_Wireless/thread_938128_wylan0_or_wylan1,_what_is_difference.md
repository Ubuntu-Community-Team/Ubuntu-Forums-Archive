---
title: "wylan0 or wylan1, what is difference?"
date: 2008-10-04
forum: Networking &amp; Wireless
---

### Post by Rodney2 on 2008-10-04
I am still trying to understand when and why either wylan0 or wylan1 is used.  When I type sudo dhclient wlan0 I get
rodney@rodney-desktop:~$ sudo dhclient wlan0
[sudo] password for rodney: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ 
 and when I do the same for wylan1 I get

rodney@rodney-desktop:~$ sudo dhclient wylan1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wylan1: ERROR while getting interface flags: No such device
wylan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ 

Now, the above is without the USB card pluged into the port.  The following with the USB card also plugged in.

rodney@rodney-desktop:~$ sudo dhclient wylan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wylan0: ERROR while getting interface flags: No such device
wylan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ sudo dhclient wylan1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wylan1: ERROR while getting interface flags: No such device
wylan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ 

is is with only the wired ethernet, when I try to use the wireless USB Zonet unit, I get 
rodney@rodney-desktop:~$ sudo dhclient wylan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wylan0: ERROR while getting interface flags: No such device
wylan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ sudo dhclient wylan1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wylan1: ERROR while getting interface flags: No such device
wylan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
rodney@rodney-desktop:~$ 

I am trying to connect to the internet with the wireless card and am having trouble consistantly connecting.  I can always get on with the wired connection.  The following is also done with the USB installed.

rodney@rodney-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: eth0
       version: 10
       serial: 00:14:6c:c1:a0:30
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.2.5 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:fd:07:91:aa:38
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RT73 WLAN
rodney@rodney-desktop:~$

---

