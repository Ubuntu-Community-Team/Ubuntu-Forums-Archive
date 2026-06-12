---
title: "I have two WiFi cards.  How do I turn one off at the command line?"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by Jim March on 2008-11-03
I have Intrepid, and two WiFi adapters - one laptop internal broadcom at Eth1 with normal restricted drivers, another with a Realteck chipset, WLAN1 on a USB port.

I also have a cellular modem that works great (Verizon KPC680).  What I want to do is share the cellmodem over WiFi with a friend.  Problem is, the Broadcom doesn't seem to support promiscuous mode while I suspect the Realteck does (or at least might?).

I've tried:

sudo ifdown eth1

...and variants and I'm not getting anywhere.  Yeah, I know, what I really need is something Atheros-based but that'll be down the road.

So how do I turn off that damn Broadcom without use of a screwdriver and just yanking it out?

Thanks...

---

