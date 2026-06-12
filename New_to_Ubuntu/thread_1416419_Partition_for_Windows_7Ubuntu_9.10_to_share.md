---
title: "Partition for Windows 7/Ubuntu 9.10 to share"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by flyface on 2010-02-26
I would like to create a partition that both Windows and Ubuntu can use so I can pass music/videos/anything from one to the other.  From the searching around that I did, I know the partition must be FAT32 (VFAT), but that's about all I took away from that.  I would like to do this in the least headachey way possible.  Any suggestions?

---

### Post by Elfy on 2010-02-26
I'd suggest you use NTFS instead.

You can use any partition editor to do the work - there's one on the livecd's in the System > Admin menu. I use a standalone one though - partedmagic.

There is then a GUI tool you can use to set up access to the partition in ubuntu - pysdm 

If though you actually have a wubi install instead of a normal one the windows partitions are in /hosts and already available.

---

### Post by Peter09 on 2010-02-26
Just a thought - you should be able to see your Windows 7 partition from Ubuntu. Are you trying to do something else?
 
Try the terminal command 
```
df -h
```
to show what filesystems you have mounted.

---

### Post by spectralblue on 2010-02-26
> **flyface said:**
> I would like to create a partition that both Windows and Ubuntu can use so I can pass music/videos/anything from one to the other.  From the searching around that I did, I know the partition must be FAT32 (VFAT), but that's about all I took away from that.  I would like to do this in the least headachey way possible.  Any suggestions?

Yes, you should be able to view your windows partition in ubuntu. To enable write access make sure you have ntfsprogs or ntfs-config installed. It does NOT have to be FAT32.

---

### Post by Darvenkry on 2010-02-26
There is a program that u can install on Windows that can view Linux partitions. It's called ext2fsd [www.ext2fsd.com](www.ext2fsd.com)
So to pass stuff between windows 7 and Ubuntu, just install ext2fsd on windows and Ubuntu 9.10 should already be able to write to Windows partition. To note, ext2fsd only works with ext2/ext3. So if you installed 9.10 with ext4 then this wont work. Secondly i would suggest put everytrhing onto the linux partition. I believe that linux is more secure and reliable than shitty windows lol. Ie. viruses and corruption will most likely destroy ur windows partition before ur linux one.

---

