---
title: "grub2 install after windows 7 install"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by rmsmith87 on 2010-04-10
I installed Windows 7 and it eliminated grub2.  Ive been trying to reinstall following this articles. [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)
 
I get this result for the fdisk -l step.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea428

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           10200       14727    36371160   83  Linux
/dev/sda3           14728       19457    37993725    5  Extended
/dev/sda5           19178       19457     2249068+  82  Linux swap / Solaris
/dev/sda6           14728       18988    34226419+  83  Linux
/dev/sda7           18989       19177     1518111   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc27c4f8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       77825   625128288+   c  W95 FAT32 (LBA)


But when I try the next step all I get is this.
ubuntu@ubuntu:~$ sudo mount /dev/sda2/ mnt
mount: mount point mnt does not exist

Any help would be appreciated.

---

### Post by linuxman94 on 2010-04-10
You have to create that folder.

Enter this command:

```
sudo mkdir /mnt
```

---

### Post by rmsmith87 on 2010-04-10
ubuntu@ubuntu:~$ sudo mkdir /mnt
mkdir: cannot create directory `/mnt': File exists


I got this when I tried that.  I don't know if it makes a difference, but I am running off a livecd right now.

---

### Post by linuxman94 on 2010-04-10
OK that is good that it exists.

I just noticed a typo.

You put in:

```
sudo mount /dev/sda2/ mnt
```

Where it should be:

```
sudo mount /dev/sda2 /mnt
```

---

### Post by rmsmith87 on 2010-04-10
Ah.  Went through again and rebooted.  And both OSs boot.  Thanks.

---

