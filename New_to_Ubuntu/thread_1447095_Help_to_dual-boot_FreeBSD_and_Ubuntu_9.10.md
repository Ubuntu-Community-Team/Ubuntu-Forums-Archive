---
title: "Help to dual-boot FreeBSD and Ubuntu 9.10"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by Ahava591 on 2010-04-04
Could anybody help me dual-boot these two OS? Really I just want to screw around with FreeBSD, play around with it, learn from it, etc.

I currently have Ubuntu 9.10; I have roughly one thousand files that I have to back up, which I will do anyway.

Some specifics I need help with are:

Will I have to wipe my drive? I have one(1) 500GB hard drive; Ubuntu is my only operating system.

If I do have to start from scratch, which operating system should I install first and for what reasons?

Using the Disk Utility located in System/Administration/Disk Utility, my hard drive appears to be divided thusly:
490GB ext4 filesystem;
10GB extended, which appears to be where my swap space is located.


I have made a Live USB for FreeBSD using a 2GB USB-drive and ImageWriter. I used my BIOS to change the boot device priority to be: USB, CD/DVD and then the hard drive.

I have an ASUS M4A78LT-M LE motherboard, an Nvidia 9800GT 1GB video card, (as well as an integrated video chipset,) 4GB DDR2 RAM and an AMD Phenom II X2 550 Black Edition CPU, if any of that hardware info helps at all.


Thank you for any help you can provide, and I'm sorry if it seems like I'm being needy or bossy, I'm just trying to figure out how all of these things work.

---

### Post by NightwishFan on 2010-04-05
I would assume all you need is free space for a freebsd partition. I have never used freebsd though. If you want to recover GRUB after installing a new OS, use a live cd and follow the process here.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Paqman on 2010-04-05
> **Ahava591 said:**
> 
Will I have to wipe my drive? I have one(1) 500GB hard drive; Ubuntu is my only operating system.


No, but you wil have to partition it before you install BSD, as it doesn't have it's own partition editor. You'll need to create a primary partition, as BSD can't be installed inside an extended partition.

> If I do have to start from scratch, which operating system should I install first and for what reasons?

It makes no difference. If you want to keep using Ubuntu's Grub bootloader then make sure you DO NOT install BSD's bootloader. There should be an option in the install process to skip this. Then just boot up into Ubuntu and run this command in a terminal:
```
sudo update-grub
```
Then when you reboot you'll be able to pick which system you want.

> Using the Disk Utility located in System/Administration/Disk Utility, my hard drive appears to be divided thusly:
490GB ext4 filesystem;
10GB extended, which appears to be where my swap space is located.

I'm not sure whether BSD will see your swap, so i'd either move it (which will require you to modify Ubuntu to suit) or simply create a second swap just for BSD's use.

You might also want to take a look at PC-BSD, which is based on FreeBSD, but contains more up-to-date stuff (such as KDE 4.3 instead of 3.5), 3D Nvidia drivers, and Compiz Fusion.

---

### Post by Ahava591 on 2010-04-05
I suppose I'll go with PC-BSD instead, then.

What are your opinions on GParted as a partition manager? Any major bugs or other concerns?

If I understand it correctly, I'll make a roughly 25 gig primary partition for PC-BSD, then maybe a five-ten gig swap partition for it as well. Is this correct?

---

### Post by NightwishFan on 2010-04-05
Gparted is fine, it is what I use.

---

### Post by Ahava591 on 2010-04-05
> **NightwishFan said:**
> Gparted is fine, it is what I use.
Okay, thank you so much for your help.

---

