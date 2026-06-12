---
title: "Fresh install missing space on HDD"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Konsolkongen on 2008-12-19
Just did a frest 8.10 install 32-bit.

I partitioned the HDD like this: 
Swap area at about 2GB
Ext3 / 20GB
Ext3 /home rest of the HDD

My HDD is 640GB and i know these things are never correct. In Disk Usage Analyzer it says: 

Total filesystem capacity: 585,0 GB (used: 2,6 GB available: 582,3 GB).

I dont know if the 585 vs 640 GB add up but here is where it gets really wierd. In my home folder it says:

Free space: 537,6 GB

and in the file system it says:

Free space: 14,8 GB

Now, i have used 2,6 GB in the filesystem so that means the file system is 17,4 GB. This might be right i don't know. But it cant be right that when you add 17,4 GB to the home partition (537,6 GB) and add about 2 GB for the swap the result is: 557,1 GB. Thats 40 GB less that what Ubuntu says i have WTF? Its a brand new computer too so i doubt that the HDD is broken. When i made the new install of ubuntu i formatted both the "/" and "/home" partitions. 

If i right-click on my home folder and press Properties it also says:

8 items, totalling 28,0 KB
(some contents unreadable)

What is wrong here and can it be fixed without formating again?

---

### Post by drs305 on 2008-12-19
537  free space
+20  /
+ 2  swap
----
559


 585 total
-559
----
 26

Linux reserves 5% of each ext3 partition for use by the system (journaling, etc). 5% of 585GB is approximately 29. (Don't know if it's taken out of swap or not). So it would seem you are pretty much in the ballpark.

If you feel strongly about it and really need the space, you can reduce the amount of reserved space using tune2fs and the "m" switch.

I like the "df -h" command to check hard drive usage.

---

### Post by Konsolkongen on 2008-12-19
Ok sounds great! I was really worried that something was wrong. I never had a HDD bigger than 160 GB. So i'm sure i won't need the extra space anytime soon :)

Thank you!

---

