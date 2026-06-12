---
title: "make partition mount at same point automatically"
date: 2009-01-13
forum: New to Ubuntu
---

### Post by simtaalo on 2009-01-13
my main hard drive is split into 3 partitions, 1st partition linux mint, 2nd fedora 10 and then the 3rd partition is all my data.

output of sudo fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x282d282d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406   83  Linux
/dev/sda2            2554        3039     3903795   82  Linux swap / Solaris
/dev/sda3            3040       14593    92807505    5  Extended
/dev/sda4            1276        2553    10265535   83  Linux
/dev/sda5            3040       14593    92807473+  83  Linux

```

when i have external usb drives plugged in /dev/sda4 mounts itself at /media/disk-2

some work i've done on my music program+installation of plugins (lmms) was done whilst it was mounted at /media/disk-2

now if my partition that contains the lmms project/plugin files isn't mounted at /media/disk-2 they won't load. i could redo it all in lmms but it seems like it would be less hassle to be able to mount the partition at the same point automatically.

can anyone help?

---

### Post by MighMoS on 2009-01-13
Assuming your partition is formatted as ext3, add this line to /etc/fstab
```
/dev/sda4 /media/disc-2 ext3 defaults 0 0
```

Alternately, you could use UUID=XXXXXXXXXX instead of sda4. To find the UUID, execute "ls -lh /dev/disc/by-uuid" in a terminal, and see which one points to sda4. UUIDs have the benefit of not moving when your hard discs do.

---

### Post by simtaalo on 2009-01-14
tried first with the dev line but it didn't work, so tried with the UUID but the partition is still mounting at /media/disk 

my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a21a2df6-80f7-45d0-b312-b8302a27b588 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=d49896c1-7fae-470f-9202-de204c6f76c1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# /dev/sda4
19f65cef-ae04-4dc2-9b64-e43703bdd2a7 /media/disk-2 ext3 defaults 0 0

```

---

### Post by MighMoS on 2009-01-14
prefix those numbers with UUID= as seen in the rest of the fstab. Also, make sure that /media/disk-2 exists (if it doesn't, `sudo mkdir -p /media/disk-2` from a console will do the trick).

---

### Post by simtaalo on 2009-01-14
> **MighMoS said:**
> prefix those numbers with UUID

whoops

works now, thanks :)

EDIT: where's the option gone to mark thread as solved?

---

