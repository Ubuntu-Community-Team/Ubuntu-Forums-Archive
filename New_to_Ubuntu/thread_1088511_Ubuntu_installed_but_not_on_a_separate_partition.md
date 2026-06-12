---
title: "Ubuntu installed but not on a separate partition"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by ChIngalls on 2009-03-06
Hello everyone.

I'm totally new to the wonderful world of Ubuntu (I installed it yesterday) and I have some troubles making it work.

I have a dual boot (Vista and Ubuntu), but it looks like Ubuntu is not really on a partition of one of my 2 drives (I guess there are 2 drives, even though it's possible that I only have one that's factory partitioned with one partiton containing Vista, letter C, and the other one the rest of my files, letter D). There's just a folder called "Ubuntu" that contains every file used by the OS but I'd really like to keep both OS separate.
I thought that intalling Ubuntu would meant have it installed on a partition, not just in a folder I can access with Vista.

I installed version 8.10 this way:
- downloaded the .iso file
- since I don't have a cd-burner, I use UNetbootin to be able to boot from a USB stick
- despite I changed my BIOS settings to boot from USB, my computer booted from the hard drive, as usual
- I don't what the UNetbootin did, but I found a folder called "Ubuntu" with a .exe file in it, so I launched it and it installed Ubuntu without creating a partition (with 30GB on a drive allowed to Ubuntu) and it works.

So, it works (except for some drivers, but I'll eventually find a way to deal with it) but I'd like to "transfer" my new OS to a partition that can't be polluted with Vista viruses and stuff.

I don't know if my post is understandable, but I'd be glad to get some help. Thanks in advance.


Maybe that could help:
Acer Aspire 5100, AMD Turion 64 2GHz, 1GB RAM

---

### Post by albandy on 2009-03-06
you've installed the wubi version, it uses the files in ubuntu folder as a partition

---

### Post by ChIngalls on 2009-03-06
Thanks for the quick answer, albandy.
I specifically wanted to avoid the wubi installer for that particular reason. Now what could I do to have my Ubuntu OS on a separate partition? That's my problem.

---

### Post by albandy on 2009-03-06
When you insert the cd or the usb copy in windows, it will show you a menu (if not check what opens autorun.inf), you can select to install in a partition or inside windows (I have no windows so I can't use wubi to explain you the steps)

---

### Post by ahop on 2009-03-06
Did you simply move the .iso file onto the flash drive?  I am not an expert on this, but my assumption is that in itself will not work.  When you are able to burn to a disk, you simply don't want to burn the file because that in itself is not executable.  If you don't have ability to burn, I suggest finding a friend who does, or order a disk to be sent to you: [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by draclear on 2009-03-06
My advice would be to uninstall (via Control Panel) Ubuntu from Windows.  Then clean up your hard drive, defragment it, and then reboot your machine with the Ubuntu disk in the CD drive.

The system setup will walk you through it fairly easily.  When it comes to the actual partitioning I usually take the 'manual' option and set 10GB for the boot drive (/), 4GB for my swap file and have a separate home partition (/home) of 20GB (though the latter is not a requirement).  I have a dual boot system too and it works fine.  As I fiddle about with Ubuntu quite a bit, I tend to use my Windows partition for most of my data storage, as there's less chance of me 'doing something' to it.  The only other thing I use Windows for is iTunes.

From memory, one of the alternatives you will be offered will split the drive between windows and ubuntu quite amicably.  If in any doubt, go for that.

EDIT: Whoops, missed the bit about the CD burner.  Never mind.  I'm sure some kind friend will burn it on to disk for you.

---

### Post by Big_Croc7 on 2009-03-06
As others have said, you seem to have installed the wubi version.  I don't think there is any way to convert it to a standard installation.  If that's what you want, you-ll probably have to install again.

---

### Post by tarps87 on 2009-03-06
You have preformed the wubi version, from you post I assume that this is not what you want. The easiest way to transfer the install is to backup any data you need an reinstall it.
What when wrong was it did not boot from the usb device, it should have given you a few options if it booted from the usb. Some of them are:
Try Ubuntu
Install Ubuntu
Check cd (even though it is a useb :))

It also will be noticeable buy the Ubuntu logo on the screen.

I would suggest recreating the boot usb and setting the bios to boot from usb again. You may need to press a Fn (n = a number) key to select the usb device to boot from.

Hope this helps

---

### Post by ahop on 2009-03-06
A bit of a clarification on my point . . .

If when you open the USB drive (in Windows Explorer) you see the single file, you won't be able to boot.

If instead you see something like the below file tree, you just need to tweak bios to make sure USB is booting first.

```

.disk
casper
dist
install
isolinux
pics
pool
pressed
autorun.inf
md5sum.txt
etc...

```

---

### Post by avtolle on 2009-03-06
You could use LVPM ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) to make a permanent installation of your existing Ubuntu installation installed using Wubi. *Caveat*: I am unsure this works with 8.10.

---

### Post by suitedaces on 2009-03-15
> **avtolle said:**
> You could use LVPM ([http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)) to make a permanent installation of your existing Ubuntu installation installed using Wubi. *Caveat*: I am unsure this works with 8.10.

This isn't my exact issue, but I am wondering if this lvpm supports 8.10? It's an upgraded wubi 8.04 install.

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

