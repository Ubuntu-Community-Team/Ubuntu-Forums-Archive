---
title: "wireless file transfers slower than they should be"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by bytemehard on 2008-06-15
Ok so here is my situation, it has a few quirks as well which might be clues to figuring this out:

I have a Vista desktop and a fairly old Gateway 4025GZ laptop running xubuntu.

Desktop is connected to a Linksys WRT54 running DD-WRT firmware via wired ethernet, and the laptop is connecting over wifi (802.11g)

I setup shared folders in xubuntu, now here is where things seem funky:

If i connect the laptop via ethernet cable, transfers are very fast as I would expect. 8+ MB/sec.

If I transfer over 802.11g I would expect speeds to be in the few MB/sec, right? (not as fast as wired obviously, but faster than what I'm getting)
Instead I get about 600-700 KB/sec when sending a file FROM vista desktop TO xubuntu laptop, and I only get about 40-50 KB/sec when sending FROM xubuntu laptop TO vista desktop.

When I click on "Connection Information" on the wifi connection monitor thingy, it says Interface: 802.11 Wifi (wlan0) Speed: 1 Mb/sec Driver: <blank>

The driver was one of those "restricted drivers" that I had to enable after installing xubuntu.

So, anybody have any idea why the wifi transfers are slower than I would think they should be, especially when pulling a file FROM the laptop? Could it have something to do with the Connection Information indicating the connection speed as only "1 Mb/sec"?

---

