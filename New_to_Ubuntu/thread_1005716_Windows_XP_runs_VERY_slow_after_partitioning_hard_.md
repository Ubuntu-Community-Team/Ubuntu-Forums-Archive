---
title: "Windows XP runs VERY slow after partitioning hard drive for dual-boot with Ubuntu"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by docjones2 on 2008-12-08
I have recently partitioned my laptop's hard drive to setup a dual boot with Ubuntu.  I was able to do it successfully, both OSes run, however, the Windows XP partition is significantly slower than it was before the partition.

The hard drive's total capacity is 152 gb, 105 of which are the XP partition.  40 are for the Ubuntu partitions (one of them being a swap partition) and another 600 mb are for another partition which I believe is used by the XP partition to increase performance, names SERVICE001.  The XP partition has 43 gigs free, so I know the problem has nothing to do with low storage levels.

Could perhaps the XP partition no longer be using the SERVICE001 partition for whatever reason?  If so, how would I go about making the XP partition use the SERVICE001 partition again?

Thank you for your time.

---

### Post by kestrel1 on 2008-12-08
I suspect that the SERVICE001 partition is a small startup restore partition created at the factory for WinXP & will not be used by XP apart from when the system goes toes up & you need to restore it.
It could be that the swap file on the XP partition has become fragmented. Not working on XP at present & cant remember what you need to do. Do a search on google, it should throw up a result of twenty.

---

### Post by kestrel1 on 2008-12-08
Have a look here:
[http://techrepublic.com.com/5208-6230-0.html?forumID=5&threadID=197710&messageID=2061116](http://techrepublic.com.com/5208-6230-0.html?forumID=5&threadID=197710&messageID=2061116)

---

### Post by docjones2 on 2008-12-08
I found a working solution, for the time being anyway.

for anyone experiencing a similar problem:

run cmd

enter "chkdsk c:"  (assuming your drive letter is c)

if any errors are reported, enter

"chkdsk c: /f" and reboot

I've read that using the /f parameter can possibly cause a partition not to boot, I have not experienced this problem however it would be wise to exercise caution in doing this.

Thank you for your suggestions, and to anybody with a similar problem, good luck.

---

