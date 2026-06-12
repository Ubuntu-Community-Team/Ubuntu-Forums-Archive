---
title: "Fresh install, missing HDD space?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by suverity on 2011-03-07
Just installed Ubuntu 10.10 couple of days ago - learning a lot, but I cannot figure out whats going on here. Ubuntu is installed on a 750GB HDD. This system is single boot. I used the Guided Partitioning during the Ubuntu installation, telling it to use the entire drive. I set aside ~18 GB for swap. Just earlier I noticed in Nautilus that it said my free disk space was only 370.3 GB. 

GParted shows the following:

Partition - System - Mount - Size
/dev/sda1  ext2   /boot   243 MB
/dev/sda2 extended - 698.40 GB
-> /dev/sda5 lvm2 - 698.40 GB

And something I thought was a little odd.. opening file system -> properties thru computer:/// the resulting dialog says, "Contents: 306,144 items, totalling 128.0 TB
(some contents unreadable)"  ... 128 TB??? 

more info (note there is also a 1TB external connected):  

~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Desktop1-root
                     414952416   5667332 388206660   2% /
none                   4086796       308   4086488   1% /dev
none                   4096848       340   4096508   1% /dev/shm
none                   4096848        92   4096756   1% /var/run
none                   4096848         0   4096848   0% /var/lock
/dev/sda1               233191     50792    169958  24% /boot
df: `/home/nick/.gvfs': Transport endpoint is not connected
/dev/sdb1            976760032 279592196 697167836  29% /media/FreeAgent GoFlex Drive
/home/nick/.Private  414952416   5667332 388206660   2% /home/nick

-----------

~$ sudo fdisk -l
[sudo] password for nick: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000412de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      248832   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32       91202   732322817    5  Extended
/dev/sda5              32       91202   732322816   8e  Linux LVM

Disk /dev/dm-0: 431.7 GB, 431686156288 bytes
255 heads, 63 sectors/track, 52482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 18.2 GB, 18249416704 bytes
255 heads, 63 sectors/track, 2218 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
1 heads, 63 sectors/track, 31008335 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2    31008256   976760032+   7  HPFS/NTFS

Disk /dev/dm-2: 18.2 GB, 18249416704 bytes
255 heads, 63 sectors/track, 2218 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x006532c9

Disk /dev/dm-2 doesn't contain a valid partition table


-------------

~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/Desktop1-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=ca38bccc-2690-4ce7-bf1d-f946ff660bcf /boot           ext2    defaults        0       2
/dev/mapper/Desktop1-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

--------------

~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/mapper/Desktop1-root
                       425G   5.9G   398G   2% /
none                   4.2G   316k   4.2G   1% /dev
none                   4.2G   349k   4.2G   1% /dev/shm
none                   4.2G    95k   4.2G   1% /var/run
none                   4.2G      0   4.2G   0% /var/lock
/dev/sda1              239M    53M   175M  24% /boot
df: `/home/nick/.gvfs': Transport endpoint is not connected
/dev/sdb1              1.1T   287G   714G  29% /media/FreeAgent GoFlex Drive
/home/nick/.Private    425G   5.9G   398G   2% /home/nick

------------


Any help greatly appreciated!

---

### Post by Dutch70 on 2011-03-07
Welcome to UF suverity.

Can you open Gparted and take a screenshot of your partitions and attach it to your next post.

Also, a pic of Nautilus showing your free space that you question.

I'm thinking Nautilus is just giving you the free space in a folder or partition or something, but would like a visual, or maybe it will help someone with more knowledge than myself.

---

### Post by mrhhug on 2011-03-07
first off Welcome to linux!

Im surprised that the guided install of 10.10 chose ext2 filesystem. If it were me and i just installed a new OS, i would reformat into ext4. 16GB of swap is serious overkill. swap space should be 2x your ram but never over 1 GB(in non server environments).

whats mounted at /dev/dm-X?

if you could please remove the external drive until you get your base system running smooth, then add externals and card readers and printers and the such after your core system is solid.

the bits to bytes conversion is awkward because bytes are base 8 instead of what most people are used to (base10) hard drive manufactures exploit that.

if you think something is eating away at your hard drive-- like a viruses or some uncompress video I was working with 2 months ago and forgot to delete. use baobab to track down whos eating my hard drives.

the 128TB thing is really goofy. that would have made me have to clean my glasses!

---

### Post by grahammechanical on 2011-03-07
Use Disk Utility in System>Administration and you will get a pictorial view of you hard disc complete the measurements of the drive and the partitions. Nautilus is not the tool for finding out how Linux measures your hard disk. It is a file manager.

Regards.

---

### Post by suverity on 2011-03-07
> **Dutch70 said:**
> Can you open Gparted and take a screenshot of your partitions and attach it to your next post.

Also, a pic of Nautilus showing your free space that you question.

