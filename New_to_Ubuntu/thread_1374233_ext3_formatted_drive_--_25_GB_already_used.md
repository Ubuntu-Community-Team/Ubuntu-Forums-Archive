---
title: "ext3 formatted drive -- 25 GB already used?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by bnhrobotics on 2010-01-06
I formatted a RAID 1 drive, originally 500GB. Its ext3 formatted capacity is 465.66 GB. However, 23.5 GB have already been used according to nautilus and 7.5 GB according to Gparted. What is going on? There is a lost+found folder. Is this taking up all of that space? I just reformatted it and I still have the same capacity issues.

Edit: Just to clarify, after the 23.5 GB used, the capacity drops to 434.9 GB

---

### Post by jonest1 on 2010-01-06
I'm not in the best position to answer this question, but there is space reserved by the operating system for emergency use by root.  Also, the formatting process does use some space as inodes are pre-allocated, etc.  There is a method to adjust the reserved space, but you may have to look around as I do not have a lot of time at the present.

---

### Post by louieb on 2010-01-06
Reserved space for essential processes  - default 5%. Can be changed with tune2fs. 
**[*Ext3* Filesystem Tips - ArchWiki]("http://www.google.com/url?sa=t&source=web&ct=res&cd=6&ved=0CBMQFjAF&url=http%3A%2F%2Fwiki.archlinux.org%2Findex.php%2FExt3_Filesystem_Tips&ei=yf5ES-LOGpH8NcCb9e0F&usg=AFQjCNFoA2ovT-66wnQOp5rALAxep09MbA&sig2=H21yPYnVHqICNJmoMm101Q")**

---

