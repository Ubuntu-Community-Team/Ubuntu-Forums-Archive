---
title: "mysterious hard drive ??"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by squrl on 2010-02-09
I have 8.04 loaded on a 1t drive. When I go to places it shows Home and Computer but it also shows a 526.4 gig drive. There are no other drives on this machine. Where is this drive coming from. More to the point how do I get rid of it?

Thanks

---

### Post by nhasian on 2010-02-09
lets take a look at your hard disks and partitions.  open a terminal from applications->accessories then give us the output of this command:

```
sudo fdisk -l
```

---

### Post by squrl on 2010-02-09
[sudo] password for squrl: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe47de47d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30394     9879975    5  Extended
/dev/sda5           29165       30394     9879943+  82  Linux swap / Solaris

Partition table entries are not in disk order
squrl@squrl-desktop:~$

---

### Post by warfacegod on 2010-02-09
Okay. This is certainly a sarcastic comment but... Why on Earth would you want to get rid of an extra 1/2 TB of drive space you didn't know you had!!??

---

### Post by Psyco430404 on 2010-02-09
warfacegod makes a very good point, tho it could be a misslable on a partition, or a fake split in your 1t drive

---

### Post by warfacegod on 2010-02-09
Does it show up in Gparted?

---

### Post by nhasian on 2010-02-10
this output shows that you only have one hard disk and that it is 250 gigs.

> **squrl said:**
> [sudo] password for squrl: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe47de47d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+  83  Linux
/dev/sda2           29165       30394     9879975    5  Extended
/dev/sda5           29165       30394     9879943+  82  Linux swap / Solaris

Partition table entries are not in disk order
squrl@squrl-desktop:~$

---

### Post by audiomick on 2010-02-10
+1 for warfacegod's suggestion to look at it with gparted.

---

### Post by warfacegod on 2010-02-10
```
sudo fdisk -l
```

Not only is that not showing it but it does show that you are 750 GB short of 1 TB. If indeed you do have a full TB then *perhaps* the 1/2 TB you see is a partition of it. If so, that still leaves you about 250 GB short.

By the way, to get Gparted:

```
sudo apt-get install gparted
```

or use Synaptic.

It will probably be listed in your Admin. menu as Partition Editor because you are in 8.04

---

### Post by nhasian on 2010-02-10
gparted will just tell you the same information.  It doesnt matter how the drive is partitioned or weather the partitions are mounted or not, they will show up with "sudo fdisk -l"

reasons fdisk would not see a hard disk:

a) controller is disabled in bios
b) drive is physically disconnected from cable or host controller
c) host controller has an unsupported chipset and requires drivers

I think the simplest question would be "How many physical hard disks do you have in your computer?"  because fdisk is saying only 1.

---

