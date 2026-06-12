---
title: "dead partition - failed installation followed by successful installation"
date: 2010-08-08
forum: New to Ubuntu
---

### Post by newuser921 on 2010-08-08
I installed Ubuntu 10.04 onto a Toshiba laptop that was already running Vista. My first attempt failed, due (I think) to a faulty installation disc. I burned another install disc at a lower speed, and it worked. 
 
My problem is that my hard drive now has 3 partitions, one of which is useless. I was kinda hoping that my second attempt at installing Ubuntu would recognize the dead partition from the failed first attempt, and just overwrite the partially installed operating system that was there. Instead, it created a third partition and installed Ubuntu there. 
 
How do I clean out the bunk partition and absorb it into either the Vista or the Ubuntu partition? If I can do this without reinstalling everything that would be great.
 
Thanks in advance!

---

### Post by SpockVulcan on 2010-08-08
You have to erase and use the erase and use entire disk mode during the install process. This will wipe the whole HDD. There is another way to erase the 3 partitions if this dosnt work but its harder so try this first. :D

---

### Post by john newbuntu on 2010-08-09
You could use GParted from a liveCD to do that.  But, just to get some info on your partitions, please post the output of the following command.  Run this command from a terminal in Ubuntu using Applications->Accessories->Terminal.

```
sudo fdisk -l
```Also identify the working Ubuntu partition in the output.

---

### Post by KROwen1959 on 2010-08-09
I have windows 7 and I shrank my hard drive. restarted my computer with disk in rom and it did its own thing. It went to the part I shrank automatically. I also have a 1000 gig hard drive

---

### Post by newuser921 on 2010-08-09
> **john newbuntu said:**
> You could use GParted from a liveCD to do that.  But, just to get some info on your partitions, please post the output of the following command.  Run this command from a terminal in Ubuntu using Applications->Accessories->Terminal.

```
sudo fdisk -l
```Also identify the working Ubuntu partition in the output.

Ok, here's the output of sudo fdisk -l:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73bf4a50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192       13203   104510273+   7  HPFS/NTFS
/dev/sda3           37779       38914     9118720   17  Hidden HPFS/NTFS
/dev/sda4           13203       37779   197404673    5  Extended
/dev/sda5           21395       37108   126214144   83  Linux
/dev/sda6           37108       37779     5387264   82  Linux swap / Solaris
/dev/sda7           13203       21055    63072256   83  Linux
/dev/sda8           21055       21395     2726912   82  Linux swap / Solaris

Partition table entries are not in disk order

```

How do I determine the working Ubuntu partition?

---

### Post by john newbuntu on 2010-08-10
Open up a terminal (Applications->accessories->Terminal). Run the command:
```
df
``` and post the output of this.  If you look for a "/" in the last column of output, the first column corresponding to this gives the current partition.

Like in my case, /dev/sda5 is the root partition where Ubuntu is installed.
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda5              7052464   4572468   2121752  69% /

Also list the output of: ```
swapon -s
``` that will be your swap partition.

---

### Post by newuser921 on 2010-08-10
ok, thanks for the help.  the working version of Ubuntu is on sda7 and the swap partition is sda8.  could I use gparted to shrink the unwanted partition down to 0?

---

### Post by john newbuntu on 2010-08-11
Yeah, so what you could do is to use gparted after booting from an Ubuntu liveCD and delete /dev/sda5 and /dev/sda6, which will free up a good 130GB.  You will than have to partition and format this space for Vista or Ubuntu. Here are some options:

Option 1.
My preference (and the easiest IMO) would be to create a new NTFS partition in that unallocated space so that you can store data here that could then be shared between Vista and Ubuntu.  Assign the new partition a label like "DATA" or anything of your choice and you should automatically see this partition in both OSs (most likely).

Option 2.
Same as 1 above.  But format this unallocated space as ext3 or ext4 but Vista will not be able to use it by default. You could then mount this in Ubuntu and use it or even move your /home to this partition.

Option 3.
Combine the space with Ubuntu.  Use gparted, delete /dev/sda5 and /dev/sda6.  Then deactivate the swap flag of /dev/sda8 and delete this partition.  Then resize /dev/sda7 all the way to the right till it occupies (almost) the entire unallocated space(extended partition).  Just leave about 2GB at the end so that you can create a new swap partition of 2GB at the end.  You will then have to modify the UUID for swap your /etc/fstab file in Ubuntu so that it points to this newly created swap partition.  All this is doable but slightly more involving.

Option 4.
Combine the free space with vista.  Requires a lot more of moving partitions, reinstalling grub, modifying fstab, reducing the extended partition, resizing /dev/sda1 and for a good measure running chkdsk on win and fsck on ubuntu(if gparted does not already do it).

Note that resizing operations are slow and interrupting them could result in loss of data.  Should you choose to resize/move partitions, ALWAYS back your data up. Really speaking, you should always have your data backed up in any case(if you really value your data and applications)

Here's a page from the gparted manual for your reference:
[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

---

