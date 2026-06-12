---
title: "Link or mount separate data partition?"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by japhyr on 2010-08-17
Hello,

When I installed 10.04 recently, I made a separate /data partition in anticipation of future dual-booting, and to keep data separate from configuration files.  Is there a difference between mounting this partition to my home directory and linking it?

For example, I could mount the data partition to a folder in my home directory (mount /dev/sda9 /home/eric/data).  I would use fstab to do this, but I know fstab uses mount.

Or, I could link the data partition to a folder in the home directory (ln -s /data /home/eric/data).

What is the difference, and is either approach preferred?

---

### Post by Ozymandias_117 on 2010-08-17
> **japhyr said:**
> Hello,

When I installed 10.04 recently, I made a separate /data partition in anticipation of future dual-booting, and to keep data separate from configuration files.  Is there a difference between mounting this partition to my home directory and linking it?

For example, I could mount the data partition to a folder in my home directory (mount /dev/sda9 /home/eric/data).  I would use fstab to do this, but I know fstab uses mount.

Or, I could link the data partition to a folder in the home directory (ln -s /data /home/eric/data).

What is the difference, and is either approach preferred?

The only difference is if you mount it, all your configuration files for your programs will get saved on the Data partition as well. This can be both a blessing and a curse, so it just depends on your specific needs. I personally just mount it in /mnt and make a link in my home.

---

### Post by GaryTheCat on 2010-08-17
I have a similar query - I keep my music / documents  in a partition on one hard drive (that I can also access from vista). I have to mount this partition before opening a music player for example.

If I was to link it to my home folder would I:

a. not need to keep mounting it; and
b. would I need to re link every time I booted into ubuntu?

TIA

G

---

### Post by Ozymandias_117 on 2010-08-17
> **GaryTheCat said:**
> I have a similar query - I keep my music / documents  in a partition on one hard drive (that I can also access from vista). I have to mount this partition before opening a music player for example.

If I was to link it to my home folder would I:

a. not need to keep mounting it; and
b. would I need to re link every time I booted into ubuntu?

TIA

G

It needs to be mounted, the only question here is WHERE it's going to be mounted.

The link will stay, so as long as the hard drive is mounted, you're fine.

If you post the output of ```
sudo fdisk -l
``` (Lowercase L not the number 1) we can help you modify your /etc/fstab file so it is mounted when you turn your computer on.

---

### Post by GaryTheCat on 2010-08-17
here's the output  ....

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          28      224878+  de  Dell Utility
/dev/sda2              29        1334    10485760    7  HPFS/NTFS
/dev/sda3   *        1334       14267   103886844    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b32ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33033   265330317+   7  HPFS/NTFS
/dev/sdb2           33033       54427   171852801    5  Extended
/dev/sdb3           54427       60802    51200000    7  HPFS/NTFS
/dev/sdb5           53676       54427     6034432   82  Linux swap / Solaris
/dev/sdb6           33033       52925   159782912   83  Linux
/dev/sdb7           52925       53675     6028288   82  Linux swap / Solaris


```

---

### Post by japhyr on 2010-08-17
> **Ozymandias_117 said:**
> The only difference is if you mount it, all your configuration files for your programs will get saved on the Data partition as well.

Is this accurate?  If I mount the data partition to ~/data, I would expect:
[LIST]
[*]Anything I save in the ~/data directory would be written to the data partition;
[*]configuration files would be saved in the actual home folder, ~/, which is in its own partition.
[/LIST]

Is my understanding wrong?

---

### Post by Ozymandias_117 on 2010-08-17
> **japhyr said:**
> Is this accurate?  If I mount the data partition to ~/data, I would expect:
[LIST]
[*]Anything I save in the ~/data directory would be written to the data partition;
[*]configuration files would be saved in the actual home folder, ~/, which is in its own partition.
[/LIST]

Is my understanding wrong?

Sorry, I thought you were referring to mounting it as ~ a lot of people do that. If you're talking about mounting to ~/data or linking to ~/data there is no difference at all.

---

### Post by Ozymandias_117 on 2010-08-17
> **GaryTheCat said:**
> here's the output  ....

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          28      224878+  de  Dell Utility
/dev/sda2              29        1334    10485760    7  HPFS/NTFS
/dev/sda3   *        1334       14267   103886844    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b32ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33033   265330317+   7  HPFS/NTFS
/dev/sdb2           33033       54427   171852801    5  Extended
/dev/sdb3           54427       60802    51200000    7  HPFS/NTFS
/dev/sdb5           53676       54427     6034432   82  Linux swap / Solaris
/dev/sdb6           33033       52925   159782912   83  Linux
/dev/sdb7           52925       53675     6028288   82  Linux swap / Solaris


```

My guess is you want /dev/sdb1

So in your fstab it would be ```
/dev/sdb1 /place/you/want/it ntfs-3g defaults 0 0
```

---

### Post by GaryTheCat on 2010-08-17
One last stupid question - where would I find fstab to add that line?

and do I need to make the 'place I want it' directory before putting the line in fstab?

TIA

G

---

### Post by Ozymandias_117 on 2010-08-17
> **GaryTheCat said:**
> One last stupid question - where would I find fstab to add that line?

and do I need to make the 'place I want it' directory before putting the line in fstab?

TIA

G

Yes, you need to make the place you want it first. It's ```
gksudo gedit /etc/fstab
``` (Assuming you're running Ubuntu)

---

### Post by GaryTheCat on 2010-08-17
Thanks Ozymandias_117, it worked like a charm :D

---

