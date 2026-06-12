---
title: "Quick windows question...."
date: 2009-07-25
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-07-25
If I partition my external hard drive will windows be able to see the partitions and access them?

---

### Post by desperado665 on 2009-07-25
If you partition with ext3 or ext4, then, in theory no. I hear that there are windows programs to allow access to ext3 formatted drives, but I dont know how reliable they are. If you must be able to access the partition from windows, you should format it with fat32, but I believe there is a 4GB limit on partition size. 

I use a common partition for data storage between the 2 OSes, but I installed windows first and formatted the partition using NTFS, which allows Ubuntu to read/write to it.

---

### Post by kamitsukai on 2009-07-25
> **desperado665 said:**
> If you partition with ext3 or ext4, then, in theory no. I hear that there are windows programs to allow access to ext3 formatted drives, but I dont know how reliable they are. If you must be able to access the partition from windows, you should format it with fat32, but I believe there is a 4GB limit on partition size. 

I use a common partition for data storage between the 2 OSes, but I installed windows first and formatted the partition using NTFS, which allows Ubuntu to read/write to it.

Well I've decided instead of just creating a partition I'd create and encrypted one with truecrypt using ntfs:D

so it should work xD

---

