---
title: "Shows 160gb as full when it is not"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by abeisgreat on 2009-05-15
Ok this is an unusual issue, I have a 160gb sata harddrive, the only harddrive in my machine, I have it formatted that:

sda1 : operating system : ext4      : 4.88gb
sda2 :                  : extended  : 5.42gb
sda3 : home             : ext4      : 138.4gb
sda5 : swap             : swap      : 5.42gb

And heres the thing, gparted shows sda3 as 138gb, but "df -h" shows it as 67, and this is what ubuntu thinks it is. It thinks I only have 7gb of free space when sda3 is little over half full, and looking at it in gparted, it thinks that it has 10gb free, and again, that ~60gb disappears. I have no idea what is causing this, any help? 

P.S. I've attached a screenshot to help demostrate what exactly is going on

---

### Post by nhasian on 2009-05-15
did you resize your partitions or did you create them from scratch?  I had a similar glitch where it did not show 100% of my ext3 partition after i resized it.  I fixed it by resizing it slightly smaller, then resizing it to the max again.  

warning: never resize a volume that is currently mounted.  you can boot off the liveCD and use gparted to resize parititons on your hard disk.

---

### Post by abeisgreat on 2009-05-15
> **nhasian said:**
> did you resize your partitions or did you create them from scratch?  I had a similar glitch where it did not show 100% of my ext3 partition after i resized it.  I fixed it by resizing it slightly smaller, then resizing it to the max again.  

warning: never resize a volume that is currently mounted.  you can boot off the liveCD and use gparted to resize parititons on your hard disk.

Hmm... I believe the partitions were created in the ubuntu 9.04 installer, but it could be a similar issue, I'll give that idea a shot, cause that seems like the type of thing it could be.

---