Attatched.



[QUOTE=mrhhug]Im surprised that the guided install of 10.10 chose ext2 filesystem. If  it were me and i just installed a new OS, i would reformat into ext4.  16GB of swap is serious overkill. swap space should be 2x your ram but  never over 1 GB(in non server environments).  
...
if you think something is eating away at your hard drive-- like a  viruses or some uncompress video I was working with 2 months ago and  forgot to delete. use baobab to track down whos eating my hard drives.
[/QUOTE]

I have 8GB RAM, so I was just doing 2x that, plus a little extra. 

I don't think anything is eating away at it - actually I was mostly thinking I probably either made a mistake in the initial partitioning, or that I was just confused... or perhaps a little of both. If that's the case, its not a *major* deal at this point to wipe and do another clean install, and maybe use the ext4 filesystem as you suggested. 

Thanks for the replies guys.

---

### Post by Dutch70 on 2011-03-07
> **suverity said:**
> 
I have 8GB RAM, so I was just doing 2x that, plus a little extra. 

I don't think anything is eating away at it - actually I was mostly thinking I probably either made a mistake in the initial partitioning, or that I was just confused... or perhaps a little of both. If that's the case, its not a *major* deal at this point to wipe and do another clean install, and maybe use the ext4 filesystem as you suggested. 

Thanks for the replies guys.

LOL, Now that's a pic!!! I said "Attach" it to your next post. As in, with the little paper clip in the toolbar when you post. j/k btw :P

Is there a reason why your flagged sda5 with lvm? That may have something to do with it showing that way in nautilus. I've never used lvm though. 

Also, is there a special reason you have a dedicated boot partition?

With 8GB of RAM, I doubt you need swap at all, but with a TB of hdd, it wouldn't hurt to make one equal to your physical RAM. 1.5 or 2x your RAM is mostly for people with very little RAM. I have 4GB RAM & an equal swap file that **never** gets used. 

If it's no big deal for you, I would recommend you go with the ext4 filesystem. Create a "/" (root) partition, and a separate /home partition. /home is equal to "documents & settings" in windows, as swap is similar to a pagefile. With a separate /home, you can re-install without losing your documents & settings & it's quite simple.

*Note: It's easier to partition your hdd from the live cd/usb before you start the install. *

Maybe this will help...
[[COLOR="Blue"]http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml[/COLOR]]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")

Also, did you download the 32bit or 64bit version? If you're processor is capable of 64bit, I recommend it, considering the amount of RAM you have.

---

### Post by suverity on 2011-03-08
> **Dutch70 said:**
> LOL, Now that's a pic!!! I said "Attach" it to your next post. As in, with the little paper clip in the toolbar when you post. j/k btw :P
Yeah. I was looking for something like that but I didn't even see the little paper clip. 

> Is there a reason why your flagged sda5 with lvm? That may have something to do with it showing that way in nautilus. I've never used lvm though. No, I'm not even really sure what that's for.

>  Also, is there a special reason you have a dedicated boot partition?Nope. It was created automatically with the guided partition.

> With 8GB of RAM, I doubt you need swap at all, but with a TB of hdd, it wouldn't hurt to make one equal to your physical RAM. 1.5 or 2x your RAM is mostly for people with very little RAM. I have 4GB RAM & an equal swap file that **never** gets used. Good to know.

>  If it's no big deal for you, I would recommend you go with the ext4 filesystem. Create a "/" (root) partition, and a separate /home partition. /home is equal to "documents & settings" in windows, as swap is similar to a pagefile. With a separate /home, you can re-install without losing your documents & settings & it's quite simple.How much space should I set aside for these?

> Also, did you download the 32bit or 64bit version? If you're processor is capable of 64bit, I recommend it, considering the amount of RAM you have.Yeah, I'm running the 64bit currently.

---

### Post by mrhhug on 2011-03-08
were all tossing around file-system recommendations and swap space rule of thumbs.

but what is the primary purpose of this machine?

---

### Post by Dutch70 on 2011-03-08
> **mrhhug said:**
> were all tossing around file-system recommendations and swap space rule of thumbs.

but what is the primary purpose of this machine?
That's a very good question!

> How much space should I set aside for these?

Assuming it's for home use.

Although it's not recommended, you **can** install "/" (root) into a 5GB partition, 10-20 is recommended. If I had a TB, I'd make it at about 30GB for good measure. 

