---
title: "best way to static IP on wi-fi"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by andb on 2007-02-11
One of the largest problems faced right now with wi-fi, using NetworkManager, is dealing with the need for static addresses on some networks, dynamic on others. Id like some feedback on recommended solutions, as I need to implement something for my wi-fi connections.

Im thinking of having cron call a script every few minutes.  Ill grep the iwconfig output for the ESSID that I've connected to. In the event I find an ESSID that needs a static address Ill plumb a second address to the card, like ifconfig ath0:0 192.168.1.XXX, (ath0 being my wi-fi card) meaning that Ill have the DHCP assigned address and the static one that I needed.

Im going on the assumption that DHCP is functional on all nets (which of me it is), however  I could easily script gateway changes and DNS changes into the procedure.

Anyone see any problems with this solution or see a better way around this?

Thanks for feedback!

---

