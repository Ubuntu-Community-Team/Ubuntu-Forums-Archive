---
title: "Aspire 532h won't boot after fresh install"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by Flimm on 2010-12-23
A friend of mine has recently installed Ubuntu 10.10 on his Acer Aspire 532h netbook (with full-disk encryption). Now all he gets upon boot-up is a blank screen with a flashing cursor in the upper-left corner. Holding down shift doesn't do anything, except make the computer beep.

He has previously installed Ubuntu 10.04 on this netbook with no problems.

What should I do? I'm going to try and guide him the [Grub2 troubleshooting](https://help.ubuntu.com/community/Grub2) with a live USB, but I'm wondering if anyone has experienced this problem before. Would installing Ubuntu 10.04 and upgrading to Maverick present any problems?

---

### Post by Flimm on 2010-12-28
Bump.

---

### Post by amjjawad on 2010-12-28
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by VonSpyder on 2010-12-28
sounds like it didnt install the bootloader. try reinstalling but select custom partitioning so you can tell it to install bootloader.

---

