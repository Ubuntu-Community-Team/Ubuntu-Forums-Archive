---
title: "NTFS resizing"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by Uruk-hai on 2010-11-01
I was wondering if there is any easy way to resize my NTFS partion. Is there an easy way of doing this with a program or some kind command? I'm very new at this so use basic terms please...lol.
thanks all. ;)

---

### Post by Hippytaff on 2010-11-01
You can do it with a programme called Gparted from a live CD, but back everything up first because things can go wrong :-)

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by zvacet on 2010-11-01
Boot your Ubuntu live CD and under system start gparted.With it resize partition.You can add unallocated space to ubuntu partition.

---

### Post by NertSkull on 2010-11-01
If you have ubuntu installed and the NTFS drive is just another mounted drive (i.e. the windows mount).  You don't even need to use a live CD.  GParted is in the repositories and is a great little tool.

But yeah, definitely back up everything first.

---

### Post by Uruk-hai on 2010-11-01
> **NertSkull said:**
> If you have ubuntu installed and the NTFS drive is just another mounted drive (i.e. the windows mount).  You don't even need to use a live CD.  GParted is in the repositories and is a great little tool.

But yeah, definitely back up everything first.

Why would I need to back everything up first? Is it possable that I could loose my stuff? Or will it just wipe it anyway?
Also. How do I use this program gparted? Is it idiot proof or is it for crazy linux people?

---

### Post by sandyd on 2010-11-01
> **Uruk-hai said:**
> Why would I need to back everything up first? Is it possable that I could loose my stuff? Or will it just wipe it anyway?
Also. How do I use this program gparted? Is it idiot proof or is it for crazy linux people?

because whenever you mess with partitions, something bad can possibly happen.



its quite easy.
First, install gparted.
```

sudo apt-get install gparted
gksudo gparted
```

Second, choose the partition (mind you, choose the right one!)
right click it and choose resize.

Play with the slider until you have the space you want, and click ok.

click on the green checkmark.

oh, and don't resize it with gparted if the partition contains windows vista/7.

---

### Post by Uruk-hai on 2010-11-01
So is there a way to tranfer hard drive space to my ubuntu partion so its not like 7 GBs? How do you do it in gparted?

---

### Post by sandyd on 2010-11-01
> **Uruk-hai said:**
> So is there a way to tranfer hard drive space to my ubuntu partion so its not like 7 GBs? How do you do it in gparted?

post output of
```

sudo fdisk -l
```

actually, a screenshot of gparted would be better.

---

### Post by cariboo on 2010-11-01
You would probably be better off resizing your NTFS partition using the Windows disk management software. Then use gparted to increase the size of you Ubuntu partition.

---

### Post by Uruk-hai on 2010-11-01
> **sandyd said:**
> post output of
```

sudo fdisk -l
```

actually, a screenshot of gparted would be better.

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       59527   478110465    7  HPFS/NTFS
/dev/sda3           60742       60802      484352   82  Linux swap / Solaris
/dev/sda4           59528       60742     9751553    5  Extended
/dev/sda5           59528       60684     9285632   83  Linux
/dev/sda6           60684       60742      464896   82  Linux swap / Solaris

---

### Post by Uruk-hai on 2010-11-01
> **cariboo907 said:**
> You would probably be better off resizing your NTFS partition using the Windows disk management software. Then use gparted to increase the size of you Ubuntu partition.

Is increasing the size of a partition and resizing a partition different? All I want to do is make it so I have more hardrive space in my ubuntu partition.

---

### Post by sandyd on 2010-11-01
> **Uruk-hai said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       59527   478110465    7  HPFS/NTFS
/dev/sda3           60742       60802      484352   82  Linux swap / Solaris
/dev/sda4           59528       60742     9751553    5  Extended
/dev/sda5           59528       60684     9285632   83  Linux
/dev/sda6           60684       60742      464896   82  Linux swap / Solaris

any reason why you have two swap partitions?
If you don't have any,
post output of 
```

cat /etc/fstab
```

Current thoughts (dont do it though...)
delete /dev/sda3
resize /dev/sda2 with free space created on the right
boot into livecd, swapoff /dev/sda6 (or whatever it will be called after /dev/sda3 is deleted)
expand the extended partition
expand the linux partition

