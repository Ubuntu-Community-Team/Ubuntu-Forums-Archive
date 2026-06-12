---
title: "Can't connect to wireless network."
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by Knifa on 2008-06-14
Hi there.

I'm having some trouble trying to connect to my wireless network. I get as far scanning the network, trying to connect and asking for the passkey but then it seems to fail and doesn't finish connecting. I also can't connect with encryption turned off.

My wireless in the laptop the problem is on is some strange integrated USB wireless dongle, an MSI-6865, which has an RT2500 chipset. I would try using ndiswrapper but I have no idea what drivers I would download from the MSI website as it doesn't let you search by model numbers and googling for it only returns the lists of cards with RT2500, etc.

I had a similar problem with Gutsy Gibon. It used to connect (not before doing nothing for about 5 minutes) but then disconnected about 15 minutes later.

Any help would be greatly appreciated. Thanks!

---

### Post by Knifa on 2008-06-14
Disregard. I fixed it.

I managed to find the drivers from the laptop's website (listed under the wrong model, for some reason) and then used them with ndiswrapper.

Hooray!

---

