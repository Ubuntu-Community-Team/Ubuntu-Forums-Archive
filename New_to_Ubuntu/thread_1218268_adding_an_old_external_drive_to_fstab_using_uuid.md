---
title: "adding an old external drive to fstab using uuid"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by m_ad on 2009-07-20
This is a *very old* drive, one of Seagates first. It has a vfat filesystem.

I want to add this device to /etc/fstab so that I (not sudo) have write access to it, and also because I often add/remove external drives to this desktop, so the location of the drive changes. However, when I do

```
ls -l /dev/disk/by-uuid
```

I get

```
total 0
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 07D7-0402 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-07-20 12:00 1BF01501126BEDB9 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 4ac7144d-c29e-4cc2-a93e-e72c74c89005 -> ../../sda7
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 5FDE77B2003BFE84 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 923CF8013CF7DDE3 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 9493f3bc-b78f-4de9-a402-96c0091b3ca0 -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-07-20 03:08 e87c9022-8820-4e7b-b1d8-1886d825ca48 -> ../../sda6
```

In other words, it doesn't show up. The device (right now) is /dev/sdc1, so when I do

```
sudo vol_id /dev/sdc1
```

I get

```
/dev/sdc1: unknown volume type
```

One last thing, when I do

```
sudo blkid
```

It shows up! I get 

```
/dev/sdc1: LABEL="SEAGATE" UUID="0000-0F12" TYPE="vfat"
```

Now I have a UUID, right? Nope, when I add the device to /etc/fstab using the above UUID, and then try and mount it using

```
mount /media/Seagate
```

I get

```
mount: special device /dev/disk/by-uuid/0000-0F12 does not exist
```

What's up?

---

### Post by yabbadabbadont on 2009-07-20
Try mounting it using the LABEL instead of UUID in your /etc/fstab.  The uuid listed for that drive looks suspiciously like some generic that is used when a volume has a fat12 filesystem on it...  If it is a small drive, and hasn't been formatted in a long time, then it might be fat12 instead of fat32.  In which case you might need to mount it as msdos and not vfat.  I'm just guessing though, but it should give you some things to try out.

---

### Post by m_ad on 2009-07-20
Thanks for the response. I may have been wrong when I said it's *really* old. Its around 5 years old.

The problem is, when I do

```
ls -l /dev/disk/by-label
```

it doesn't show up.

In case it helps,

```
[matt@matt-desktop:~]$ sudo fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       48641   390708801    c  W95 FAT32 (LBA)
```

:lolflag: W95 FAT32 LBA? and BOOT?!

---

