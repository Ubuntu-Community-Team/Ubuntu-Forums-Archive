---
title: "USB install"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by upshutdown on 2010-08-13
Is there any way to install Ubuntu on a usb HDD and boot from it?

---

### Post by zolr on 2010-08-13
Do you mean an external hard drive? If so, you should be able to use the Universal USB Installer to create a live "CD" from the iso on the drive.

From there, you should be able to restart your computer and go to boot management and choose USB (make sure there are no CDs or other flash drives plugged in before turning the computer on because it will ask you to restart otherwise)

---

### Post by upshutdown on 2010-08-13
Hi, thanks for replying.

So I have actually done that on my Macbook pro, but the problem is when i choose to boot form the external HDD in rEFIt, it says "failed to boot". Any ideas? Should i redirect the post to another forum? which?

---

### Post by zolr on 2010-08-13
Have you tried booting it on another computer? It might just be some weird incompatibility or maybe there was just an error when creating the live drive.

You could try posting on another forum as well, but I don't have any to really recommend; sorry.

---

### Post by upshutdown on 2010-08-13
No i haven't... I've tried to look around for solutions but i haven't found any :/ 

Ill redirect it else where.

---

### Post by zolr on 2010-08-13
Are you trying to boot on a mac or a pc? If you're tying to do it on a pc, with a current Windows configuration, perhaps you could try QEMU (virtualization system to run linux from within windows) Are you actually trying to install from the live cd or just test it?

Do you not have a CD or other USB device on hand; or do you just want to keep trying to get the hard drive to work?

---

### Post by zolr on 2010-08-13
You can look for assistance elsewhere, I'm just trying to offer ideas and suggestions. I haven't tried running an OS straight from an external hard drive before so I'm not positive how much help I can be anyway. Hopefully you find a solution one way or another.

---

### Post by upshutdown on 2010-08-13
I'm trying to boot off a mac, and I'm interested in installing it, because I want it so that my Mac OSX is taking 100% of the internal HDD, and use my external for Ubuntu, so i would love to get it to work :D

Any help is appreciated really!

---

### Post by zolr on 2010-08-13
Maybe this will help; I found this on another thread where someone was asking the same question:

"I just got it to work on my Macbook C2Duo 2.0!

Nothing worked until I used a 100mb big partition on my main harddrive  as /boot and installed grub on that instead of any MBR. Now Refit shows  Mac, Win and Linux on the main drive. Then grub is responsible for  loading ubuntu from the external drive.

Now I got MacOSX, Windows XP and /boot on the internal 80gb drive and Ubuntu on an external 300gb drive."

[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

So if you haven't tried something like that, that could work; although managing partitions isn't something I have ever had success with personally (granted, I have only made two attempts; one of which was on a hard drive that was having problems regardless).

---

### Post by zolr on 2010-08-13
Or maybe this will help:

[http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/](http://www.pendrivelinux.com/installing-ubuntu-to-a-usb-hard-drive/)

---

### Post by ugm6hr on 2010-08-13
Macs (even Intel) have specific problems...

Maybe ask at [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by upshutdown on 2010-08-13
Once again thank you for helping.

Ok so i guess my next step would be to install GRUB on a small 100 MB partition on my internal drive where Mac OSX is located that points to Ubuntu on the external usb HDD drive. Does that sound about right?
Any tips for that I might want to know?

---

