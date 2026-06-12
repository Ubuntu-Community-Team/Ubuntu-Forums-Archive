---
title: "Belkin F5D7000 (version 20) - Driver needed."
date: 2008-06-18
forum: Networking &amp; Wireless
---

### Post by robertkane on 2008-06-18
I'm trying to get my Belkin F5D7000 wireless G card operating. I followed a couple solutions on here using the ndiswrapper and and few suggested drivers (rtl8185, bcmwl5/bcmwl5a). 

It turns out that for the specific version of the card I have (version 20) it requires a driver, blkwgdv7, that is only available from the installation CD.

I no longer have the installation CD. Is it possible to get this driver somewhere (or from someone) or is there an alternate driver?

---

### Post by chili555 on 2008-06-19
Can you get it here? [http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=221](http://www.belkin.com/support/article/?lid=en&pid=F5D7000&aid=6001&scid=221) I downloaded version 2xxx. Although the file is an .exe, I did, in a terminal:```
cabextract f5d7000_v2_uk.exe
```The needed .inf and .sys were extracted. You card, by the way, is *not* a version 2xxx. The file I grabbed is for a Realtek chipset.> Extracting cabinet: f5d7000_v2_uk.exe
  extracting _SETUP~2.EXE
  extracting rt2500.cat
  extracting Rt2500.sys
  extracting Rt25009x.sys
  extracting setup.exe

---

