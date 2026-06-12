---
title: "a huge bad wierd problem"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Wraith619 on 2010-01-17
hi guys i've been trying to install ubuntu 9.04 for a week now...and i can't , when i install it from inside windows and restart after installation , it boots and goes into ubuntu when i choose it from boot menu , but it says no defined root partition and i go back i unistall it , i try installing it outside windows , it doesn't detect windows xp SP2 or even my partitions!!
help guys plz
thx for listenin'....

---

### Post by baltadt on 2010-01-17
1) Have you shrunk your windows partition from inside of windows first?
2) Are you using a live dvd or a download copy?
3) Are you trying to keep windows?

---

### Post by Wraith619 on 2010-01-17
1) nope.
2) the downloaded copy.
3) yes , i am

and thx for caring;)

---

### Post by baltadt on 2010-01-17
ok what windows does it it puts files at the end of the hard drive to make to os use the whole thing. first thing to do is to shrink it with windows. Second is to format the partition you made as a unused format not ntfs like windows wants to. then try and install with the GUI installed on the disk, select " install side by side, chose at startup". this should do it for you.

---

### Post by Wraith619 on 2010-01-17
total thx , it's clear now :popcorn:~wwwwwwwwwwwwwoooooooooooooo~:popcorn:

---

### Post by Wraith619 on 2010-01-17
how do u resize partitions in windows xp?
i already defraged the partition i am going to resize , the partition is 39 GB and the free space on it is 21 GB.

---

### Post by J V on 2010-01-17
You can't in xp afaik, you resize while installing ubuntu...

---

### Post by Wraith619 on 2010-01-17
i can't , it doesn't detect the partitions , detects the whole hd as one big unpartitioned mass.

---

### Post by baltadt on 2010-01-17
[http://www.theeldergeek.com/hard_drives_05.htm](http://www.theeldergeek.com/hard_drives_05.htm)


Method 2 - Use a program that is designed to handle partitioning tasks from inside the existing Windows operating system. The best known program of this type is probably PartitionMagic by PowerQuest, although there are many others including PartitionExpert by Acronis and Partition Commander by V Communications. A Google search will turn up many others as well as some free utilities to accomplish the same results.

how to 

[http://www.ehow.com/how_5074934_resize-partitions-windows-xp.html](http://www.ehow.com/how_5074934_resize-partitions-windows-xp.html)

---

### Post by thatguruguy on 2010-01-17
> **Wraith619 said:**
> i can't , it doesn't detect the partitions , detects the whole hd as one big unpartitioned mass.

By default, ntfs pushes everything to the front of the drive.  Make sure to defrag your drive under Windows first, which will clear up space at the end.  Make a note of how much space you have.  When you install ubuntu, it will let you decide how much of your windows partition to convert to ext3 (or ext4, if you choose that) to install ubuntu into.  Good luck.

---

