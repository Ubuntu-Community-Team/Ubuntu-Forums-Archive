---
title: "file system to use for a shared windows/linux partition"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by hekastos on 2010-11-13
I know this question was asked before, but the answers are 3 years old and so I am unsure, if they are still solid, could you give me a hint?

Additional how about ext4 and I really have probs with fat32 because of files > 4gb...

The orgiginal question:

I'm going to be  installing a new system soon, and I want it to be dual boot Windows and  Ubuntu.  In addition to the partitions for Windows and Linux, I want to  have a partition that they both can access.  Which would be the best to  use?  I will probably spend most of my time on Ubuntu, and only boot  into Windows for gaming or anything else that doesn't work on Linux.

*ext 2/3, with windows ext2 driver
*ntfs, with Linux ntfs read/write driver
*fat32, native on both, but requires defragmentation


The original thread:
[http://ubuntuforums.org/showthread.php?t=375459](http://ubuntuforums.org/showthread.php?t=375459)

Thx a lot for any help!

---

### Post by marshmallow1304 on 2010-11-13
NTFS.  I believe the NTFS read/write driver is in most distros by default now and it's probably better than the ext2/3 driver for Windows.  Besides, ext4 is here and btrfs is around the corner, so you don't want to be limited when it comes to your Linux filesystem.

---

### Post by Hippytaff on 2010-11-13
NTFS is the best format for a shared partition/drive (as the above post says). Windows doesn;t like may filesystems where as Linux is extremely versitile :-)

---

### Post by CBR_Rob on 2010-11-13
I had to replace a hard drive and am looking to do this same thing on my system, also got rid of the extra system that did my Windows needs. I've finally got XP back running would it be better to install 10.4 and manually assign the partition size I want then use a partition manger in XP to shrink the XP partition and create the new "data" partition? Also can I point the home folder in 10.4 to the "data" partition? I know with XP I can reassign where the "My Documents" folder is looking.

---

