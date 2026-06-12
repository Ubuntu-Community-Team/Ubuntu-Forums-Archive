---
title: "Booting"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by KermitDaFrog on 2009-11-14
Hey guys pretty new to unbuntu so please try and keep it simple...

i jut installed ubuntu on a friends computer and whenever we try and dual boot into ubuntu...instead of starting it goes to a black screen with something like Bash Grub version 1.97 and all this txt below it.  It gives us a command line and we try and type "boot" and it says something about a kernel not being selected.  Any help just to get to the os would be awesome.  We had just updated his ubuntu, through its auto-updater and rebooted.

-thanks in advance

---

### Post by kansasnoob on 2009-11-14
> **KermitDaFrog said:**
> Hey guys pretty new to unbuntu so please try and keep it simple...

i jut installed ubuntu on a friends computer and whenever we try and dual boot into ubuntu...instead of starting it goes to a black screen with something like Bash Grub version 1.97 and all this txt below it.  It gives us a command line and we try and type "boot" and it says something about a kernel not being selected.  Any help just to get to the os would be awesome.  We had just updated his ubuntu, through its auto-updater and rebooted.

-thanks in advance

Please boot the Live CD choosing "Try without changes" and from the Live Desktop run the Boot Info Script as explained here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Then post the results here using the "code" tags.

---

### Post by KermitDaFrog on 2009-11-14
I cant even get into the os its just the black screen how can i run that script?

---

### Post by KermitDaFrog on 2009-11-14
GNU GRUB 1.97~beta4
 Minimal bash-like line editing and supported....

and that is the message we get...wen we type command boot it says no kernel is selected

also we have no live cd, just manually installed

also commands

root (hd0,1) --> file system is fat
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda2 vga=791 -->uknown command kernel
boot- no kernel selected

---

### Post by KermitDaFrog on 2009-11-14
bump...really need some help

---

### Post by ViperChief on 2009-11-14
> **KermitDaFrog said:**
> GNU GRUB 1.97~beta4
 Minimal bash-like line editing and supported....

and that is the message we get...wen we type command boot it says no kernel is selected

also we have no live cd, just manually installed

also commands

root (hd0,1) --> file system is fat
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/sda2 vga=791 -->uknown command kernel
boot- no kernel selected

What do you mean manually installed? How did you install Ubuntu on there?

---

### Post by KermitDaFrog on 2009-11-14
is there a way to repair/remove the operating system through windows...cause htat would work too

---

### Post by synicalx on 2009-11-14
As Kansasnoob has already said, boot from the LiveCD not the HDD. The LiveCD is the disc you installed from and all the data it needs to boot is on the disc, if you don't already have one just download an Ubuntu .iso (9.04 or 9.10) and boot from that by selecting it as the boot option. Instructions can be found [here.]("https://help.ubuntu.com/community/LiveCD")

---

### Post by kansasnoob on 2009-11-14
+1 and thanks!

---

### Post by kansasnoob on 2009-11-14
Actually you could at least tell us what version of Windows it is. If you have the Windows installation disc(s) we might be able to help you recover Win's boot record to the mbr.

---

