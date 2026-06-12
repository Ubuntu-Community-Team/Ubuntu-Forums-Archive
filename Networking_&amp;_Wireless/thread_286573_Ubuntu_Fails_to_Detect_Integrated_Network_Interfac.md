---
title: "Ubuntu Fails to Detect Integrated Network Interface"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by reggert on 2006-10-27
I installed Ubuntu 6.10 on my (dual-boot with WinXP) desktop machine, but it doesn't seem to detect the integrated LAN interface (which, if I'm not mistaken, is a Marvell Gigabit LAN chipset built into my Gigabyte S-series motherboard).  

The Device Manager lists an "Unknown" Marvell device attached to the PCI-E bus.  However, the Network Admin tool only lists a Modem Network Connection.  ifconfig lists the loopback adapter and an IPv6-over-IPv4 adapter, but does not list any Ethernet interface.

I've tried manually modprobe-ing the sk98lin module, which loads successfully, but it doesn't help.

I tried upgrading to a more recent version of the sk98lin driver, but Marvell's install script doesn't seem to work properly (it complains about a missing .config file).

Everything works fine under Windows (which is how I'm able to post here).

Anyone have any idea of how to fix this?

---

### Post by reggert on 2006-10-27
In case it helps, Windows refers to the device as the following:
Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller

---

