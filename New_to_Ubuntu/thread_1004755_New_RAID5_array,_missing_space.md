---
title: "New RAID5 array, missing space?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by BassKozz on 2008-12-07
_My setup:_
**MoBo:** [Intel D865GBF Desktop Board]("http://www.intel.com/support/motherboards/desktop/D865GBF/")
**CPU:** P4 3.0Ghz
**RAM:** 4x1GB G.Skill Sticks
**VIDEO:** FX5200 AGP card
**IDE1:** Seagate 250GB (ST380013A)
**IDE2:** Maxtor 250GB (Diamond Max Plus9)
**SATA1:** Western Digital 320GB (WD3200JD-22KLB0)
**SATA2:** Seagate 200GB (ST300822AS) - ******UBUNTU INSTALLED ON THIS ONE******

I just created a RAID5 array (on IDE1,IDE2,& SATA1) using this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

But when I pull up the properties in Nautilus it says there is only 435GB of free space available instead of 500GB, is this correct?
I know > The International Electrotechnical Commission's recommendation is to add a "bi" for binary bytes, and use gibibytes instead of gigabytes. A 20GB drive would therefore be 18.6GiB. There are also kibibytes (KiB), mebibytes (MiB), tebibytes (TiB) and so on.
-[http://www.guardian.co.uk/technology/askjack/2007/oct/25/wherehasmymissingharddriv]("http://www.guardian.co.uk/technology/askjack/2007/oct/25/wherehasmymissingharddriv")

But that would mean 20-18.6= 1.4GB missing from every 20GB
So...500GB/20=25*1.4=**35GB** missing, yet I am showing **65GB** missing ???
What gives?

---

### Post by stefangr1 on 2008-12-08
> **BassKozz said:**
> _My setup:_
**MoBo:** [Intel D865GBF Desktop Board]("http://www.intel.com/support/motherboards/desktop/D865GBF/")
**CPU:** P4 3.0Ghz
**RAM:** 4x1GB G.Skill Sticks
**VIDEO:** FX5200 AGP card
**IDE1:** Seagate 250GB (ST380013A)
**IDE2:** Maxtor 250GB (Diamond Max Plus9)
**SATA1:** Western Digital 320GB (WD3200JD-22KLB0)
**SATA2:** Seagate 200GB (ST300822AS) - ******UBUNTU INSTALLED ON THIS ONE******

I just created a RAID5 array (on IDE1,IDE2,& SATA1) using this guide: [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

But when I pull up the properties in Nautilus it says there is only 435GB of free space available instead of 500GB, is this correct?
I know 
-[http://www.guardian.co.uk/technology/askjack/2007/oct/25/wherehasmymissingharddriv]("http://www.guardian.co.uk/technology/askjack/2007/oct/25/wherehasmymissingharddriv")

But that would mean 20-18.6= 1.4GB missing from every 20GB
So...500GB/20=25*1.4=**35GB** missing, yet I am showing **65GB** missing ???
What gives?

This could have to do with space reserved for the root user, which is 5% by default. Especially on large drive, this can take an unnecessarily large amount of disk space.

You can change this by taking the steps below:

df     
this shows which partitions you have, and where they are mounted

sudo umount /dev/sda1    
to unmount drive sda1 (example)

sudo tune2fs -m 0 /dev/sda1    
to change reserved blocks to 0%

sudo mount /dev/sda1    
to mount again

df     
to look how things have changed


You should do the steps above only for 'storage' partitions, and definitely keep enough reserved space on your system partitions with / /var /tmp.

---

### Post by BassKozz on 2008-12-08
Thanks stefangr1,

I'l give that a try, but first...
Is is safe to umount a drive that is in an array (/dev/md0) ? I guess because RAID5 has parity it shouldn't be a problem, but I am just wondering if there is some other command I should issue first to fail/drop the drive from the array before I umount it?

Thanks again,
-BassKozz

---

### Post by stefangr1 on 2008-12-08
> **BassKozz said:**
> Thanks stefangr1,

I'l give that a try, but first...
Is is safe to umount a drive that is in an array (/dev/md0) ? I guess because RAID5 has parity it shouldn't be a problem, but I am just wondering if there is some other command I should issue first to fail/drop the drive from the array before I umount it?

Thanks again,
-BassKozz

No, that is not a problem since you're not unmounting the separate drives but the entire RAID 5 array at once. I believe the operation (changing the reserved blocks) isn't very risky or extensive either, even without unmounting it shouldn't give trouble though I wouldn't recommend it, and the extra space should show up immediately.

---

### Post by BassKozz on 2008-12-09
I can't umount /dev/sda1:
```

sudo umount /dev/sda1
umount: /dev/sda1: not mounted

```

Here is **fdisk -l**:
```
sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000e3ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a59a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00054205

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       23330   187398193+  83  Linux
/dev/sdc2           23331       24321     7960207+   5  Extended
/dev/sdc5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005dadf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001   fd  Linux raid autodetect

```

and **df**:
```
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1            184457332   2874388 172213036   2% /
tmpfs                  1880512         0   1880512   0% /lib/init/rw
varrun                 1880512       508   1880004   1% /var/run
varlock                1880512         0   1880512   0% /var/lock
udev                   1880512      2792   1877720   1% /dev
tmpfs                  1880512       104   1880408   1% /dev/shm
lrm                    1880512      2000   1878512   1% /lib/modules/2.6.27-9-generic/volatile
/dev/md0             480726864    224372 456082904   1% /media/RAID-storage

```

---

### Post by stefangr1 on 2008-12-09
Everything looks fine. The missing 2*250-480=20Gb is likely due to reserved space.

---

### Post by BassKozz on 2008-12-09
I am still confused,

I noticed after running **df** it says that */dev/md0* has **456082904** available, but when I right click on a folder with in */dev/md0* in naultius it says I only have 435GB available, what's with the 21GB discrepancy?

---

### Post by BassKozz on 2008-12-10
> **BassKozz said:**
> I am still confused,

I noticed after running **df** it says that */dev/md0* has **456082904** available, but when I right click on a folder with in */dev/md0* in naultius it says I only have 435GB available, what's with the 21GB discrepancy?

:roll::bump::roll:

---

