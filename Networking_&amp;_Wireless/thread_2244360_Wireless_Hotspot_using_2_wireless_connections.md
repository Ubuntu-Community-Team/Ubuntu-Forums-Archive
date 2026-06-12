---
title: "Wireless Hotspot using 2 wireless connections"
date: 2014-09-15
forum: Networking &amp; Wireless
---

### Post by lee30 on 2014-09-15
Sorry if this has been asked or posted before, but forum/internet search is not leading the way.

The short.....
I am heading out of town tomorrow.  The place that feet will land and sleep only offers internet access at premium price.  Can I configure my 14.01 TLS laptop as a hotspot for my phones via 2 different wireless "cards"?  My laptop doesn't have a wired network connection, but I do have the built-in wireless connection and a seperate mini usb wireless adapter.

Thanks

---

### Post by weatherman2 on 2014-09-15
Yes, you can, and yes, I have done it, though not in 14.04.  In 12.04, where I did it, it didn't quite work out of the box.  I had to install something to make it work (sorry, I forget what that was.)  You can try it in 14.04 and see if it works automatically; if not, google for more instructions.  Start by going to your list of Wireless networks, from the menu choose Create New Wireless Network, and on the Connection list choose "Hotspot."  (This was for 12.04, may be slightly different.) This also assumes your USB wireless card works.

---

### Post by ian-weisser on 2014-09-15
It works out-of-the-box if one of the wifi chips supports master mode or ad-hoc mode. Some do, some don't.

Everything you need is in Network Manager. Create a new network to share, then share the internet connection. NM magic will do the rest.

---

### Post by sammiev on 2014-09-15
> **ian-weisser said:**
> It works out-of-the-box if one of the wifi chips supports master mode or ad-hoc mode. Some do, some don't.

Everything you need is in Network Manager. Create a new network to share, then share the internet connection. NM magic will do the rest.

+1 with wep

wpa2 is a little work which seems to be hit or miss yet.

---

