---
title: "WiFi install issues"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by veehexx on 2007-03-18
i got a belkin F5D8010 PCMCIA WiFi card im trying to get working under 6.10, but having some issues.

i got v1.23 of ndiswrapper and drivers for my PCIID code according to the Wiki onthis WiFi card, but still having issues.

tap in ndiswrapper -l, returns
netani          driver installed, hardware present 
utility invalid driver!

no blinky lights on the card. i presume it has something todo with that utility invalid driver bit, but being a complete linux newbie, i aint got a clue where to start for a fix.
help!?!!!utility invalid driver!

ok, fixed it myself :) the guide i was following didnt have the final 'modprobe ndiswrapper' step.

---

