---
title: "On Boot looking for removed hard drive"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by held7over on 2011-02-13
Ubuntu 10.04  I had two hard drives in my computer, but I removed one and transferred it to another computer.

In my notes, I am showing that the command "sudo update-grub" is used to update Grub when a hard drive is added or removed.....so I executed that command in terminal. 

However, on boot, my system spends a long time looking for the missing drive and finally asks me if I want to (S) Skip looking for it or (M) Manually find it......so.....evidently the update-grub command isn't doing what I thought it was suppose to do.....or I am missing something in the formula of the command...

How do I change Linux's mind on this matter?

Thanks! :D

---

### Post by ajgreeny on 2011-02-13
More likely that an edit of /etc/fstab is needed if the now removed disk was previously mounted at boot time automatically, as I suspect the system may be looking to mount that removed disk.

Can we see the output of ```
sudo fdisk -l
sudo blkid
cat /etc/fstab
``` one at a time please.

---

### Post by held7over on 2011-02-13
The hard drive that I removed was slaved (sdb) to my primary drive (sda), although the slave drive (sdb), had an operating system on it....just in case. I was using rsync everyday to back up the primary (sda) to the slave (sdb) drive.

Here's the info you asked for:

lucky@ispy:~$ sudo fdisk -l
[sudo] password for lucky: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002caf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+  83  Linux
/dev/sda2            1913       30401   228837862    5  Extended
/dev/sda5            1913        2034      979933+  82  Linux swap / Solaris
/dev/sda6            2035       30401   227857896   83  Linux
lucky@ispy:~$ sudo blkid
/dev/sda1: UUID="dd373a27-bceb-4032-924d-d44568160e47" TYPE="ext4" 
/dev/sda5: UUID="a98a717f-ffd4-47e0-8fa2-7f88c7db0cc7" TYPE="swap" 
/dev/sda6: UUID="18c1e92a-9da5-437f-91fd-c6d4b87e81c6" TYPE="ext4" 
lucky@ispy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=dd373a27-bceb-4032-924d-d44568160e47 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=18c1e92a-9da5-437f-91fd-c6d4b87e81c6 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=a98a717f-ffd4-47e0-8fa2-7f88c7db0cc7 none            swap    sw              0       0
# swap was on /dev/sdb2 during installation
UUID=5356aa7e-8e81-4017-bcdf-4e35aef7d231 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
lucky@ispy:~$

---

### Post by drs305 on 2011-02-13
Delete these two lines regarding swap, which reference a partition not currently on this system (as found by the "blkid" results):

> [COLOR="DarkRed"]# swap was on /dev/sdb2 during installation
UUID=5356aa7e-8e81-4017-bcdf-4e35aef7d231 none swap sw 0 0[/COLOR]

Note that even though the comment references sdb2, these comments are not updated to changing conditions and should not be trusted unless verifed by other means.

You can edit the file with:
```
gksu gedit /etc/fstab
```

---

### Post by held7over on 2011-02-13
Hey! It's fixed!  Thanks!

---

