---
title: "wireless usb choice"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by hockeyhead019 on 2008-10-20
ok guys so i'm looking at a usb adapter for the wireless...

found the linksy compact g wireless usb adapter and it looks fine cost wise and is said to be supported... could anybody confirm this or have any other recommendations... not looking to spend more than $70

thanks

---

### Post by pytheas22 on 2008-10-20
There's a list [here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") of recommended wireless cards that should be mostly accurate.

An important thing to understand, however, is that hardware vendors often change the chipset of wireless cards without changing the name that they're sold under.  Since the chipset is the only part that really matters to Linux, this can cause a lot of confusion, because the Linksys Compact G adapter that you buy may have a completely different chipset from one that someone else buys, even though both products say the exact same thing on the box (I don't know for a fact that the Linksys Compact G comes in different versions; it may not).

So your best bet is to try to figure out which chipset is in the card.  Unfortunately, it doesn't usually say on the box or website, and the only way to know for sure which chipset is in a particular card is to put it in a Linux machine and look at its 'lsusb' or 'lspci' entry.  But if you contact the seller they might be able to tell you the chipset, or at least which revision number it's sold under.  If you know the revision number (e.g. something like 'rev A' or 'rev C1') you can usually google around to figure out which chipset it contains.

Otherwise, make sure they have a friendly return policy so that you can return it if necessary for a more Linux-friendly device.

---

