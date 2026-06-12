---
title: "Created file with ddrescuse, now what?"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by e-9 on 2010-02-22
Long story short:  I more or less destroyed my Windows drive to the point where I can't load Windows anymore so I used ddrescue:
```
ddrescue -r3 /dev/sdc2 /media/my500/olddrive logfile
```No errors to report, so now I have a ~107 gig binary file that I can't find a way to mount.  I've tried
```
mount -t ext2 -o ro /dev/sdc2 /mnt
The filesystem was not mountable
mount -o loop,offset=1378785165312 -t auto /media/my500/olddrive /mnt
The filesystem was not mountable
```On *fdisk -u -l /media/my500/olddrive* I get this output:
```
You must set cylinders.
You can do this from the extra functions menu.

Disk /media/my500/olddrive: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

                Device Boot      Start         End      Blocks   Id  System
/media/my500/olddrive1   ?   218129509  1920119918   850995205   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(368, 111, 45) logical=(13577, 238, 11)
Partition 1 has different physical/logical endings:
     phys=(371, 101, 51) logical=(119521, 238, 60)
Partition 1 does not end on cylinder boundary.
/media/my500/olddrive2   ?   729050177  1273024900   271987362   74  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(67, 115, 32) logical=(45381, 70, 3)
Partition 2 has different physical/logical endings:
     phys=(299, 114, 44) logical=(79242, 34, 29)
Partition 2 does not end on cylinder boundary.
/media/my500/olddrive3   ?   168653938   168653938           0   65  Novell Netware 386
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(114, 111, 32) logical=(10498, 56, 41)
Partition 3 has different physical/logical endings:
     phys=(353, 115, 52) logical=(10498, 56, 40)
Partition 3 does not end on cylinder boundary.
/media/my500/olddrive4      2692939776  2692991410       25817+   0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(167627, 190, 52)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(167630, 245, 26)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```I've tried testdrive on it, but still nothing appeared wrong.  I'm getting kind of desperate now.  I've simply try another recover, but in my *ahem* enthusiasm I deleted and reformatted the partition to make space for the restore.  Any help would be greatly appreciated.

---

### Post by blazemore on 2010-02-22
Have you tried
```
mount -t ntfs
```
?

---

### Post by e-9 on 2010-02-22
Forgot to mention that (tried a bunch of things but didn't write them all down):
```
NTFS signature is missing.
Failed to mount '/media/my500/olddrive': Invalid argument
The device '/media/my500/olddrive' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

---

### Post by e-9 on 2010-02-22
Is this actually a newbie question?

---

### Post by ibuclaw on 2010-02-22
I take it you are using this page as a reference? [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Not sure why you are setting an offset, since you dd'ed a partition, not an entire filesystem.

You could try:
```
sudo mount -t ntfs -o r,force,loop /media/my500/olddrive /mnt
```
Or run fsck/mount on the partition:
```

sudo fsck -ay /dev/sdc2
sudo mount /dev/sdc2 /mnt

```

Regards
Iain

---

### Post by e-9 on 2010-02-22
Correct, I used that website but chose to write to a file because I didn't have enough free space to set up a new partition for the ddrescue result.

First one puts out
```
NTFS signature is missing.
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@laurence-desktop:~# fdisk -l

```
Second
```
fsck from util-linux-ng 2.16
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdc2

```

---

### Post by e-9 on 2010-02-22
Any more ideas guys?

---

### Post by e-9 on 2010-02-23
Should I try posting this in another section perhaps?

---

