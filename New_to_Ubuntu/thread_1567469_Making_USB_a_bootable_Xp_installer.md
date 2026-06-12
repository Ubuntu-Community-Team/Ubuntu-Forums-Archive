---
title: "Making USB a bootable Xp installer?"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by JamesParnell on 2010-09-03
After hours of hunting, I've found my copy of my windows CD (which broke a while ago - yes, it is a legit copy) stored on my HDD, but i have no CD-R's floating about and the only CR-RW I have wont work (test run completes fine, real run fails at 37mb), so my only option is to stick it on a USB stick. now i have a 4gb stick with gparted on it (just wiped) and was wondering, in 10.04, how would I go about doing the following:

Make the usb bootable
burn (or place) the content of the .iso of the cd into the usb
get it to actually work :P

---

### Post by ubudog on 2010-09-03
Try unetbootin, it's in the repos.

---

### Post by C.S.Cameron on 2010-09-03
I don't think Unetbootin will do it but you might search the EEE site, I seem to recall instructions came for installing XP when I got my daughter an EEE.

---

### Post by lbrty on 2010-09-03
> **ubudog said:**
> Try unetbootin, it's in the repos.

According to [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) UNetbootin will not write a Windows OS to a USB drive.

> UNetbootin allows you to create bootable Live USB drives for Ubuntu, Fedora, and other Linux distributions without burning a CD.

---

### Post by Ducatiboy Stu on 2010-09-04
[http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/](http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/)

---

### Post by lbrty on 2010-09-04
> **Ducatiboy Stu said:**
> [http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/](http://www.downloadsquad.com/2009/08/27/make-a-bootable-usb-installer-for-windows-xp-vista-7-with-wint/)

I believe the OP is referring to installing a bootable Windows .iso OS to a USB flash drive on Ubuntu 10.04. I have not found or know of a solution as of yet.

---

### Post by ubudog on 2010-09-05
Sorry, didn't know that.  Maybe there's another program like unetbootin that will do it for you.

---

### Post by CharlesA on 2010-09-05
The only way I was able to get XP to install from USB was to use a Windows program, but I cannot recall the name off the top of my head.

I don't know of any way to create a bootable XP USB stick using Ubuntu.

---

### Post by MrWES on 2010-09-05
deleted

---

### Post by lbrty on 2010-09-05
> **CharlesA said:**
> The only way I was able to get XP to install from USB was to use a Windows program, but I cannot recall the name off the top of my head.

I don't know of any way to create a bootable XP USB stick using Ubuntu.

It works really well too. It's called WinToFlash. That would be great if there was a program for Ubuntu.

[http://download.cnet.com/WinToFlash/3000-2094_4-10974471.html](http://download.cnet.com/WinToFlash/3000-2094_4-10974471.html)

---

### Post by CharlesA on 2010-09-05
> **linuxliberty said:**
> It works really well too. It's called WinToFlash. That would be great if there was a program for Ubuntu.

[http://download.cnet.com/WinToFlash/3000-2094_4-10974471.html](http://download.cnet.com/WinToFlash/3000-2094_4-10974471.html)

That was it. Thanks. Now that I think about it.. I wonder if it would run in WINE.

---

### Post by ubudog on 2010-09-06
Cool.

---

