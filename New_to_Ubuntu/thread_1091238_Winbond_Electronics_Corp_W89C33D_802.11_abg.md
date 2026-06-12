---
title: "Winbond Electronics Corp W89C33D 802.11 a/b/g"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by RichardCL on 2009-03-09
Hi Forum,

I've just installed Ubuntu x64 on a TCM Cytron x64 PC. This one is from Tchibo but there should be a similar device from Aldi/Medion.

```
lspci -v
```

gives
> 
00:11.0 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
	Subsystem: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
	Flags: medium devsel
	I/O ports at 2000 [disabled] [size=256]
	I/O ports at 1080 [disabled] [size=128]
	Memory at 48021000 (32-bit, non-prefetchable) [disabled] [size=512]
	Capabilities: <access denied>


A google search on this driver for Ubuntu gives a lot of not happy people also trying to install...

Windbond have a manual [http://www.winbond-usa.com/products/winbond_products/pdfs/WLAN/W89C33DProdBrief_20050622.pdf]("http://www.winbond-usa.com/products/winbond_products/pdfs/WLAN/W89C33DProdBrief_20050622.pdf"), which I found via google. This document claims at least a Linux 2.4 kernel driver. However, there is no mention of WLAN products on thier site at all.

Did anyone have any joy installing?


Richard

---

### Post by jnalli121 on 2009-09-24
fairly old thread, but im having the same problem. Any way to install this driver? if so, could you please give some newbie friendly instructions. Thanks in advance.

---

### Post by RichardCL on 2009-09-28
I never got it to work so I sold the system. Had all kinds of problems with the low-end PC including some serious degradation of the flat pannel. Can't recomend the Tchibo PC. Gto about 15 Euros in Ebay for the unit sold as defect.

Good luck.

---

### Post by kevdog on 2009-09-28
I helped a user with this card a long time ago but the thread kind of died so I never know what happened.  The only way I might suggest a solution would be to use ndiswrapper with the winxp version of the driver.  I have no idea if this will work, however there doesn't seem to be a native driver available for this card the last time I checked (~ 6 months ago).

---

