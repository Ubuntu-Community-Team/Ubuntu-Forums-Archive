---
title: "Expand my Ubuntu  hard drive"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by carvish on 2011-02-10
Hi ,
I dual boot Ubuntu10.10 and Windows 7 on my desktop, after a few issues with grub2, everything is working greatly, so much so that I now dual boot my laptop with the same config.My question is with my laptop, Windows 7 was already installed so i added Ubuntu 10.10, during the installation I was prompted to partition sections of my hard drive for Ubuntu, I was unaware that you can only partition a hard drive so many times. I am left with about 100 gig of unallocated space on my hard drive. I tried to make another hard drive  on Windows 7 (which my intention was, to make a separate partition for general storage for both os's) and that's where i received the message about the hard drives so I tried to expand Ubuntu to use the extra space there. Ubuntu posted a warning that if I proceed, it may render my os as unbootable. that would really suck because I have ubuntu running perfectly, grub2 is doing a good job and I have installed compiz and compiz is "firing" on all cylinders. Should I just leave this extra space or can I add it to my Ubuntu partition without issues?

---

### Post by thefasterblueone on 2011-02-10
Here are two links to help you. It's not that hard to do but you must be sure about each step before you click apply. 


[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

[http://www.howtoforge.com/partitioning_with_gparted]("http://www.howtoforge.com/partitioning_with_gparted")

---

### Post by P4man on 2011-02-11
They key is running gparted from a livecd. Dont try this while you are running the installed ubuntu, it wont work. Its like trying to move the chair you are sitting on.

anyway, boot the cd, run gparted, and you might have to swapoff and unmount all partition. To swapoff, right click the swap partition in gparted and select swapoff. As long as the swap is active, you cant move/resize that partition, or the extended partition it might be in.

---

### Post by Mark Phelps on 2011-02-11
Win7 Disk Management gets easily confused ...

I ran into a similar problem when I tried to extend (the Win7 phrase for expand) a partition to fill some unallocated space.  Even though I only had three partitions on that drive, Win7 kept warning me that extending the third partition would transform all the partitions into Dynamic Disks.  Perhaps this is the warning you are seeing.

If you're going to ask partitioning questions, it would be better if you would provide us some info on your existing partitions.  To do that, open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).

---

### Post by carvish on 2011-02-15
Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29362175    14680064   27  Unknown
/dev/sda2   *    29362176    29566975      102400    7  HPFS/NTFS
/dev/sda3        29566976   666443775   318438400    7  HPFS/NTFS
/dev/sda4       666445822  1054949375   194251777    5  Extended
/dev/sda5       666445824   667420671      487424   83  Linux
/dev/sda6       667422720   677185535     4881408   82  Linux swap / Solaris
/dev/sda7       677187584   696717311     9764864   83  Linux
/dev/sda8       696719360  1054949375   179115008   83  Linux

---

### Post by carvish on 2011-02-15
> **carvish said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    29362175    14680064   27  Unknown
/dev/sda2   *    29362176    29566975      102400    7  HPFS/NTFS
/dev/sda3        29566976   666443775   318438400    7  HPFS/NTFS
/dev/sda4       666445822  1054949375   194251777    5  Extended
/dev/sda5       666445824   667420671      487424   83  Linux
/dev/sda6       667422720   677185535     4881408   82  Linux swap / Solaris
/dev/sda7       677187584   696717311     9764864   83  Linux
/dev/sda8       696719360  1054949375   179115008   83  Linux



sorry it took a while to respond, the thread doesn't show up when I search for carvish, and i had forgotten what I called it

---

### Post by carvish on 2011-02-15
> **carvish said:**
> sorry it took a while to respond, the thread doesn't show up when I search for carvish, and i had forgotten what I called it


Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xee68ee1c


in case it makes a difference, I tried to post a photo of my terminal but the site asks for a url site

---

### Post by oldfred on 2011-02-15
If the free space is at the end of your drive which it looks like, then you need to expand the extended partition first to include all the free space. Then you can expand the last partition for move them around.

Since any partitioning has risks be sure to have good backups.

You have to use a liveCD so all partitions are unmounted and the liveCD will often automount the swap partition so you have to click on it and swapoff to unmount it.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by carvish on 2011-02-19
na, it's not working, I boot off the gparted live cd and I click on the unallocated space, format. it tells me that I will lose data on the entire disk. I click on the partition where ubuntu is and click expand, it doesn't give me anywhere to expand to, the number is  zero , I can shrink it but can't expand it... somewhere in there it also says that you are only allowed 4 primary partitions. there is a light blue line between the ubuntu partition and the unallocated space, but no partitions 

further more, the gparted itself has icons across the top , none of these icons appear to be working, I tried to take a screen shot of it, and nothing. terminal, help, etc, all not working.

maybe I will just call that 93 gig my buffer zone, and leave it as is....

---

### Post by carvish on 2011-02-19
> **carvish said:**
> na, it's not working, I boot off the gparted live cd and I click on the unallocated space, format. it tells me that I will lose data on the entire disk. I click on the partition where ubuntu is and click expand, it doesn't give me anywhere to expand to, the number is  zero , I can shrink it but can't expand it... somewhere in there it also says that you are only allowed 4 primary partitions. there is a light blue line between the ubuntu partition and the unallocated space, but no partitions 

further more, the gparted itself has icons across the top , none of these icons appear to be working, I tried to take a screen shot of it, and nothing. terminal, help, etc, all not working.

maybe I will just call that 93 gig my buffer zone, and leave it as is....


how do I expand the extended partition first to include all the free space?

---

### Post by deconstrained on 2011-02-19
> **carvish said:**
> how do I expand the extended partition first to include all the free space?
To resize a partition and the filesystem it contains, right click on the partition in gparted and select "resize/move". That should then bring up the dialog which will allow you to specify growing the partition *into* the unallocated space. *You do not need to format the unallocated space, and, as a matter of fact, should not format it.*  It should be pretty simple. Unless you're using a filesystem that doesn't allow you to resize it, like JFS, then you can't change its size. If you're expanding the filesystem *backwards*, i.e. toward the beginning of the disk, partitioning will take a very long time (because it has to copy blocks to the new beginning), so be warned.

> **carvish said:**
> My question is with my laptop, Windows 7 was already installed so i added Ubuntu 10.10, during the installation I was prompted to partition sections of my hard drive for Ubuntu, I was unaware that you can only partition a hard drive so many times.
Actually, FYI you can **re**partition your hard drive as many times as you darn well please, but most partition table types don't permit you to have more than 4 physical partitions.  Furthermore, if you want to have a large number of partitions, it's generally advisable to use LVM2 on top of existing physical partitions instead of slicing up your hard drive even more.

> **carvish said:**
> Ubuntu posted a warning that if I proceed, it may render my os as unbootable. that would really suck because I have ubuntu running perfectly, grub2 is doing a good job and I have installed compiz and compiz is "firing" on all cylinders. Should I just leave this extra space or can I add it to my Ubuntu partition without issues?
If resizing the partition ends up making your system non-bootable, you can recover by booting to a livedisk, mounting/chrooting into your root filesystem, and rebuilding the initial ramdisk. Just ask if you need to do this; I've messed up and rendered my system un-bootable scores of times, and I practically have the procedure memorized.

---

### Post by carvish on 2011-02-21
I "think" I have attached a screenshot of g parted (not live) through Ubuntu. when I right click on the 170 GB (which is SDA8 )  on the "live" g parted and select resize/move, I can shrink the partition, but the first category on the list is zero,thanks for your patience I'm a noob. also I don't know what a JFS is, how would I find out if it is one?

---

### Post by oldfred on 2011-02-21
sda4 is the extended partition, it is shown as the blue border around the logical partitions. You have to expand sda4, the container before you can expand the contents.

---

### Post by wizard10000 on 2011-02-21
> **oldfred said:**
> sda4 is the extended partition, it is shown as the blue border around the logical partitions. You have to expand sda4, the container before you can expand the contents.

Also, after you've resized sda4 to take up the rest of the disk and resized sda8 to make use of the new free space you've got to resize the filesystem, otherwise sda8 will have almost 100gb of unusable space  ;)

After you've got your partitions set up the way you want (and assuming sda8 is still the partition you resized) you do this on the unmounted partition:

```
resize2fs -p /dev/sda8
```

good luck!

---

### Post by carvish on 2011-02-21
Well thank you again for all your help and patience. I believe I have the unallocated space added to Ubuntu. On the g parted live, instead of expanding SDA 8 right away, I had to expand SDA 4 first... Thanks oldfred for your help to finally sink that knowledge through the hat and (finally) into my hat rack. Everything seems to be working top notch.
Thanks again
Carvish

Now where did that SOLVED button go????

---

### Post by carvish on 2011-02-21
in the terminal? I assume everything went according to plan, SDA 8 under blocks has increase by about  100,000,000, is this what it should look like?

---

### Post by wizard10000 on 2011-02-21
> **carvish said:**
> in the terminal? I assume everything went according to plan, SDA 8 under blocks has increase by about  100,000,000, is this what it should look like?

Yes, but expanding the partition doesn't expand the filesystem inside it.

Open a terminal window and type

```
df
```and I think you'll find that although the partition resized the filesystem didn't.

---

### Post by carvish on 2011-02-21
everything seems to there, I think?

---

### Post by wizard10000 on 2011-02-21
I stand corrected then - gparted didn't used to grow filesystems.

Glad you got it sorted  ;)

---

### Post by P4man on 2011-02-21
> **wizard10000 said:**
> I stand corrected then - gparted didn't used to grow filesystems.

Yes it did. I think you may be confused with extended partitions. Those are containers that hold logical partitions. Increasing the size of an extended partition doesnt increase the size of the logical partitions contained in it. Never did, never will. But if you increase the size of a logical or a primary partition, you increase the size of the "filesystem'. Its always been like that, and always will be (until the world is finally rid of the need for extended partitions ;) ).

---

### Post by wizard10000 on 2011-02-21
> **P4man said:**
> Yes it did. I think you may be confused with extended partitions. Those are containers that hold logical partitions. Increasing the size of an extended partition doesnt increase the size of the logical partitions contained in it. Never did, never will. But if you increase the size of a logical or a primary partition, you increase the size of the "filesystem'. Its always been like that, and always will be (until the world is finally rid of the need for extended partitions ;) ).

Nah, I'm not confused about partitioning at all  ;)

But - I guess maybe the last time I grew an ext partition I didn't use gparted as I did have to use resize2fs to make filesystem size and partition size line up.  That makes sense because it's been more than a few years since I did it  ;-)

Heard an interesting idea the other day about resizing partitions - I can't remember whether it was here or in the Kubuntu forums but somebody had the idea of growing a partition by using fdisk to delete the partition then recreating it using the same start cylinder but a different end cylinder - then using resize2fs to grow the filesystem to fit the new partition size.

It's interesting enough that I may try it on a scratch disk just for fun.

---

