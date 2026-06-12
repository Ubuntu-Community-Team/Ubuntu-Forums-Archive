---
title: "I toasted my grub/image file?"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by eddski on 2009-09-09
Ideleted an old kernel, ending in 13, and now I cannot boot Ubuntu. I get an "error 15" message. there is info on error 15, but what throws me is that I can still boot windows from grub with no problems. I believe my images are still in /boot as I looked with a boot cd. I 3 primary partitions(2 ntfs and /boot) and an extended partition with the rest my Ubuntu partitions. I read on epost about editing at boot time and changing the hd(?,?) setting, but I believethe current setting is correct because I have the same partiton scheme on my laptop.What would be my best course of action? Should I reinstall grub?

---

### Post by PunkLV on 2009-09-09
Posting your current /boot/grub/menu.lst would help a bit.

Also, when in OS selection menu, select the image that you want to boot and enter the Edit mode ("e" key as I reckon) and see if "kernel" and "initrd" lines are correct and that they DO point to your new kernel images.

---

### Post by Pirolocito on 2009-09-09
The best you have to do is to boot with a ubuntu cd and see your /boot/grub/menu.lst

I dont believe your image is broke, but menu.lst maybe is....

---

### Post by eddski on 2009-09-10
thanks guys, it was my menu.lst file that, for some strange reason, was changed. But everything is good, thanks again.

---

