---
title: "Wireless connection degrades very quickly"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by davidraine on 2008-01-27
I just bought a computer and installed Ubuntu 7.10 (Gutsy) on it, and I'm after a couple of days I'm still having trouble getting my wireless to work.  I don't have a wired connection, and I'm using a Zonet ZEW1630 MIMO wireless card.  With the help of the Community Docs, I downloaded, compiled, and installed the RT61 drivers, and managed to tweak the rt61sta.dat to a state where I can connect to the router over DHCP.

Unfortunately, that apparently isn't enough to get networking running.  Right after I bring the interface up (via "sudo ifup ra0"), the connection is excellent.  However, the card quickly starts dropping more and more packets, such that after a few minutes every packet sent is lost.  At this point the network is unusable, but taking the interface down and bringing it back up again returns the connection to perfect for another minute or so.

 At this point I don't know what's going on and don't know where to look for more information.  Any ideas?

---

### Post by kevdog on 2008-01-27
sounds like you know what you are doing -- are you talking about the serial monkey rt61 drivers? Can you post specifically your lshw -C network statement?  Are you using network manager or other GUI to complete the connection?  RUTILT perhaps?

---

### Post by davidraine on 2008-01-27
Wow, that was quick.  Thanks!

The driver in question is the RT61 driver off of the Ralink Linux support page.  The driver's archive as downloaded is:
2007_1210_RT61_Linux_STA_v1-2.1.2.0.tar.bz2

I've uninstalled Network Manager since I've read that it's buggy and could cause problems, and I've been using the command line and directly modifying the rt61sta.dat file for configuration.

Results of "sudo lshw -C network" while ra0 is up:

```

*-network
description: Wireless interface
product: RT2600 802.11 MIMO
vendor: RaLink
physical id: a
bus info: pci@0000:05:0a.0
logical name: ra0
version: 00
serial: 00:e0:5d:f1:35:39
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt61 ip=192.168.1.107 latency=32 link=yes module=rt61 multicast=yes wireless=RT61 Wireless

```

---

### Post by kevdog on 2008-01-27
Just for kicks can you download and compile the cvs rt61 serial monkey build.  Here is the best link I know:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

Its for the rt73.  Just use some common sense.  Where it states rt73, use rt61, and either uninstall or blacklist the module you just compiled.  Ive heard the serial monkey driver is more reliable.

Ive also heard others claim upgrading the Hardy's developing kernel and using the rt2x00 driver to work also.

---

### Post by davidraine on 2008-01-28
Unfortunately, I can't compile any of serial monkey's drivers -- I tried the latest RT61 beta as well as two hourly dumps.  All of them perform an illegal operation during the make, and I have the latest version of build-essential and linux-headers.  Doesn't look like I'll have much luck tonight.  How stable is Hardy in general?  I'm a bit worried about installing an unstable OS since I'm not as familiar with Linux as I would like to be.

---

