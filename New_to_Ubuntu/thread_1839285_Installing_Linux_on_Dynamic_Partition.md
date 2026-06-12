---
title: "Installing Linux on Dynamic Partition"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by evanbas on 2011-09-05
Hello, I am a newcomer here.. So my apologize if I made any fault (and my bad English too)

Right now, My laptop uses Dynamic Partition in my hard disk

First, they used all the 320GB space for Windows so I can't make a new Linux partition to use

Finally somehow I've succeeded to make an empty 32GB partition


But when I boot my computer and install Ubuntu, the partition doesn't appear..
Instead of it, it showed a partition sized 260GB and second partition sized 60GB

How should I do to my Windows partition? Note that for some reason I prefer using a classic install, not using wubi..

Thank You

---

### Post by snip3r8 on 2011-09-05
I would guess that the 60gb partition is supposed to be the 32 gb one. check the filesystem types when you install.

---

### Post by Johnb0y on 2011-09-05
> **snip3r8 said:**
> I would guess that the 60gb partition is supposed to be the 32 gb one. check the filesystem types when you install.

+1 but defo check the types 1st!

---

### Post by evanbas on 2011-09-05
Okay, I'll Check the type later... Thanks for your suggestion :)

---

### Post by oldfred on 2011-09-05
Do you really want or need dynamic partitions? It is somewhat like LVM is in Linux. Not really supported in Linux and even all Microsoft tools do not work with it.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by Mark Phelps on 2011-09-05
You running Win7? Did your PC come with Win7 preinstalled?

If the answers are yes, then BEFORE you mess around any more with partitions, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in handy later, should you need to repair the Win7 boot loader or restore the original Win7 MBR.

---

