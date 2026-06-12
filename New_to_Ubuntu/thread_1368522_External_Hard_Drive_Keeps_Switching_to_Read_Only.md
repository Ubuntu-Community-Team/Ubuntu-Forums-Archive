---
title: "External Hard Drive Keeps Switching to Read Only"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by completeidiot on 2009-12-30
I have a 1 TB Lacie External Hard Drive.
It's divided into 2 partitions
1 small Win/Fat 32 Partition
1 Large Mac Partition
Both partitions only contain mp3 and .jpg files. NO OPERATING SYSTEMS, ETC.
There have never been any problems whatsoever with the Fat32 partition.
I have now had two incidents where the Mac Partition switches to read only. There were no power outages or problems of any kind that I noticed. I was simply moving some files within the partition and it suddenly made the switch. 
The first time I solved the problem by simply plugging the drive into a mac and transfering some files off of it. There were no problems and the next time I plugged into Ubuntu I could read and write. I have no idea what is causing this. I am going to buy a new hard drive just to be safe, and probably never use a mac file system again. But it would be very nice to know how to simply switch it back again.

---

### Post by jbrown96 on 2009-12-30
It's very unlikely to be a hardware problem, but if you have important stuff on it, you can't be too safe.

I'm much more inclined to think that it is a HFS+ (Mac FS) problem. I haven't ever done much with HFS+, but it is structured very funky. And I don't think there is very good Linux support for it. 

I would recommend switching to Fat32 or if you have large files or want a more advanced FS NTFS. Linux and Mac have very good support for both.

---

### Post by completeidiot on 2010-01-06
i'm thinking about backing up the data and formatting the drive and switching to a different file system. 
i guess fat32 would be the best because it's well supported?

---

