---
title: "Use of second hard disk for storage"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by sherryshero on 2011-06-12
Hello,

I am new to Ubuntu, have installed on a boot drive which is a SSD,  system also has a second normal hard disk, which I want  to use as my storage area, how do I do this, as at the moment the system is using the SSD for this. 

Thanks from Grahame

---

### Post by cbowman57 on 2011-06-12
> **sherryshero said:**
> Hello,

I am new to Ubuntu, have installed on a boot drive which is a SSD,  system also has a second normal hard disk, which I want  to use as my storage area, how do I do this, as at the moment the system is using the SSD for this. 

Thanks from Grahame

I use mount bind to do it for my Music, Downloads & Maintenance partitions.  You might be able to find some good links to help explain it better than I can, but if for some reason you hit a wall just let me know and I'll walk you through my down & dirty method.

I make my changes right in fstab & don't use symbolic links, though some people recommend that method.

---

### Post by Rocket2DMn on 2011-06-12
Are you going to share that second drive with other operating systems?  If the drive is already setup with data, you can mount it as-is and use it. Otherwise you can format it and then mount it, and it will be completely empty. You should be able to see the drive under Computer or Places in nautilus (the file browser).

If it's not mounting automatically, we can help you set it up to do so.

---

### Post by philinux on 2011-06-12
> **sherryshero said:**
> Hello,

I am new to Ubuntu, have installed on a boot drive which is a SSD,  system also has a second normal hard disk, which I want  to use as my storage area, how do I do this, as at the moment the system is using the SSD for this. 

Thanks from Grahame

Does this disk show up in places?

Open a terminal, Apps>access>terminal and post back the output of this.

```
sudo fdisk -l
```

---

### Post by Morbius1 on 2011-06-12
Don't understand the question. Are you currently mounting the partitions on the second hard disk?

Why not post the output of the following commands and indicate which partition you want to use for the storage partition:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

---

### Post by cbowman57 on 2011-06-12
After thinking about this for a minute the simple solution is probably just to install / to the SSD and /home to the HDD.  But if he want's /home on the SSD but wants to manitain large files on the HDD, but access them as if they were native to his /home folder, then my original suggestion would probably work best.

---

### Post by sherryshero on 2011-06-12
Hi phil,

thanks for reply, it shows up in disk utility as dev/sdb1, so I assume its setup for linux but I dont see it in home folder, but say if I put a stick in a usb slot, then that shows up in home folder and I can access that as normal. I have had a reply from someone else asking if it shows up in nautilus, but I dont know what that is. Sorry if the points are simple, but this is my first day with Ubuntu, I was unsure about using this with sandybridge cpu after reading about incompatibility ? problems, but it seems to be working fine here.

---

### Post by philinux on 2011-06-12
> **sherryshero said:**
> Hi phil,

thanks for reply, it shows up in disk utility as dev/sdb1, so I assume its setup for linux but I dont see it in home folder, but say if I put a stick in a usb slot, then that shows up in home folder and I can access that as normal. I have had a reply from someone else asking if it shows up in nautilus, but I dont know what that is. Sorry if the points are simple, but this is my first day with Ubuntu, I was unsure about using this with sandybridge cpu after reading about incompatibility ? problems, but it seems to be working fine here.

Have a look under Places, top left on Desktop. What do you see there.

---

### Post by sherryshero on 2011-06-12
under places, which I find in "home folder", is grahame ( ie me), desktop, file system, network, wastebasket, and if inserted, a memory stick. If I look in file system it shows the folders of the boot drive, no ref to the second hard disk

---

### Post by sherryshero on 2011-06-12
Phil, this was message returned from the fdisk query.

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfc5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7273    58419200   83  Linux
/dev/sda2            7274        7784     4101121    5  Extended
/dev/sda5            7274        7784     4101120   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000abc31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513472   8e  Linux LVM

Disk /dev/sdc: 2002 MB, 2002780160 bytes
16 heads, 32 sectors/track, 7640 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65035a6a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              16        7640     1951808    b  W95 FAT32

---

### Post by philinux on 2011-06-12
It shows sdb1 as Linux LVM. Was it formatted by you as LVM.

---

