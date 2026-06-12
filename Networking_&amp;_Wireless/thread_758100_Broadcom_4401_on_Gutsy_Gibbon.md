---
title: "Broadcom 4401 on Gutsy Gibbon"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by matchu on 2008-04-17
Mmkay, here's the thing.

Just started with the magical Ubuntu-ness, dual-boot w/ Vista and all that good stuff. Everything's working fine, except that about every single method I've tried for setting up my Broadcom card didn't seem to work out in the end.

For reference, lspci returned:
```
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

So... is there any hope for me? Lemme know if there's some special method I haven't quite discovered yet :)

I think I'll go ahead and uninstall all those random repositories I downloaded so that y'all can help me start from scratch xP

---

### Post by dstew on 2008-04-18
Enable the repositories, update, and check the Restricted Drivers Manager (in System --> Administration) to see if there is anything for your ethernet controller.

---

### Post by matchu on 2008-04-18
Alas, I've got multiverse enabled and everything in Restricted is on (nothing about internet whatsoever), but still no dice.

I also think there might be a software-level issue, see [new thread](http://ubuntuforums.org/showthread.php?t=758198) :)

---

