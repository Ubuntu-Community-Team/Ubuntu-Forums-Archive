---
title: "Partition Size Issues - Vista/Ubuntu"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by TommyD82 on 2009-10-27
Hi Everybody,

I'm brand new on these forums, and to Linux too.  For fun, and to broaden my computing horizons, I've downloaded and installed Ubuntu 9.04 as a dual-boot with Windows Vista.  I've run into a problem though with partition sizes.  When I installed Ubuntu, the system only allocated about 2gb for the Ubuntu partition.  I've tried to Google solutions, and have had a quick look on here too, but it seems that all the solutions require me to have sorted it out during the setup stage.  I have managed to chop 10gb from the Vista partition, but I can't seem to reallocate it to Ubuntu.  

I can't download anything/start working through my other Ubuntu issues until I manage to get this sorted.  SOS!  All help gratefully received!

Cheers,

Tom

---

### Post by halitech on 2009-10-27
how did you install as a dualboot? did  you use wubi or did you do a true dualboot install?

run ```
sudo fdisk -l
```and post the output here

---

### Post by TommyD82 on 2009-10-27
I downloaded the ISO image from the web, burned it onto a DVD, and then followed the installation instructions.  Output from your instruction is as follows.

tom@TomsLaptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaaa1de2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702         893     1536000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3             893       12858    96107992    7  HPFS/NTFS
/dev/sda4           14269       14593     2610562+   5  Extended
/dev/sda5           14269       14571     2433816   83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris

---

### Post by halitech on 2009-10-27
ok, you have a true dual boot setup which is good. There is some info here about resizing partitions from the Ubuntu side but  you will need to defrag at least twice in windows and use the windows tools to shrink your windows partition. then use the steps in the link to enlarge your Ubuntu install

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Charles Ingalls on 2009-10-27
I also have some issues regarding partitions with my computer. Since I'm kind of new to Linux, I'd love some advice. I have XP and 9.04 as dual boot but I think I have way too many partitions on my drive because of a few manipulations I did without knowing exactly what I was doing.

Here is my fdisk-l:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x789cf960

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3754    30153973+   7  HPFS/NTFS
/dev/sda2            3755       18431   117893002+   5  Extended
/dev/sda3           18432       19452     8201182+  1c  Hidden W95 FAT32 (LBA)
/dev/sda4           19453       19457       40162+  82  Linux swap / Solaris
/dev/sda5            3755       17709   112093506   83  Linux
/dev/sda6           18058       18431     3004123+  82  Linux swap / Solaris
/dev/sda7           18036       18057      176683+  82  Linux swap / Solaris
/dev/sda8           17710       18013     2441848+  83  Linux
/dev/sda9           18014       18035      176683+  82  Linux swap / Solaris

And here is a link to a screenshot I made with GParted: [http://img300.imageshack.us/img300/2312/screenshotdevsdagparted.png](http://img300.imageshack.us/img300/2312/screenshotdevsdagparted.png)

I gotta admit I'm a bit lost with this stuff, so my questions are :
1 - Do I need as many swap partitions?
2 - What size should I choose, knowing that I have 1GB RAM on my EeePC?
3 - How do I change these things without taking the risk of losing crucial files?

Thanks in advance for any kind of advice regarding these matters.

---

### Post by halitech on 2009-10-27
> **Charles Ingalls said:**
> I also have some issues regarding partitions with my computer. Since I'm kind of new to Linux, I'd love some advice. I have XP and 9.04 as dual boot but I think I have way too many partitions on my drive because of a few manipulations I did without knowing exactly what I was doing.

Here is my fdisk-l:


And here is a link to a screenshot I made with GParted: [http://img300.imageshack.us/img300/2312/screenshotdevsdagparted.png](http://img300.imageshack.us/img300/2312/screenshotdevsdagparted.png)

I gotta admit I'm a bit lost with this stuff, so my questions are :
1 - Do I need as many swap partitions?
2 - What size should I choose, knowing that I have 1GB RAM on my EeePC?
3 - How do I change these things without taking the risk of losing crucial files?

Thanks in advance for any kind of advice regarding these matters.

might want to start a new thread to keep the issues seperate :)

as far as answers:
1. no, you only need 1 swap partition
2. I would go with a 1 gig swap partition
3. knowing you don't have a cdrom in your eeepc, I'm not sure how to make a usb boot but you can't do it from a running install

---

### Post by TommyD82 on 2009-10-27
Thanks Halitech,

I followed the link you posted, and I'm now in the process of mucking about with my partitions.  I really didn't think I'd be enjoying this kind of fiddling around as much as I am!

Tom

---

### Post by TommyD82 on 2009-10-27
Right, now I feel like a bit of a spanner.  Following instructions, I copy/pasted the following into the terminal.

sudo mkdir /old
sudo mount -t ext3 */dev/sda1* /old
sudo mkdir /new
sudo mount -t ext3 */dev/sda3* /new

I thought I would then have the opportunity to change the partition names from the example to my own before I hit enter.  Of course, that didn't happen.  As soon as I pasted it in, the terminal processed it.  Any tips on how to fix this schoolboy error?

Cheers!

---

### Post by martrn on 2009-10-27
There are two live CD's that you can burn to a cd to do these things for you and are CDs' full of partitioning formatting and mounting tools for you to mount resize and manage graphically the partitions of your hard drive.  Just be careful because changing the partitions of your hard drive is unrocoverable if there is an error so just make sure what you want to do, is what you are asking the computer to do before you click confirm and make the changes pertinents.  Planning is a good thing before ensuring you commit to a new solution.

[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")
[http://partedmagic.com/]("http://partedmagic.com/").

I sudgest 1GB for vista and the rest to ubuntu, but its not my disc.

500MB is fine for a swap partition.

---

### Post by LewRockwell on 2009-10-27
Vista does not take kindly to other partitioning editors messing with it's partition so you'll probably want to use the Vista editor

.

---

