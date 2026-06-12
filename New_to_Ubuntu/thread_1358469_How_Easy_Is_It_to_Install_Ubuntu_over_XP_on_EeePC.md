---
title: "How Easy Is It to Install Ubuntu over XP on EeePC?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by nictu on 2009-12-18
Hi Folks,
 
I've seen an Asus eeePc on Amazon, but it has XP pre-installed. I want to run ubuntu, so how easy to install over XP?
 
Help and advice much appreciated,
nictu.

---

### Post by daemonkity on 2009-12-18
I have that type of netbook, but I started out with XandrosLinux not XPWindows... can't imagine it's too much different in difficulty formatting over either to Ubuntu Remix, which I did using a flash drive and it was incredibly easy.

---

### Post by nwadams on 2009-12-18
which model eeepc is it? but ubuntu or ubuntu netbook remix run great on almost all eeepc netbooks. just download an iso image and use unetbootin to make a bootable usb.

---

### Post by Pierrot Lafouine on 2009-12-18
Hi
I have eeePC with XP-sp3, and want to install Ubuntu LTS.  So far, I failed to make a bootable USB key with Ubuntu install on it.  Any detailed indications on how to install this ?

Thanks

---

### Post by joes7 on 2009-12-18
Very easy. You can use the LiveCD or the Wubi installer. I recommend to download the ISO and then burn it into a CD,
```

http://www.ubuntu.com

```

---

### Post by Pierrot Lafouine on 2009-12-18
Thanks, but I dont have USC CD
Anyway to do that with USB stick or SD card ?
Thanks

---

### Post by sgosnell on 2009-12-18
Yes.  Get the Ubuntu liveCD .iso, download unetbootin, and then put the .iso on your SSD or another USB drive.  You only need 1GB size for this, but any larger size will work, as long as it will hold the .iso.  You'll need another 1GB drive for the liveCD.  Use unetbootin, running under Windows, to burn the .iso to the USB drive.  Then boot from the LiveCD on the USB stick, and use that to install Ubuntu onto your SSD.  If you want to get rid of Windows, it's easy, just tell the installer to use the entire sda drive.  It shouldn't take more than 30 minutes to do the whole thing, after you have the .iso downloaded.  That's the slowest part.

I don't recommend any of the netbook remixes.  I detest all of them, and prefer standard Ubuntu by far.  I have 9.04 installed, with the 2.6.32 kernel, and everything works out of the box.

---

### Post by Extract_Here on 2009-12-18
use a live usb for netbook and live cd for regular laptop or desktop

---

### Post by Pierrot Lafouine on 2009-12-19
Thanks,
I'm not sure I understood everything, but from previous post, this is what I tried:
1) Download and start UNetbootin on eeePC
2) In unetbootin, selected Ubuntu 8.04_Live, with USBDrive as destination
3) Waited 45 minutes for download and write on USB
4) Reboot eeePC, press F2 to get to BIOS, selected USB Boot
5) Ubuntu started from USB,
6) From menu, I selected Installation
7) I followed installation instructions, but now ask me to "Prepare partition".

I'm stock there, as I want dual boot, with XP-sp3.
Shouldn't this dual boot part of the menu selection ?
What do I do now to get this dual boot ?

Thanks

---

### Post by sgosnell on 2009-12-19
One of the options should be "install side by side".  This is what you want, it doesn't specifically say 'dual-boot', that's just one expression out of many.  You want to install Ubuntu side by side with Windows, and that shouldn't be a problem.

Try [this tutorial](http://www.psychocats.net/ubuntu/wubi) for more information.  It tells you how to use wubi, which I don't have a lot of experience with because I don't have Windows installed, but it may work for you.

---

### Post by Pierrot Lafouine on 2009-12-20
Hi
I tried Wubi as per previous post.
When selecting Ubuntu from menu, it start Ubuntu, but stop in command line BusyBox Built-in-Shell (ash).

What am I doing wrong ?

---

### Post by sgosnell on 2009-12-20
I don't know.  I've never bothered with wubi, I do a complete install.  Are you certain you have a good .iso?  Have you checked the md5sum, and then checked the disk for errors?  The instructions for verifying the md5sum are [here](https://help.ubuntu.com/community/HowToMD5SUM).  To check the burn on the disk, boot from it and select Check Disk for Errors.

---

### Post by Pierrot Lafouine on 2009-12-20
> **sgosnell said:**
> Are you certain you have a good .iso?
I have tried 2 versions : 8.04 (lts version) and 9.10, using Uebuntin to burn this on USB stick

> **sgosnell said:**
> Have you checked the md5sum, and then checked the disk for errors?
I have tried that to

Any other tutorial to install Dual Boot on eeePC ?

Thanks

---

### Post by sgosnell on 2009-12-20
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Also make sure you check the USB drive for errors after you do the burn, by booting from the USB drive and selecting "Check disk for errors", or something like that, before you actually try the install.  It's common to get errors even with a good .iso.

---

