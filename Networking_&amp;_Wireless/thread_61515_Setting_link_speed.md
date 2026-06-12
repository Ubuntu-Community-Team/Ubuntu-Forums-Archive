---
title: "Setting link speed"
date: 2005-09-01
forum: Networking &amp; Wireless
---

### Post by Gigalo on 2005-09-01
I have been having some issues with Warty that have been narrowed down to my network link speed (apparently 10baseT, single-duplex). VERY SLOW.

I need to know how to manually set my link speed to 100BaseTX full-duplex.  Please help.

Relevant output from lspci is as follows:

0000:02:01.0 Ethernet controller: Intel Corp. 82547EI Gigabit Ethernet Controller (LOM)

Thank you for any and all assistance in this matter.

Michael

---

### Post by santosh_gr on 2007-12-08
use ethtool for setting speed/duplex.

try ethtool -h or man ethhelp for more info.

in general the command below should help.

ethtool -s eth0 speed 100 duplex full autoneg on

-s change
interface eth0

---

