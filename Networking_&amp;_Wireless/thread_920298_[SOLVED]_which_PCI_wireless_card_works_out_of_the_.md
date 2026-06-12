---
title: "[SOLVED] which PCI wireless card works out of the box in Australia"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by charonred on 2008-09-15
setting up a home network for a friend, but need to go wireless on 2 PCs (1 old PIII500 and 1 new AMD2.7Ghz).

which PCI card will work out of the box and is available in Australia

Spent about 3 hours trying to get a Linksys Wireless G working in Win XP, and then tried in Hardy - no luck with either

---

### Post by gnusci on 2008-09-15
Well, I don't live in Australia, but I think this info can help you

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Best...

---

### Post by charonred on 2008-09-16
Seems the Linksys WMP54G Wireless-G requires a PC with 500 Mhz + CPU, so this card will be going in the new AMD PC for the eldest boy. I tested it in both XP and Hardy on a Celeron 900Mhz with 384 RAM and it worked flawlessly (just needs NDISwrapper for it to work in Ubuntu), so it should be fine in any newer PC.

The old PC is moving down the line to his younger brother and is a aOpen 500Mhz PIII with 384 RAM. I tried a Netgear W311 PCI card which has a 300Mhz minimum requirement - PC won't post; take card out, PC posts and boots; put card back in, won't post - so it's off to find a cheap brand card that will work. This PC has a clean dual boot install of XP & Hardy, all I added was a 128 MB AGP and Compiz runs fine, though the PC itself runs a little slow in both OS's.

---

### Post by charonred on 2008-09-17
As there were too many confilcts with wireless in the old 500Mhz, I had a 733Mhz PIII lying around, so I dropped the drives etc into that along with the Linksys Wireless-G.

Unbelievably the mainboard in that PC didn't like the XFX 128 MB AGP graphics card, all I could get was 4 bit colour in XP; no matter how many times I tried the CD software, or drivers from Nvidia or XFX, it just looked crap. 

Luckily I had a Chimei 128 MB AGP graphics card lying around, so in that went and everything was then OK.

So after finally getting XP & Hardy with wireless in both and reasonable graphics - 3 days of stuffing around; the damned thing starts freezing up, even in bios it suddenly freezes, no keyboard - both PCs are now heading for kerbside collection.

In future not going to touch any old PCs with anything less than 1 Ghz in it, just not worth the hassle !

Now I can get on with building the new AMD PC; that'll be a piece of cake :)

---

