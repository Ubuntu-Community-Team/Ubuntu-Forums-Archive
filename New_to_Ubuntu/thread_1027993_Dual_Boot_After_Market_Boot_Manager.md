---
title: "Dual Boot: After Market Boot Manager"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by dinomite89 on 2009-01-01
Ive been having troubles wiht my dual boot of vista and ubuntu, was woneering if a new boot mangaer was avlible so when i boot up i have the choice of eitehr opwerating system and do not get any BOOTMGN or GRUB Errors

---

### Post by xenolalia on 2009-01-01
Well, so far, I've had a pretty positive experience with grub.  It's been working well for me, and the few problems I've had with it have been easily fixed with super grub disk.  But, if you're looking for a different bootloader entirely, I've heard of one by the name of lilo and another by the name of extlinux.

Good luck!
Xenolalia

---

### Post by teh_yodeler on 2009-01-02
GAG [http://gag.sourceforge.net/](http://gag.sourceforge.net/) the graphical boot manager

---

### Post by bumanie on 2009-01-02
Gag bootloader is one option, but dual boot vista/ubuntu should work OK. Can you post the output of > sudo fdisk -land>  cat /boot/grub/menu.lst 

---

