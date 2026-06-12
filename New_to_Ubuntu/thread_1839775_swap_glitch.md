---
title: "swap glitch"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by fractalman on 2011-09-06
Ok, i currently have 11.04 on my pc's internal hard drive,

yesterday i came across ubuntu studio so i thought i'd install it and have a look,

i installed studio to a external harddrive, no problems at all,  i want to be able to boot it on other pc's so i disconnected the internal hd whilst i installed and put the grub on the ext hd.  everything works fine, i just enter bios and select which drive i want to boot from and hey presto i get natty on my pc or studio on my ext. 

after installing studio, i formatted an ext 4 partition on the ext hd so i can keep all my music, pictures and documents there as a back up if either o/s goes wrong,  all works fine, i can access the partition from natty or studio with no problems (except permissions which i can sort out no probs so not an issue)

at the moment the 500g ext looks like this (roughly) 

ubuntu studio - 100g
swap - 6g
ext4(backup data) 150g

Now today i decided to add backtrack5 to my ext hd, following the same procedure as studio, i want to be able to boot it on other machines. the problem i am having is with setting the swap partition

i select set partitions manually
i select 50g ext4 primary partition with / as the mount point
this works and shows on the partition table but the rest of the free space on my ext  drive is showing as 'unusable.  so i am unable to set a swap partition

i tried using gparted in natty and formatting a 60g partition which i wanted to use 50g for bt5 and 5g for swap, but on resiszing the partition in bt5 install it still shows the rest of my drive as being unusable.

if i were to allocate a 250g ext4 partition in gparted it will format the partition with no probs, so why is the rest of my drive showing as unusable?

I have done about a dozen various installs since i started using linux,
maverick alongside windows
maverick instead of windows
bt5 alongside maverick
natty replaced maverick and bt5
bt5 alongside natty
natty on whole disc with bt5 on ext hd
natty re-install after i broke it trying to use kismet and aircrack :p
studio on an ext hd
natty on several friends computers

all of these have installed  with no problems, i have nuked my discs a few times in between installs to make sure there is less chance of problems.

so why can't i set a swap partition for bt5,?  there are no problems with the ext hd so why does it show as unusable?
if you need any outputs please give me the codes and i will post them.


thanks

---

### Post by Bodsda on 2011-09-06
> **fractalman said:**
>  
at the moment the 500g ext looks like this (roughly) 
 
ubuntu studio - 100g
swap - 6g
ext4(backup data) 150g
 

 
Do you know what it is *exactly*
Are you able to show us the partition table on that drive. run
```

sudo fdisk -l

```
 
The first thing that pops into my mind is that you may have 4 primary partitions. This would stop you from being able to create any more. You would have to remove one and recreate it as an Extended partition.
 
Cheers,
Bodsda

---

### Post by arubislander on 2011-09-06
I'm guessing you're hitting the limit of 4 primary partitions.

Doing what Bodsda says will allow us to be sure.

*Oops, I see that I just seconded Bodsda's first thought!*

---

### Post by fractalman on 2011-09-06
Thanks, i din't realise you could only put 4 primary partitions on a disk.

the output from sudo fdisk - l  reads as follows

```

Disk /dev/dm-0: 5023 MB, 5023727616 bytes
255 heads, 63 sectors/track, 610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8908bb25

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000341af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       12170    97753088   83  Linux
/dev/sdf2           12170       12900     5858305    5  Extended
/dev/sdf3           12900       32022   153600000   83  Linux
/dev/sdf5           12170       12900     5858304   82  Linux swap / Solaris
phi@EPSILON5:~$ 



```

gparted looks like this

/dev/sdf1     should be ubuntu studio
/dev/sdf2     should be the swap for studio
/dev/sdf3     should be my partition for data back up


i have no idea why i have /dev/sdf5 set as 5g,   im guessing dev/sdf/5 has to be deleted so i can put bt5 on the disk? can i just delete it without affecting the studio install or swap?

also my drive is meant to be 500g but at the top it is showing as 465.67g.  how can i locate the extra 35g? i was using my ext with my xbox briefly so it might be that,  any ideas how i can reclaim that part of my drive,? will it need to be totally wiped and i start all over again?

