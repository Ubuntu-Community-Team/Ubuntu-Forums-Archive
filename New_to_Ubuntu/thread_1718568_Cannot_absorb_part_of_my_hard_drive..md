---
title: "Cannot absorb part of my hard drive."
date: 2011-03-31
forum: New to Ubuntu
---

### Post by Zanderist on 2011-03-31
So I deleted my HP recovery Partition, to allow for another primary partition. 

My problem now is that I cannot extend the size of any of my other partitions. 

I can format it to whatever I want, I just can't get it to be reabsorbed.

I am thinking this is due to the physical location of the former partition on the actual magnetic plate with repsect to the location I want to extend.

However if that where the case then I should still be able to extend it.

So I have 21gigs of unallocated space just floating.

Just so you know, sda4 is the part I cannot reabsorb.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85f81c3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       31696   254390272    7  HPFS/NTFS
/dev/sda3           31696       58050   211687424    5  Extended
/dev/sda4           58050       60802    22104064    7  HPFS/NTFS
/dev/sda5           31696       32239     4358144   82  Linux swap / Solaris
/dev/sda6           32239       44987   102400000   83  Linux
/dev/sda7           44987       58050   104926208    7  HPFS/NTFS
```

---

### Post by plucky on 2011-03-31
> My problem now is that I cannot extend the size of any of my other partitions.

I can format it to whatever I want, I just can't get it to be reabsorbed.


What partition do you want to extend?


From what I can see,you have 2 NTFS partitions, an extended partition in which the linux partitions are located and then another NTFS primary partition which is the one you deleted.

---

### Post by fabricator4 on 2011-03-31
It's not unnallocated - sda4 is there!  Unallocated would mean there was nothing there at all.

You have to delete the partition.

Next, you'll have to increase the size of the extended partition sda3 because the other partitions actually exist inside the extended partition.  Once you've done this you should find that you can move and resize the other partitions.

It looks like sda7 might be /home but it's been set up as NTFS ?

If so, you don't really need 100 GB for the filesystem sda6. 20-30 GB should be more than enough.

/home should really be be ext4 if possible - if you need to access it from the windows boot you can run the ext2 driver in windows to do so.


Chris

---

### Post by Zanderist on 2011-03-31
> **fabricator4 said:**
> It's not unnallocated - sda4 is there!  Unallocated would mean there was nothing there at all.


Oh what happened was that, while I was posting this I decided to format  it, because I didn't know if it would of show up in the fdisk report.

See  attachment.

I have that sda7 set up to be a nomansland between windows and ubuntu,  hence why I made it ntfs. It's for music,pictures,documents,etc.

> **fabricator4 said:**
> 
You have to delete the partition.

Next, you'll have to increase the size of the extended partition sda3 because the other partitions actually exist inside the extended partition.  Once you've done this you should find that you can move and resize the other partitions.

It looks like sda7 might be /home but it's been set up as NTFS ?

If so, you don't really need 100 GB for the filesystem sda6. 20-30 GB should be more than enough.

/home should really be be ext4 if possible - if you need to access it from the windows boot you can run the ext2 driver in windows to do so.


Chris


So I delete it and resize it within gparted? 

(from a live CD of course)

---

### Post by plucky on 2011-03-31
You still don't say where you want to add the space when you delete sda7.

---

### Post by Zanderist on 2011-03-31
> **plucky said:**
> You still don't say where you want to add the space when you delete sda7.
Well in windows I wanted to give it back to the windows partition (sda2), but it's disk manager didn't have the extend volume option available. And there isn't a merge partitions option in gparted.

 I'd like to give it back to windows.

---

### Post by plucky on 2011-03-31
> I'd like to give it back to windows. 

If it is already NTFS,doesn't windows just see it as another drive(E)?

The best bet is to add it to the NTFS partition located in the extended partition.

You can only resize a partition if the space is adjacent to the partition and to the rear of it.You cannot resize the start of a partition,but you can move it into adjacent space.

Remember to backup your important data before trying to resize or move your partitions.

Good Luck

---

### Post by fabricator4 on 2011-03-31
> **Zanderist said:**
> Oh what happened was that, while I was posting this I decided to format  it, because I didn't know if it would of show up in the fdisk report.


You're quite right, it would not have shown up in fdisk if there was no partition there.

> 
So I delete it and resize it within gparted? 
(from a live CD of course)
[/quote]

Absolutely.  You'll have to resize the extended partition that all the other's sit in first, then you should be able to move and resize the partitions inside the extended partition.

And yes, it would be best done while booted off the LiveCD.

Chris

---

### Post by Zanderist on 2011-04-01
> **plucky said:**
> If it is already NTFS,doesn't windows just see it as another drive(E)?


Yes it does, but while in windows in the disk manager, this partition is not right next to windows. It's next to the extended partition, so I can't do it.

I'll just have to do what fabricator4 said.

---

