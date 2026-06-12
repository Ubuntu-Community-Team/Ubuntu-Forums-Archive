---
title: "Trouble with Vista/Ubuntu Dualboot"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by shrumhead on 2009-03-26
I've been having a lot of trouble with a Vista/Ubuntu dualboot.  I'm trying to use EasyBCD to edit the vista boot menu but I just can not get it to boot Ubuntu 8.10.  I have 2 different hard drives, one is SATA, the other IDE.  I had Vista first (On the SATA drive) and now I've installed Ubuntu on an older HD (IDE).  

The Vista HD is listed as "sda" and the IDE drive with Ubuntu installed on it is listed as "sdb".  I had Grub install itself on /dev/sdb1 because the guide I was following said to install it on the partition of the linux install to give EasyBCD an easier time.  I directed EasyBCD to that partition but it doesn't pick up anything when I try to use it when booting.  Says something along the lines of no file found and to enter a system disc.  

Then I tried NeoGrub... I took the Grub Parameters in /boot/grub/menu.lst and put that in the NeoGrub menu.lst (c:\NST\menu.lst)  but still no dice.

Both operating systems are 64bit.

I also tried installing grub to the bootsector of the IDE HD but I couldn't get it to recognize that either.  

Any suggestions?

---

### Post by shrumhead on 2009-03-26
Nevermind... I decided to take the easy way out and just change the order of HDs in my bios... still bugging me that I couldn't figure it out but at least dual booting is working.

---

