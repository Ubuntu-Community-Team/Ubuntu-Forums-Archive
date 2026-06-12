---
title: "dual boot issues"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by jfkehoe on 2009-04-05
I almost hate to be posting this, but I'm having a some issues narrowing down my search on this forum to find the information I need. 

Here is as short of story as I can make: 
1. I attempted to install ubuntu dual boot on an xp box with two drives, grub got lost and I couldn't boot anything
2. Ubuntu ended up installed on one drive, windows on the other (which is cool) 
3. Pulled the windows and got ubuntu working. 
4. Pulled ubuntu drive and reinstalled xp on the other drive, its working
5. Installed both drives, grub comes up and asks which which OS (so far so good), ubuntu works, windows doesn't (expected) 
6. /boot/grub/stage1 is (hd0,4) right now and there are two drives 
7. menu.lst shows windows on (hd0,0) which is wrong. so I edit the command line of windows start (before modifying menu.lst) to make it (hd1,0), doesn't work... (NTLDR is missing) and that's where my issue seems to lie.  In grub (at start up) I can't seem to find hd1 at all. In ubuntu I can see it and in grub after ubuntu loads. 

Any suggestions?  I would be grateful for any help. 

I am sure that I will be asked for the following information, so here it is: 
**device.map:**
(hd0)	/dev/sda
(hd1)	/dev/sdb

**sudo fdisk -l:**

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0730ccb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20669   166023711    7  HPFS/NTFS
/dev/sda2           20670       24321    29334690    5  Extended
/dev/sda5           20670       24165    28081588+  83  Linux
/dev/sda6           24166       24321     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4862    39053983+   7  HPFS/NTFS


**end of menu.lst**
## ## End Default Options ##

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=0648e1d6-0d06-49c0-b07e-a9b0e4d03b36 ro quiet splash
initrd          /boot/initrd.img-2.6.24-23-generic
quiet

title           Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.24-23-generic root=UUID=0648e1d6-0d06-49c0-b07e-a9b0e4d03b36 ro single
initrd          /boot/initrd.img-2.6.24-23-generic

title           Ubuntu 8.04.2, memtest86+
root            (hd1,4)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Bakon Jarser on 2009-04-05
I think this post should help you:

[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by ranch hand on 2009-04-05
Does xp boot if you pull the ubuntu drive?

---

### Post by -kg- on 2009-04-05
It sounds to me like you have two options.

First, you have two separate drives with a viable operating system and bootloader for that operating system on each.  When wishing to switch to the other operating system, you could go into BIOS and change the boot order of the drives, which would tell BIOS which disk you're looking to boot from.  This would keep both drives (and the OSes on them) autonomous from each other, as you could hide the other drive partition(s) from the OS you are using.

Or, you can put them in in the order that you want them, then reinstall GRUB into the MBR of whichever drive you select as hd0 (which should be set as the first hard drive to be checked for booting).  That way, GRUB is where it belongs, and when you reinstall GRUB, it will (or should) point to the correct bootable partition for each OS.

A method for reinstalling GRUB is on the following link, the third post down.  And if you have any further questions, just post.

[http://ubuntuforums.org/showthread.php?t=1114171]("http://ubuntuforums.org/showthread.php?t=1114171")

Oh, and I probably don't need to tell you to ignore the part about "After the XP install."

Basically, you are opening a terminal and running GRUB under root privileges.  You're looking for where GRUB stage 1 is located, moving there, and then running GRUB install to hd0, which is the Master Boot Record of your first hard drive.

When it installs, it should detect your Windows partition as well as your installation, and the information in your menu.lst should be right.

Hope this helps!
):P

---

