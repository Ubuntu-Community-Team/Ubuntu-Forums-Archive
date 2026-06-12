---
title: "Intel X710 Network Issues"
date: 2016-09-01
forum: Networking &amp; Wireless
---

### Post by erikk2 on 2016-09-01
[COLOR=#111111][FONT=Ubuntu]I have an issue where I can ping random IP addresses and the ones I can ping are dropping TCP/UDP packets from multiple servers with a Intel X710 10Gb network adapter.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried Ubuntu 14.04 and 16.04 and can repro the issue on both. I've also tried multiple Kernel versions to no avail. I've also tried the latest driver provided by Intel along with upgrading the firmware on the card.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I unplug the X710 and connect a 1Gb adapter, it resolves the issue. I have 10 of these servers and I can repro it on all of them. If I install Debian 8.5 the issue does not persist. It seems to be an issue with Ubuntu and the Intel X710 cards.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas? I haven't found much on forms.[/FONT][/COLOR]

---