---

### Post by sandyd on 2010-11-01
> **Uruk-hai said:**
> Is increasing the size of a partition and resizing a partition different? All I want to do is make it so I have more hardrive space in my ubuntu partition.

if you don't have windows7/vista, you don't need to resize the ntfs partition in windows.

The thing is, free space is best created to the right of a partition when it is shrunk. That part is easy and quite fast.
The really slow part is expanding the ubuntu partition.

---

### Post by Uruk-hai on 2010-11-01
> **sandyd said:**
> if you don't have windows7/vista, you don't need to resize the ntfs partition in windows.

The thing is, free space is best created to the right of a partition when it is shrunk. That part is easy and quite fast.
The really slow part is expanding the ubuntu partition.

okay. I am using xp right now. So how do make my ubuntu partition bigger? Do I use gparted? If so, how do I use it?

---

### Post by Mark Phelps on 2010-11-01
The vast majority of problems reported using GParted to resize NTFS partitions where when the partitions were Vista/Win7 OS NTFS partitions.  And even then, not ALL cases were reported as problems -- only some.

But ... in those problem cases, Vista/Win7 was rendered unbootable -- which meant that without repairing the partitions (something that could NOT be done using Ubuntu or GParted), the folks lost usage of their Vista/Win7 OSs.

Which is why SOME of us tell everyone who is going to resize a Vista/Win7 OS partition to use the MS Windows builtin Disk Management utility -- NOT Gparted.

---

### Post by NertSkull on 2010-11-01
I'd agree that using the windows management would be ideal in your case.

Basically you would want to shrink your windows partition (NTFS) using the windows disk utility.

THEN, after you have shrunk it, load into linux and use GParted to increase the Ubuntu disk space into the free/unformatted space you just created.

More steps, but probably the safest way.

And again, backup.  The design is not to lose any data, if all runs smooth the backup will not be used.  BUT, as always with partitioning, things can often go wrong.  Better to be safe.


How to use it.

I don't remember for sure in windows.  Been years since I've used it.  But GParted is pretty straight forward.  You select the hard drive (in upper right) then you can go through all the actions you want it to do.  But it actually doesn't change anything until you hit start or apply or go or some button like that.  GParted has a GUI and is way easy to use.  I'm sure there is lots of stuff out there on how to do the windows portion though.

---

### Post by sandyd on 2010-11-01
> **Uruk-hai said:**
> okay. I am **using xp** right now. So how do make my ubuntu partition bigger? Do I use gparted? If so, how do I use it?

> **NertSkull said:**
> I'd agree that using the windows management would be ideal in your case.

Basically you would want to shrink your windows partition (NTFS) using the windows disk utility.

THEN, after you have shrunk it, load into linux and use GParted to increase the Ubuntu disk space into the free/unformatted space you just created.

More steps, but probably the safest way.

And again, backup.  The design is not to lose any data, if all runs smooth the backup will not be used.  BUT, as always with partitioning, things can often go wrong.  Better to be safe.


How to use it.

I don't remember for sure in windows.  Been years since I've used it.  But GParted is pretty straight forward.  You select the hard drive (in upper right) then you can go through all the actions you want it to do.  But it actually doesn't change anything until you hit start or apply or go or some button like that.  GParted has a GUI and is way easy to use.  I'm sure there is lots of stuff out there on how to do the windows portion though.
Only windows 7/vista has the partiton resizer.
-----------------------

anyways,

do you need the swap space that I mentioned earlier?
and can you post the output of
```

cat /etc/fstab
```

---

### Post by NertSkull on 2010-11-01
ah, I stand corrected.  Like I said I haven't used windows in some time.  But thats right, XP doesn't have that capability.

You can get commercial ones (like partition magic) but that doesn't seem worth it for the price.

I'm sure sandyd and others will have better advice :)

---

### Post by Jerry N on 2010-11-01
I don't think it has been mentioned but if you want to resize an NTFS partition containing Win XP and you want to continue using XP, it is imperative that you run your Windows defragmenter, preferably more than once.  You should then start defragment again and note where the last used sectors are located on your hard drive, ie  at 50%, 75%.  You can then boot up one of the partition editor programs and resize the NTFS partition but don't make it so small that you delete the last used sectors noted above.  I would suggest then booting into Windows XP to see if everything is still OK.  I have done this several times without hurting anything.  And yes it is very easy to screw up the works with the partition editor.  It will give you a chance to back out of whatever you have told it to do but beyond that the changes are irreversible.  Back up all files important to you before doing any of this stuff.  As a matter of fact, back up those files even if you aren't going to do any of this stuff!!!  

