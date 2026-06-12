---
title: "Remove GRUB?"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by computerguts on 2010-08-06
Hi, I recently installed kubuntu 10.04 on an external hard drive that I have. I am also running windows seven 64bit on my internal hard drive of my computer. When I unplug my external hard drive and try to boot into windows seven it gives me an error with a whole bunch of letters and numbers like a system file, and it says not found. Then it says <Grub Rescue>_ with a terminal, is there anyway that I can get rid of grub so that when I boot my computer I can just go into the bios boot menu and select my internal hard drive to boot from my windows seven operating system, even when my external hard drive with Kubuntu 10.04 64bit installed on it is not plugged in? Thanks, also I have gone into the bios boot menu and changed the boot priority so that my internal hard drive is the first to be searched for an operating system (again, my internal hard drive is the one that has windows 7 64bit installed, thanks

---

### Post by Bachstelze on 2010-08-06
With XP, you could erase GRUB from the MBR by booting with the CD and typing the command [font=monospace]fixmbr[/font] in the recovery console.  That has probably changed with 7, but there should still be a similar thing, a search for something like "windows 7 fix mbr" should give you something.

Don't forget to also install GRUB on the MBR of your external drive, otherwise you won't be able to boot Ubuntu from it.

---

### Post by oldfred on 2010-08-06
You should install grub to the external and set it as first to boot. Install windows boot loader to the internal and if external not found it will boot internal.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by computerguts on 2010-08-06
ok, thanks I will try both of those 
if neither work I will let you guys know

---

### Post by computerguts on 2010-08-07
thanks, the instructions from source forge worked, thanks both of you

---

### Post by eriktheblu on 2010-08-07
I make it a point when installing to a USB disk to physically disconnect the internal HDD. There's probably a software method, but this way I know for certain it will not mess with the MBR.

---

### Post by computerguts on 2010-08-07
Thanks for the tip, I do that when installing windows to a second internal hard drive, that way I don't format my data from my old hard drive, I guess I should start doing that with ubuntu and other linux distros to.

---

