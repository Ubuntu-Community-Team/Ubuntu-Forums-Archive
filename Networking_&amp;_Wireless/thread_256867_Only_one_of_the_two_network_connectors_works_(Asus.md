---
title: "Only one of the two network connectors works (Asus P5B)"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by jespdj on 2006-09-13
Hello,

I have a PC with an Intel Core 2 Duo E6600 processor on an Asus P5B Deluxe (with Intel P965 chipset) motherboard. This motherboard has two plugs for Ethernet cables and one WLAN adapter.

I am running Ubuntu 6.06.1 AMD64 on it. Output of uname -a:
```
Linux jesper-desktop 2.6.15-26-amd64-xeon #1 SMP PREEMPT Thu Aug 3 03:58:27 UTC 2006 x86_64 GNU/Linux
```

My problem is that of the two Ethernet connectors, only one works. (I'm not interested in the WLAN adapter right now). In Windows XP I see two Ethernet controllers:

1. Marvell Yukon 88E8056 PCI-E Gigabit Ethernet Controller
2. Marvell Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller

In Ubuntu I see the devices eth0, wlan0 and ppp0 in the networking config. eth0 corresponds to the second controller. Shouldn't I be seeing a second controller (eth1) under Ubuntu?

Are there others who have the same problem with their Asus P5B motherboard; is it a known problem?
What should I do to make Ubuntu see both controllers?

With lspci I see the following two lines for the Ethernet controllers:
```
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd.: Unknown device 4364 (rev 12)
0000:05:04.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

The contents of my /etc/network/interfaces:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp



auto eth0
```

---

### Post by azsd on 2006-10-02
I have an Gigabyte GA-P965-S3 and the network adapter (88E8056) totally can't recongized in ubuntu.

I had added sk98lin/skge in moudle but it seems no help.

I have found a workaroud by Erik of this problem:

[http://kerneltrap.org/node/7135](http://kerneltrap.org/node/7135)

---

### Post by azsd on 2006-10-04
I have used install-8_36.tar.bz2(2006/07/28) instead install-8_40.tar.bz2(2006/03/22) from marvell website and generate patched kernel with sk98lin.ko then It working fine now.

---

