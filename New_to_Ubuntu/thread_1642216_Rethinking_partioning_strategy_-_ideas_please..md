---
title: "Rethinking partioning strategy - ideas please."
date: 2010-12-10
forum: New to Ubuntu
---

### Post by CDSH on 2010-12-10
**Although I was successful with all of the assistance I recieved on my last plea for help thread on resizing a partition, in the process, it occured to me that maybe I was going in the wrong direction in the first place. **
 
**I've spent quite some time reading other threads in regards to partitioning strategy, and I would like some clarification on the reasons for setting up the partitions on my machine.**
 
**Currently I have a 320 gig hard drive that I cloned from an 80 gig drive. That left 200+ gig of unallocated space. **
 
**Here's my usage scenario:**
 
**I often move large quantities of data from one machine to another (50-100 gigs of music, movies, etc.) at a time. If I transfer from one hard drive to a different one on the same machine, or across my gigabit network the transfer rate is around 100 MB/s (good speed).**
 
**Sometimes I have to move those data from folder to folder on the same machine as well. On the Windows machines (I have 3 of them), the cut and paste happens nearly instantaneously (when the folders are on the same hard drive and partition).   If the folders are on the same hard drive BUT different partions the transfer rate is about 30 MB/s (too slow). **
 
**Here's the question for my Ubuntu machine:**
 
**Would it be better to extend my partition to include that 200+ gigs of unallocated space, OR, to allocate that extra space as another primary partition and move my home folder (where I keep all the data) to the new partition ? **

---

### Post by CDSH on 2010-12-10
**Bumping for the eyes of the *Day Shift.***

---

### Post by Girya on 2010-12-10
Move to LVM that will give you incredible flexibility in partitioning. you can shrink and grow volumes as you wish with out unmounting filesystems: no live cds. I use it like this, / on a standard partition of 100G for easy booting, /home, /music and /pictures on volumes of 200G each with 400G of unallocated space in reserve to add to as needed. if I consume the extra 400G I'll just buy another 1T drive and add it to my volume.

---

### Post by amjjawad on 2010-12-10
Why the duplication?

[http://ubuntuforums.org/showthread.php?t=1641902](http://ubuntuforums.org/showthread.php?t=1641902)

You could post back on that thread instead of marking it "SOLVED" while apparently it's not.
I'm confused now and not sure what exactly do you want.

---

### Post by aytech on 2010-12-10
Your transfer speed over network is 100 Mb/s? sounds strange to me. 
 
I'd move home folder to that partition, that way you can keep the data when you reinstall the OS

---

### Post by CDSH on 2010-12-10
> **amjjawad said:**
>  Why the duplication?
 
[http://ubuntuforums.org/showthread.php?t=1641902](http://ubuntuforums.org/showthread.php?t=1641902)
 

 
**Actually, in my simple mind this looks like a different issue than the one addressed by my last thread.**
 
> **amjjawad said:**
> 
 
You could post back on that thread instead of marking it "SOLVED" while apparently it's not.
I'm confused now and not sure what exactly do you want. 
 
**I was able to accomplish the intent of my last thread.  That is why I marked it as *"Solved".*   And, in fact, it was one of your posts that got me thinking that I might be barking up the wrong tree.  So there you have it ... I feel stupid squared.**
 
**All kidding aside, I really do appreciate your assistance and patience.  What my real question is;  what are the advantages to moving my "/home" and all associated data away from the Ubuntu file system partition ?  Or, am I still missing some enormous point that has all seasoned Ubuntu aficionados in stitches ? **

---

### Post by CDSH on 2010-12-10
> **aytech said:**
>  Your transfer speed over network is 100 Mb/s? sounds strange to me. 
 
**That would be MB/second (as in MegaByte) - and, that is quite normal on my Gigabit network.**

---

### Post by amjjawad on 2010-12-10
> **CDSH said:**
> **I was able to accomplish the intent of my last thread.  That is why I marked it as *"Solved".*   And, in fact, it was one of your posts that got me thinking that I might be barking up the wrong tree.  So there you have it ... I feel stupid squared.**
 
**All kidding aside, I really do appreciate your assistance and patience.  What my real question is;  what are the advantages to moving my "/home" and all associated data away from the Ubuntu file system partition ?  Or, am I still missing some enormous point that has all seasoned Ubuntu aficionados in stitches ? **

I don't mean anything bad but creating more than one thread for the same issue (regardless what happened later) will confuse someone else. Never mind, sorry about that.

I'd suggest to read here first before doing anything:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning")


Edit:
I could answer your questions but the best thing is to read what the official documents said :)

---

### Post by owiknowi on 2010-12-10
Something about partitions and moving files (as far as I know).

1. A partition is seen as a separate device by most OS.
You can (un)mount them independently from the partition where your OS resides.

In case you use only 1 partition for both OS and personal files, you should have a lot of space to work.
Thus never make the OS partition to small (temp files a.s.o.).

2. Copying or moving files from one partition to another is more or less the same as to another HDD (relatively slow).

3. I prefer first to copy and not move files to another partition/device/network. After that went successful delete the original file.
Sometimes just 1 bit goes wrong during moving and can leave the file unusable.

4. Also I have separate partitions for / (OS) and /home (personal files). This improves manipulation of files considerably.

Even under ms wx you can place your personal folder (Documents and Settings\) to an other partition. In the past I used TweakUI but with regedit you can do the same.

---

### Post by CDSH on 2010-12-10
> **amjjawad said:**
> 
I'm confused now and not sure what exactly do you want.

[B]Success.

Thank you all ever so kindly !



see attached ...
[/B]

---

### Post by amjjawad on 2010-12-10
> **CDSH said:**
> [B]Success.

Thank you all ever so kindly !



see attached ...
[/B]

Glad you made it ;)
If you don't have any other questions, please mark this thread as SOLVED for future reference by others :)

---

