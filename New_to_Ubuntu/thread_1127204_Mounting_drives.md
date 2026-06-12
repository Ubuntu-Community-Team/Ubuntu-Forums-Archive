---
title: "Mounting drives"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-16
Ubuntu does not recognize my hard drives when I start it up... how do I mount those drives?

I'm using Ubuntu 8.04 LTS Edition.

---

### Post by davidbilla on 2009-04-16
By "hard drives", do you mean "other" partitions after you've booted into ubuntu? Can you give the output of: ```
sudo fdisk -l
```

---

### Post by iamleaf on 2009-04-16
this is the result:

fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by halitech on 2009-04-16
it should be a lower case L, not the number 1

```
sudo fdisk -l
```

---

### Post by iamleaf on 2009-04-16
Oops. Sorry. Here's the code

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4665    37471581   83  Linux
/dev/sda2            4666        4870     1646662+   5  Extended
/dev/sda5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd88022f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+   7  HPFS/NTFS
/dev/sdb2           13055       19457    51432097+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

---

### Post by halitech on 2009-04-16
ok, so it looks like you have 3 drives total, is that correct?

whats the output of```
sudo mount
```

---

### Post by Sir Jasper on 2009-04-16
Hi,

With 8.10 I right clicked on a panel and chose add then "Disk Mounter"

You can always delete it if it doesn't work or suit your needs.

My regards

---

### Post by belikralj on 2009-04-16
Ok, it is recognising some hard disks, but which one in particular do you mean? It has recognised that you have 3 hard disks one of which has your Ubuntu on it and the other two have NTFS partitions on them.

Try using the following commands

```

sudo mkdir /media/sdb1 /media/sdb2 /media/sdc1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
sudo mount -t ntfs /dev/sdb2 /media/sdb2
sudo mount -t ntfs /dev/sdc1 /media/sdc1

```

if it gives some ntfs related errors try 

```

sudo apt-get install ntfs-3g
sudo mount -t ntfs /dev/sdb1 /media/sdb1
sudo mount -t ntfs /dev/sdb2 /media/sdb2
sudo mount -t ntfs /dev/sdc1 /media/sdc1

```

and then have a look if it worked in the /media/ directory in the sdb and sdc folders.
If this solves it come back and we can tell you how to make it permanent.

Hope this helps...

---

### Post by iamleaf on 2009-04-16
It has created the three directories.
These directories contain the files that are in the other drives.

It doesn't copy into this directory right? Because I don't want to use disk space.

---

### Post by SuperSonic4 on 2009-04-16
> **belikralj said:**
> Ok, it is recognising some hard disks, but which one in particular do you mean? It has recognised that you have 3 hard disks one of which has your Ubuntu on it and the other two have NTFS partitions on them.

Try using the following commands

```

sudo mkdir /media/sdb1 /media/sdb2 /media/sdc1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
sudo mount -t ntfs /dev/sdb2 /media/sdb2
sudo mount -t ntfs /dev/sdc1 /media/sdc1

```

if it gives some ntfs related errors try 

```

sudo apt-get install ntfs-3g
sudo mount -t ntfs /dev/sdb1 /media/sdb1
sudo mount -t ntfs /dev/sdb2 /media/sdb2
sudo mount -t ntfs /dev/sdc1 /media/sdc1

```

and then have a look if it worked in the /media/ directory in the sdb and sdc folders.
If this solves it come back and we can tell you how to make it permanent.

Hope this helps...

> **iamleaf said:**
> It has created the three directories.
These directories contain the files that are in the other drives.

It doesn't copy into this directory right? Because I don't want to use disk space.

If you have ntfs-3g installed I would choose that driver of the ntfs one, root owns it but user can still read and write which is good news if you want to access your data.

If you copy something to /media/sdb1 (for example) it will copy it onto the partition mounted there - in this case sdb1. Your ubuntu space will be unaffected

If you want them to automount you can use ntfs-config ```
sudo apt-get install ntfs-config && gksu ntfs-config
```. This will edit your fstab to mount any ntfs drive you want on boot (or you can avoid that and edit fstab manually

---

### Post by iamleaf on 2009-04-16
Thank you so much!!

---

