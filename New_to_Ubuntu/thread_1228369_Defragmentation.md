---
title: "Defragmentation?"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by Nigalius on 2009-07-31
Hi, I am a complete noob on Mint 7 and Ubuntu. I have had great fun in starting to learn Linux in general but have not even scratched the surface at the moment. I am learning quite a lot by looking in the forums and reading previous threads. But I have a question of my own now... Is defragmentation neccesary in Linux, the same as it is in Windows. I can find no referance to it wherever I look.

Cheers

Nigel

---

### Post by Humanum on 2009-07-31
Defragmentation is a word that almost doesn't exist under Linux (Ubuntu) even though you can face it somehow.

But be sure it won't happen as it happen with windows, it will take a long time if not ages before you start experimenting such problems...

---

### Post by gettinoriginal on 2009-07-31
I would like to point out these threads for your perusal.  Welcome to linux.
[http://ubuntuforums.org/showthread.php?t=383100](http://ubuntuforums.org/showthread.php?t=383100)

---

### Post by saidinesh5 on 2009-07-31
defragmentation is not really necessary when it comes to the ext3/4 file system...
atleast thats what i ve read in some forum ...
so i guess thats 1 less thing for you to worry about :)

good luck with your journey on ubuntu :)

---

### Post by Sef on 2009-08-01
If you are using ext3 or ext4, it will automatically defrag about every 25 boots.

---

### Post by Shig on 2009-08-01
[http://en.wikipedia.org/wiki/Ext3#Defragmentation](http://en.wikipedia.org/wiki/Ext3#Defragmentation) - A breif overview

Ext2 and Ext3 do not do automatic de-fragmentation, and an on-line de-fragmentation tool does not exist for Ext3. This is basically because Ext2,3 and 4 are fragmentation resistant, and do not get as fragmented as NTFS or FAT file systems. That said, these file systems do get fragmented, and the best way to defragment them (5 years from now) is to backup your system, format the partitions, and restore the files onto the file system, which has the same effect as a defrag. This is not exactly user friendly however :D

XFS and Ext4 both have defragmentation tools that can be used to keep the filesystem contiguous. Ext4 is creeping it's way into Ubuntu, and can be selected as a file system at install-time on 9.04. That said, for now, stick with Ext3 as it's very stable, and it will be a loooong time before you notice fragmentation slowing your computer down.

---

### Post by CatKiller on 2009-08-01
> **Sef said:**
> If you are using ext3 or ext4, it will automatically defrag about every 25 boots.

No it won't. It will check the filesystem, but that's not the same thing.

---

### Post by Sef on 2009-08-01
To read up about defragging and why GNU/Linux does not need to be, read [this]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting").

---

### Post by infestor on 2009-08-01
what about reiserfs?

---

### Post by hyperAura on 2009-08-01
well defragmentation once every 5 years is much better than defragmenting my windows machine once a month.. question: how many people keep their OS for more than 5 years? For me the only OS i had for more than 5 years i think it was windows XP nothing else, as with Linux i upgrade almost every year..:)

---

### Post by Geoff918 on 2009-08-01
Linux file systems write differently than NTFS or FAT16 / FAT32 systems. Disk fragmentation occurs from modifications and deletions primarily, e.g. 0101010101MOREDATA and I delete a character which leaves 0_01010101MOREDATA on the disk and the _ is a now fragmented file. And if we add to it, e.g. 0_01010101MOREDATA__EVEN___ then the portion that is "EVENMOREDATA" is now fragmented and requires additional references to piece the file back together while accessing.

To understand how a Unix-like OS writes data you need to remember that it was designed for many concurrent connections and constant data updating / deleting / rewriting. Therefore, the disk may look more like the following: _____0101010101_____MOREDATA_____ so if we then add or delete from this setup it will show _____0_01010101_EVENMOREDATA____ so fragmentation is lessened.

It's not that a Unix-like OS file system will not be fragmented, it's just that it is much less of an issue than for an NTFS or FAT-type file system. I do not know of any tools to defragment a Linux drive (not that they don't exist elsewhere), but I have seen where if you actually experience performance degradation you could backup your data, format your drive and then copy the data back which would clear up the fragmentation.

Cheers,

:popcorn:

---

### Post by fates on 2009-08-01
Well the friend of mine explained Linux this way. Linux with partitions makes upgrading the operating system painless. As long as you have a partition mapped to /home for your user(s) files the *worst* you have to do is download the applications you use again. The application packages know all their dependancies so reinstalls and upgrading them is also painless.

And unlike Windows the applications just have to be recompiled to work in the next version. Windows doesn't make things this easy, the interface changes, networking layers change, and it goes on and on. Windows has broken compatibility with  95/98, again with XP, XP Pro x64, and yet again with Vista forcing you to upgrade all your applications and *hope* that any niche applications you use are still being developed and for you to pay for them again. Hell, I know people that worship the DosBox ground because they can now run DOS apps again.

I have only been using Ubuntu for a few months now, and I cringe every time work requires me to boot Windows
    Fates

---

