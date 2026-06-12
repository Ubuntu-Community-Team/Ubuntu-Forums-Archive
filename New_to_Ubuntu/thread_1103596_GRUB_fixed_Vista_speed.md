---
title: "GRUB fixed Vista speed?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by stalkier on 2009-03-22
Ok So here is the history of this. I had a dualboot using XP pro and Ubuntu 8.10. I had some kind of messup with Adobe CS3 on my Windows. I installed Vista Ultimate 64bit over the XP install. It worked flawlessly though startup to full use was a little long. (average of 45 or so). However, I missed my Ubuntu since the GRUB was over written by the Windows MBR. I used Super Grub Disc to fix GRUB and then rebooted into Ubuntu to make sure it still worked correctly. It did work. Now comes the weird part. I rebooted into Windows and then after I logged in it only took like 10 seconds. Why would this be?? Does anyone have any ideas? Thanks.

---

### Post by 123456789123456789123456 on 2009-03-22
could be a result of the deletion of vista boot loader.  Don't see how though.  I am aware that Vista does not exactly like have GRUB part 1 booting Vista.  I use Vista boot loader, with a program called Easy BCD to boot GRUB part1 adn 1.5 from the ubuntu partition.

---

### Post by meierfra. on 2009-03-22
> I am aware that Vista does not exactly like have GRUB part 1 booting Vista. 
???????????????????????????????????????????????????????
Vista couldn't care less. Grub does not actually load Vista, it just calls the Vista boot loader, and the Vista boot loader boots Vista.  (OK, there are some very rare case where grub  is  not able call the Vista boot loader)


> Why would this be?? 
No idea. This is very strange.

Before you reinstalled Grub the booting process was like this:

Bios->Windows MBR -> Vista Boot Loader

afterwards:

Bios>Grub Stage 1-> Grub Stage 2-> Vista Boot Loader


That really should not be any faster. Maybe the Windows MBR was corrupt. If you have more than one hard drive, it might also be  that there was no boot code in the MBR and the boot process work like this

Bios->MBR of fist drive (fails)
Bios-> Windows MBR on second drive -> Vista Boot Loader 


If you want to pursue the matter further, please post the output of "sudo fdisk -lu" so that we have a better idea of your setup.

---

