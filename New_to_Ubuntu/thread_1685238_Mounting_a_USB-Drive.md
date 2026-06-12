---
title: "Mounting a USB-Drive"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by wagaboom on 2011-02-10
Hi,

I have downloaded and instaleld Ubuntu mainly for once reason:
one of our server harddisks crashed and we have no backup. Now i need to see what's on that disk. So I use a USB-connector for the Harddisk and attached it to Ubuntu...

Somehow it wont recognize the drive though... how do i mount an external drive then?

thanks guys.

---

### Post by cariboo on 2011-02-10
If it is formatted as NTFS, you may have to connect to a system running Windows and run chkdsk on it. Ntfsfix is available in the NTFSprogs package, but if you data is important, I'd connect it to a Windows system.

If the drive is formatted as a linux partition, use the appropriate tools for the file system:

[LIST]
[*]ext2/3/4 - fsck
[*]reiserfs - reiserfsck
[*]xfs - fsck.xfs
[/LIST]

---

### Post by quadproc on 2011-02-10
> **wagaboom said:**
> 
Somehow it wont recognize the drive though... how do i mount an external drive then?

I am not sure just what hardware is involved but I think that you wrote that you have a crashed disk which you have plugged into a running Ubuntu system and that Ubuntu system does not see the crashed disk.  If my interpretation is correct then you may have a completely dead disk.  If that is the case then your only recourse may be to engage a data recovery service; those services are expensive and time consuming and are not guaranteed.

However, if the disk isn't dead, then you should be able to do some diagnosing of it.  With the disk connected to a running Ubuntu system, bring up gparted and see what you find with that disk selected.  If that display  shows you stuff like partitions and filesystems then you have a chance.  Mount the partition of interest and do an ls on that mount point.

quadproc

---

### Post by wagaboom on 2011-02-12
I see it in the Gparted... but being a windows user I have NO IDEA how to mount it...

clicking on the partitions in Gparted also only gives me the option to "unmount" the drive (which is strange, since i never even mounted it on that system... [not knowing how ;/ ]

anyone can help a lamer with a step by step description?

---

### Post by oldfred on 2011-02-12
Often just plugging in a USB device mounts it.

If you look in places, computer and the left panel do you see something like 100GB drive or if labeled then it will show the partitions by label.

---

### Post by wagaboom on 2011-02-13
I see "Array" there which seems to be the USB Disk... since this is what appears when I plug in the Disk... however: it gives me a warning "Unable to mount disk - can't mount file" :/

---

### Post by wagaboom on 2011-02-15
Can noone help me :/ ?

Cheers,

Tamara

---

### Post by oldfred on 2011-02-15
does this show it?
```

sudo fdisk -lu
```

---

