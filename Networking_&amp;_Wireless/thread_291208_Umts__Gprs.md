---
title: "Umts / Gprs"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by morgan@ronning.se on 2006-11-02
Using a laptop and a pcmcia card I can connect to Internet over a UMTS (3G) network, enabling me to work anywhere. In Windows XP that is.

Is there any solution that I can get the same function in Linux?

---

### Post by Jussi Kukkonen on 2006-11-02
Sure, if there's a driver for the pcmcia card...

Post the make and model of the card, or better yet, do a search on google: 
*  cardname cardmodel pcmcia 3G linux*
or alternatively 
*  cardname cardmodel pcmcia 3G debian*
and see what comes out

---

### Post by info2 on 2006-11-02
UMTS/HSDPA is working very well for me and without problems.

I have the Option 3G - PCMCIA-Card from Vodafone in Germany. The Vendor "option" published OpenSource Drivers that are working well.
(i currently use Kernel 2.6.17).

If you want to find out how to get the thing working, just take a look at
pharscape.org. There you'll also find howtos for other UMTS-Devices.

The HowTos are not the gnome-friendliest (if you don't use kde) because they are using kppp as dealer, but you can use "wvdeal" instead, for example.

It wasn't very hard to me to get the thing working. You just need to read the few posts in the forum there and a cup of coffee to make it.

By the way, using HSDPA i often get about 170kB and more. :)

---

