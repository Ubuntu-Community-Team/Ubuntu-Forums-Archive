---
title: "Can't get my network speed to 1000"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by HBorough on 2007-01-27
I have Yukon Marvell chipset with Gigabit switch. When I checked using ethtool it showed speed only 100 eventhough it recognized that the nic is capable of gigabit.

I tried to use ethtool to set the speed to 1000 but since it is set to autonegotiate it reverted (or never set) back to 100.  If I set autoneg to off and set speed to 1000, the whole ethernet connection is dead.

The computer and swith worked with gigabit speed in Windows. I'm now running on 6.10 version for server.

Thank you for the help in advance...

---

