---
title: "Issue with Broadcom STA driver Ubuntu13.10, Host Unreachable with Netgear N150 router"
date: 2013-11-14
forum: Networking &amp; Wireless
---

### Post by niteshnandy on 2013-11-14
[COLOR=#333333][FONT=UbuntuRegular]BCM4313 chip on my laptop. When using the Broadcom STA (wl) driver, wifi connects successfully to the Netgear N150 router but when I ping the router (192.168.1.1) it says Host Unreachble. If I connect to any other wifi router like D-Link or Linksys (or even tethered android phone) everything works fine. The issue is precisely with the Netgear router only.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Moreover, everything works fine with the brcmsmac driver. Yes, even connection with Netgear router works fine in this case. My problem being brcmsmac driver does not work well for me, shows lower signal strength and quite a few dropped packets. Basically Broadcom-sta driver works much much better for me than brcsmsmac, so I want to use the sta drivers. Started happening after I did a fresh install of Ubuntu 13.10.  In 12.10 things worked pretty well.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've hunch that Netgear router is blacklisted somewhere in the STA drivers, I'm not sure how to figure this out. Any help is appreciated.[/FONT][/COLOR]

---

### Post by niteshnandy on 2013-11-19
Bumping this thread. Anyone? 

I tried using the b43 driver this time around. The wifi stops working completely with this, the wifi adapter is not even detected.  Should I give ndiswrapper a shot?

---

