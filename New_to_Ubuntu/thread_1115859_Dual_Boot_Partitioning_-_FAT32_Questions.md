---
title: "Dual Boot Partitioning - FAT32 Questions"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by sschnee on 2009-04-04
I would like to have a dual boot Windows/Ubuntu desktop.  I would use Ubuntu for most everyday computing, but would use Windows for games (Starcraft 2 should be out in the next year, I hope) and some commercial software like iTunes, Palm Desktop, and Rosetta Stone, that I don't believe have good alternatives in Linux yet.

Anyway, I would partition my hard drive with a NTFS partition for Windows, a ext3 partition for Ubuntu, a Linux Swap partition, and a FAT32 partition for sharing data between the two operating systems.  

My question is (and I suspect it is a dumb question) will both operating systems automatically "see" the FAT32 partition?  Will it be D: in Windows, and will it be mounted automatically in Ubuntu?

Also, what can I put on a FAT32 partition?  Just data files like documents, music, and video, or can program files be installed to a FAT32 partition?

Thanks.

---

### Post by loneowais on 2009-04-04
Ubuntu will automatically see both Fat32 & NTFS partitions...You don't have to manually configure anything.

And hey, who said we don't have good alternatives to those commercial apps?

Try Amarok & Songbird(MultiPlatform)...They'll kick iTunes out of your mind.

---

### Post by loneowais on 2009-04-04
You can run Rosseta Stone or Rock with WINE..
[http://ubuntuforums.org/archive/index.php/t-877975.html](http://ubuntuforums.org/archive/index.php/t-877975.html)
[http://ubuntuforums.org/showthread.php?t=607470](http://ubuntuforums.org/showthread.php?t=607470)


Ubuntu has a nice Sync tool for Palm Devices shipped by default.

Best of luck

---

### Post by jmszr on 2009-04-04
sschnee,

 You do realize that FAT32 has a 4GB file size limit? Your documents and music files would be unlikely to be that large but video files (movies) can exceed that. You might want to go with NTFS instead.

---

### Post by sschnee on 2009-04-04
Thanks for the replies loneowais.

I have tried Amarok, and was not happy with it, as it didn't handle my podcasts as well as iTunes does.  Have I not played with it enough, or does it do a good job with music files but not as good for podcasts?

I haven't checked out Songbird; I'll do that.  Thanks for the tip.

I also haven't tried WINE at all.  I'll see how hard it is to set up Rosetta Stone.

Is there a reasonable expectation Starcraft 2 will run well under WINE?  I see WoW and Starcraft 1 do, but I don't know how long it takes between when a game is released and when people figure out how to get it to run well under WINE.

Finally, what about how Windows "sees" a FAT32 partition?  Will it be D: automatically or will something else happen?  And what data can each operating system store on a FAT32 partition?

---

### Post by sschnee on 2009-04-04
> **jmszr said:**
> sschnee,

 You do realize that FAT32 has a 4GB file size limit? Your documents and music files would be unlikely to be that large but video files (movies) can exceed that. You might want to go with NTFS instead.

No, I didn't realize that.  Is there any advantage to using FAT32 for a shared partition then, or should I just have 1 NTFS partition for Windows and a 2nd one for shared data?

Thanks again.

---

### Post by James_Lochhead on 2009-04-04
> **sschnee said:**
> Thanks for the replies loneowais.

I have tried Amarok, and was not happy with it, as it didn't handle my podcasts as well as iTunes does.  Have I not played with it enough, or does it do a good job with music files but not as good for podcasts?

I haven't checked out Songbird; I'll do that.  Thanks for the tip.

I also haven't tried WINE at all.  I'll see how hard it is to set up Rosetta Stone.

Is there a reasonable expectation Starcraft 2 will run well under WINE?  I see WoW and Starcraft 1 do, but I don't know how long it takes between when a game is released and when people figure out how to get it to run well under WINE.

Finally, what about how Windows "sees" a FAT32 partition?  Will it be D: automatically or will something else happen?  And what data can each operating system store on a FAT32 partition?

Try Banshee 1.4 as well for the music. It does video libraries as well.

---

### Post by jmszr on 2009-04-04
sschne,

    FAT32 has just been used longer and it wasn't until relatively recently that Ubuntu had the read/write driver for NTFS. In Ubuntu you will need to enable the ntfs-3g read/write driver in the Synaptic Package Manager (System > Administration > Synaptic Package Manager > Search: ntfs-3g > click on box > Apply. This obviously allows Ubuntu to read/write from/to the NTFS partition. 

Hope that helps.

Edit: Please read this also: [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

### Post by sschnee on 2009-04-05
Absolutely that helps.  Thanks.

---

