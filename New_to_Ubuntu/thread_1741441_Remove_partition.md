---
title: "Remove partition?"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by aaron76 on 2011-04-28
I created a partition (for one reson or another) of 10 GB on my hard drive a while ago and now I'd like to remove it. It was never used so there's nothing important on there.
Now, when I check in Disc Utility, there are two sections to image of the partition on the hard drive. One is "Extended 10GB" and one is "10GB Swap Space".
Are these there by default or is it something I have done? Sounds silly, I know, but I don't know what the information was before I created the partition. I uninstalled the software (I think it was VirtualBox, not sure. But seems that the partition is still there. I would like to remove it but it comes up "Error".
Would a fresh install of 11.04 be the best and easiest solution?
Thanks

---

### Post by An Sanct on 2011-04-28
> **aaron76 said:**
> I created a partition (for one reson or another) of 10 GB on my hard drive a while ago and now I'd like to remove it. It was never used so there's nothing important on there.
Now, when I check in Disc Utility, there are two sections to image of the partition on the hard drive. One is "Extended 10GB" and one is "10GB Swap Space".
Are these there by default or is it something I have done? Sounds silly, I know, but I don't know what the information was before I created the partition. I uninstalled the software (I think it was VirtualBox, not sure. But seems that the partition is still there. I would like to remove it but it comes up "Error".
Would a fresh install of 11.04 be the best and easiest solution?
Thanks

The swap space is a system partition and should be left there, the other (extended) is the one you created.

---

### Post by sikander3786 on 2011-04-28
Can you please post the complete output of this command from your Terminal under Applications > Accessories.

```
sudo fdisk -lu
```

It would help us better understand your setup.

And for partitioing, I would recommend GParted.

```
sudo apt-get install gparted
```

It would appear under System > Administration > GParted.

Basically a Logical Partition exists inside an Extended one so you need to delete the logical one and create a new partition in its place. Or if you want to add the freed up space to one of your primary partition, you'll need to delete the extended one as well.

4 primary partitions is the limit if it matters...

---

### Post by aaron76 on 2011-04-28
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c2f9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   468520959   234259456   83  Linux
/dev/sda2       468523006   488396799     9936897    5  Extended
/dev/sda5       468523008   488396799     9936896   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7479a95a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    7  HPFS/NTFS

---

### Post by aaron76 on 2011-04-28
Thanks for that :-) I was in the dark.

---

### Post by aaron76 on 2011-04-28
Yes, it did mention logical partitions existing In the error. Thanks.

---

### Post by grahammechanical on 2011-04-28
If I am correct, there are three types of partition: Primary, Extended, and Logical. Some operating systems will only let you partition an hard disc into four primary partitions and no more. The way around this is to create an extended partition. It counts as one of the four primary partitions but you can extend the number of partitions by creating logical partitions inside the extended partitions.

When you installed Ubuntu the partitioner program created a primary partition for Ubuntu. Then it created an extended partition in which it put the swap partition. So, sda5 Linux swap is exactually inside sda2 Extended.

If you delete the extended partition you will also delete the swap partition and Ubuntu will not work or not work very well. The error message comes if you try to remove a partition that is being used by the OS or mounted as they say in Linux.

Regards.

---

