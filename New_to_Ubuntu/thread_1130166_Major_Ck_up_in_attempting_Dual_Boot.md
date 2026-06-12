---
title: "Major C**k up in attempting Dual Boot"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by randomnosity on 2009-04-19
Hi.

I switched to ubuntu 8.10 about a month ago, and accidently wiped my copy of xp off the hard drive. after obtaining a xp boot disk, and trying to reinstall xp (for using CAD programs) for a dual boot. i managed to format the hard drive ready fro windows (NFTS). However due to a small c**k up during installation my PC restared and when GRUB loads up i get 

GRUB Loading Stage1.5.
GRUB Loading, please wait...
Error 15

I have Ubuntu Live Cd, Windows XP SP2 Boot CD and made an Ubuntu 8.10 Bootable USB Stick, however I cannot get any of these to even load up now. Im using an Elonex Artisan Media Centre Computer as a desktop, and during the start up splash, it doens't give any options to access BIOS or boot menu. Please Help!

---

### Post by Wiebelhaus on 2009-04-19
[Repair grub.]("http://www.gnu.org/software/grub/manual/grub.html")

[http://ubuntuforums.org/showthread.php?t=210820](http://ubuntuforums.org/showthread.php?t=210820)

[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

---

### Post by randomnosity on 2009-04-19
Sorry. still no help there, as i cannot access the BIOS of the computer. 

If I am able to obtain another internal HDD, swap the orignal one (as it is set to master, switch it to slave) with the new one (making this one the master), will I be able to format the drive in question again and start from fresh?

---

### Post by randomnosity on 2009-04-19
i removed the hard drive, and boots straight to the live cd. will try and resolve problem from here.

thanks for the help however :D

---

### Post by lolol i r linux noob on 2009-04-19
u can download a super grub disk iso and burn it to cd. 

Super grub disk allows you to write grub back to the mbr or put windows back in the mbr. it can also boot linux and boot windows by bypassing the mbr.
search "super grub disk" on google

---

### Post by randomnosity on 2009-04-19
managed to format the hard drive, got windows xp installed again. now having problems installing ubuntu. using the live cd it wont load the demo/installer giving the reason as code 15.

i think i may have a dodgy disk or something.

---

