---
title: "ext3 vs ntfs"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-12-14
hi everyone.i am presently using ubuntu hardy on my pc,and i have two ntfs parttitions and three reiserfs partitions(including a root partition).but i now want to revert back to ext3.now,i have a 31 GB ntfs partition that houses windows which needs to remain untouched.i plan to back up all my data,delete all drives using Gparted(except the above said windows partition) and then carve out an ext3 root partition(20 GB)out of the free space.and,the remaining free space has to be converted into another partition about 110 GB in length,which i shall use for storage purposes.now,i am unable to decide whether i should choose ext3 or ntfs for this partition.i don't mind the partition being unreadable for windows.but,i want speed and performance.but i am a bit skeptical about ext3 because i read on this forum that it is relatively slower.so will i have a faster system with ntfs?

---

### Post by Dedoimedo on 2008-12-14
NTFS is a closed, proprietary format. So any Linux support for it will always be a best-guess, even if it's a 100% accurate guess. Therefore, I think you should go with ext3. Unless you're really milking the drive every single second, you won't feel any drastic performance issues anyhow. Storage probably means seldom access rather than real-time processing...

However, if you use NTFS, this also means your Windows can use it...

Dedoimedo

---

### Post by theozzlives on 2008-12-14
> **Dedoimedo said:**
> NTFS is a closed, proprietary format. So any Linux support for it will always be a best-guess, even if it's a 100% accurate guess. Therefore, I think you should go with ext3. Unless you're really milking the drive every single second, you won't feel any drastic performance issues anyhow. Storage probably means seldom access rather than real-time processing...

However, if you use NTFS, this also means your Windows can use it...

Dedoimedo

Ext2Fsd will allow Windows to mount and access your ext3 partitions (even assign drive letters)

---

### Post by logos34 on 2008-12-14
> **stonecoldjha said:**
> .i don't mind the partition being unreadable for windows.but,i want speed and performance.but i am a bit skeptical about ext3 because i read on this forum that it is relatively slower.so will i have a faster system with ntfs?

then you want ext3.  Even if ntfs were slightly faster, fragmentation and security issues are enough to tip the advantage back to ext3. And you can even access/read/write ext3 from the windows side with the fs-driver as suggested above, should you ever need to.

reiserfs is better/faster with lots of small files, and there are other fs that are better with larger files or booting (xfs, jfs), etc, but ext3 is a close second.  reliable and plenty quick for everyday desktop usage.

---

### Post by Dedoimedo on 2008-12-14
> **theozzlives said:**
> Ext2Fsd will allow Windows to mount and access your ext3 partitions (even assign drive letters)

The problem is, I have seen the ext2 drivers conflicting with too many windows (security) applications, which quite a few windows users run. BSOD becomes a motd.
Dedoimedo

---

### Post by bryanl on 2008-12-14
> but i am a bit skeptical about ext3 because i read on this forum that it is relatively slower.so will i have a faster system with ntfs?
The difference isn't enough to worry about, IMHO.

The issue is the same as trying to figure out a file system for an external drive.

If you go ntfs, you will have no hassle accessing the drive with either Linux or Windows without having to install any additional software. FAT or FAT32 used to be the choice here but, I think, we have finally got past the Win98 and DOS era so can use some of the features and capabilities of a more modern fs.

Of course, if you have to have an extra couple of percent in speed or have some unique requirements or use the drive almost exclusively with one particular OS, then those concerns will flavor your choice. But for a generic storage drive needing to be available across several booted systems, then reducing hassle has its benefits.

Of course, you should always have good backup no matter what decision you make and be prepared for both software and hardware fault. 

But do keep things in perspective.

---

### Post by scorp123 on 2008-12-14
> **bryanl said:**
> The difference isn't enough to worry about But it is. NTFS support in Linux is accomplished with a few extra programs (e.g. "ntfs-3g") that run in "user space", ie. outside of the OS kernel. Ext3 is native to Linux and its driver is part of the kernel; Ext3 like all native Linux filesystems therefore run in the context of the way way faster "kernel space".

