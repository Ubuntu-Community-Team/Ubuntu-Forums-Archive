---
title: "Partitioning Questions"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Trev_or on 2009-02-28
Hey,

I installed ubuntu today,and so far everything is going a-ok. I'm actually getting accustomed to it pretty quickly, and I would like to give myself a little more space on the partition on which it is installed to work with. I have a few things I would like to do, but I'm not sure how to go about them.

First, I'd like to transfer some video files from windows to linux, so I don't have to go to the trouble of downloading them again. I have figured out how to access my windows partition and get the files into linux, but I am quickly running out of space. What I need to do is transfer the files, then delete them from windows, and then alter the partition to give the newly freed space to linux, and continue the process until I have all the files I want. If this is not possible I can get an external harddrive, but I'd rather save the money.

Second, once I have everything from windows that I need, and am ready to remove it from my machine completely, how do I go about merging the space so that Linux can use my entire drive? Ideally I'd like to be able to format the drive that windows is currently on, and then merge the empty drive with the partition that Linux is currently on. Is this possible?

I appreciate any advice that anyone can offer.

Thanks in advance,
Trev

---

### Post by agurk on 2009-02-28
Hi Trev_or,

Sure, sounds doable. First: backup, backup, backup. With that out of the way, let me give you a suggestion of how to proceed.

1. Get the excellent [GParted Live CD](http://gparted.sourceforge.net/livecd.php).
2. Defragment your Windows partition. This will prepare it for shrinking.
3. Boot off the CD and use it to shrink your Windows partition and to enlarge your Linux partition.
4. Depending on your partition layout, you may have to adjust the Grub bootloader as you go. Just ask on the forum if you get stuck. Repeat from step 2 until you have transferred everything you need.
5. When you have transferred the last files to Linux, use the GParted Live CD to remove the Windows partition completely and to resize your Linux partition to cover the available space. No need to format anything*.

* You are talking about drives and partitions, it is not entirely clear to me what you mean. Do you have more than one drive in your system?

---

### Post by rraj.be on 2009-02-28
Try this tool.

[GPARTED]("http://gparted.sourceforge.net/larry/resize/resizing.htm") Help to resize.

To install this Gparted type this in terminal 

```
sudo apt-get install gparted 
```

---

### Post by agurk on 2009-02-28
rraj.be: No, you can't resize the partitions of a running system from inside this system.

---

### Post by rraj.be on 2009-02-28
> **agurk said:**
> rraj.be: No, you can't resize the partitions of a running system from inside this system.

Yeah agurk, I am sorry. I made a mistake. Sorry dude.  . .i forgot that its for installed partition  !!

---

### Post by davec64 on 2009-02-28
agurk is absolutely right, here's the quote from the Gparted Documentation:

> Running GParted from a Linux system is the same as running it from the livecd, BUT  the livecd doesn't mount any drive ! If you run GParted from a running system, you can't work on THIS system.

At [http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

:)

---

### Post by Trev_or on 2009-03-01
@agurk 

Sorry about the confusion. I just have the one drive, and it has two partitions on it. I don't know why I started saying drive later.

Thanks for the gparted suggestion everyone. I'm going to give it a shot right now. I appreciate the support!

---

### Post by vanadium on 2009-03-01
You are aware that Ubuntu can perfectly read and write to ntfs partitions? As long as you are also using Windows, I would keep the space devoted to Ubuntu minimal, but configure my system instead to have convenient access to the data (including "My documents") on the Windows partition. That way, you can access the same data seamlessly from within the OS you happen to have running. It will provide you with a smoother experience and eventually ease your transition to Ubuntu.

---

### Post by Trev_or on 2009-03-07
@vanadium Thanks, I didn't realize that, it has been a big help.

I still have a few questions about gparted if anyone feels like taking a shot at them. Thanks to people who have come back to this thread.

Ok, so I booted from a gparted cd, and got into the program but wasn't able to move any space around. I was able to reduce space that was devoted to windows, but that left me with unallocated space that I couldn't format (because I have too many partitions currently -I have some questions about this later).

I'm hoping that I'll be able to delete my "linux-swap" partition, but first I have a few questions about the way my partitions are currently set up. 

First of all, my linux partition is highlighted by two boxes, one dark blue, the other light blue, and each box is described differently in the space below. 

the first description is:

[B]extended dev/sda4 and that has 40.07 gb, 
[/B]
and the second extension is:
[B]
ext3 /dev/sda5 and that has 38.39 gb
[/B]

but again these two apparently seperate partitions occupy the same space in the visual representation. 


The four partition that come before the one I have already described are:

fat16...39.19mb.../dev/sda1 |
ntfs recovery...9.77GB..../dev/sda2  |
NTFS.....183.01 GB..../dev/sda3| 
unallocated 1.53 mb 

and following the original partition I described is:

linux-swap  1.69gb  /dev/sda6




I also think I should point out that when I boot up my machine I have five options to select from. One is for windows, and the other four are for Ubuntu..I hope someone can shed some light on this, and I hope it wasn't too confusing.

Thanks in advance to anyone!

Trev_or |

---

### Post by Elfy on 2009-03-07
First - 5 options on your menu - 1 for windows, then you will also have 2 for each of your kernels, one normal and one recovery - as they get upgraded you get a new option added.

Second - the reason you can't format any more partitions is that you cvan have a maximum of 4 primary partitions - which includes an extended so sda1,2,3,6.

It would be easier if you gave the result of 

```
sudo fdisk -l
```

> one dark blue, the other light blue one is the extended sda5 at a guess - with sda6 inside.

To use your unallocated space, the extended needs to be resized - then you can create logical partitions inside.

Hope that helps :d

---

### Post by Trev_or on 2009-03-07
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2               6        1280    10240000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1280       25170   191895503    7  HPFS/NTFS
/dev/sda4           25171       30401    42018007+   5  Extended
/dev/sda5           25171       30181    40250826   83  Linux
/dev/sda6           30182       30401     1767118+  82  Linux swap / Solaris


Thanks for all your help pixie! I am still pretty lost on this.

---

### Post by Elfy on 2009-03-07
Ok sda4 is an extended partition - that means it can have a lot of logical partitions inside it - sda5 and sda6 are both logical partitions.

What you have to do is resize sda4 before you can use any unallocated space to resize sda5 or even to create a new logical inside. It won't work otherwise :)

I would _seriously_ consider vanadium's point that linux will allow you to read and write to ntfs partitions. Resizing and moving partitions about can take a _long_ time and there is always the possibility of data loss.

If you can move data out of sda2 into sda3 (possibly c:\ and d:\ - only you can know that at the moment) then you could then delete the now superfluous sda2 and create a new partition there - this (as long as win is installed to sda2) would achieve your aim of removing windows and gaining maximum data storage - albeit you would have 1 ntfs adn 1 linux partitions.

---

### Post by theozzlives on 2009-03-07
Your two partitions are probably root (/) and /home. You want tomove your root to make way to grow your /home. Unless sda5 is swap, then nevermind. It should say what the mountpoint is.

---

