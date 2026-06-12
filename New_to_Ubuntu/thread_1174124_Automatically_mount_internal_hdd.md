---
title: "Automatically mount internal hdd"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by gzav on 2009-05-30
Hi all,

I've been using Xubuntu 8.1 for a while and have to do a clean reinstall because my computer messed up. But I'm hesitating between Xubuntu and Ubuntu. My computer is a laptop and i really like that Xubuntu is so fast and lightweight compared to Ubuntu. But one thing Ubuntu has for it is that "Places" tab where all internal harddrives show up automatically. So i'm wondering if it's possible to have the same feature in Xubuntu or a way to automount a hard drive automatically upon booting? Is it possible?

---

### Post by Elfy on 2009-05-30
Use fstab - if it's ntfs the easiest way is to use ntfs-config gives you a tool to do the work, pysdm will work with linux formats I believe.

If you want to do it by hand - [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

If you need help - we'll need to know a few things - what you want to call the partition when it has mounted and the results of the following

```
sudo fdisk -l
ls -al /dev/disk/by-uuid
cat /etc/fstab
```

Please use code tags around any pastes - [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by gzav on 2009-06-21
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e046cd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785        4054    26260600    7  HPFS/NTFS
/dev/sda3            4054       18140   113150810+   7  HPFS/NTFS
/dev/sda4           18141       19457    10578802+   5  Extended
/dev/sda5           18141       19214     8626873+  83  Linux
/dev/sda6           19215       19457     1951866   82  Linux swap / Solaris

```

```
ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 140 2009-06-21 16:12 .
drwxr-xr-x 6 root root 120 2009-06-21 16:12 ..
lrwxrwxrwx 1 root root  10 2009-06-21 16:12 1b838355-162b-4d3b-a1f4-fb2764057235 -> ../../sda6
lrwxrwxrwx 1 root root  10 2009-06-21 16:12 2898BD9998BD65CA -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-06-21 16:12 5E70369D70367BB9 -> ../../sda3
lrwxrwxrwx 1 root root  10 2009-06-21 16:12 8ed0a0ba-41d6-48f8-a98b-c00d86b8ef8f -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-06-21 16:12 AAD0BEF2D0BEC43B -> ../../sda2


```

```
 cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8ed0a0ba-41d6-48f8-a98b-c00d86b8ef8f /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=1b838355-162b-4d3b-a1f4-fb2764057235 none            swap    sw              0       0

```

There's all the code requested. The HDD I would like to automatically mount is sda3. Would it be possible to have it automatically under "places" like in Ubuntu?

(I'm sorry I didn't reply sooner, I got caught up in some stuff before coming back to this)

---

### Post by Elfy on 2009-06-21
Hi - as I said, install ntfs-config and use that tool to mount sda3 - it's an ntfs partition

```
sudo apt-get install ntfs-config
```

Once installed there will be an entry in System Tools - use that and you can get the partition to mount at boot, should be able to give it a name as you wish.

Reboot and the drive will be mounted.

---

