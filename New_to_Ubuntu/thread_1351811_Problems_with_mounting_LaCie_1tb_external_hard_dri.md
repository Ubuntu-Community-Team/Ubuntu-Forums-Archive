---
title: "Problems with mounting LaCie 1tb external hard drive"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by MentalOxide on 2009-12-10
OK, so I am trying to use my new LaCie Rugged XL 1tb, but I've hit a wall (figuratively). When I first connected it via USB it mounted, but only saying only 4.5mb available. Seems the Hard drive contained LaCie software. So from the forums it seemed the common thing to do was format it, so I did, under gparted. But now it doesn't mount.

Can anyone offer me guidance on this?

Thanks in advance. 

PS.

lsusb lists this:
 redexe@redexe-laptop:~$ lsusb
Bus 001 Device 002: ID 059f:1024 LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Geoff918 on 2009-12-10
Hmm, sounds to me like that's the "extra partition" that has the software loaded on it. That's the only reason it would show 4.5 MB free on a new drive.

sudo fdisk -l 

output please?

******

that's an "ell"

---

### Post by MentalOxide on 2009-12-10
Wow! Fast response, thanks heaps. 

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009868a

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Geoff918 on 2009-12-10
Your device is /dev/sdb...

It's definitely there, it's showing 1000.2 GB

When you're in pamplimpset or gparted or whatever partition editor you desire (could even be fdisk from CLI--let's not though).

Go ahead and make sure you're on device sdb

From there, go ahead and partition as you so desire. If you keep it as NTFS you can still use that drive w/windows without further modification.

If you instead go for an EXT2 or EXT4 type drive of course you can't use that on a windows system w/o first installing appropriate utils to make Windows "get it".

You can format. Then it should automatically "hot swap" (mount on USB insert).

Let me know how this goes for you. :)

---

### Post by MentalOxide on 2009-12-10
OK, thanks for the pointers. 

Just on the ext2 point, can I install those utils after formatting?

---

### Post by Geoff918 on 2009-12-10
Well, you can certainly. But you'd need those utilities on any Windows machine you may use. And, keep in mind that having those utils on the ext2 formatted drive wouldn't be readable from the windows machine you want to use it as such from.

For that, perhaps create a second small partition that's NTFS or FAT32 and store the utils there?

EXT2 is fast, but doesn't journal, e.g. have a stored copy of data before write. I didn't mention EXT3 because it's pretty abysmal when it comes to performance. Probably the worst filesystem that's offered today. Even IBM's JFS vastly outperforms EXT3 and it predated EXT3 by nearly a decade.

Okay, enough random babbling from me.

---

### Post by egalvan on 2009-12-11
> **Geoff918 said:**
> 
For that, perhaps create a second small partition that's NTFS or FAT32 and store the utils there?

Or download onto the Windows machine while it is logged onto the internet.

> EXT2 is fast, but doesn't journal, e.g. have a stored copy of data before write. I didn't mention EXT3 because it's pretty abysmal when it comes to performance. Probably the worst filesystem that's offered today. Even IBM's JFS vastly outperforms EXT3 and it predated EXT3 by nearly a decade.

Curious...
ext2 is ext3 without journal
ext3 is ext2 with journal

(take an ext3 filesystem, and you can access it read/write with an older kernel that only understands ext2... just turn off journal)

so if ext2 is fast, how is ext3 abysmal?

and let's not forget that ext3 has been in use for quite some time, 
by many, many systems both large and small,
and is considered very solid, reliable and fast.

And many "benchmarks" can be tweaked to show better performance on one type of access or another...
small-block read
small-block write
large-block read
large-block write
random, sequential, blah, blah, blah.
reliability
ease of back-up
journal

pick your poison... some file systems do better in one,
some in others.

in the end, it's YOUR choice.
As most things in Linux-Land.

ext3 has been around the block more than once :)

---

### Post by Geoff918 on 2009-12-11
> **egalvan said:**
> Or download onto the Windows machine while it is logged onto the internet.



Curious...
ext2 is ext3 without journal
ext3 is ext2 with journal

(take an ext3 filesystem, and you can access it read/write with an older kernel that only understands ext2... just turn off journal)

so if ext2 is fast, how is ext3 abysmal?

and let's not forget that ext3 has been in use for quite some time, 
by many, many systems both large and small,
and is considered very solid, reliable and fast.

And many "benchmarks" can be tweaked to show better performance on one type of access or another...
small-block read
small-block write
large-block read
large-block write
random, sequential, blah, blah, blah.
reliability
ease of back-up
journal

pick your poison... some file systems do better in one,
some in others.

in the end, it's YOUR choice.
As most things in Linux-Land.

ext3 has been around the block more than once :)

Wow, okay, okay, easy there. I didn't mean to get anyone all riled up. Ext3 is tried and true. I'm sorry, I've seen more than enough benchmarks to say Ext3 fails pretty hard performance-wise versus other file systems. I don't choose to use it. I'd rather use EXT4, (EXT2 if it's not too mission critical, e.g. boot partition). If it were more standard, I'd probably adopt JFS rather than Ext3. I personally use EXT4 on all of my drives. It's several years old as well.

---

### Post by MentalOxide on 2009-12-11
OK. All cool. Thanks a million Geoff. My 1 tb is up and running. I made a 3 gig FAT 32 partition for the win apps you mentioned, the rest is in ext 2. 

Consider this one solved.

---

