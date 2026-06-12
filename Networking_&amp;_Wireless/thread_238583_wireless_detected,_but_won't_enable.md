---
title: "wireless detected, but won't enable"
date: 2006-08-17
forum: Networking &amp; Wireless
---

### Post by savethesquirrels on 2006-08-17
I have a Gateway 7422GX. I can see my wireless card in the network settings, but when I try to enable it it disables. I also have an FN key that enables it and I cannot enable it via that either. Does anyone have any ideas? I can't ifup because it isn't enabled. Thanks

...I think I found out why:

main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:00:0c.0' with driver 'bcm43xx'

guess I'll try ndiswrapper drivers

---

