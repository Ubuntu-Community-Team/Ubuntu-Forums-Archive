---
title: "Zonet ZEW2500P connects, but doesn't."
date: 2007-11-06
forum: Networking &amp; Wireless
---

### Post by ChrisE on 2007-11-06
I'm having a rather strange problem with my wireless connection.

I've currently got two boxes running ubuntu, a toshiba satellite and a compaq desktop, from a buffalo air station wireless router.  The toshiba satellite has no problem connecting to my wireless network (and neither does a windows xp box).

On the other hand, the compaq presario, with a zonet zew2500p wireless modem, is being extremely difficult.  It recognizes my wireless network (and several others), and looks like it's connected to it.  However, it won't actually load any anything - not a web page, and not the router's ip address.

Previously, I used a netgear wgr614 (or something like that), and the modem didn't have any problems.

Can anybody help me figure out what's wrong, or at least point me in the right direction?  I'm at a loss.

Thanks.

---

### Post by ChrisE on 2007-11-07
If this isn't enough information, or if nobody really feels like helping me solve this problem, can anybody suggest resources that could help me solve this problem myself.

e.g. I suspect the problem may be that my wireless card isn't being recognized properly.  How can I determine if ubuntu is using the right driver?

---

### Post by ChrisE on 2007-11-09
anybody?

I assume this isn't a driver problem, because I have a "wireless connection" tab in my network connections menu.  Is it possible that the wrong driver is being applied to my network card, or is this definitely a router problem? (or something else entirely?)

If it is potentially a driver problem, can anybody tell me how I can check and see if my wireless card is configured properly?

---

### Post by The_PhAnT0m on 2007-11-09
I'll try and help. First post the results of iwconfig when the network appears to be connected. I'll see if I can find anything there.

---

### Post by alasdepinguino on 2007-11-11
> **The_PhAnT0m said:**
> I'll try and help. First post the results of iwconfig when the network appears to be connected. I'll see if I can find anything there.


o        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

:confused:

---

### Post by The_PhAnT0m on 2007-11-12
I won't say I am an expert at this, but it looks like either Ubuntu can not see the card or there is no driver. Try entering "lshw" without the quotes in a terminal and look for something about your card. If there is a little section about the card, post it on the forum.

---

