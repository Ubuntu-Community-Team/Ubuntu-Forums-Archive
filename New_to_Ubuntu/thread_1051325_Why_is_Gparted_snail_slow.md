---
title: "Why is Gparted snail slow?"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by yogo on 2009-01-26
I am resizing my hd and using the Gparted live cd . All I am doing is freeing up 16 gigabytes Part of it took 27 minutes, this after at least ten minutes prior. When this completed I am now stuck with 56 minutes remaining. In all it looks like it will take over two hours, much worse than installing an OS.

Why should it take so long? Is it because I am using the live cd? 

Thanks

---

### Post by Hospadar on 2009-01-26
It could be for several reasons, mainly that gparted will need to move a lot of files around:

First: if you are shrinking the drive from the front end, it will have to copy a whole lot of files, probably all 16 gig, which takes a long time, especially going from one part of the same drive to another, since the data has to go from Hdd->memory then the drive seeks to the new location, then memory -> hdd about a gazillion times.

Also even if you are shrinking the partition from the rear end, if your drive is sufficiently fragmented (yes even linux partitions do get fragmented over time) there may be all kinds of files even at the end of your drive, which then need to be copied, same problem as above.

In general too, resizing operations involve a large number of small changes, which involves a lot of seeking on the part of the drive, which is what really takes a lot of time.  it takes orders of magnitude more time to change a little data that's in 3 different parts of the disk than it would if that data where located sequentially on the disk.

Of course, there could just be some errors, in which case your best bet would probably be resize by hand from the command line.  but I think your resize time is really pretty resonable.
last time I did serious drive reconfiguring (copy a partition to another drive, resize some stuff, blah blah blah) it took almost 8 hours for the whole thing.

---

### Post by Vantrax on 2009-01-26
Check to make sure Gparted is using your swap file off the live CD (unless that is something your messing with) Else it has to do every operation through ram which will be slower than just moving it to disk on the swap.

It does sound alot slower than normal for some reason.

---

### Post by yogo on 2009-01-26
> **Hospadar said:**
> It could be for several reasons, mainly that gparted will need to move a lot of files around:

First: if you are shrinking the drive from the front end, it will have to copy a whole lot of files, probably all 16 gig, which takes a long time, especially going from one part of the same drive to another, since the data has to go from Hdd->memory then the drive seeks to the new location, then memory -> hdd about a gazillion times.

Also even if you are shrinking the partition from the rear end, if your drive is sufficiently fragmented (yes even linux partitions do get fragmented over time) there may be all kinds of files even at the end of your drive, which then need to be copied, same problem as above.

In general too, resizing operations involve a large number of small changes, which involves a lot of seeking on the part of the drive, which is what really takes a lot of time.  it takes orders of magnitude more time to change a little data that's in 3 different parts of the disk than it would if that data where located sequentially on the disk.

Of course, there could just be some errors, in which case your best bet would probably be resize by hand from the command line.  but I think your resize time is really pretty resonable.
last time I did serious drive reconfiguring (copy a partition to another drive, resize some stuff, blah blah blah) it took almost 8 hours for the whole thing.

Thanks that explains it, I went to Wal*Mart and came back and it is done. I just did not think it would take quite so long but thanks a lot for the explanation..
Marked as solved.

---

### Post by yogo on 2009-01-26
> **Vantrax said:**
> Check to make sure Gparted is using your swap file off the live CD (unless that is something your messing with) Else it has to do every operation through ram which will be slower than just moving it to disk on the swap.

It does sound alot slower than normal for some reason.


I think it may have used ram. 

BTW, the mark as solved is removed from my thread tools?

---

### Post by -kg- on 2009-01-26
Hospadar is absolutely right.  The time it takes to resize a partition is definitely affected by the amount of data in the partition, and the state of that data (as in it's level of fragmentation). I would not call 2 hours (or even 4 or more) an unreasonable amount of time for a resize operation of 16 GB.

> (yes even linux partitions do get fragmented over time)

Not only that, but the way data is stored on an ext2/3 file system is such that, given even a moderate amount of files, the data is spread over a large part of the partition instead of in consecutive "clusters."  This is what makes fragmentation of a Linux partition less of an issue (although it doesn't eliminate it).

The only time I would question that amount of time is if you had just created the partition and then resized it with no files in it.  As it is, if it only takes you a couple of hours, you're getting off easy.  I've had to leave a partition operation running overnight and have them still running when I get up.

---

### Post by -kg- on 2009-01-26
Well, a couple of posts later I finally posted my post :p

> BTW, the mark as solved is removed from my thread tools?

Yes.  Earlier the forums had some issues with the server and the forums were down for a couple of days.  Until the stability issues are resolved they have disabled the "Solved" function, and the "Thanks" button, as well.

---

### Post by mrbiggbrain on 2009-01-26
AGreed, my last resize took ~10 hours, resizeing NTFS, by 20GB of 160, core2 duo 1.8ghz, 2GB of memeory, and it took a LONG time

---

### Post by yogo on 2009-01-26
Good to know on all of the replies. I only had about 20gigs that needed to be moved so I was surprised. Now I know for the future, I am not the most patient person.
 
Well with the 16 gigs I freed up I installed Windows 7. I must say that I am quite impressed so far. I did not time install but I imagine it was about 35 minutes.
 
It looks like Windows finally got some things right, much better than any previous install of Windows but I only have a little time using it so far.

---

### Post by kansasnoob on 2009-01-26
Resizing partitions is by nature very, very slow!

Gparted first checks for errors, then transfers the data to the newly sized partition, then checks for errors again!

If you have the capability you can copy an existing partition using Partimage (which saves only the data) and then transfer that back to a newly created partition.

Neither is fast!

---

