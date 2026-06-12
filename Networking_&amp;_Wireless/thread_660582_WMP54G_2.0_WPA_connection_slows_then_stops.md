---
title: "WMP54G 2.0 WPA connection slows then stops"
date: 2008-01-06
forum: Networking &amp; Wireless
---

### Post by russbuss on 2008-01-06
I just did a fresh install of 7.10 and finally activated WPA.  I am using an Airport Extreme router with WPA2 Personal security enabled.

My problem is that, despite connecting and working perfectly at first, my connection slows down over time and eventually stops.  If I restart the computer, the connection comes back and does the same thing: Starts out fast, then slows to a crawl.  I determined this from trying to download updates (including the latest kernel) and watching the download speeds sag from 100 MB/s down to 1-2 B/s before finally just stopping.

I have looked around, but can't find a post that addresses this specific problem for my version of the WMP54G.  Part of my confusion comes from here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys)

This page lists my card as being a Broadcom, but the rt2500 driver is installed according to my Device Manager.  So, I don't know if I need a better driver or to tweak the one I have.  If anybody could point toward a good post, that would be a appreciated.

Thanks.

---

### Post by kevdog on 2008-01-07
Ok, so it sounds like your device has a rt2500 chipset.  There are three drivers that you could use for your situation.  The built-in rt2500pci driver (probably the worst one), the cvs serial monkey rt2500 driver (the one I would try first), and ndiswrapper+winxp driver for your card. 

The serial monkey driver doesnt get along with network manager really well.  Its native however.  Ndiswrapper is an emulation driver, but works better with network manager.

Just kind of depends how adventerous you are!

---

