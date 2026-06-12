---
title: "Resizing partitions"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by leviathan8 on 2010-07-23
[B]Hello. I am using ubuntu 10.04 and I would like to move some gigabytes on another partition.
On dev/sda/9 I have 90 GB (the Linux partition) and I would like to move some of the memory to another partition that is located on windows.
My linux partion is ext3 format, and the other ones are NTFS. I would  like to move around 50 GB to an NTFS partition from an ext3. 
I have some questions regarding to this.

1. What program do I use?
2. What I have to do before moving memory.
3. What I have to do after making changes.
4. What are the risks?

I experienced a bad grub fail last month - so I couldn't boot anything  after making a new partition - so I am a bit scared of playing around  with this.
Thanks.

This is my fdisk:

[/B]```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a602a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38245   204798976    7  HPFS/NTFS
/dev/sda3           38245       63741   204798976    7  HPFS/NTFS
/dev/sda4           63742      121602   464760832+   f  W95 Ext'd (LBA)
/dev/sda5           63742       76490   102400000    7  HPFS/NTFS
/dev/sda6           76490       80314    30720000    7  HPFS/NTFS
/dev/sda7           80314       89238    71677952    7  HPFS/NTFS
/dev/sda8           89238      108853   157559808    7  HPFS/NTFS
/dev/sda9          108854      121602   102398976   83  Linux
```

---

### Post by cjv8888 on 2010-07-23
> **leviathan8 said:**
> [B]Hello. I am using ubuntu 10.04 and I would like to move some gigabytes on another partition.
On dev/sda/9 I have 90 GB (the Linux partition). I would like to move them to another dev/sda that is located on windows.
My linux partion is ext3 format, and the other ones are ntfs. I would  like to move around 50 GB to an NTFS partition from an ext3. 
I have some questions regarding to this.

1. What program do I use?
2. What I have to do before moving gigabytes.
3. What I have to do after making changes.
4. What are the risks?

I experienced a bad grub fail last month - so I couldn't boot anything  after making a new partition - so I am a bit scared of playing around  with this.
Thanks.

This is my fdisk:

[/B]```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x02a602a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38245   204798976    7  HPFS/NTFS
/dev/sda3           38245       63741   204798976    7  HPFS/NTFS
/dev/sda4           63742      121602   464760832+   f  W95 Ext'd (LBA)
/dev/sda5           63742       76490   102400000    7  HPFS/NTFS
/dev/sda6           76490       80314    30720000    7  HPFS/NTFS
/dev/sda7           80314       89238    71677952    7  HPFS/NTFS
/dev/sda8           89238      108853   157559808    7  HPFS/NTFS
/dev/sda9          108854      121602   102398976   83  Linux
```
Since your linux is at sda9, you should use a live CD and contract and move the sda9 towards the right then expand sda8 towards the right by 50GB.

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> If you have space in one of those NTFS partitions, the easiest way would be to copy and paste the files across while you are booted up in linux.

[B]That's time wasting, and it isn't really useful :| Windows can't even see the linux partition...
Thanks anyway.
[/B]

---

### Post by cjv8888 on 2010-07-23
I might have misunderstood.  Did you want to move data or just move space from the linux partition to the Windows?

If you have worries doing the latter, go through this tutorial on [Gparted]("http://www.dedoimedo.com/computers/gparted.html").

If you are moving data, linux can see all the ntfs partitions so it can be done easily when you are booted into linux. (timewasting? If there are other ways to cut and paste data I would love to know too)

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> I might have misunderstood.  Did you want to move data or just move space from the linux partition to the Windows?

If you have worries doing the latter, go through this tutorial on [Gparted]("http://www.dedoimedo.com/computers/gparted.html").

If you are moving data, linux can see all the ntfs partitions so it can be done easily when you are booted into linux. (timewasting? If there are other ways to cut and paste data I would love to know too)

[B]Yes, I would like to move memory from a partition to another partition. Not data :) Thanks for info.
Edit: I can't do anything to the ext3 partition. All options are disabled, why?
[/B]

