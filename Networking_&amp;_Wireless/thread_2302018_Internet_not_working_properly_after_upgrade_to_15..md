---
title: "Internet not working properly after upgrade to 15.10"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by bloff-sites on 2015-11-07
Ever since I upgraded from Kubuntu 15.04 to 15.10, my internet is not working properly.

This manifests in a number of ways: web pages stop responding ("waiting for..." messages hang forever), ftp connections stop responding, and so on.

DNS resolution seems to work properly, and I seem to be able to ping even those servers which are not responding properly.

Any idea of how to debug this to find out why it's happening?

---

### Post by bloff-sites on 2015-11-07
I should add, of course, that the problem actually *is* with linux. I dual boot with windows, and windows has no problem. And my tablet and phone can access the internet with no problem.

---

### Post by bloff-sites on 2015-11-08
The most notable feature is that web browsing is impossible to do properly. There is always some chance the some server will get the "waiting for ..." message, and nowadays websites have so many dependencies on external servers (google APIs etc) that this problem becomes widespread. An image is attached to explain what I mean.

---

### Post by Bucky Ball on 2015-11-08
Perhaps give the output of:

```
sudo lshw -C network
```

Might give us some clues. Please use code tags. See the last link in my output. Thanks.

---

### Post by bloff-sites on 2015-11-08
[FONT=monospace][COLOR=#000000]Interface is plain network cable going to an adsl modem/router. My motherboard is an Intel Z97 (Asus brand). I don't expect this will be an issue with lack of drivers or such. iptables are empty...

Here is the output your requested:

[/COLOR]```
description: Ethernet interface
product: Ethernet Connection (2) I218-V
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 00
serial: 10:c3:7b:9b:ee:0b
size: 100Mbit/s
capacity: 1Gbit/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.5-k duplex=full firmware=0.1-4 ip=192.168.1.1 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:36 memory:f7300000-f731ffff memory:f7338000-f7338fff ioport:f040(size=32)

```[/FONT]

---

### Post by bloff-sites on 2015-11-28
Just to clarify: I have reinstalled 15.10, and I have the exact same problem.

---

