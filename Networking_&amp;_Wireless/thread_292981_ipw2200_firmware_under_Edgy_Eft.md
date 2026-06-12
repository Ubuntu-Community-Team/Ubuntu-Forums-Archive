---
title: "ipw2200 firmware under Edgy Eft"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by Ponder on 2006-11-04
I'm trying to configure a friend's laptop to use wireless but none of the guides I've seen are any help because they all refer to the hotplug subsystem but that's apparently not available as described under this release.
Initially I was getting an 'drivers need updating' message as a result of 'modprobe ipw2200' so I got and built the ieee80211 and ipw2200 drivers, and the ipw2200 firmware.
Now when I modprobe I get the drivers loaded but no signs of firmware even attempting to load. I've put the firmware files in /lib/firmware/2.6.17-10 generic ( /usr/lib/hotplug/firmware... diesn't exist) but nothing.
What am I missing? Is it something blindingly obvious or is it something more complicated?

Just in case it helps, these are the lines from syslog as a result of 'modprobe ipw2200'

Nov  4 20:25:08 caz-lappy kernel: [17191253.456000] ieee80211_crypt: registered algorithm 'NULL'
Nov  4 20:25:08 caz-lappy kernel: [17191253.464000] ieee80211: 802.11 data/management/control stack, 1.2.15
Nov  4 20:25:08 caz-lappy kernel: [17191253.464000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Nov  4 20:25:08 caz-lappy kernel: [17191253.472000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0mprq
Nov  4 20:25:08 caz-lappy kernel: [17191253.472000] ipw2200: Copyright(c) 2003-2006 Intel Corporation

---

### Post by Ponder on 2006-11-11
I get the most obscure problems. It seems if I can't figure out the problem myself then nobody else has a clue either... either that or nobody's interested.
Well, Windows is back on that laptop now, and will be unless a solution can be found. Still no ideas?

---

### Post by MaraMax on 2006-11-18
I think it's a bug into edgy kernel source ([https://features.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/42387)](https://features.launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/42387)).
U can try compilin' the Torvald's kernel from kernel.org or waitin' an official update from ubuntu
(u r not alone, my laptop ipw2200 is down too!)

---

### Post by Ponder on 2006-11-18
Thanks for that. I think we'll wait, I've never had much luck in compiling a clean kernel, I'm never sure what to include/exclude. I've done it before but never sure if it's a decent build.

---

### Post by MaraMax on 2006-11-18
This is a good kernel compiling howto on Ubuntu:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

if u don't change anything u'll get a kernel with the same modules chioce of ur distro but a fresher and maybe bugless version

---

### Post by Ponder on 2006-11-18
Thanks, looks simple enough. Will try that next time the opportunity presents itself :)

---

### Post by MaraMax on 2006-11-18
No luck for me!
I tried with a new kernel but problem's still alive!!!

---

