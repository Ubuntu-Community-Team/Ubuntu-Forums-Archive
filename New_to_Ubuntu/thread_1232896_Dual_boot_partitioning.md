---
title: "Dual boot partitioning"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by Majik_420 on 2009-08-06
Alright so I'm trying to get a dual boot setup because my windows is not legal and I had to screw around with some stoptimer crap that ended up not really working like it was supposed to. So I tried Ubuntu, and now I'm switching to Kubunutu, but when I had Ubuntu installed I couldn't get to any of the files on my windows side(mainly my music.)

I'm doing my best to read and search for info, but this linux stuff is still pretty confusing to me.

So right now, I burned Kubuntu 9.04 onto a cd as well as well as a SystemRescue Cd fo use GParted. I tried to install Kubuntu but I don't think I had enough space or a free partition for it. I was screwing with my partitions on windows earlier and Don't really know what I did but I went from having just C:(OS) and D:(RECOVERY) to also having M:(MEDIADIRECT) and V: Local Disk. 

I'm just not quite sure if I can delete the three besides C and just go from there with /home, /root, and /swap.

I was also looking at the setups on this page [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and thinking about the last dual boot setup that gets rid of fat32. 

Any help is appreciated. Thanks

---

### Post by Paqman on 2009-08-12
Gparted is actually on the Ubuntu LiveCD anyway. You can go ahead and delete any weird partitions you might have created (be seriously careful about this, obviously). Leave your recover partition intact unless you have install disks for Windows.

I wouldn't recommend using the ext2ifs Windows driver for accessing a Linux partition. Linux has better NTFS drivers than Windows has EXT drivers. So if you need a shared data partition just use NTFS. I wouldn't use FAT32 myself. It's a dinosaur, and has a some pretty serious bad points (no support for large files, terrible fragmentation, poor performance on large partitions, etc)

---

### Post by LarsW_Tierp on 2009-08-12
Have you looked at [this]("https://help.ubuntu.com/9.04/switching/index.html"). It might give you a few pointers to what may have gone wrong.

---

