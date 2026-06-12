---
title: "Cannor remove old kernels"
date: 2011-02-19
forum: New to Ubuntu
---

### Post by yildiz.a on 2011-02-19
Hi all,

I currently use Ubuntu 64-bit on my computer. I tried to look for "menu.lst" under /boot/grub/ but it was not there. I also checked "linux-image" phrase from Synaptic Package Manager, again does not show the old ones.

I would like to remove existing old kernels. Can you help me about this? Thank you.

It seems grub is not installed because when I enter "**grub**" in terminal, it asks me to install it. But when I power up my computer, a list possibly about grub comes that lists the old kernels with the newest one and Windows 7.

---

### Post by grahammechanical on 2011-02-19
Try loading Synaptic Package Manager and typing linux-generic in the quick search box. Mark any old ones (not the present one) for removal and they will be removed and the GRUB menu will be corrected accordingly.

Regards.

---

### Post by yildiz.a on 2011-02-19
> **grahammechanical said:**
> Try loading Synaptic Package Manager and typing linux-generic in the quick search box. Mark any old ones (not the present one) for removal and they will be removed and the GRUB menu will be corrected accordingly.

Regards.

OK. I have mistaken. I did it. Thanks.

---

### Post by waynefoutz on 2011-02-19
the easiest and less dangerous way to do this is with Ubuntu Tweak.

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

