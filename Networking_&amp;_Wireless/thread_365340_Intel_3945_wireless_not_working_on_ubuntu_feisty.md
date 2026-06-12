---
title: "Intel 3945 wireless not working on ubuntu feisty"
date: 2007-02-19
forum: Networking &amp; Wireless
---

### Post by drunken_sapo on 2007-02-19
Hi, in my infinite hapyness with Unbuntu, I've installed my 10th ubuntu machine, which is a HP dv9000 pavilion laptop. I've chosen Feisty and everything went fine, all detected and working, except for the wireless card, I have an Intel 3945. The ipw3945 module is loaded, but it behaves in a weird way. It is takes ages to associate to the access point (with WEP) Sometimes, it doesnt get connected at all. If I'm lucky, with some modprobe -r ipw3945 and modprobe -v ipw3945 I'm able to make it work. But most of the time, when i do that, it takes like 20mins to connect. I'm completely lost because I can't see any useful info in the logs. The only related thing are these messages:

Feb 14 15:39:58 upf kernel: [ 809.448000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Feb 14 15:40:01 upf kernel: [ 812.256000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Feb 14 15:40:01 upf kernel: [ 812.256000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Feb 14 15:40:01 upf kernel: [ 812.268000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.3mp
Feb 14 15:40:01 upf kernel: [ 812.268000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
Feb 14 15:40:01 upf kernel: [ 812.268000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Feb 14 15:40:01 upf kernel: [ 812.268000] ipw3945: Detected Intel PRO/Wireless3945ABG Network Connection
Feb 14 15:40:02 upf kernel: [ 814.052000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
Feb 14 15:40:03 upf kernel: [ 814.396000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Feb 14 15:40:10 upf kernel: [ 821.852000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
.
.
.
Feb 14 15:47:11 upf kernel: [ 1237.520000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready

As you can see the first one is when I unloaded the module, when I loaded it i got the "link is not ready" message. After that (where the dots are) I get the "detected geography" message many times.
I've read many post here in the forums and in other places, but I coulnd't came up with a reasonable solution.
Any help would be appreciated.
Thanks in advance.

---

### Post by dphoebus on 2007-03-05
Check this article out.... [http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754]("http://www.ubuntuforums.org/showthread.php?p=2253754#post2253754")

Hope that helped...

---

