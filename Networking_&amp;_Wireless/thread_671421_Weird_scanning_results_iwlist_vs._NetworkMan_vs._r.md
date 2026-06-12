---
title: "Weird scanning results: iwlist vs. NetworkMan vs. reality"
date: 2008-01-18
forum: Networking &amp; Wireless
---

### Post by krausest on 2008-01-18
Recently I moved into a area with a lot of WLAN access points.
Sometimes the gnome Network Manager doesn't find my own WLAN, but shows some others. When I run iwlist scanning I'm getting completely different results from what's shown in Network Manager. Inbetween seconds there may be a single WLAN or almost ten WLANs - with or without my own.

Is there something I can do when Network Manager doesn't find my WLAN? (Current workaround is a wild mixture of enabling / disabling wireless, restarting Networkmanager and calling iwlist scanning). 
Is there a way to make scanning results more consistent?

I'm having this issue with 7.10 32bit and the ipw3945 driver.

Thanks!

---

### Post by growingtedium on 2008-01-18
I don't know about making the scanning results more stable (other than getting a better antenna?) but if your network isn't listed in network manager, you should still be able to connect to it by using "connect to other wireless network".  That's what I do as I have a hidden essid, so it doesn't ever show up in the network list - but once it's been entered, network manager finds it every time.  Hope this helps.

---

