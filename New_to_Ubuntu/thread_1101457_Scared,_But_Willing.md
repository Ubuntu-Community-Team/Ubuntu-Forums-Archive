---
title: "Scared, But Willing"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by daniell59 on 2009-03-20
For sometime I wanted to install Ubuntu. I chickened out however. I was afraid that it would ruin my Vista operating system. I would appreciate it if someone could walk me through the process of installing Ubuntu 8.10 on my second hard drive. I left a partion there for it.

Thanks in advance

---

### Post by Therion on 2009-03-20
Have you tried running a LiveCD?  The LiveCD lets you take Ubuntu on a "test drive" without making any changes to your existing installation.  Pop in a CD, boot to it, play with Ubuntu.  Reboot, remove the CD and you're back in Vista like nothing ever happened.

Or, if you're really ready to take the plunge and install, sure, I can link you to some tutorials that will walk you through dual booting alongside your current Vista install.

---

### Post by leonardo_neo on 2009-03-20
Download this pdf book (which is free) from the link given below

> [http://www.ubuntupocketguide.com/download2.html](http://www.ubuntupocketguide.com/download2.html)

Then from this book, read how to install Ubuntu. This book has very nicely explained how you can do "dual-boot" which I think is best for you since you are freshly moving from Windows.

This book not only explains how you can install Ubuntu, but it also guides you through the basics of Ubuntu.

Best of luck :D

---

### Post by daniell59 on 2009-03-20
Yes I ran the program off the CD. Everything worked perfectly, even my wireless router. It is the installation that I am not sure of. I want to put it in the hard drive that does not have Vista. I am not sure how to do that.

---

### Post by SunnyRabbiera on 2009-03-20
actually you can install it on the same drive as vista, just make sure to compress your filesystem and defrag before doing it.

---

### Post by daniell59 on 2009-03-20
I would rather install it on my other hard drive. That is what I am confused about. How to do this.

---

### Post by ddnev45 on 2009-03-20
Your hard drives and partitions are numbered sequentially.

The first hard drive will be sda (is that where vista is installed?); the second hard drive will most likely be sdb (possibly sdc if your cd-rom is counted). The partitions on each drive will be numbered - i.e. sda1, sdb1, sdb3 etc .. Please note that the "s" may be reported as an "h" - hda, hdb. The main point is to avoid installing on your Vista drive, sda in this example.

Follow the instructions during the installation, when you get to the part about partitioning, I always select to do it manually. All your partition information will show up and you can select the free space you set aside for Ubuntu.

As far as I know, grub works fine with Vista. Search through the "Tutorials and Tips" forums for dual booting with Vista first.

And be sure to back up any important data on your Vista drive first.

---

### Post by mlentink on 2009-03-20
That is basically as simple as instructing ubuntu to do precisely that. During install, you will find that the ubuntu installer will call your first hard drive sda (with partitions sda1, sda2 sda..) and your second harddrive sdb (with partitions sdb1, sdb2...).

Just instruct ubuntu to install on sdb, and you Vista will be safe (well, to the extent that Windows is ever safe)

Edit: Wups, double, sorry...

---

### Post by daniell59 on 2009-03-20
Thanks to all for your informative replies. I hope to join the Linux community soon.

---

### Post by 123456789123456789123456 on 2009-03-20
two ways to install on the second drive.  Grub, that is linux boot loader, will most likely install onto the main sda master boot record.  and will boot to either disk from there.  This has caused problems with some people.  You can however, in options, settings under the install ubuntu installer.  Tell grub to install there Ubuntu is going to be installed.  You will either have to edit Vista's boot loader, to locate and run the grub from the second disk.  Or use BIOS to select which disk to boot from.  BIOS startup has a f function key setting, that allows you to select the device you want to start from.  when pressing it, it will give you something like, boot from cd rom, hard disk primary or master, hard disk slave, so on.

My friend does that to boot a second hard disk that contains Mac OS X.

---

