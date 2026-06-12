---
title: "wired connection dropped out and won't come back"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by Buster95 on 2008-04-10
Although wireless on my laptop has been little more than a wistful dream on my laptop,  I've never had a problem with the wired ethernet connection.
Until today!
The router, a netgear WG834G, is wired to another computer, a desktop unit and it works OK.
On my laptop however, although the connection icon tells me that it's connected, it can't find a web page. When I unplug it, it tells me "The network connection has been disconnected". Plug it back in and it still can't find a web page.

In a terminal, I tried "sudo ifconfig eth0 down" (got the disconnect message) and "sudo ifconfig eth0 up". No result.

I reviewed what documentation I could find about troubleshooting ethernet connections but it didn't lead me anywhere.
Can someone either direct me to a documentation page that will help me troubleshoot further or advise me what to do next?
I'm using 7.04 on the laptop.
Thanks

more:
I've changed the ethernet lead to the laptop - no success
I've plugged it into a different port in the router - no success
I can successfully ping the router from the laptop but when I log onto the router from my desktop and search for "attached devices", the router doesn't "see" the laptop.
Cheers

---

### Post by Buster95 on 2008-04-13
More information:
Do these 2 commands suggest that I actually DO have a wired connection?

I'd appreciate any guidance here.
Thanks

dexter@dexter-laptop:~$ sudo modprobe via-rhine 
dexter@dexter-laptop:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 

wmaster0: unknown hardware address type 801 
wmaster0: unknown hardware address type 801 
Listening on LPF/eth0/00:90:f5:57:ba:bb 
Sending on   LPF/eth0/00:90:f5:57:ba:bb 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPOFFER from 192.168.0.1 
DHCPREQUEST on eth0 to 255.255.255.255 port 67 

dexter@dexter-laptop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: VT6102 [Rhine-II] 
       vendor: VIA Technologies, Inc. 
       physical id: 12 
       bus info: pci@00:12.0 
       logical name: eth0 
       version: 7c 
       serial: 00:90:f5:57:ba:bb 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s 
       resources: ioport:4800-48ff iomemory:cb400400-cb4004ff irq:19 
  *-network 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:15:af:12:7d:b7 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
dexter@dexter-laptop:~$ 
DHCPACK from 192.168.0.1 
bound to 192.168.0.4 -- renewal in 42845 seconds. 
dexter@dexter-laptop:~$

---