---

### Post by cjv8888 on 2010-07-23
> **leviathan8 said:**
> [B]Yes, I would like to move memory from a partition to another partition. Not data :) Thanks for info.
Edit: I can't do anything to the ext3 partition. All options are disabled, why?
[/B]

You cannot change the partition while you are booted up in it.  So you will need to boot up using a live CD and run Gparted while the partitions are unmounted.

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> You cannot change the partition while you are booted up in it.  So you will need to boot up using a live CD and run Gparted while the partitions are unmounted.

**Uuh... this sounds risky. Can you tell me what to unmount exactly? Only the linux partitions or all other? After unmount what I have to do? Mount them again? If yes, how?**

---

### Post by cjv8888 on 2010-07-23
> **leviathan8 said:**
> **Uuh... this sounds risky. Can you tell me what to unmount exactly? Only the linux partitions or all other? After unmount what I have to do? Mount them again? If yes, how?**

Before doing any change in partitioning, always back up your data of course.  Otherwise resizing partitions is generally quite safe.  I have done it tens of times.
Now when you boot up on a live CD, all the partitions are unmounted to begin with.  As your space is at sda9, you can only give the space to the neighbouring partition, which is sda8.
So all you have to do is to run system/gparted.
Click on sda9 to resize it, and move the left boundary of the partition towards the right to contract it by 50GB.
After this operation, there will be free space on the left of the partition. Then just click on sda8 to resize it and move the right boundary towards the right to take up that free space.
As there is no change to the partition numbers, you should not need to update the grub.
If there is a lot of data in sda9 to move, the operation can take a while though.

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> Before doing any change in partitioning, always back up your data of course.  Otherwise resizing partitions is generally quite safe.  I have done it tens of times.
Now when you boot up on a live CD, all the partitions are unmounted to begin with.  As your space is at sda9, you can only give the space to the neighbouring partition, which is sda8.
So all you have to do is to run system/gparted.
Click on sda9 to resize it, and move the left boundary of the partition towards the right to contract it by 50GB.
After this operation, there will be free space on the left of the partition. Then just click on sda8 to resize it and move the right boundary towards the right to take up that free space.
As there is no change to the partition numbers, you should not need to update the grub.
If there is a lot of data in sda9 to move, the operation can take a while though.

**Let's get this clear.**
[B]1. I boot up the LiveCD.
2. I start the program, select the sda9 partition and resize it. This will leave 50 GB unused memory after resizing it.
3. The unused memory can be later added to an existing partition. This is possible both from windows and linux?



Ok. I understood that this way.
But i'm a bit confused.
I have to choose the RESIZE option or the MOVE option.
What's the difference between them.
As I can see, the move option is a bit more complex, because it requires to move subsequently the memory from a partition to another. If this is the case, can I still use the resize method, or should I just stick to the move?
Which is more safe and more handy? 
Remember, all I want is too substract 50 GiB from the ext3 partition to add it later to an NTFS partition. So my point is to leave unused memory which I can add later. But instead of this, the move method will move (as far as I understand) the memory to a partition above it (sda8). This means that once I substracted the memory from sda9 (which is 96 GiB, but therefore will be 46 after moving), and the sda8 will be grown (which is now 29,2 GB and will be grown to 79 GB). Am I right? 

You mean moving by this method, right?

[IMG]http://www.dedoimedo.com/images/computers/2009/gparted-move.png[/IMG]

One more question.
What preceding and following refers to?
I think that: preceding will leave space before sda9 (which is sda8) and following will move unused memory after sda9. I'm not sure here.

