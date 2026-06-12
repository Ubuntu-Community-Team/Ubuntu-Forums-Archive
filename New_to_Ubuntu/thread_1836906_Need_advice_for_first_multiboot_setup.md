---
title: "Need advice for first multiboot setup"
date: 2011-08-31
forum: New to Ubuntu
---

### Post by JMT391 on 2011-08-31
Good evening folks, I have been using ubuntu on my netbook for a few months now and love it.  On my desktop I now want to tri-boot ubuntu windows 7 64-bit and OSX 10.6 (using BURG as a bootloader), but have been having extreme issues with it.

Details:
I have 3 HDDs, the plan was to use one for each OS.  One already had windows 7.  I installed ubuntu to another, booting to the win7 HDD by default.  I then found out about BURG and said "ooh eyecandy" and went for it.  After installing it, I got the grub rescue> prompt and was not able to boot into either OS from the win7 HDD.  Ubuntu worked when booting to its HDD as a primary.

After FINALLY getting BURG to work on the ubuntu HDD, it did not see windows.  I couldn't do a repair install and when I try to completely reinstall I get error messages (I tried gparted and windows disc to partition to NTFS).  Ubuntu (to no surprise) works perfectly with BURG.

My guess (keyword guess) as to what happened is I overwrote the win7 MBR (tried restoring it 2137428032 different ways, didn't work) when installing BURG improperly the first time, and now since theres an MBR from Ubuntu, windows won't install.  

My plan now is to install all 3 OS's to a single hard drive partitioned out, with all 3 sharing a partition for music and documents etc... How much space do you all give your OS's?  I was thinking 50gb for win7 (I have some games) 20 for ubuntu and 10 for OSX.  Also, if I install win7 first, then ubuntu, then OSX, and finally BURG, will I avoid having this happen again?  Does anybody know what could have happened before?  Sorry for the mouthful guys, I'm just at a total loss.  Thanks!

TL;DR
I destroyed my computer during a multi-boot attempt and want to multiboot win7 64-bit OSX 10.6 and ubuntu natty using BURG. How much should I partition for each OS and what order do I install everything in to avoid any MBR/bootloader problems?

---

### Post by oldfred on 2011-08-31
Welcome to the forums. But we cannot help with OSX unless you have an Apple Mac as forum rules prevent it.

Ubuntu Forums Code of Conduct
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

I always suggest each operating system on separate drives. Then each drive is independantly bootable.


Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

