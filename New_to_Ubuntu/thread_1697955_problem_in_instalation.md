---
title: "problem in instalation"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by kiraku on 2011-03-01
hi:

i'm trying to install ubuntu 10.10 together with windows 7, but after resizing the drive of windows, the free space shows as unuseful and i can't do anything...

some screenshoots:
[IMG]http://dl.dropbox.com/u/14114808/Pantallazo0.png[/IMG][IMG]http://dl.dropbox.com/u/14114808/Pantallazo.png[/IMG]

hope u can help me

---

### Post by turtle153 on 2011-03-01
The free space is just unallocated at the moment, so you can use it in your current windows installation or on the Ubuntu installation.

---

### Post by seawolf167 on 2011-03-01
You'll format the unallocated space during the Ubuntu installation. Any space that you don't assign to /, /home, swap, etc. during installation can be formatted after install or you can use GParted to resize on of your other Ubuntu partitions.

[Dual boot guide]("https://help.ubuntu.com/community/WindowsDualBoot")
[Clonezilla ]("http://www.clonezilla.org")(for drive imaging backup)

---

### Post by coffeecat on 2011-03-01
According to your second screenshot you have four primary partitions, sda1, sda2, sda3 and sda4. This is the maximum number of primary partitions possible on one drive. This is why you cannot partition the unallocated space. You need to remove one primary partition and create an extended partition instead. Then you will be able to create as many logical partitions as you need. For more on partitioning, see here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

By the way, you've pasted your image URLs wrongly. If you want to attach images, please use the forum "manage attachments" utility. It's much easier than image hosting sites for those trying to help you

---

### Post by kiraku on 2011-03-01
> **coffeecat said:**
> According to your second screenshot you have four primary partitions, sda1, sda2, sda3 and sda4. This is the maximum number of primary partitions possible on one drive. This is why you cannot partition the unallocated space. You need to remove one primary partition and create an extended partition instead. Then you will be able to create as many logical partitions as you need. For more on partitioning, see here:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

By the way, you've pasted your image URLs wrongly. If you want to attach images, please use the forum "manage attachments" utility. It's much easier than image hosting sites for those trying to help you

i see, but i only recognize 2 of the partitions, i don't know wichone to erase..., there is no other thing to do?...

---

### Post by coffeecat on 2011-03-02
> **kiraku said:**
> i see, but i only recognize 2 of the partitions, i don't know wichone to erase..., there is no other thing to do?...

No, there is nothing else you can do. This is a limitation of the mbr partition table which is what PCs running Windows use. It is more than likely that one of your partitions is expendable but we need to identify which one. It is probable that your partitions are something like this:

sda1 - ntfs - 208MB - this look like the Windows boot partition.
sda2 - ntfs - 100GB - probably the Windows C: partition.
sda3 - ntfs - 23GB - possibly a data partition, perhaps D: or E: in Windows. But it might be a recovery partition which you would want to keep.
sda4 - fat32 - 108MB - possibly a partition with manufacturer's utilities.

Is this a Hewlett-Packard machine by any chance? If not, what make and model? It's possible the sda4 partition could be removed, but we need to be certain what it is.

Boot into the Ubuntu live CD, open a terminal and post the output of this command:

```
sudo blkid
```Please post the output between [noparse]```
 and 
```[/noparse] tags for clarity. You can use the # icon in the message toolbar for this. This output includes partition labels might give us more useful information.

Also - before you do anything else. There should be a manufacturer's utility in Windows to create a set of restore DVDs, so that you can restore Windows in case of any problems. If you have not created a set of DVDs, **do it now.**

And - in Windows 7 you can create a bootable Windows 7 repair disc which has the Windows repair console. This will fit on a CD. If you have not created one yet, **do it now.**

You may need both. Do not omit doing this.

---

### Post by kiraku on 2011-03-04
hi, thanks for answering... i was already giving uo the recovery partition.... so i already did the recovery and repair disks...

here the code:

```

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="SYSTEM" UUID="8E940E5D940E4863" TYPE="ntfs" 
/dev/sda2: UUID="744C148D4C144C6C" TYPE="ntfs" 
/dev/sda3: LABEL="RECOVERY" UUID="7A3029EB3029AF57" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="7E58-1295" TYPE="vfat" 

```

---

### Post by coffeecat on 2011-03-04
OK, you didn't explicitly answer my question about whether it was a HP machine, but the answer is in the code you posted. It is; my hunch was right. :)

Before you delete the recovery partition, I suggest you rethink whether you need the HP_TOOLS partition. I have no experience of HP machines but I see from other threads that some owners prefer to lose the HP_TOOLS partition and keep the recovery one.

If you delete the HP_TOOLS partition you'll be able to create an extended partition in the ~500GB space you've already made, but that will leave 108MB unusable at the end where the HP_TOOLS partition was. Which is not much to worry about. Alternatively, if you delete the 23GB recovery partition, you could add that 23GB to the space you already have and then make a larger extended partition. Either way, you can then create as many logical partitions as you want in the extended partition for Ubuntu. The choice has to be yours since you know what is on HP_TOOLS and you know whether or not you have followed my advice to create Windows recovery DVDs. :wink:

Then, read the partitioning link I posted earlier. You need to understand that stuff. Good luck!

---

### Post by kiraku on 2011-03-04
ok, thanks for everything!!

---

