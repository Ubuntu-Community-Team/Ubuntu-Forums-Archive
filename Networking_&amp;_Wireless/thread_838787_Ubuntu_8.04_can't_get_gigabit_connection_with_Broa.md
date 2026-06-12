---
title: "Ubuntu 8.04 can't get gigabit connection with Broadcom bnx2 / Nortel 1010-48 switch"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Sxooter on 2008-06-23
Well, the subject pretty much says it all.

My Nortel switch is set to auto-negotiate.  My IBM thinkpad T-42 connects at gigabit by just plugging it in and bringing it up (it's using an intel ethernet centrino chipset).

ethtool eth0 shows that the broadcom chipset on my dell 2950s supports 1000baseT-Full, but it negotiates to 100 full.  I tried using 

ethtool -s eth0 advertise 0x020 to force it to only do 1000 full.  following that by ethtool -r eth0 results in a down connection.

I also tried forcing the setting to 1000 on the nortel switch, and that also results in no connection.

Forcing autoneg off and setting the speed to 1000 also results in a dead link.

Anybody got any ideas?

---

