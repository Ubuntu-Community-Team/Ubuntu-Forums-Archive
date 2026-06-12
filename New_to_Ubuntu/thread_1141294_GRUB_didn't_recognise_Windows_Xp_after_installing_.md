---
title: "GRUB didn't recognise Windows Xp after installing Ubuntu 9,04"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by SACHINVD on 2009-04-28
I have installed fresh ubuntu 9.04.
After installation when i restarted PC i found no option for Windows Xp in grub menu.

what is the problem ?
whether i need to change menu.lst ?

Current content of menu.lst are

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dcb9b8b-0452-461c-9242-4cebc5daa298 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dcb9b8b-0452-461c-9242-4cebc5daa298 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/memtest86+.bin
quiet

---

### Post by Kosimo on 2009-04-28
> **SACHINVD said:**
> I have installed fresh ubuntu 9.04.
After installation when i restarted PC i found no option for Windows Xp in grub menu.

what is the problem ?
whether i need to change menu.lst ?

Current content of menu.lst are

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dcb9b8b-0452-461c-9242-4cebc5daa298 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7dcb9b8b-0452-461c-9242-4cebc5daa298 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7dcb9b8b-0452-461c-9242-4cebc5daa298
kernel		/boot/memtest86+.bin
quiet



Which option did you choose during the installation / partitioning?

---

### Post by x33a on 2009-04-28
try adding this to the end of the menu.lst```


# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```(hd0,0) means the first partition of the first disk. change it to where you have xp installed.

---

### Post by SACHINVD on 2009-04-28
In windows i have four partitions C,D,E and F and Xp is installed on D drive.

In case of ubuntu D: partition corresponds to /dev/sda5

so is it (hd1,0) ?

---

### Post by x33a on 2009-04-28
try hd(0,4)

---

### Post by SACHINVD on 2009-04-28
(hd0,4) didn't work.

I got error "Invalid device requested"

---

### Post by x33a on 2009-04-28
post the output of
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by SACHINVD on 2009-04-28
Output of fdisk -l is

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcfddcfd

Device Boot Start End Blocks Id System
/dev/sda2 * 2434 7969 44467920 f W95 Ext'd (LBA)
/dev/sda3 7970 9729 14137200 c W95 FAT32 (LBA)
/dev/sda5 2434 4866 19543041 7 HPFS/NTFS
/dev/sda6 4867 7299 19543041 7 HPFS/NTFS
/dev/sda7 7300 7931 5076508+ 83 Linux
/dev/sda8 7932 7969 305203+ 82 Linux swap / Solaris

and output of cat /etc/fstab is

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7dcb9b8b-0452-461c-9242-4cebc5daa298 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=00e99932-1756-465e-b958-f795ff341f89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by x33a on 2009-04-28
hmm.. there aren't any sda1 and sda4 for some reason.

well, you can try hd(0,2)

---

### Post by SACHINVD on 2009-04-28
That also not worked, got error   starting up . . .          Remove disk or any other media      press any key to restart        
after pressing enter key following text displayed 
DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER

---

### Post by x33a on 2009-04-28
well, you can try to first fix windows bootloader, and then reinstall grub.

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

other than this i am out of ideas.

---

### Post by SACHINVD on 2009-04-29
Now i get to know why GRUB not detected my XP.

because what i did ......... to increase size of ext3 for linux i freed some space from C drive but i was unable to merge it so i deleted whole c drive and kept it as freed space in thinking that i would format that it in Window.

but as c: doesn't exit windows was not starting.

Thanks to X33a  !!!

---

### Post by x33a on 2009-04-29
glad, things got sorted :D

---

