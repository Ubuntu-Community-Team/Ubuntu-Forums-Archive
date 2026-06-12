---
title: "Is there a way to see the NTFS partitions right after boot"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Friccy on 2009-05-03
Hi!
I am using UBUNTU for quite a long time. Since the 8.10 there is a problem with starting the laptop (it freezes and remains frozen till I press a key), but also it can't see and access the NTFS partitions. I have the desktop image saved there, signature that is used in Thunderbird, that needs to be accessed right after boot. Sometimes even say that are not accessible, because they are not mounted. These partitions became visible just if I mount them manually, otherwise the desktop is blank, the Thunderbird mails have no signature, etc. 
How can I make them mounted at the boot, as were before the 8.10 edition?
I would appreciate any help!
Thanks!

---

### Post by Skrynesaver on 2009-05-03
Add the NTFS partition to /etc/fstab ie. add aline like
```
/dev/sda1    /Windows    ntfs    none    0    0
```
to /etc/fstab

---

### Post by unutbu on 2009-05-03
You can cause the NTFS partition to be mounted at boot time by adding an entry in /etc/fstab. See 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
for instructions on how to edit /etc/fstab.

If you would like some help making the entry, post
the output of 
```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by Friccy on 2009-05-03
> **unutbu said:**
> You can cause the NTFS partition to be mounted at boot time by adding an entry in /etc/fstab. See 
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
for instructions on how to edit /etc/fstab.

If you would like some help making the entry, post
the output of 
```

sudo fdisk -l
cat /etc/fstab

```

The output is:
sudo fdisk -l
[sudo] password for friccy: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e80241d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9716    78041604    7  HPFS/NTFS
/dev/sda2            9716       17097    59288576   83  Linux
/dev/sda3           17098       18512    11365987+   f  W95 Ext'd (LBA)
/dev/sda4           18513       19457     7590712+   7  HPFS/NTFS
/dev/sda5           17238       18512    10238976    7  HPFS/NTFS
/dev/sda6           17098       17237     1124487   82  Linux swap / Solaris

Partition table entries are not in disk order

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=5e8a0b46-795c-4a25-b3b1-5ceecb5b89b1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f25704c0-cf16-4bd1-926b-667b52c4d04b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by unutbu on 2009-05-03
The following will mount your NTFS partitions at the following mount points:


```
partition             mount point
sda1        ---->     /mnt/windows
sda4        ---->     /mnt/sda4
sda5        ---->     /mnt/sda5
```

You can change the mount points (/mnt/windows, /mnt/sda4, /mnt/sda5) to whatever you like, just change the corresponding strings everywhere it occurs below.

Open a terminal and type

```
sudo mkdir /mnt/windows /mnt/sda4 /mnt/sda5
gksu gedit /etc/fstab
```

Add these lines to the end of the /etc/fstab file:
```

/dev/sda1 /mnt/windows ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
/dev/sda4 /mnt/sda4 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
/dev/sda5 /mnt/sda5 ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=137 0 0
```

Save and exit gedit.
Reboot.

---

