---
title: "Installing Atheros card"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by telovoyagarcar on 2007-02-09
Ok.. a few days ago i installed Ubuntu from scratch so finally i was able to install a linksys card using ndiswrapper. 

Now i got a Netgear card with the Atheros chip, so i can learn how to crack my access point.

iwconfig keeps listing eth0 as my connection for the wireless card, but i dont know if the new card is automatically binded to eth0 or should i reconfigure everything?
Because scanning does not seem to be working like it did with the linksys.

What are the steps to make this new card work? And should i uninstall the ndiswrapper and remove it from some init.d file that i edited somewhere now i dont remember to make the linksys card work.

or may be is possible to have both drivers installed and i can swap cards without problems...

Im clueless

Thanks!

---

### Post by spd106 on 2007-02-09
There shouldn't be any conflict between the drivers. Since Atheros cards have they're driver included with Ubuntu they don't need to use ndiswrapper and there's no need to find a driver.

Have a look at the [madwifi]("http://madwifi.org") website for details.

---

