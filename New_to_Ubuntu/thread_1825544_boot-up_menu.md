---
title: "boot-up menu"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by camelot8 on 2011-08-15
ubuntu 10.04
sudo gedit /boot/grub/menu.lst is giving me an empty file.
How to erase old ubuntu boot-up option?

---

### Post by coffeecat on 2011-08-15
Welcome to the forum!

> **camelot8 said:**
> ubuntu 10.04
sudo gedit /boot/grub/menu.lst is giving me an empty file.

That's because 10.04 doesn't have a menu.lst. Since 9.10/Karmic, Ubuntu has used grub2 which uses different configuration files.

> **camelot8 said:**
> How to erase old ubuntu boot-up option?

I'm guessing you mean that you want to remove old, unused kernel entries. If you simply edit the grub menu, you still have all the old kernel files taking up quite a bit of hard drive space. It is better to uninstall the old kernel packages, and then the grub menu will be updated for you automatically. Open Synaptic and search for '2.6.32-XX' where XX is the number of the kernel version you want to remove. There will be 3 or 4 packages. Mark them for complete removal. Repeat for any other kernels you want to remove, and then click on "Apply". Obviously, don't remove your latest running kernel!

---

### Post by Daveth on 2011-08-15
it now lives in /etc/default/grub, by the way:D

---

### Post by slotto on 2011-11-12
Thanks for this!
slotto

---

