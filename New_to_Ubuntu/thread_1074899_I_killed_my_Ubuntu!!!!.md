---
title: "I killed my Ubuntu!!!!"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by lee292 on 2009-02-19
I was planning on making a backup partition on my Ubuntu hard drive using gparted.  I had partitioned the drive into two and somehow got two copies of Ubuntu, one in each partition.  I used gparted to shrink one partition and reformat it, and expanded the other.  Alas, I erased the boot partition!  When I tried to boot up, Grub gave an Error 15.  How can I fix this so the other partition will boot?  I think I can save my data by copying it to a CD using the Live CD.  I can reinstall, but it means having to download lots of updates, and I'd rather not do that.  Help!

---

### Post by scorchgeek on 2009-02-19
The Live CD should work just fine. Just put in the CD and boot your computer. If it doesn't boot, you probably need to adjust the boot order in the BIOS.

---

### Post by lee292 on 2009-02-20
I can boot from the CD, but what do I have to do to get Ubuntu to boot from my hard drive? Won't a reinstall wipe out my updates and documents?

---

### Post by sonu 1807 on 2009-02-20
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You can recover your grub from live CD. Just follow the instructions on this thread

---

### Post by lee292 on 2009-03-01
Went up to the local community college and downloaded Intrepid and installed it.  Works much better!  Thanks, all!

---

### Post by presence1960 on 2009-03-01
> **lee292 said:**
> I was planning on making a backup partition on my Ubuntu hard drive using gparted.  I had partitioned the drive into two and somehow got two copies of Ubuntu, one in each partition.  I used gparted to shrink one partition and reformat it, and expanded the other.  Alas, I erased the boot partition!  When I tried to boot up, Grub gave an Error 15.  How can I fix this so the other partition will boot?  I think I can save my data by copying it to a CD using the Live CD.  I can reinstall, but it means having to download lots of updates, and I'd rather not do that.  Help!

try this next time instead of reinstalling:

[HTML]1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
whatever your hard disk + partition nr is, to install GRUB to a 
partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.[/HTML]

---

