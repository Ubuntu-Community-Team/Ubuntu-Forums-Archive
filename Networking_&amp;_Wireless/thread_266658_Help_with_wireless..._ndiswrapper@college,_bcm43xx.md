---
title: "Help with wireless... ndiswrapper@college, bcm43xx@home"
date: 2006-09-27
forum: Networking &amp; Wireless
---

### Post by gironja on 2006-09-27
Hi!

I'm using a BCM4306 on my Laptop with ndiswrapper at college, since BCM43xx does not worked here. It used to work only at home. When I got here, it appeared that the wireless was always switching between access points, and since at home there is only one, it didn't disconnect, but here there are many, so my connection was very unstable, and didn't found a way to solve it.

Then, I tried NDIS (with NDISGTK) thanks to some posts (really don't remember  which and it's link; I download them --a lot of them-- and read them at my home here--at college--, where I don't have internet) and with it, I can get access at college, but not at home. I don't know why, but it is...

I tried to make scripts for switching between both drivers, but nothing... only ndis worked... with bcm it can't found the hardware... Is there's a way to do this "changing"?

At college, I'm getting problems with the IP's. Constantly the connection is going down (not always, but too frequently), and when I do

```

$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPOFFER from 192.168.100.100
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.100.100
bound to 192.168.5.113 -- renewal in 1683 seconds.

```

I think that this disconnecting issues are related to this "renewal" of the IP. Is there any way to maintain it up?

... How can I make BCM43xx work here at college?


Thanks for all your help on this issues!


jNa

---

### Post by trubblemaker on 2006-10-17
what's the speed on your connection?  see if 
```
 iwconfig $myInterface rate 36M
``` provides more stability or
even worse
```
 iwconfig $myInterface rate 36M
```
if all that works for stability I can show you how to right a script that will enable you to do it at runtime, alternatively there is a way to switch drivers on boot, I think using rmmod in a script.  Well I can show you how I'd do it anyways

let me know how it goes

---

