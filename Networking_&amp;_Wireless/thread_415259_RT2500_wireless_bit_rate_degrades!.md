---
title: "RT2500 wireless: bit rate degrades!"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by vaskeli on 2007-04-20
Using Edgy, kernel 2.6.20.7, and the open source rt2500 driver (CVS from April 19th). Neither the official ralink driver, nor the more "stable" open source beta driver will compile under my kernel, so I have to use the CVS tarballs.)

Problems:

1. My wireless connection degrades over time. From 54 Mb/s to 1 Mb/s, sometimes climbing back partially for a while. Restarting will temporarily bring it back to full speed, but lately it starts degrading within a few minutes. No other PCs on the network (including a laptop running Debian and an old kernel) have any problems with the network.

2. I can't connect at all if WEP security is turned on (other PCs can). So I turn it off and still have problem #1.

3. Is there a log file that might record these problems as errors, to help me figure out what's going on?

This is driving me nuts. Thanks for any and all help!

---

### Post by Xav' on 2007-12-03
Well, I can't help you but I have the exact same problem with a Broadcom bcm4318 (installed via ndiswrapper and bcmwl5 driver). Have you figure out what the problem was ?

---

