---
title: "unable to login to Ubuntu after installation via wubi in windows XP"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by cloube on 2011-01-16
hi  im new on ubuntu and unix. need some help. my laptop is running on  intel pentium M processor 1400Mhz 587 Mhz with 1.23G ram microsoft XP 2002 SP 2.

i install ubuntu via wubi which installed ubuntu 10.4 . after finish  downloading the package, i boot my PC and have dual selection either  "window xp" or "ubuntu" .i finish the installation(after editing i915.modeset=1) on selecting ubuntu.  after that the system reboot.after rebooting the system have selection either   to use "window xp" or "ubuntu", i select ubuntu but then it pop out

GNU GRUB 1.98-1 ubuntu6
"MICROSOFT XP Professional "

i can't proceed to use ubuntu .it only will select microsoft XP and will revert back to the dual OS selection page  .it will go into loop when i select ubuntu on the selection to the previous page and only can select windows XP as OS. thus i can't login to ubuntu.
anyone have idea or can help me on this?

---

### Post by bcbc on 2011-01-16
Did you click on the SKIP button while you were installing? This is a known issue - you have to reinstall to fix it.

FYI If and when you get Wubi ubuntu running, do not update packages grub-pc and grub-common when prompted by the Update Manager.

---

### Post by diablo75 on 2011-01-16
I am not a fan of Wubi.  I would recommend you go to your control panel in Windows and uninstall it via the Add/Remove Programs applet, and then reinstall Ubuntu by burning a Live CD ISO file (which you can download from Ubuntu.com; there are instructions for how to correctly burn with links to software (InfraRecorder) to do it).  You will boot from the disc and install Ubuntu alongside Windows on it's own partition.

---

### Post by cloube on 2011-01-17
i've installed using wubi in the first place because my laptop is an old laptop and i don't have a CD-RW to burn ubuntu . after the first reboot , and the ubuntu is fnalizing and is downloading the package,my laptop suddenly restart itself. i've tried for 4 times and it happen the same things .the downloading file unable to finish the installation.For the 5th time i just press skip to finish the installation.

i try to find way to burn ubuntu into the CD and update in the forum

---

### Post by diablo75 on 2011-01-17
> **cloube said:**
> i try to find way to burn ubuntu into the CD and update in the forum

It's possible your laptop supports USB booting, but the older it is, the less likely it can.

You can use Windows + unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to create bootable USB flash drives, which work just the same as a burnt CD would.

---

### Post by cloube on 2011-01-17
> **diablo75 said:**
> It's possible your laptop supports USB booting, but the older it is, the less likely it can.

You can use Windows + unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to create bootable USB flash drives, which work just the same as a burnt CD would.



nope i guess my laptop don't support the usb booting...my bad :( .

---

### Post by mastablasta on 2011-01-17
perhaps you can:
 
1. get someone else to burn the ISO to the CD for you
2. order one free CD to be shipped (might take 5-6 weeks) from Cannonical
 
--- 
 
The reason why propperly burned LiveCD is good to have is that if anything goes wrong you will have a working system on the CD. it also feratures plenty of good programmes that can help you recover data. And you can test (although it will be slow) if everything works before installing it, by booting the system off a CD.
 
1.4Mhz with 1.2GB ram will run very nicely. I had a similar setup before. Appart from flash everything ran great. Though i still upgraded the motherboard and processor for other reasons.

---

### Post by cloube on 2011-01-21
Just finish installing  ubuntu 10.10 on my laptop. and exploring it now. thanks for all the help and suggestion..:D

---

