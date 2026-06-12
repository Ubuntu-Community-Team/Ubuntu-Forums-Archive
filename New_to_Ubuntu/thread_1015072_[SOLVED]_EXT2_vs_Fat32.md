---
title: "[SOLVED] EXT2 vs Fat32"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-18
I will be installing Ubuntu 8.10 on a netbook that uses a 8GB solid state drive. Should I install Ubuntu with an ext3 Reiserfs, or Reiserfs4 to preserve the life of the SSD??? Please explain in layman and in detail when you answer.

---

### Post by taurus on 2008-12-18
You will run into problems with ownership and permissions if you use fat32/vfat filesystem for Ubuntu.

---

### Post by decoherence on 2008-12-18
> **som1special2 said:**
> I will be installing Ubuntu 8.10 on a netbook that uses a 8GB solid state drive. Should I install Ubuntu with an ext2, fat32 or someother filesystem to preserve the life of the SSD??? Please explain in layman and in detail when you answer.

ext2 is your best bet. there are up-and-coming filesystems designed to prolong the life of solid state drives but they aren't quite ready for ubuntu prime-time.

there are other tricks you can do to prolong the life of the drive. Limit the amount of logging, turn down the kernel's swappiness, etc.

[https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes](https://help.ubuntu.com/community/EeePC/Using#Reducing%20Drive%20Writes)

---

### Post by Duck2006 on 2008-12-18
[http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=EXT2+vs+Fat32&sa=Search](http://www.google.com/cse?cx=012285703143635244993%3Ai9yr8qlpb18&q=EXT2+vs+Fat32&sa=Search)

---

### Post by ibuclaw on 2008-12-18
Perhaps you could try one of the alternative filesystems, such as JFS or XFS. They provide journaling, but not block journalling, as what ext3 does (JFS also keeps the journal capped at 32MB, unlike XFS), so the impact on your SSD drive may be minimal in terms of frequency of write-backs caused by journalling.

Regards
Iain

---

### Post by Herman on 2008-12-18
> Should I install Ubuntu with an ext2, fat32 or someother filesystem to preserve the life of the SSD???I believe in using ReiserFS for flash memory because the Reiser File System is *up to fifteen times faster for writing small files* to disc, and writing small files is something that a running operating system does a lot (all the time).

Flash memory is generally slower than a hard drive for writing to disc because the flash memory's controller chip is always erasing blocks of data and re-writing them to unused blocks to spread the wear out over all the entire SSD. That's called 'wear levellng, and it means than you can't wear out the SSD by continuosly writing to the same spot in the SSD all the time, such as many people imagine will happen with a file system journal.

The use of the Reiser File System means that the slowness of the flash memory controller when writing to disc is offset by the faster speed of ReiserFS, so we end up with an operating system that writes small files to disc at a normal speed. However, the seek time for flash memory is lightning quick and the read speeds are very fast, so overall we end up with a nice fast operating system. 

With the Reiser File System I just install Ubuntu by choosing manual partitioning and then selecting the ReiserFS, and carry on with the rest of the installation as normal.

Then after Ubuntu has been installed, I boot into it, and if I want to turn off file system journaling, I just open my /etc/fstab file and edit it.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda1
UUID=6178d387-9ab5-4f23-a56d-8e0cba0addc3 / reiserfs notail,**nolog**,relatime,errors=remount-ro 0       1

# /dev/sda6
UUID=c6d20ccc-de8e-42ea-b568-aaf0cd049166 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```I edit my /etc/fstab file with the option 'nolog' to turn off file system journaling. 
The reason I do that is to make my operating system even faster, (it probably would save some wear on the flash memory as well), but I believe that a modern SSD will last as long as a hard disk in any case. I'm not particularly concerned about wear. Frankly, I don't believe all the scare-mongers who like to keep repeating old out of date information that used to apply to flash memory a few years ago.

To my way of thinking, SSDs are made for speed, like a race horse. To buy a SSD and then install an operating system in a slow file system and not use the speed is like buying a racehorse and hobbling it so it won't hurt itself. 

This is only my opinion so take my ideas with a grain of salt. I realize I'm contradicting the advice of most experts.  
If you have time, try installing with various file systems and see which one you think performs better. I have, and I think you'll agree with me when you try them all out.
> Perhaps you could try one of the alternative filesystems, such as JFS or XFS.I agree with tinivole.
Sometimes you might find a particular fie system suits your needs and your particular flash memory controller best, so give JFS and XFS a try too, I have read that those are also very good file systems.
There is no 'best file system', they all have their uses, this link explains it well, [Linux File System Benchmarks]("http://fsbench.netnation.com/")

Regards, Herman :)

---

