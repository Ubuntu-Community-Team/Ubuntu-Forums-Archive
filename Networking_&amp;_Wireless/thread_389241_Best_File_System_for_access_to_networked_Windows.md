---
title: "Best File System for access to networked Windows?"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by hansoffate on 2007-03-20
Hi Guys,

         I am about to build a mythtv/file server computer.  I was wondering what my partitioning scheme should be.  I have been reading around and apparently windows can not handle shared XFS which is supposedly the best for a media center pc. 

    What file system should I use to have as a share for both networked Windows and Ubuntu computers to have Read/Write access?

   I plan on putting backed up documents, music, videos etc on that file system and I plan on accessing the file system a lot from both environments.

Thanks for the help,
Hans

---

### Post by newlinux on 2007-03-20
I would go with ext3 and use install fs-driver in windows. Although not the best and fastest filesystem for mythtv recordings, ext3 works fine these days. I use ext3 for my mythtv recordings and mythvideo storage, and access them on my XP box read/write through samba shares with fs-driver. I also use one of my mythbackends as a fileserver (ext3) I access with my XP, and Linux boxes.

---

### Post by hansoffate on 2007-03-20
Awesome.  Nice to see somone else has the same setup.  I have a quick question about partitioning.

How does this sound?
hda1 /    ReiserFS 10gb
hda2 SWAP          1gb
hda3 /mythtv  xfs    180gb TV Recordings
hdb1 /videos   ext3 200gb hd dedicated

Does that sound ok?

Thanks for the help
-Hans

---

### Post by newlinux on 2007-03-20
looks good, but it's hard to say without knowing more. How much RAM do you have? If you have 1GB this would be sufficient, but if you ever plan on increasing your RAM you might want a larger swap. The other partition sizes depend completely on your storage and viewing habits.

Any particular reason you want ReiserFS as you root filesystem? Not frowning on it, just curious of your reasons.

---

### Post by hansoffate on 2007-03-20
I have 2x512mb sticks in the computer.  SO, I think a 1gb swap is good.

The reason why the tv recordings are in XFS is because I won't be viewing them on my Windows computer, I would rather just go to the HTPC and view it there.  

The reason why I chose ReiserFS is because of this howto guide.  [http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv)

ReiserFS is very good at handling large amounts of small files. It's very good at indexing them, and it's a journaling file system by nature.

Should I use a different file system?

Thanks for the help
-Hans

---

### Post by newlinux on 2007-03-20
No, ReiserFS is good. See more and more people using it for their root partitions. Just curious is all. 

Not that you'd probably ever want to (and you probably already know this), but keep in mind you can't shrink an XFS filesystem. It would have to be destroyed (losing all data) and then recreated. You can grow it however, which would probably be more of interest to you in the future. So it's just important that pick the right sizes for your partitions because you won't be able to shrink your XFS partition to add to some other partition.

I just tend to stick with ext3 because it is tried and true, and delete times aren't that big a deal with me. I don't have any problems - and thus from a mythtv user standpoint it makes no difference in anything fo rme. I have about 500GB of storage in ext3 for HDTV and SDTV recordings. Ext3 gives me the added benefit of being able to easily access everything from my windows box. But XFS and ReiserFS do offer better performance.

---

### Post by hansoffate on 2007-03-20
How much space does a base install of ubuntu take up?  I think maybe a 10gb root parititon is too much.  How much should I make it?  5gb? 7gb?

Thanks
-Hans

---

### Post by newlinux on 2007-03-20
I think 10GB is good. By default you need less than 3GB, I believe. However you may want to add programs, and modify configuration files, etc. 10GB keeps it safe. I have 5 ubuntu installations and with all the software I want none of them are more than 6GB (most between 3 and 5). But I made them all 10GB just in case... You could probably get away with 7GB just fine.

---

