---
title: "Wubi Install Problem"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by JaxDragon on 2009-09-26
After running the wubi installer on my XP laptop, I restarted. When it loads up, there is no option to boot into Ubuntu. It boots straight into XP. Any help?

---

### Post by sandyd on 2009-09-26
i hope you ran the installer with admin privelages. if you didn't... well... you know what to do...

---

### Post by JaxDragon on 2009-09-26
Yes of course it was installed with admin. And I've tried reinstalling wubi but that didnt help.

---

### Post by zeroseven0183 on 2009-09-27
So you mean you installed it inside Windows? (Can display here the contents of your boot.ini?)

What version of Ubuntu did you install?

---

### Post by Darkwing-Duck on 2009-09-28
Okay, You need to fix your MBR and make sure that GRUB is used. The reason for this (I don't know why wubi failed you) is that Windows Bootloader (go figure) doesn't play nice with others. 

So, what you need to do it get a LiveCD. Once you boot into it then follow this guide to help you get GRUB in place and your dual-boot problems solved.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

