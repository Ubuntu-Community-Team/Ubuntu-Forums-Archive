---
title: "So is it true that I will never have to defrag my drive in Ubuntu?"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by papuccino1 on 2010-01-18
I've been told that using Linux means that your hard drive will never have the need to drefrag.

Is this statement true, or just propaganda? :popcorn:

---

### Post by pythonscript on 2010-01-18
It is true that the ext3, ext4 file systems fragment *far* less than the NTFS file system. Because of this, very few defragmentation tools exist for Linux, as far as I know.

---

### Post by Marlonsm on 2010-01-18
It's mostly true.
Ubuntu uses the ext4 file system, that as long as the HD has about 20% of its capacity free, there is no need to defrag.

---

### Post by Cabs21 on 2010-01-18
This is true.  Ubuntu organizes the data on your disc differently then windows does.  The way I understand it is with an example.  Imagine your HDD is a dart board and the data is the thumb tacks.  Windows will get a handful of tacks (data) and as fast as it can place them all over the board anywhere that is available and then connect all the tacks with a string so you know they all go together.  De fragmenting will take the tacks and line them up next to each other.  Linux does not place the tacks randomly and so there is no need to de fragment the HDD since it is nice and neat already.  This is a simple example has not technical reasoning behind it just observations.

---

### Post by kseise on 2010-01-18
No, it is true.  Someone smarter can probably explain it better, but the linux filesystems are handled differently than the Windows systems.  You do not have to defrag a linux machine.  One caveat though, if you dual boot, or share a drive with a windows machine and that drive is formatted for Windows, you might have to defrag, but it's not Linux's fault.

---

### Post by DestructionsRightHand on 2010-01-18
For what very little it does get fragmented, as stated above as long as it has 20% free it will degrag itself when the computer is idle.  Same can be said with windows, only windows frags so much that its a full time job to defrag during idle times

---

### Post by Hogosha on 2010-01-18
The way NTFS works is that it will fill blocks with data. If data is deleted that block is free and it will fill it with data again, even if all the data will not fit in that block. It will just fill it and move on to the next free block. This is what fragmenting is. Pieces of data are all over these blocks in different places. NTFS has a map saying where the data is and what all belongs to each other. When you defrag it puts all the data in order.

Unfortunately i am not sure how EXT3 or EXT4 works. I would love an explanation.

---

### Post by papuccino1 on 2010-01-18
> **kseise said:**
> No, it is true.  Someone smarter can probably explain it better, but the linux filesystems are handled differently than the Windows systems.  You do not have to defrag a linux machine.  One caveat though, if you dual boot, or share a drive with a windows machine and that drive is formatted for Windows, you might have to defrag, but it's not Linux's fault.

Well, before installing Ubuntu on my laptop, I had Windows 7.

Two partitions were created, Drive C: and Drive D:.

When I installed Ubuntu I deleted Drive C: but left D: alone because it was just information (pictures, movies, songs, etc.).

Does this mean that I have to defrag my drive? Why would it affect Ubuntu when it's just information and has nothing to do with the OS (besides the file system type).

---

### Post by Marlonsm on 2010-01-18
I've found this explanation, that seems quite good: [http://www.whylinuxisbetter.net/items/defragment/index.php?lang=](http://www.whylinuxisbetter.net/items/defragment/index.php?lang=)

---

### Post by J V on 2010-01-18
> **papuccino1 said:**
> Does this mean that I have to defrag my drive? Why would it affect Ubuntu when it's just information and has nothing to do with the OS (besides the file system type).No, the guy you quoted is wrong, only NTFS gets fragmented (so the windows partition will, the linux won't) and you can't install ubuntu on NTFS.

Also, look up suggested partitioning schemes, theres lots of tricks with partitions that can for one thing make upgrading fresh easy (just install on one part, and all your stuff is still there)

---

### Post by bodhi.zazen on 2010-01-18
Every file system fragments, no question about that.

The issue is, is the fragmentation severe enough to affect performance. When fragmentation affects performance, defragmentation will help.

Fragmentation on a Linux native partition, enough to affect performance, is very very rare.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

You can see your fragmentation with fsck

```
fsck -n
```

---

### Post by audiomick on 2010-01-18
@ bodhi.zazen
thanks for that link. I forgot to bookmark it last time I read it...;)

---