(the image is not actual, it's from the tutorial you gave me)
[/B]

---

### Post by cjv8888 on 2010-07-23
Resize or move is pretty much the same, but as the sda9 is the last partition on the disc, you can only move the left boundary to the right to create room on the left of the partition.

preceding and following refers to before and after the move.

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> Resize or move is pretty much the same, but as the sda9 is the last partition on the disc, you can only move the left boundary to the right to create room on the left of the partition.

preceding and following refers to before and after the move.

[B]Ok! Thank you very much.
To make everything sure, can you tell me the values to input in preceding, new size, and following boxes? This implying that I want to move 50 GiB.
[http://www.dedoimedo.com/images/computers/2009/gparted-move.png](http://www.dedoimedo.com/images/computers/2009/gparted-move.png) <- using that image.
Is there any case of disaster? Like grub won't show up, or windows/linux can't be booted? Or anything similar to this? I'm always cautious :P
[/B]

---

### Post by tarps87 on 2010-07-23
> **cjv8888 said:**
> Resize or move is pretty much the same, but as the sda9 is the last partition on the disc, you can only move the left boundary to the right to create room on the left of the partition.

**preceding and following refers to before and after the move.**

It is the free space before the partition and after the partition, not before and after the move action

Unless you are planning on crating a new partition, and if sda9 is in fact on the end of the disk, I would only move the left boundary/side. Else you will just have to move the partition at a later date.

---

### Post by cjv8888 on 2010-07-23
> **tarps87 said:**
> It is the free space before the partition and after the partition, not before and after the move action

Unless you are planning on crating a new partition, and if sda9 is in fact on the end of the disk, I would only move the left boundary/side. Else you will just have to move the partition at a later date.

Thanks for correcting. 

As you are moving the left boundary, you will see the first box increasing in size to 50 GB as you move and the middle box decreasing in size to your planned 46GB.  This is diagramatic only. The move does not happen until you click Apply.

---

### Post by leviathan8 on 2010-07-23
[B]Ok. I am ready to do this. I pray to God so nothing goes wrong :D

Last question. After moving the space, there will be a new partition on the harddisk, looking like this:
[IMG]http://www.dedoimedo.com/images/computers/2009/gparted-moved.jpg[/IMG]

The unallocated space. This will appear after moving, right?
Later I can allocate this free space to an existing partition, from both linux and windows, or only from linux? The unallocated partition will have no format (such as NTFS or ext3)?
Also, what should I backup? The whole home directory or the file system?
[/B]

---

### Post by cjv8888 on 2010-07-23
> **leviathan8 said:**
> [B]Ok. I am ready to do this. I pray to God so nothing goes wrong :D

Last question. After moving the space, there will be a new partition on the harddisk, looking like this:
[IMG]http://www.dedoimedo.com/images/computers/2009/gparted-moved.jpg[/IMG]

The unallocated space. This will appear after moving, right?
Later I can allocate this free space to an existing partition, from both linux and windows, or only from linux? The unallocated partition will have no format (such as NTFS or ext3)?
Also, what should I backup? The whole home directory or the file system?
[/B]
The unallocated space will have no format.  From Windows, you can use another program like Partition Magic to expand the neighbouring partition to take up that space.  Generally, expanding a partition is very quick and safe.  Error sometimes can happen when you have to move a lot of data from one place on the disk to another.
For back up, I would just back up the files that you don't want to lose onto an external drive for example.

---

### Post by leviathan8 on 2010-07-23
> **cjv8888 said:**
> The unallocated space will have no format.  From Windows, you can use another program like Partition Magic to expand the neighbouring partition to take up that space.  Generally, expanding a partition is very quick and safe.  Error sometimes can happen when you have to move a lot of data from one place on the disk to another.
For back up, I would just back up the files that you don't want to lose onto an external drive for example.

[B]Thanks a lot. I understood everything and now i'm good to go.
I don't really have what to backup on linux, I mainly use it for technical stuff. The filesystem won't be touched, I hope :)
[/B]

---

### Post by tarps87 on 2010-07-23
I think there is an issue here, gparpted is reporting the drive as 4GiB (~4GB) and as /dev/sdb where as fdisk reported it as 1000.2 GB and /dev/sda
Are you using two hard drives? I think this should be cleared up before you make any changes. Not to mention the lack on ntfs partitions

---

### Post by cjv8888 on 2010-07-23
> **tarps87 said:**
> I think there is an issue here, gparpted is reporting the drive as 4GiB (~4GB) and as /dev/sdb where as fdisk reported it as 1000.2 GB and /dev/sda
Are you using two hard drives? I think this should be cleared up before you make any changes. Not to mention the lack on ntfs partitions

I think the diagram is just an example he copied from somewhere.  His actual disk is just the 1000.2 GB sda.

---

### Post by leviathan8 on 2010-07-23
> **tarps87 said:**
> I think there is an issue here, gparpted is reporting the drive as 4GiB (~4GB) and as /dev/sdb where as fdisk reported it as 1000.2 GB and /dev/sda
Are you using two hard drives? I think this should be cleared up before you make any changes. Not to mention the lack on ntfs partitions
[B]
No no! That's just an example image from a tutorial :p
[/B]

---

### Post by tarps87 on 2010-07-23
That's ok then, better safe that sorry :)

---

### Post by leviathan8 on 2010-07-23
**I'm doing it right now. For the beginning i'll only take out 1 GiB for precaution. If it works, than i'm gonna take all the 50 GiB needed. If any problem appears, i'm going to post here.**

---

### Post by leviathan8 on 2010-07-23
**Phiuh... 1 hour already passed and the test is  still not done. I'm moving only 1 GiB! I don't know what to expect at 50 GiB... Are this checks, copy tests, read-only stuff and other things that will come up are so necessary? :| **

---

### Post by tarps87 on 2010-07-23
Yep, it's trying to be as careful as possible.
It will be move the data bit by bit and as you have move the start of the partition it has to move it all to the right (so to speak) remember it's not moving the 1GB it's moving all the data in sda9 to create the one 1GB.
The good news however is that it should take about the same time to make the 50GB (49GB :)) move.

