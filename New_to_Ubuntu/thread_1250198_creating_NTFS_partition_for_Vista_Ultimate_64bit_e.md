---
title: "creating NTFS partition for Vista Ultimate 64bit ed"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by stalkier on 2009-08-26
Ok guys/girls I need help. I have a Linux filesystem and swap partition. I need to create a NTFS part for windows, since it is gay and will not install to USB disc. How do I need to do this without ruining my current Jaunty install on 270GB.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c7e36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37973   305018091   83  Linux
/dev/sda2           37974       38913     7550550    5  Extended
/dev/sda5           37974       38913     7550518+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a279a27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris
john@john-desktop:~$ 

```

---

### Post by compiledkernel on 2009-08-26
I believe your going to run into a problem with the installer after the fact stalkier. When you go to install Win32, I believe (and someone can correct me if Im wrong), it will destroy the mbr and create its own. This will render your existing install rather unhappy, which you can fix with a livecd and some fancy work. 

Generally speaking, its much easier to install windows FIRST, then install Linux on top of that.

---

### Post by Mark Phelps on 2009-08-26
Recommend that you use Gparted to shrink the sda1 (Linux) partition to allow 30GB for an NTFS partition.

Since Vista (or for that matter, ANY MS Windows OS) will automatically overwrite the MBR of the first hard drive it finds, you will need to both restore the MBR for Ubuntu, and add a stanza to your menu.lst file to select Vista for booting later.

But, other than that, it should have no effect on your Linux installs.

---

