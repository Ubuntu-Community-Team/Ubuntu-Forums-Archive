---
title: "Curious network problem"
date: 2005-09-20
forum: Networking &amp; Wireless
---

### Post by deadlock on 2005-09-20
My network card has started behaving really strangely. Basically, it works as normal for an arbitrary period of time and then I lose network connectivity for no apparent reason. Only a reboot brings it back. I can ping my eth0 IP address, but I can't ping any devices on the network - I get destination unreachable from my eth0 IP. Restarting network in /etc/init.d doesn't make any difference; neither does shutting down the interface manually with ifconfig. Only a reboot seems to bring it back.

The card is a Broadcom 57xx (can't remember the exact model) that works perfectly on Windows XP. Which is a shame, cos I want it to work perfectly under Ubuntu.

Any pointers/help would be appreciated.

deadlock

---

