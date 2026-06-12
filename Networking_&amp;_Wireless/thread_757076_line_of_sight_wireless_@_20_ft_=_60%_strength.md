---
title: "line of sight wireless @ 20 ft = 60% strength"
date: 2008-04-16
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-04-16
hardware = Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multipro, coupled with Netgear Rangemax WPN824v2. Using proprietary drivers - tried inf file from install disk - told me I had wrong driver.

Installed madwifi tools. Can't find 'em.

Decided to manually configure. Now have a terminal applet as if I were hardwired. Now nothing else works.

Does this really have to be this hard?

Windows box sits 5 ft away, same config - 98% strength, SNR excellent

---

### Post by prshah on 2008-04-16
> **mandrill said:**
> hardware = Ethernet controller: Atheros Communications, Inc.
Does this really have to be this hard?


Maybe a step by step guide [http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260) will help?

---

### Post by mandrill on 2008-04-16
strange - the very first command in the how-to is "lspci | grep -i wireless" and I get zero response.....................

More  positive results: jim@foobar:~$ ndiswrapper -l
wp311v1.22 : invalid driver!
wpn311 : invalid driver!
wpn311v2 : invalid driver!
wpn311v2.sys : invalid driver!
 When I get the current driver there is no separable inf file, and the guide was written for dual boot, which made things worse.

I DEFY anyone to make this work!!!!

---