Jerry

---

### Post by Uruk-hai on 2010-11-02
> **sandyd said:**
> Only windows 7/vista has the partiton resizer.
-----------------------

anyways,

do you need the swap space that I mentioned earlier?
and can you post the output of
```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=95b658e1-267a-48fb-86f8-e105f8942629	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda2 :
UUID=60E09790E0976AD4	/media/sda2	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda6 :
UUID=88b65607-1657-4dd1-a26d-79273b496304	none	swap	sw	0	0

ok...I'm still a bit confused. There's no easy way to just make it so that the NTFS partition has less and then just add that to the ubuntu partition?

---

### Post by Mark Phelps on 2010-11-02
> **Uruk-hai said:**
> ok...I'm still a bit confused. There's no easy way to just make it so that the NTFS partition has less and then just add that to the ubuntu partition?

That's called "resizing" -- shrinking one partition and growing another.

As to MS Windows partitioning apps, Google for EASEUS Partition Master.  It's a free download that should allow you to resize the XP NTFS partition without problems.

---

### Post by AnjanaSofia on 2010-11-15
Jumping in here with a related issue...(And as a disclaimer I'm totally new to Linux, Ubuntu 10.10 will be popping my cherry... if I can get it to work!)

I'm trying to install 10.10 alongside the already-installed XP on my eee pc 1005HA. For some reason the disk came formatted into 4 partitions, so the "install alongside another OS" option in the Ubuntu install does not show up for me, so I have to do some tinkering with partitions.

I'd like to make my XP (ntfs) partition as small as possible... right now it's about 77GB with a little over 22GB used. Ideally, I'd like to shrink it down to 30 or maybe 35 just to be on the safe side. 

I've seen people say stuff like:

> **Jerry N said:**
> I don't think it has been mentioned but if you want to resize an NTFS partition containing Win XP and you want to continue using XP, it is imperative that you run your Windows defragmenter, preferably more than once.  You should then start defragment again and note where the last used sectors are located on your hard drive, ie  at 50%, 75%.  You can then boot up one of the partition editor programs and resize the NTFS partition but don't make it so small that you delete the last used sectors noted above.  
Jerry

So here's my issue: after defragging 3 times, the partition with XP on it still looks like the attached picture; there's nothing left to defrag, but after a bunch of free space there's some file(s) left way out on the right side. I don't want all that space wasted, but I'm afraid if I try to shrink it to less than 50% of the drive it will erase those out-there files and eff things up. 

Is there a way to move those stupid files closer to the beginning so I can shrink this partition? The XP disk management utility won't allow me to shrink the C: drive. I've heard that gparted can do this, but I've also heard the opposite, and like I said I'd rather not screw things up and have to restore XP from CD. 

Any suggestions??? 

Oh and let me know if this belongs somewhere else on the forum - dumb newbie here. 

Thanks in advance!

---

### Post by Mark Phelps on 2010-11-16
Resizing is NOT your problem.  Your problem is that you already have the maximum partition limit.  Your problem is a LOT harder to solve.

Please don't "jump in here" with your own, different, problem.

You would do better starting your own thread -- and mention that you already have 4 primary partitions -- so folks will know what kind of problem you have.

---

### Post by AnjanaSofia on 2010-11-16
OK, I'll start a new thread, but just to clarify:

I don't actually think the number of partitions is my main problem, because I can delete one. See, Acer shipped the laptop with the 150GB hard drive split up into two 72GB partitions (C: and D: in Windows), a small recovery partition, and a tiny partition that I'm guessing is for something Windows system-related. Anyway the D: drive is practically empty, so I'm pretty sure I can just delete that partition to make room for Ubuntu. The thing is, I want to make even more room by shrinking the C: drive, and that's where the resizing comes in, which is what I'm asking for help with. Is that not related to the discussions in this thread? Especially Jerry's advice?

---