---

### Post by leviathan8 on 2010-07-23
> **tarps87 said:**
> Yep, it's trying to be as careful as possible.
It will be move the data bit by bit and as you have move the start of the partition it has to move it all to the right (so to speak) remember it's not moving the 1GB it's moving all the data in sda9 to create the one 1GB.
The good news however is that it should take about the same time to make the 50GB (49GB :)) move.

[B]Well that's a lot of work. Hope that the CD won't burn literary until it's done :))
There will be no errors in grub when booting the PC, right?
[/B]

---

### Post by leviathan8 on 2010-07-23
[B]The 1 GiB test was a succes! Tomorrow i'm going to get the real facts.
For further reference, visitors can use this method to shrink the ext3 file system volume. Everything works fine.
Estimated time to complete: 2 hours.
[/B]

---

### Post by tarps87 on 2010-07-23
> **leviathan8 said:**
> [B]Well that's a lot of work. Hope that the CD won't burn literary until it's done :))
There will be no errors in grub when booting the PC, right?
[/B]

> **leviathan8 said:**
> [B]The 1 GiB test was a succes! Tomorrow i'm going to get the real facts.
For further reference, visitors can use this method to shrink the ext3 file system volume. Everything works fine.
Estimated time to complete: 2 hours.
[/B]

There's your answer :)

---

### Post by diagram30 on 2010-07-24
> **leviathan8 said:**
> [B]For further reference, visitors can use this method to shrink the ext3 file system volume. Everything works fine.
Estimated time to complete: 2 hours.
[/B]

Except for the fact that absolutely everyone else that would read this forum would know this already...
I'm really curious how you've managed to install Ubuntu if you don't know jack about partitioning.

---

### Post by tarps87 on 2010-07-26
> **diagram30 said:**
> Except for the fact that absolutely everyone else that would read this forum would know this already...
I'm really curious how you've managed to install Ubuntu if you don't know jack about partitioning.

Quite easy really, hit the install side by side option and it does it for you. Please note that your tone can be taken as being offensive and therefore against the code of conduct.

---

