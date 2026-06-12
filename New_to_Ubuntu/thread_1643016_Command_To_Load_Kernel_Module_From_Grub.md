---
title: "Command To Load Kernel Module From Grub?"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by thelonelywind on 2010-12-11
Hello, and thank you for reading. 

Objective : Boot Ubuntu from partition using NeoGrub and Ubuntu 10.10 ISO files (ISO files are on the partition) 

The other day I made a partition (hd0,2) and used Unetbootin to install the Ubuntu 10.10 ISO to that partition which basically just extracted the ISO to the partition. Then I installed NeoGrub to the Windows Boot Menu and after I choose NeoGrub I insert these commands to try and load/boot Ubuntu like I would from lets say... a usb. 

I type in .... 

root=(hd0,2) (Sets GRUB's root device to the drive where the OS images are stored)

#2 kernel /casper/vmlinuz (Load the kernel image)

#3 module /??????/?????? (Load Module) 

#4 boot


So my problem is, where do I locate the module file in the Ubuntu ISO files I put on the partition (so that I can load the module and boot)? Or if I'm just doing it plain wrong help me out please! I am rather new to Ubuntu.

---

### Post by bodhi.zazen on 2010-12-11
Usually, if you need something loaded, you build it into the initrd

If you do not need it initially loaded, you configure the module to then be loaded (/etc/modprobe.d)

[http://www.ibm.com/developerworks/linux/library/l-initrd.html](http://www.ibm.com/developerworks/linux/library/l-initrd.html)

Hard to give you more specific advice.

---

### Post by iponeverything on 2010-12-11
an easy way to add a module to initrd is to copy it to a file with gz extension, gunzip it and mount it via loopback. After you add the module to modules directory -- umount the loop, gzip it again and rename it.

I would keep a backup of the original, it there was one.

---

### Post by oldfred on 2010-12-11
If you just want to boot the ISO you can do that directly.

 
HardDrive 
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

---

