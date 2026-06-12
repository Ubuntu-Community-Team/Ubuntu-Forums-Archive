---
title: "possible to make Belkin pcmcia card work ?"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by dag0 on 2007-11-07
Just installed ubuntu 7.10 on an old compaq laptop with Belkin Wireless G plus pcmcia card but no luck. The info written on the card: F5D7011. ver. 1323yy
Wireless G Plus Notebook Card. 125 high speed mode.

Or is this a card that never will work in Linux ?

Witch card (USB or pcmcia) do you recomend that work "out of the box" without having some headache :popcorn:  ?


Best Regards
Dag

---

### Post by spd106 on 2007-11-09
This sounds like a Broadcom card. Is there nothing in the Restricted Drivers Manager?

It should at least work with ndiswrapper, [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/)

See the wiki for a list of cards that have been found to work in Ubuntu.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