Thanks

---

### Post by nothingspecial on 2011-09-06
Before you go repartitioning and installing, you don't have to use a partition for swap, you can use a swap file

Read this [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

The swap file bit is towards the end.

---

### Post by Bodsda on 2011-09-06
> **fractalman said:**
> Thanks, i din't realise you could only put 4 primary partitions on a disk.
 
the output from sudo fdisk - l reads as follows
 
```

Disk /dev/dm-0: 5023 MB, 5023727616 bytes
255 heads, 63 sectors/track, 610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8908bb25
 
Disk /dev/dm-0 doesn't contain a valid partition table
 
Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000341af
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       12170    97753088   83  Linux
/dev/sdf2           12170       12900     5858305    5  Extended
/dev/sdf3           12900       32022   153600000   83  Linux
/dev/sdf5           12170       12900     5858304   82  Linux swap / Solaris
phi@EPSILON5:~$ 
 
 

```
 
gparted looks like this
 
/dev/sdf1 should be ubuntu studio
/dev/sdf2 should be the swap for studio
/dev/sdf3 should be my partition for data back up
 
 
i have no idea why i have /dev/sdf5 set as 5g, im guessing dev/sdf/5 has to be deleted so i can put bt5 on the disk? can i just delete it without affecting the studio install or swap?
 
also my drive is meant to be 500g but at the top it is showing as 465.67g. how can i locate the extra 35g? i was using my ext with my xbox briefly so it might be that, any ideas how i can reclaim that part of my drive,? will it need to be totally wiped and i start all over again?
 
Thanks
 
Hmmm, I can't be certain but I think it is seeing it like this
 
/def/sdf1 - Primary
/def/sdf2 - Extended
/def/sdf3 - Primary
/def/sdf5 - Primary
 
Note: Someone please correct me if a swap partition can/can't be a primary partition. 
 
That would stop you from creating another partition, assuming that 3 and 5 are not logical (inside the extended).
Can you show us the partition table from a graphical perspective using gparted?
 
Also, are you aware you can use the exisiting swap partition for this second install?
 
Bodsda

---

### Post by fractalman on 2011-09-06
Thanks

I didn't know i could use a swap area for more than one install, how would i go about configuring my drive for this?




i attached a screenshot of gparted in my previous post, but in case it's not showing i have uploaded it here as well

[http://v1.iimmgg.com/images/is8gr/d32690e157c012e7ac2c32082c3d19d8.jpg](http://v1.iimmgg.com/images/is8gr/d32690e157c012e7ac2c32082c3d19d8.jpg)

[IMG]http://v1.iimmgg.com/images/is8gr/d32690e157c012e7ac2c32082c3d19d8.jpg[/IMG]

---

### Post by Bodsda on 2011-09-07
Ah, I see the problem. You have a primary partition, then a 5gb extended partition with a 5gb logical partition, then you have another primary finally leaving the unused space at the end of the disk. With that unused space, you will only be able to create 1 further partition. 
 
P
E
_L
P
U
 
In gparted, select the unallocated space and create an extended partition using all of the available free space. You will then be able to create as many logical partitions with the leftover space as you like. Although this is quite messy as you would then have 
 
P
E
_L
P
E
_L
_U
 
If you don't mind loosing the data from sdf3, I would suggest deleting it (or moving it if possible, which wouldnt incur data loss), then growing the extended partition to use the unallocated space, then recreate the partition as a logical partition, leaving you with this.
 
P
E
_L
_L
_U
 
Which is much nicer.
 
To reuse the swap partition, during the install, select the manual/advanced partitioning option, configure your / and /home and then select the preconfigured swap partition and mount it as swap. 
 
Hope this helps, and makes sense.
Bodsda

---

### Post by fractalman on 2011-09-07
Thanks bodsda,

i removed the 2nd 5g partition, the logical one and it would allow me to set a swap for backtrack,  however having read your method i think i am going to restart and re-organise the drive, it might take a bit longer to nuke it and re-write it but it will be organised properly and will look nicer too,:)

Much appreciated

Thanks

---

