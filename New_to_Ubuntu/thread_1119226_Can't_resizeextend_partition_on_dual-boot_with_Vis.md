---
title: "Can't resize/extend partition on dual-boot with Vista"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by jondgls on 2009-04-07
I've found many threads regarding partitioning but haven't found the right thread so...sorry if this has been covered.

As you can see from the attachment I have the following drive partitions:
/dev/sda1 - 63.47GB - NTSF - Windows Vista (Original OS)
/dev/sda2 - 9.76 GB - Extended
    /dev/sda5 - ext3 - ubuntu 8.10 (recently installed)
159.65 GB Unallocated space

As far as I know the unallocated space is after both partitions. I would like to increase the size of the /dev/sda2/5 partition (ubuntu) because I intend to transition fully into ubuntu over time.

I am not able to extend the ubuntu partition with GParted or Vista Disk Management.

I have a feeling I have not setup the partitions correctly by installing ubuntu on an extended partition rather than a primary / logical partition.

I am looking for a long term solution. I am comfortable making complete OS backup images if required to re-format the drive and setup correctly (I have a few TB's of space available if needed.)

I also don't understand any of the /root or swap drive file system terms. Any comments / advice / suggestions would be greatly appreciated. 

JonDgls

---

### Post by Odd_sam on 2009-04-07
You can't use a disk to resize it's self. You will need to boot into the live CD and use gparted. I'll watch this thread so post back if this was what you were looking for or if you need more info.

---

### Post by louieb on 2009-04-07
About partitions and Gparted.
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") 

and as pointed out before - in your case you you will have to run Gparted from a live CD. When I need to use Gparted. I use a [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by Didius Falco on 2009-04-08
When you boot from the Live cd, make sure you resize the extended partition (sda2) before you try to resize the logical partition inside it (sda5). Otherwise, you'll run into the same problem.

Root is where Ubuntu itself is installed. If you look at your screenshot, you'll see that the sd5 partition is listed as "/" under the mount category - that indicates that it is the Root. You can make another small partition and designate it as a Swap partition. Ubuntu will automatically recognize it, and use it as needed. 

I'd recommend creating a third logical partition inside that extended partition and making it your Home partition. It makes reinstalls/back ups much easier and helps protect your personal data.

A search in these forums/Google should give you plenty of guidance on how to do all that, and the folks in these forums are great about helping out with tips and advice.

As always, a backup of important data is recommended before you mess with partitions.

Good luck!!

---

### Post by jondgls on 2009-04-08
So if I wanted to add a swap drive and /home partition to my existing partitions how would I go about that? (See attachment in top post for current partitions)

When i try to create a new partition using GParted on live CD there is no swap partition option only primary or extended. 

I would like to end up with ubuntu on 20gb, swap partition on 4gb (2gb RAM on-board) and then the remaining unallocated space for the /home partition.

Should I take the following steps?:
1. Extend my current ubuntu partition (sda2) to use all unallocated space.
2. Create new logical partition inside of the extended partition of 145gb for /home
3. Create another new logical partition inside the extended partition of 4gb for swap
4. Leaves 20gb with ubuntu
5. Transfer /home to the new partition

JonDgls

---

### Post by Didius Falco on 2009-04-08
yep, that's about the size of it. As you create the logical partition inside the extended partition you'll be using for swap, you set it to a linux-swap File system using the dropdown box.

Here is a link to the Wiki. It should tell you everything you need to accomplish this.

[http://wiki.partedmagic.com/index.php/Using_GParted](http://wiki.partedmagic.com/index.php/Using_GParted) 

To move your existing Home partition data:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I hope this helps...

On Edit: that psychocats site has a lot of great tutorials. If you just want to wipe it all out and do a fresh setup, check out the "Planning Partitions" section. Between that and the Gparted Wiki, you'll be set up in no time.

Here is one more resource for information that may be useful:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by jondgls on 2009-04-09
I have completed the tutorial at [[COLOR="Blue"]_psychocats_[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") to create a separate /home partition but I am not sure if it has worked.

The reason I am unsure is because 
1. A /home directory still exists on (sda5) where it was installed with ubuntu; and
2. The used space on partition (sda6) has remained the same after I completed the tutorial.

How do I verify which /home directory in use on startup?

I have included screenies of GParted & Nautilus showing partitions and filesystem after tutorial completed.

JonDgls

---

### Post by JoshuaRL on 2009-04-09
> **jondgls said:**
> I have completed the tutorial at [[COLOR="Blue"]_psychocats_[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome") to create a separate /home partition but I am not sure if it has worked.

The reason I am unsure is because 
1. A /home directory still exists on (sda5) where it was installed with ubuntu; and
2. The used space on partition (sda6) has remained the same after I completed the tutorial.

How do I verify which /home directory in use on startup?

I have included screenies of GParted & Nautilus showing partitions and filesystem after tutorial completed.

JonDgls

Well, the way Linux works is that even separate partitions, disks, and devices aren't separate from the system.  They're "mounted" onto the root filesystem in appropriate places so that the OS can use them.  So, if you connected an iPod, it wouldn't be found in the root folder, but under /media/iPod.  So if you have a separate /home, it would still be found under /home in the root folder like it's supposed to be.  This is different from Windows that puts all that in under My Computer.  A little different, but it makes sense once you understand it.

To check if you've got it moved over correctly, right click the /home folder and see what it says for space.  If it isn't over 100GB, then its probably not right.

---

### Post by louieb on 2009-04-09
Congrats looking at the Gparted screen shot shows /home is the mount point for sda6. 

The directory /home is as it should be (on sda5 that is) but now you made it the mount point for the base directory of sda6. :guitar:

---

