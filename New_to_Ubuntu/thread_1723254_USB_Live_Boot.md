---
title: "USB Live Boot"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by SquirrelyDirge on 2011-04-06
Alright, I'm not -entirely- certain as to this being the proper location for this post, however I am a beginner so...

Recently, I purchased a 16 GB Patriot USB pendrive with the intent of putting a copy of Ubuntu (10.04.02) onto this drive with a persistent memory space reserved for installed programs for live boot sessions.

Universal USB Installer, supposedly, permits this. However, I must confess that I do not know whether it has worked or not. Whenever I go to actually boot from the USB, I can manage to select the "live boot" option from the menu, but actually booting into Ubuntu never happens. On my desktop it hangs indefinitely at the splash screen with "Ubuntu" and the five loading dots. On my cousin's laptop, it hangs on the black screen where it lists all the operations that are actually happening. And on my netbook, it just completely bypasses it and boots Crunchbang !?.

Any help you may provide would be greatly appreciated!

---

### Post by rosencrantz on 2011-04-06
Hi SquirrelyDirge,
there are a number of ways to run Ubuntu from an USB stick, you could just try whether a different variant works better for you. See this link
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Cheers,
rosencrantz

---

### Post by oldfred on 2011-04-07
I do not think persistent can be that large.

With 16GB you have enough room for  a full install. Realize that USB is slower than a hard drive & writing to flash is real slow. System can be functional on USB flash depending on your expectations. I have a full install in a 16GB flash and it seems to work ok. Slow compared to hard drive but not unreasonable.

Install to flash drive is just like an install to any second drive except you make some setting changes to reduce writes. You need to use manual install so you get the choice on installing grub2's boot loader to the MBR of the flash drive. Grub likes to default to sda which can then cause problems.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)

See post #19 C.S.Cameron - recommends disconnection sda so grub can only install to flash drive.
Maverick now only gives combo box on grub location if you use manual install.
Lucid:
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

---

### Post by SquirrelyDirge on 2011-04-08
I got it working, thank you for your help!

---

