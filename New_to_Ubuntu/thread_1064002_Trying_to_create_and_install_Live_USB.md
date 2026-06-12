---
title: "Trying to create and install Live USB"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by demeissner on 2009-02-08
Hi,

I've been using Wubi for a couple months and want to install to a dedicated partition.  I have not been able to create a Live USB on a pen drive that will actually make it through the bootup and begin the Ubuntu install.  I have tried the approaches on the Canonical's documentation page: Preparing Files for USB Memory Stick Booting, but can't get them to work.  I have tried several memory sticks, so the devices are not the problem.

Obviously, the problem is me.  %)  Can anyone offer me some straightforward help.

Many thanks,

Dennis

---

### Post by ptn107 on 2009-02-08
Try an install cd instead.

---

### Post by demeissner on 2009-02-08
> Try an install cd instead. 

Unfortunately, this is an Acer Aspire One, so no CD drive.  Maybe I'll need to get an external CD drive.

---

### Post by benerivo on 2009-02-08
If you are using Windows, then this live usb creator from Fedora may help...
[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)

---

### Post by unutbu on 2009-02-08
If the page "Preparing Files for USB Memory Stick Booting" that you were following is this one: [https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html)

then it will not work because that page assumes you have a Linux partition (/dev/sda1) instead of a Wubi installation. 

Unetbootin is a GUI program that runs under Windows (and Linux) which can install Ubuntu without the need of a LiveCD.

See 
[Unetbootin Homepage]("http://unetbootin.sourceforge.net/")
A [screenshot]("https://help.ubuntu.com/community/Installation/FromUSBStick") and short description of how to use unetbootin
[Other ways to install Ubuntu from Windows]("https://help.ubuntu.com/community/Installation/FromWindows")
[The papa link on all ways to install Ubuntu]("https://help.ubuntu.com/community/Installation#Installation") (including without a CD)

Be sure to back up all your important files (on both Windows and Wubi) before you try re-partitioning your system. Although it is possible to install Ubuntu without backing up first, you'll be on safer ground if you go into the process with good backups. Good luck :)

---

### Post by cyfur01 on 2009-02-08
Under Ubuntu 8.10 (Intrepid Ibex), you can use System->Administration->Create A USB Startup Disk to create a usb-startup disk (the program executed is called "usb-creator"). It's really simple, although I found that I had to re-write the master boot record to get it to boot. (That can be done from the terminal by running "install-mbr /dev/sdX" where sdX is your USB device.) With that, I configured my BIOS and was able to boot into Ubuntu without any problems.

---

### Post by demeissner on 2009-02-09
*Thanks*, one and all, for the thoughtful suggestions.  I'll play around with them and will re-post if no success.

---

