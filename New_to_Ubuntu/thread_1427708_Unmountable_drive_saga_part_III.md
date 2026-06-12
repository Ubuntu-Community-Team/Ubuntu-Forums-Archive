---
title: "Unmountable drive saga part III"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by AutumnPhoenix on 2010-03-11
Ok, so my new hard drive came and my old hard drive is sitting in a SATA to USB device

Can't figure out which is the hard drive in the device and which is in my computer.  I'm woefully incompetant when it comes to this, sorry.

Ran sudo fdisk and the output was as such
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris



Without it plugged in:
> 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

So I'm guessing that my now external used-to-be main drive is 
"dev/sdb"

so how can I force it to play with me?

It actually seems to be spinning or atleast vibrating with some consistancy.

---

### Post by b0b138 on 2010-03-11
Yes sdb is your external drive.

You just need to mount it to access it, should be available under Places.

---

### Post by presence1960 on 2010-03-11
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
[COLOR="Red"]Disk identifier: 0x0000af88[/COLOR]

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4659 37423386 83 Linux
/dev/sda2 4660 4864 1646662+ 5 Extended
/dev/sda5 4660 4864 1646631 82 Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
[COLOR="Red"]Disk identifier: 0xcccdcccd
[/COLOR]
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4659 37423386 83 Linux
/dev/sdb2 4660 4864 1646662+ 5 Extended
/dev/sdb5 4660 4864 1646631 82 Linux swap / Solaris 
```

---

### Post by AutumnPhoenix on 2010-03-12
Hi again.

It will not mount, the computer won't "see" it unless I'm running that command.

I brought it to work and plugged it into my windows pc there and it also saw, but would not acess, the drive.  Not that that surprizes me at all.

And I've tried the systemrescueCD and testdisk but I feel so much like a fish out of water with those and have no clue what to do or how to find or save my data.

I just want to get my .doc/.jpg/.xls and maybe my videos..though I don't know the extentions of those files.

---

### Post by AutumnPhoenix on 2010-03-12
Ran sdb1 insted of just sbd
> sudo e2fsck -fyv /dev/sdb1

> e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  240769 inodes used (10.28%)
     495 non-contiguous files (0.2%)
     148 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 218912/77
 3051190 blocks used (32.61%)
       0 bad blocks
       1 large file

  189438 regular files
   27113 directories
      68 character device files
      26 block device files
       0 fifos
     388 links
   24112 symbolic links (21673 fast symbolic links)
       3 sockets
--------
  241148 files


sbd2-gets me a message about there being nothing there
sbd5-gets me the bad superblock message

---

