---
title: "Mounting drives"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by impatientboi on 2009-10-21
Hi all. 

Have a dual boot xp and ubuntu machine set up.
Noticed when installed ubuntu the partitions were not set correctly
i have the xp partition. another 'media' drive, and then the ubuntu drive.
I am using ubuntu netbook remix. the 'extra' media drive is windows format
so is unecessary when booting into ubuntu
I've tried the partition manager, but it appears the only way to correct this is to do a complete reformat, not something i am prepared to do at the moment


can i "mount" these two drives so they appear as one under the file manager interface?
if so, can anybody help me out with a command?

cheers

---

### Post by Paqman on 2009-10-21
> **impatientboi said:**
> 
I've tried the partition manager, but it appears the only way to correct this is to do a complete reformat, not something i am prepared to do at the moment


The only thing that will stop you being able to modify or delete a partition is if it (or an extended partition that it is contained within) is mounted.

If it's not within an extended partition you should just be able to unmount it and delete, then grow the adjacent partition(s).

If it is within an extended partition then you'll need to boot up into a LiveCD or LiveUSB, unmount any partitions that are mounted (including swap) and make your changes.

---

### Post by j.daniel on 2009-10-21
**Hi,**

  Just a small thought: Some computers from vendors like Acer for instance usually have a partition which is invisible from windows (they use a custom file system) where they have the installation "discs" - it is into this file system you boot when you want to rescue or re-install the operating system.

  Is it this one you are seeing?

Cheers!
/ Daniel

---

### Post by impatientboi on 2009-10-21
No my pc is a asus 1000h 160 g hard disk.. out of the box configured with two disk drives (partitions?) about 80 each so i install linux in a 30 g partition and left the50 is xp partition as it was and the remaining 50 is another partition i want to add the 50 to the xp partition 80.  it sounds like it could be a factory settings thing, it just might not be possible to edit the size of the xp installation drive (partition)

---

