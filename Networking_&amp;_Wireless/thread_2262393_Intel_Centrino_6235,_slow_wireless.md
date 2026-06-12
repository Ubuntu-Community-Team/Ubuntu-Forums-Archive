---
title: "Intel Centrino 6235, slow wireless"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by mathiaswallenberg on 2015-01-24
Hey! 

I am new to Linux and need some help. I got a laptop with the intel centrino 6235 wireless card. I am using the 2,4 ghz instead of the 5 since i heard there was problem with the N. I got wired in about 100 mbit/down. On windows i got the same wireless. Now after installing ubuntu i got like 20 mbit/down. Do you know how i can fix this? 

Best regards

---

### Post by weatherman2 on 2015-01-24
To clarify terms: "N" (802.11n) is not the same as "5GHZ."  Your Intel 6235 card has two radios, one 2.4GHZ and one 5GHZ.  Both of them are 802.11n, not just the 5GHZ.  Lots of 802.11n routers and wireless cards are single band 2.4GHZ only.

Yes, sometimes these Intel cards seem to have issues with 802.11n 2.4GHZ (and 5GHZ I assume).  Myself, I've never had any issue with 802.11n (5GHZ or 2.4GHZ) with any of my Intel cards, and I've installed the 6235 card in at least four laptops besides the one I use every day, without a single override  (and now connected to dozens of routers).  It would be greatly disappointing to need to slow down to G speeds on my local network, because I often need to transfer files over my home wireless network.  5GHZ 802.11n is about 4X faster than 802.11g for me with my 6235.

Apparently there are different flavors of these 6235 cards, though.  And the kernel driver is different in different versions of Ubuntu (different kernels).  I use Ubuntu 12.04.2.  Ubuntu 14.04 or 14.10 may have different issues.  (If you are new to Linux, I highly recommend sticking to an LTS edition of Ubuntu like 14.04 or 12.04 and not 14.10 which has support for only a short time.)

To proceed to offer you help, find the "sticky" post at the top of this forum entitled "Before posting in Networking & Wireless" and download/run the wireless script there.  Run the script and posts the results it gives you.  Then people can offer you specific help.

---

