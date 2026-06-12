---
title: "RT61 Help"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by clarkyscored on 2008-06-02
Hey there guys,

I just installed Ubuntu and I can't get my Ralink RT61 wireless card to work. The card is detected and the drivers are installed but I have no options to activate or use a wireless card. I have no idea what to do...

This is what happens...

OK.
 
This is what I'm getting.

How do I make it connect to the net?


[IMG]http://i8.photobucket.com/albums/a26/g-drive/linux.jpg[/IMG]

michael@michael-desktop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@0000:00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:19:db:a5:89:85 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s 
  *-network UNCLAIMED 
       description: Network controller 
       product: RT2561/RT61 802.11g PCI 
       vendor: RaLink 
       physical id: 4 
       bus info: pci@0000:04:04.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list 
       configuration: latency=32 


michael@michael-desktop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 
michael@michael-desktop:~$ sudo dhclient if_name 
There is already a pid file /var/run/dhclient.pid with pid 0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

SIOCSIFADDR: No such device 
if_name: ERROR while getting interface flags: No such device 
if_name: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 
michael@michael-desktop:~$ 

michael@michael-desktop:~$

---

### Post by clarkyscored on 2008-06-02
Cmon guys, a little help at least!

---

