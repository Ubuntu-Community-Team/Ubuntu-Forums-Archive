---
title: "Newbie needs help with Linkskey wireless adapter"
date: 2006-12-31
forum: Networking &amp; Wireless
---

### Post by Loki123 on 2006-12-31
Hello all. I just installed Ubuntu 6.10 on my HP laptop. I figured out how to install ndiswrapper and the appropriate driver for my wireless adapter, which is a Linkskey LKW-G750 IEE 802.11g. When I type in "ndiswrapper -l" I get "sis163u driver present, hardware present," which I think is a good thing. But I can't connect to the internet. What do I need to do from here? I'm totally new to both Linux and command line, so hopefully you can dumb it down for me as much as possible. Thanks.

---

### Post by Loki123 on 2007-01-03
Bump. Still looking for help.

---

### Post by c.dric on 2007-01-03
Hey loki, 

i did [a search on google]("http://www.google.com/search?hl=en&q=LKW-G750+ndiswrapper&btnG=Google+Search") to find some info on your wifi adapter and i got 2 results; one of the two being a post by you on another board. So information is scarce to say the least :neutral: 

> **Loki123 said:**
> When I type in "ndiswrapper -l" I get "sis163u driver present, hardware present," which I think is a good thing. But I can't connect to the internet. What do I need to do from here? I'm totally new to both Linux and command line, so hopefully you can dumb it down for me as much as possible. Thanks.

"sis163u driver present, hardware present," that's good but only if you have the correct driver for the adapter.

your adapter may be rare but it could be that the chip inside is very common. 

you should check that with the following command : 

**sudo lshw -C network**

and post the lines about your wireless adapter.

---

### Post by Loki123 on 2007-01-04
Here's what I get when I type sudo lshw -C network in Terminal:
> 
*-network DISABLED
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@00:12.0
logical name: eth0
version: 51
serial: 00:c0:9f:0e:a6:44
size: 10 MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociaton=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=half link=no multicast=yes port=MII speed=10MB/s
resources: iport:e800-e8ff iomemory:f0000000-f00000ff irq:11

---

### Post by c.dric on 2007-01-04
oh ... my fault... your adapter is probably listed in the usb section instead of network.
try this one, and look for the lines relative to your usb adapter : 

**sudo lshw**

(make sure the adapter is plugged in when you run the command)

---

### Post by Loki123 on 2007-01-08
c.dric, I appreciate the help, but I've given up on Linux for now. Too much trouble to get it to do basic things. I don't have time to mess with it. I've decided to stick with Windows. Thanks anyways.

---

### Post by philidox on 2007-05-10
I" have come up with a complete guide to setup up your wireless adapter.  It was very easy however i'm using the ubuntu 7.04, so you should take a look its at link [http://ubuntuforums.org/showthread.php?t=437597&highlight=lkw-g750](http://ubuntuforums.org/showthread.php?t=437597&highlight=lkw-g750)

---

