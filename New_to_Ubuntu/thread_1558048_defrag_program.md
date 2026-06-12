---
title: "defrag program"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Total AI on 2010-08-21
I have a question,is there a defrag program which will defrag the H/D? I have been ask this several times by pplz who I have given the Ubuntu system to or have set it up for them. I tell them,the computer janitor is similar to the disk cleanup in windows but I don't know of a defrag program.

---

### Post by HPD2 on 2010-08-21
> **Total AI said:**
> I have a question,is there a defrag program which will defrag the H/D? I have been ask this several times by pplz who I have given the Ubuntu system to or have set it up for them. I tell them,the computer janitor is similar to the disk cleanup in windows but I don't know of a defrag program.

Arguably a defrag is some thing that doesn't need to be done in ubuntu. There are tools to defrag ext3, so i have heard, but i have never used any of them.

---

### Post by Perfect Storm on 2010-08-21
This may explain why it's not needed: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)


You might want to check bleachbit instead of janitor. It's much better IMHO.

---

### Post by Rubi1200 on 2010-08-21
> **Total AI said:**
> I have a question,is there a defrag program which will defrag the H/D? I have been ask this several times by pplz who I have given the Ubuntu system to or have set it up for them. I tell them,the computer janitor is similar to the disk cleanup in windows but I don't know of a defrag program.
The basic answer is no, you do not need a defragmentation program for Linux. This has to do with the way the file-systems handle read/write.

As far as Computer Janitor is concerned; be careful with it as it can delete things you definitely do not want deleted.

---

### Post by Total AI on 2010-08-21
Yes,I know this and I always tell my client to be very careful with the computer janitor

---

### Post by elliotn on 2010-08-21
Never defraged in linux before

---

### Post by ronnielsen1 on 2010-08-21
> As far as Computer Janitor is concerned; be careful with it as it can delete things you definitely do not want deleted. 	

Yes, I do not like this program. Dangerous. as an inexperienced user could easily damage their system. There's better out there. Get rid of this one

---

### Post by Norm24 on 2010-08-21
I'm curious as to why Computer Janitor is even included as part of an Ubuntu distro.It can be a very damaging utility especially for the novice.

---

### Post by phillw on 2010-08-21
> **Artificial Intelligence said:**
> This may explain why it's not needed: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)



Ext4 does fragment, it is just more resilient to it.>  Online defragmentation
(This feature is being developed and will be included in future releases). While delayed allocation, extents and multiblock allocation help to reduce the fragmentation, with usage filesystems can still fragment. For example: You write three files in a directory and continually on the disk. Some day you need to update the file of the middle, but the updated file has grown a bit, so there's not enough room for it. You have no option but fragment the excess of data to another place of the disk, which will cause a seek, or allocate the updated file continually in another place, far from the other two files, resulting in seeks if an application needs to read all the files on a directory (say, a file manager doing thumbnails on a directory full of images). Besides, the filesystem can only care about certain types of fragmentation, it can't know, for example, that it must keep all the boot-related files contiguous, because it doesn't know which files are boot-related. To solve this issue, Ext4 will support online fragmentation, and there's a e4defrag tool which can defragment individual files or the whole filesystem. [source](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#Online_defragmentation)

But, for the vast majority of users, the self-defragging routines it uses are quite sufficient.

(Ubuntu uses [ureadahead](http://ubuntuforums.org/showthread.php?t=1434502) to sort out the pre-loading of the boot files, and if a dev tells us files fragment - I'm with him).

Regards,

Phill.

---

### Post by oldsoundguy on 2010-08-21
This machine started with 6.10 on it .. and has been UPGRADED (not clean install) first to 8.04 and then to 10.04  and NEVER has had to be de-fragged!  And really, because of the size of my drive(s), would hate to have to try.  I have a Windows XP box that takes over 8 hours to de-frag!!!

---

### Post by phillw on 2010-08-21
> **oldsoundguy said:**
> This machine started with 6.10 on it .. and has been UPGRADED (not clean install) first to 8.04 and then to 10.04  and NEVER has had to be de-fragged!  And really, because of the size of my drive(s), would hate to have to try.  I have a Windows XP box that takes over 8 hours to de-frag!!!

I'm not starting a flame war :lolflag:

If you're still on the 6.10 filesystem (ext2, I think) then simply moving upto ext4 would give you a speed increase. The improvements from ext2 --> ext3 --> ext4 whilst not massive, bring benefits of speed. Oh, and defragging a linux system is a lot faster than a windows system as by it's nature the linux filesystem tries to avoid it.

For the record, ext4 is a 'stop-gap' filesystem, once [BTRFS](http://en.wikipedia.org/wiki/Btrfs) becomes stable linux will be most likely be moving to that. 

Regards,

Phill.

---