Current NTFS support in Linux is OK for casually reading or writing a file from there ... but you definitely should not use it for your OS installation.

---

### Post by scorp123 on 2008-12-14
> **stonecoldjha said:**
> i am a bit skeptical about ext3 because i read on this forum that it is relatively slower.  It all depends.

First of all: proper "UNIX-style" partitioning can help a great deal to speed things up, e.g. separate the filesystems that are mostly getting written to from the filesystems that mostly are only read from. Please read here:
[http://ubuntuforums.org/showpost.php?p=4251551&postcount=3](http://ubuntuforums.org/showpost.php?p=4251551&postcount=3)
[http://ubuntuforums.org/showpost.php?p=4897193&postcount=19](http://ubuntuforums.org/showpost.php?p=4897193&postcount=19)

This stuff is a bit "oldschool", e.g. oldtimers like myself insist on doing this ... but you will hear a lot of people claim "...with modern harddisks and modern filesystems this is not needed anymore.... "

In my personal opinion and based on my experience it helps a lot to keep performance up and fragmentation to an absolute minimum. Other people who put all on one single "/" partition claim they can't see a difference .... I tried that once and I easily saw a difference, but then again I make heavy use of my systems ... so your mileage may vary.

But my claim stands as above: Proper partitioning helps to keep the performance high. So that's something you might want to consider.

Then as a second thing: What stuff do you have on your harddisks? Rule of thumb: [LIST]
[*]ReiserFS is good for tons of small files, but sucks at handling very large files
[*]Ext2 has no journal whatsoever, but it is the fastest of them all. Period.
[*]Ext3 is a bit slower than Ext2 but other than that a good overall performer. It's not superb but neither does it suck badly.
[*]JFS is originally by IBM and it's the filesystem their proprietary "AIX" Unix uses. It's similar to XFS below ...
[*]XFS is originally by Silicon Graphics and is the filesystem their proprietary "IRIX" Unix-clone on their graphics super computers used. It can slow down a lot when it has to handle too many small files. But it really shines in awesome ways when it has to handle very large files.
[/LIST]

And who said that all filesystems have to be the same? I have colleagues who mix filesystems ...
[LIST]
[*]e.g. /boot is Ext2 ....
[*]/ is Ext3
[*]/var is ReiserFS
[*]/home is XFS
[*]... and so on ...
[/LIST]

If you want safety, stability and an overall acceptable performance: Stay with Ext3.

If you need speed and speed is all that counts: Use Ext2. But there is no journal and a sudden crash might destroy data.

If you have tons of small files on a partition (e.g. a mail or news server where short messages come in and go out all the time ....) then use ReiserFS.

If you have tons of very large files (700 MB per file and beyond ...) on a partition use XFS or JFS. 

> **stonecoldjha said:**
>  so will i have a faster system with ntfs? NTFS is not native to Linux. It's a closed source filesystem by Microsoft, written for Microsoft operating systems of the "Windows NT" family (NT, 2000, XP, Vista ...).

---

### Post by Kellemora on 2008-12-14
Hi StoneCold

I'm a newcomer to Ubuntu, but felt confident enough in it to convert 90% of my office over to Ubuntu (that's 6 of 8 machines are running Ubuntu now).  Still need a couple of XP machines for hardware not yet supported in any flavor of Linux.

The reason I'm chiming in as a noob is only to explain something, the way it was explained to me, and to say why EXT3 is better for the type jobs we do here.  Or simply stated, NTFS keeps getting slower and slower and slower while EXT3 never slows down.  NTFS can be defragmented and pick up speed again, but will still slow right back down again fairly quickly.

This may not be an accurate representation of how the two files systems work in real life, but it sure made a lot of sense to me when explained this way.

The NTFS file system is like a long continuous string of pearls.
When you save a file it's added to the string, EG AAAAAAAAA.
When you add the second file it gets added, EG BBBBBBBB, right behind the first file, so it looks like this. AAAAAAABBBBBBBB on the hard drive.  So far so good!  But when you EDIT file A and save your changes, the hard drive now looks like this AAAAAAAABBBBBBBBAAAA.
You come along and add file C and it goes at the end of the string.  Edit file B and your hard drive now looks like this.
AAAAAAAABBBBBBBBAAAACCCCCCCCBBBB.
To READ the file A or B it now has to pick up the parts of it from two places on the disk.  Each time you EDIT a file, it gets stuck on the end of the string.
It takes a Defrag to line them all back up again in their proper order.

OK, now lets compare this to the EXT3 files system.
Instead of a string, you have a wall filled with pigeonholes, like the mail sort cases at the post office.  The pigeonholes closest to the middle of the room are the fastest and easiest to get to, the ones near the side walls take a little longer to get to.
With that in mind, you save file A, the entire file is stuck into a pigeonhole.  File B is stuck into another pigeonhole, same with file C.  Each file has it's own pigeonhole, until the disk gets overly packed.
Now, you Edit file A, the edited file gets stuck back into the same pigeonhole it came out of.
A long time goes by before you Edited file B.  So when it gets put back, it's moved to a pigeonhole near the wall.
Files you access most often are moved to the middle!
What happens when a file gets too big for a pigeonhole, then it's split and two pigeonholes are used, right next to each other if there is room.  If not, they will be separated until two pigeonholes next to each other become available.

We do a LOT of graphics work also!
Once an image is COMPLETED and will never be changed again, they are stored on a hard drive formatted in EXT2.  I've found that retrieval of these humongous image files is much quicker on EXT2 than on EXT3 filesystems.  And since they don't get changed anymore, just stored, the EXT2 filesystem seems to work best for Archives and File Storage.  Just make sure everything is backed up though.  EXT2 does not appear to have a checksum for a bad byte as EXT3 does.  In an image file, this can be disastrous!

As far as reading files from a Windows Machine, so far it has not mattered one iota what type file system is used on the drive, if the file is accessed through the LAN that is.

I'm in the process of building a file server and one of the drives is going to remain as NTFS for files that will only be used and accessed by the Windows Machines.  But all of our Data and working image files are on EXT3.

My rendition of how the drives work, as I said, may be way off from reality, but they give the appearance of functioning this way to me, and to the person who told me this analogy too!

TTUL
Gary

---

### Post by scorp123 on 2008-12-14
> **Kellemora said:**
>  This may not be an accurate representation of how the two files systems work in real life, but it sure made a lot of sense to me when explained this way. [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Kellemora on 2008-12-14
Thanks Scorp

Based on that article, it looks like the way I described it was pretty dead on then!

NTFS lines the files up like a row of beads on a string and EXT puts the file anywhere there is an open space and keeps them scattered apart, like pigeonholes at the post office sorting counter.

Cool!  No wonder EXT stays FAST and NTFS bogs down so quickly!

TTUL
Gary

---

### Post by scorp123 on 2008-12-15
> **Kellemora said:**
> EXT puts the file anywhere there is an open space and keeps them scattered apart All Linux filesystems have such strategies, not just Ext3 ;)

---

### Post by hyper_ch on 2008-12-15
I normally refer to this here:

[http://tldp.org/HOWTO/Partition/appendix.html](http://tldp.org/HOWTO/Partition/appendix.html)

> None of these habits should be carried over to Linux and ext2. Linux native file systems do not need defragmentation under normal use and this includes any condition with at least 5% of free space on a disk. There is a defragmentation tool for ext2 called defrag, but users are cautioned against casual use. A power outage during such an operation can trash your file system. Since you need to back up your data anyway, simply writing back from your copy will do the job. 

---

