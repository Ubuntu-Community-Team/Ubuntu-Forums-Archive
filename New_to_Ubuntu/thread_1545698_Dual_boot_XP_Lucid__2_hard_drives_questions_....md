---
title: "Dual boot XP Lucid  2 hard drives questions ..."
date: 2010-08-04
forum: New to Ubuntu
---

### Post by CDSH on 2010-08-04
Hi Folks,
 
Complete Ubuntu NewB here (Windows Refugee). I have an old HP PC with XP already installed on the original HD (HP pre-installed XP). It works fine but I have no Rescue disks for it. I have disconnected that HD and installed a second HD where I have successfully installed Lucid. Lucid seems to be running fine (as far as I can tell).
 
Question (showing off my NewB-ness here): Where can I find "simple" instructions to make my system Dual Boot capable ? - hopefully without messing up either OS installation. 
 
I have searched hither and yon for details, but I am only finding examples with older versions of Ubuntu. Lucid seems to have no menu.lst and the info on Grub that I have found so far is a bit complex for my simple brain to wrap around.
 
Any assistance rendered to this Windows world escapee would be truely appreciated !

---

### Post by Mark Phelps on 2010-08-04
If you can boot into Ubuntu when only that drive is connected, there is really very little else you have to do ...
1) Reconnect the other drive
2) Continue to boot from the Ubuntu drive
3) Once into Ubuntu, open a terminal and enter "sudo update-grub"

This will generate a GRUB menu and should include an entry for Win XP.

When you reboot, you should be presented with a menu containing Linux kernel lines and an entry for Win XP.

It's as simple as that.

---

### Post by CDSH on 2010-08-04
> **Mark Phelps said:**
> If you can boot into Ubuntu when only that drive is connected, there is really very little else you have to do ...
1) Reconnect the other drive
2) Continue to boot from the Ubuntu drive
3) Once into Ubuntu, open a terminal and enter "sudo update-grub"
 
This will generate a GRUB menu and should include an entry for Win XP.
 
When you reboot, you should be presented with a menu containing Linux kernel lines and an entry for Win XP.
 
It's as simple as that.
 
Thank you !
 
OK, I reconnected and booted into Ubuntu.  I have not yet done the update-grub yet.  I would like to know first if that will permanently alter my windows OS ?  
 
Since I have not yet reached escape velocity, I am still locked into the microsoft gravity well and want to be sure of my options to bail out and start over without having shredded my parachute - if you can appreciate my drift here.

---

### Post by oldfred on 2010-08-04
No, a sudo update-grub just modifies the grub menu.

Some with multiple drives do find grub installing by default to sda on system updates of newer versions of grub. If you are booting with grub it really does not matter, but check which drive is sda & which is sdb. 

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by CDSH on 2010-08-04
> **oldfred said:**
> No, a sudo update-grub just modifies the grub menu.
 
Some with multiple drives do find grub installing by default to sda on system updates of newer versions of grub. If you are booting with grub it really does not matter, but check which drive is sda & which is sdb. 
 
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions
 
Thank you !
 
Here is what my fdisk looks like ...
 
================
 
Disk /dev/sda: 13.7 GB, 13676544000 bytes 
255 heads, 63 sectors/track, 1662 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00000a8f 
 
Device Boot Start End Blocks Id System 
/dev/sda1 * 1 1587 12743680 83 Linux 
/dev/sda2 1587 1663 609281 5 Extended 
/dev/sda5 1587 1663 609280 82 Linux swap / Solaris 
 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x8ce904f4 
 
Device Boot Start End Blocks Id System 
/dev/sdb1 1 579 4650786 b W95 FAT32 
/dev/sdb2 * 3314 9729 51528960 7 HPFS/NTFS
 
=====================
 
Does this look like it should ? sda has Ubuntu on it and sdb has WindowsXP. I'm just being careful before committing one of those acts of stupidity that I am all to capable of doing.

---

### Post by oldfred on 2010-08-04
Linux is in sda1 and it looks like your windows is in sdb2. The only issue may be if sdb was originally sda, the boot.ini may refer to the wrong drive when booting sda.
IF windows does not boot after the sudo update grub we can further review and make suggestions, but grub2 normally finds and makes windows think it is the first drive with a drivemap command.

---

### Post by CDSH on 2010-08-04
> **oldfred said:**
> Linux is in sda1 and it looks like your windows is in sdb2. The only issue may be if sdb was originally sda, the boot.ini may refer to the wrong drive when booting sda.
IF windows does not boot after the sudo update grub we can further review and make suggestions, but grub2 normally finds and makes windows think it is the first drive with a drivemap command.
 
Thank you !
 
Here is the terminal output from sudo update-grub ...
 
==============
 
 
Generating grub.cfg ... 
Found linux image: /boot/vmlinuz-2.6.32-21-generic 
Found initrd image: /boot/initrd.img-2.6.32-21-generic 
Found memtest86+ image: /boot/memtest86+.bin 
Found Windows NT/2000/XP on /dev/sdb1 
Found Microsoft Windows XP Home Edition on /dev/sdb2 
done 
 
==============
 
Hopefully it looks alright.  I tested it by booting into Ubuntu and XP and both seem to be working as expected.  I guess the real test will be when I try to do upgrades or updates to either/both systems and/or swap/replace HDs etc.  Yes, I'm that kind of person.
 
 
I'll try to figure out how to flag this thread as solved.
 
Thank you again for all the assistance !

---

