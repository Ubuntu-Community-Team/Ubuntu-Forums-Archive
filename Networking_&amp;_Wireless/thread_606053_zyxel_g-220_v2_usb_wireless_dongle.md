---
title: "zyxel g-220 v2 usb wireless dongle"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by llamabr on 2007-11-07
This arrived in the mail today, where I bought it new from ebay  for about 10 bucks.  I chose it based on the review of 

[http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/](http://www.murrayc.com/blog/permalink/2007/09/07/linux-compatible-wireless-usb-adaptor-slightly-better-in-ubuntu-gutsy/)

I looked at a few others better named, but the obvious worry is either the closed sourced driver, and fighting with nsdiwrapper (a fight I never win).

Anway, as Murry claimed, it worked nearly out of the box.  I started with a fresh install of Ubuntu 7.10, popped into gnome, opened System|Administration|Network, added my essid and wep passwd (which, as far as I can tell just edits /etc/network/interfaces, and rebooted.  That did it.

Before rebooting, I had to bring eth0 and eth1 up and down a couple times, so just to be sure, I rebooted.  sudo ifup eth1 and I'm wireless.  

This is on a new Gateway ML6230.  As confirmed on other threads, there's some propblem with the internal wireless card, so at least I no longer have to sit in the closet (where the router is) to work on my wireless card.

In conclusion, ZyXel g-220 v2 gets the recommendation of a lazy guy who doesn't care to do a long of hacking.

Cheers,

Robert

---

