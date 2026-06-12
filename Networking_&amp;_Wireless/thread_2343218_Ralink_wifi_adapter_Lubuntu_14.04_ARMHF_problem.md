---
title: "Ralink wifi adapter Lubuntu 14.04 ARMHF problem"
date: 2016-11-14
forum: Networking &amp; Wireless
---

### Post by dana77 on 2016-11-14
I have Toshiba AC100 netbook running Lubuntu 14.04 ARMHF version and a problem with a Ralink wifi adapter (ID 148f:7601 
Ralink Technology, Corp) that uses a driver called RT2870 or MT7601U available in kernel 4.2. Problem is my kernel is 3.1.9 and can't even install an old dkms driver that was previously available (mt7601-sta-dkms_3.0.0.4-
0~201602170732~rev26~pkg4~ubuntu14.04.1_all.deb; [https://code.launchpad.net/~thopiekar/+archive/ubuntu/mt7601);](https://code.launchpad.net/~thopiekar/+archive/ubuntu/mt7601);) it comes out with errors. So, my question is: can I update this special machine/snowflake's kernel to at least 4.2 somehow without screwing up my current install? Or get this driver installed some other way? I now start to think that messing with kernel on this one is not a good idea. It's just about the driver for this adapter. I'll appreciate any ideas. Thanks.

---

### Post by mörgæs on 2016-11-14
Hi, welcome to the fora.

I would do a fresh install of 16.04.1 though it means setting everything up from scratch. 14.04 has only 5-6 months of support left anyway.

---

### Post by dana77 on 2016-11-15
That is the problem; I would if I could, but this was a special case, this netbook, based on this [https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100) and I don't know if upgrading will be possible. Somebody had trouble with 15.10 here [https://ubuntuforums.org/showthread.php?t=2275719](https://ubuntuforums.org/showthread.php?t=2275719). Thanks anyway.

---

### Post by mörgæs on 2016-11-16
The thread deals with an upgrade in-place, and they are always more error prone than a fresh install.

---

