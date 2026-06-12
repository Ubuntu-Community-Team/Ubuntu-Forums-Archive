---
title: "Wipe all RAID data to start over"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by derek71 on 2010-05-17
I had originally set up a software raid 5 under ubuntu server 8.

I have since upgraded to ubuntu server 10.04 and intended to rebuild the raid using the same drives.

I followed this thread for the most part: [http://ubuntuforums.org/showthread.php?t=408461&highlight=ubuntu+10+raid](http://ubuntuforums.org/showthread.php?t=408461&highlight=ubuntu+10+raid)

The key difference being that I used fdisk to delete and recreate the partitions on the hard drives.

The errors I have run into include:
 -the raid name being changed by mdadm from /dev/md0 to /dev/md/0.
 -one of the four drives not be added to the array.

I have found some hints in other posts here, though I still am unable to form a working array.

Since I have confused Ubuntu trying to set up the RAID, is there a way to wipe ALL array information (including partition/superblock data) and start over?

---

### Post by derek71 on 2010-05-20
After more searching, I found a couple of postings that answered my questions.  Problem solved.

---

