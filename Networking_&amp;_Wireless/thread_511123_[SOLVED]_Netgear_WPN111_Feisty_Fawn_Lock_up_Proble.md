---
title: "[SOLVED] Netgear WPN111 Feisty Fawn Lock up Problem"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by Erwin Criddle on 2007-07-27
Hi, I have been having some trouble with setting up the Netgear WPN111 Wireless Network device.

So far, following this tutorial: - [http://ubuntuforums.org/showthread.php?t=414023]("http://ubuntuforums.org/showthread.php?t=414023")
I have been able to successfully set up the device with WPA-PSK on Ubuntu 6.06 Dapper Drake LTS.

But, I can't set up the device on Ubuntu 7.04 Feisty Fawn.

When I try to setup ndiswrapper I get so far until, the 'sudo modprobe ndiswrapper' command. This command causes the blue light to flash but, Ubuntu then completely locks up.
The only way out is a hard reset.

I have tried updating Ubuntu but that doesn't help.

Any Ideas?

---

### Post by Erwin Criddle on 2007-07-28
**GOOD NEWS!**

_Solved the problem_

From this post: - [http://ubuntuforums.org/showthread.php?t=511051]("http://ubuntuforums.org/showthread.php?t=511051")

I discovered that my feisty fawn had the wrong ndiswrapper version. (Discovered by typing 'ndiswrapper -v')
After replacing with correct ndiswrapper version (from ndiswrapper site) and a reboot, blue light delightfully starting winking at me, and internet access was fully functional. :-D

---

