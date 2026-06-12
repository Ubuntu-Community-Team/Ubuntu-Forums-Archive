---
title: "occasional problem"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by ACorder on 2010-07-11
I'm pretty much completely new to linux, i dabbled with it a couple years ago but my laptop crashed and that was the end of it. I just recently decided to get an external HDD to back up all of my stuff and figured i'd install Ubuntu on it as well as back up all of my important files, and keep windows vista on the internal HDD. It works great.. most of the time. Every once in awhile when i turn on or restart the computer i get an 'error: no such disk' but upon another restart it loads right to the GRUB and works like a charm, though it shows two different versions for Ubuntu as well as two different recovery modes. Everything else works great with no problems..and i guess this isn't a major problem since it's only occasional, just more of an annoyance.

---

### Post by themusicalduck on 2010-07-12
The two different versions that are shown are two kernels. Everytime a new kernel is installed in an update, it is listed on the Grub menu. You can remove them if you like with Ubuntu Tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) under Package Cleaner, Clean Kernels.

For the error: no such disk problem, I'm not sure why that would happen. Does it happen when you select Ubuntu or just when the computer is turned on? Is it a USB drive?

By the way, since you are new to Ubuntu, [http://www.ubuntu-manual.org](http://www.ubuntu-manual.org) might be useful to you.

---

### Post by diablo75 on 2010-07-12
Seems strange for the external hard drive to occasionally fail to boot.  I'm going to assume that you have grub installed on the primary hard drive along-side Windows, which of course calls on the external for booting either after the 10 second default countdown or when you press the Enter key to select Ubuntu from the menu.  Have you tried to see if the odds of this problem occurring have any relationship to the amount of time that passes from the moment grub appears to the moment Ubuntu is selected?  I'm just wondering if calling upon the external "immediately" vs. 10 seconds or so later has any impact.

---

### Post by ACorder on 2010-07-12
Since i posted i've been just searching and searching, and thinking trying to find anyway to fix it. I fixed the kernal problem, no big deal, but grub isn't even loading sometimes when it says no such disk, it is the UUID of the external HDD, and yes  it is USB, and i think it's cause it tries to find the external HDD immediately upon starting the computer, and the external HDD hasn't powered up yet..just my assumption, and it's also everytime i do a fresh boot or restart. So it's only when power is lost..when it comes up with the error message i just ctrl-alt-del and it reboots without cutting off power and it works just fine. Also i ran the Boot Info Script and it shows that Grub is installed on the internal Windows HDD and there is no boot loader in the MBR of the external HDD.

---

### Post by diablo75 on 2010-07-12
> **ACorder said:**
> Since i posted i've been just searching and searching, and thinking trying to find anyway to fix it. I fixed the kernal problem, no big deal, but grub isn't even loading sometimes, and i think it's cause it tries to find the external HDD immediately upon starting the computer, and the external HDD hasn't powered up yet..just my assumption, and it's also everytime i do a fresh boot or restart. So it's only when power is lost..when it comes up with the error message i just ctrl-alt-del and it reboots without cutting off power and it works just fine. Also i ran the Boot Info Script and it shows that Grub is installed on the internal Windows HDD and there is no boot loader in the MBR of the external HDD.

I think your assumption about the hard drive not being ready in time for boot is right.  The only thing I could think to try is find a feature in the BIOS that might slow the boot sequence down a hair.  Disable any fast booting features, perhaps change your boot device priority settings to look at other devices first before USB, like the CD-ROM or network interface.  Kind of a dumb way to go about fixing this but it's a step up from hitting CTRL-ALT-DEL.

---

### Post by ACorder on 2010-07-12
I think i have those problems fixed, deleted the old kernals, also switched some things in the BIOS so it does thorough update and tries to boot on everything else first, but now grub2 isn't showing an option to boot Windows Vista, when i update-grub i get 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done


i can still access the whole HDD from within ubuntu, just can't boot up vista

---

### Post by ACorder on 2010-07-12
Nevermind, got it all sorted out and working again

---

