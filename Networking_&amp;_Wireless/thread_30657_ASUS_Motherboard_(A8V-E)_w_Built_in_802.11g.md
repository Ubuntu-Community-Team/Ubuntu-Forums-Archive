---
title: "ASUS Motherboard (A8V-E) w/ Built in 802.11g"
date: 2005-04-29
forum: Networking &amp; Wireless
---

### Post by c1courtney on 2005-04-29
Any support for the built in 802.11g on the ASUS A8V-E Deluxe Mother Board.  I couldn't find much details about the 802.11g on the Mother Board and I've can't find any indication of it being supported.

Basically I'm building an HTPC and intend to use MythTV but like many people I don't want to pull CAT-5 through the walls but have a WiFi Router.  Instead of buying a card I figured I'd buy a MB w/ 802.11g built in and this was the only MB that I found which fit my requirements.

CCourtney

---

### Post by hobnob on 2005-04-29
You're in luck. There's even an [Ubuntu wiki](http://www.ubuntulinux.org/wiki/Rt2500WirelessCardsHowTo/) entry for it. It is based on Ralink's RT2500 chipset, which you can check using the command "lspci". It's always a good starting point when trying to get hardware working.

---

### Post by c1courtney on 2005-04-29
Wow, that was a much quicker response than I expected  :grin: 

I'm glad somebody was aware of what chipset was used (haven't received my MB yet so I couldn't even search the board for chips.)

Thanks,
CCourtney

---

### Post by hobnob on 2005-04-29
No problem. It's a great MB, you shouldn't have any problems with it. I'm using the A8V Deluxe (the non PCI Express version) and am v. pleased.

If you follow the Wiki instructions, take note that there are a two errors:

i) you need to install libqt3-dev not qt3-dev.
ii) run 'depmod' once you've copied the rt2500.ko module over.

Good luck setting it all up!

---

