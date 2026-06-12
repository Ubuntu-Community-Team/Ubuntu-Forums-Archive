---
title: "Looking for wireless card"
date: 2005-05-21
forum: Networking &amp; Wireless
---

### Post by MBro on 2005-05-21
I'll be stopping by circuit city and best buy tomorrow for a wireless card.  What kinds would you recommend for the simplest setup on my ubuntu box?  Anything up to 802.11g I can use.

---

### Post by Doctor Ninja on 2005-05-21
I got a DWL-G630 and a DWL-G650, and they've served me quite well. The G650 uses the Atheros chipset, which, by my understanding, is quite cooperative with many open-source software. The G630 has also worked with zero fuss, though, and I've no complaints about either. They can both be had for $20 from various online sources.

---

### Post by poofyhairguy on 2005-05-21
[QUOTE=MBro]I'll be stopping by circuit city and best buy tomorrow for a wireless card.  What kinds would you recommend for the simplest setup on my ubuntu box?  Anything up to 802.11g I can use.[/QUOTE]


Umm....Damn....Most 802.11g cards won't work without some fighting. 

These are the only ones I know of that are plug and play:

[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)


Be sure to shop by MODEL NUMBER, not name. Sometimes the name of the card might be the same for many different chips (most won't work). The model number is the only sure way (open the box in the store if you have to).

If you can't find one of these....buy one of the internet....or search this forum for ndiswrapper.

EDIT: Atheros cards work well to. I have one.

---

### Post by kris kincaid on 2005-05-22
I fought this battle before. I bought several different PCMCIA cards for a laptop, only to find out that many manufacters change chipsets year to year, and only change the part number by adding an a,b,c,etc on the end. Of course Linux only has the best support for last years card! I found out that the Orinoco chip cards have the driver in the Linux kernel, and Ubuntu found and configured mine automatically when I re-installed Ubuntu.

The card I specifically bought and used is this one:

[http://www.amazon.com/exec/obidos/tg/detail/-/B0000C20KH/102-3444483-8852902?%5Fencoding=UTF8&v=glance](http://www.amazon.com/exec/obidos/tg/detail/-/B0000C20KH/102-3444483-8852902?%5Fencoding=UTF8&v=glance)

Proxim 8410-WD Orinoco 802.11b Classic Gold PC Card

Keep in mind this particular card is a PCMCIA card for a laptop, however other models have this chipset on a PCI board or a USB model.

---