A good idea for swap is equal to your physical RAM.
[[COLOR="Blue"]SwapFAQ's[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

The remainder for /home.

Note that you can also create other partitions for data, back ups, music, games, just anything you want to put in it. However, you can have a maximum of 4 primary partitions per hdd, but you can have more than 60 logical partitions inside an extended partition. Sounds confusing, but it's really very simple once you play with it for a few minutes. Not to mention, you have plenty of help available.

Just for kicks, I've included a pic of my HD partitioning scheme. Although the 2nd one is a work in progress & may be wiped out at any given moment. I wish I could redo the 1st one, but I don't  have my back up windows cd. :(

Edit : notice that in the 2nd pic, Kubuntu is on a 45GB primary partition, that is so I can cut it down & install windows7 into a primary partition if I decide to do that in the future. Also of good note, is that all the OS's on that hdd share the same "data" & "swap" partitions.

---

### Post by suverity on 2011-03-08
> **mrhhug]were all tossing around file-system recommendations and swap space rule of thumbs.

but what is the primary purpose of this machine?[/QUOTE]

Nothing fancy. Daily driver, and HD streaming mostly. 


[QUOTE=Dutch70 said:**
> Assuming it's for home use.

Although it's not recommended, you **can** install "/" (root) into a 5GB partition, 10-20 is recommended. If I had a TB, I'd make it at about 30GB for good measure. 

Internal is 750GB, but 25-30 is fine. What is going to be stored in this partition?

> A good idea for swap is equal to your physical RAM.Thanks for the link, after reading a bit it does seem my initial allocation was definitely more than needed. 

> The remainder for /home.So ~ 715 GB for /home? And all my files and applications will be stored there? 

Also, use the ext4 filesystem, I don't need LVM or a dedicated /boot partition - correct?

So I would just have "/" 25-30GB, "/swap" 8GB, & "/home" ~715GB.

Should these all be logical partitions?

---

### Post by Dutch70 on 2011-03-08
> **suverity said:**
> Nothing fancy. Daily driver, and HD streaming mostly. 

Internal is 750GB, but 25-30 is fine. What is going to be stored in this partition?

The actual Ubuntu system, if you re-install Ubuntu or upgrade to a newer version of Ubuntu, say from 10.10 to 11.04 when it comes out next month. This is what you'll be re-installing.
> 
Thanks for the link, after reading a bit it does seem my initial allocation was definitely more than needed. 

So ~ 715 GB for /home? And all my files and applications will be stored there? 

Yes, Pics, Music, Docs, etc...Also your .config files will be there. That's where all your settings are stored. So, when you upgrade/reinstall, you'll keep most, if not all of them. Like your wallpaper for example. Not a big deal, but you'll come to find that many of those settings are a big deal.

> Also, use the ext4 filesystem, I don't need LVM or a dedicated /boot partition - correct?

That would be correct for a typical install. LVM (Logical Volume Manager) is mostly used if you have very little hdd space.

> So I would just have "/" 25-30GB, "/swap" 8GB, & "/home" ~715GB.

Sounds about right. Just so you know, it's just "swap" not "/swap" :)

Also, don't forget, 

1. You can have 4 primary partitions. (windows has to be in a primary if you want to add it in the future) 

2. Only 1 Extended Partition which counts as 1 of your 4 primary's.

3. More than 60 partitions inside the Extended partition, these are known as logical partitions.

A good set-up for your disk imho would be...

sda1 for "/" (root) = 25-30 GB (the sda([COLOR="Red"]1[/COLOR]) tells you its primary)
sda2 - Extended partition = All of the remainder of your disk.
sda5 - Swap 
sda6 - /home

[I]numbers 1-4 are reserved for your primary partitions. sda1, sda2 etc.
sda5 & above are logical partitions, inside an extended paritition.[/I]

You can play with Gparted to get a look at it before you **apply** anything. LOL, no more pencil & paper days. :D

---

### Post by grahammechanical on 2011-03-08
May I add something to the mix. It seems to me that we failed to get a result on the original problem.

I have just opened a Nautilus window. I have selected File System and the right clicked the window and selected properties and this is what I see:

contents: 295,553 items, totaling [COLOR=Red]128 TB[/COLOR]
(some contents unreadable)

Free space 13.7 GB

Now, I know for a certainty that my / partition is 20GB and the whole hard disc is 250GB, so what is this total of 128 TB? It is the same figure that suverity was seeing.

It cannot be terabytes.

We are still looking for an explanation. 

Regards.

---

### Post by Dutch70 on 2011-03-08
> **grahammechanical said:**
> May I add something to the mix. It seems to me that we failed to get a result on the original problem.

I have just opened a Nautilus window. I have selected File System and the right clicked the window and selected properties and this is what I see:

contents: 295,553 items, totaling [COLOR=Red]128 TB[/COLOR]
(some contents unreadable)

Free space 13.7 GB

Now, I know for a certainty that my / partition is 20GB and the whole hard disc is 250GB, so what is this total of 128 TB? It is the same figure that suverity was seeing.

It cannot be terabytes.
We are still looking for an explanation. 

Regards.

LOL, So am I. Check out the pic.

 It's a reported bug in launchpad.
[[COLOR="Blue"]https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/585472")

---

