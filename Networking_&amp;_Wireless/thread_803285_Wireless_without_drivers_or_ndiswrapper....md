---
title: "Wireless without drivers or ndiswrapper..."
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by hajk on 2008-05-22
Impossible you say? Well, consider my setup to get a wireless internet connection for my desktop computer:

1. Airport Extreme Base Station (AEBS), from Apple, installed in the meter closet, acting as router and wireless access point -- gives me a draft-N (802.11n) wireless LAN throughout the house.

2. Next to the desktop PC and printer (in my study) an Airport Express (AX), also from Apple, configured to extend the above LAN and to allow Ethernet clients. The PC connected to the AX Ethernet port, the printer to the AX USB port.

The PC gets an IP on the same LAN, the printer is visible on the LAN as an HP JetDirect printer on the AX host. Communications between PC and internet travel via the AX and then wirelessly between it and the AEBS at speeds about 20% less than a wireless connection directly to the AEBS would have (there is some overhead processing in the AX). Since the LAN uses draft-N speeds, which are an order of magnitude higher than "G" speeds, I still get something like 1500 kB/s throughput from my ADSL2+ internet connection. 

That's good enough for me, and it beats having to struggle with wireless adapters (supported yet?), ndiswrapper (where to find a suitable Win driver?) and wpa_supplicant stuff (will it support the adapter?). Of course, the downside is that a person wouldn't need this fine forum section anymore.
:lolflag:

---

### Post by chili555 on 2008-05-22
An entirely credible solution. I hope you have, however, set up WPA between the Extreme and the Express. Your packets are travelling wirelessly and are therefor available to the snoops out there, unless they are encrypted.

It seems to me the Extreme is no more than a wireless ethernet bridge. All the usual suspects, Linksys, Netgear, et al sell them. The Linksys WET54G is an example. A wireless ethernet bridge is a fine solution for those who need wireless but their sanity, too. I used a WET11 for many years back in the days of Mandrake 8, when wireless was very hard.

---

### Post by hajk on 2008-05-22
Yes, I do use WPA2. You're absolutely right that the likes of NetGear and Linksys are selling wireless bridges that do the same kind of thing. The Airport Express has the advantage of being portable, easy to use in a hotel room with only an Ethernet socket.
One more thing, it would seem at first blush that Apple products are expensive, but those wireless bridges mentioned above aren't any cheaper (I checked them out). And finally, that Apple stuff is extremely easy to set up and is cleverly designed.

Disclaimer: not an Apple fanboi here... I don't think OS X is very good, first thing I did is put Linux on my MacBook (Pro); but they do design nice hardware.

---

### Post by chili555 on 2008-05-22
> The Airport Express has the advantage of being portable, easy to use in a hotel room with only an Ethernet socket.
One more thing, it would seem at first blush that Apple products are expensive, but those wireless bridges mentioned above aren't any cheaper (I checked them out). And finally, that Apple stuff is extremely easy to set up and is cleverly designed.I agree entirely. Part of the reason I replied was to get this back to page 1 so people could see that there is a better way to get wireless than the struggles they are experiencing.

---

