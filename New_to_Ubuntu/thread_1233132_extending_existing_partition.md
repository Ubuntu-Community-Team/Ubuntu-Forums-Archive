---
title: "extending existing partition"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-08-06
I have HP notebook. It has recovery partition. If i expand the header of this partition using "partition editor" then will it be ok? means, will integrity of the recovery-data still remain?

---

### Post by DiscoKiller on 2009-08-06
I wouldnt recommend it dude, generally you are ok resizing ext3 and the like because the data is stored in a sensible way (starts at the beginning of the drive and adds data block by block). anything like fat32 or ntfs tend to scatter data about the drive so if you resize you can end up hoofing everything up. 
 
If you dont want to lose the data I would look into other ways of increasing your 'buntu space. If anyone who knows more than me wants to comment then that would be just dandy...
 
Peace,
 
DK

---

### Post by mikechant on 2009-08-06
> If i expand the header of this partition 

I've done a lot of partitioning and I'm not familiar with the idea of 'expanding the header' of a partition. Could you explain what exactly you are trying to do, and maybe illustrate it by including a printout of your partition table - the output from the command
```
sudo fdisk -l
```

(Lower case L not a number one)

---

### Post by corkscrew on 2009-08-06
> **eshant_engineer said:**
> I have HP notebook. It has recovery partition. If i expand the header of this partition using "partition editor" then will it be ok? means, will integrity of the recovery-data still remain?
 I have messed with partitions on several laptops with recovery partitions on them, dual booting etc.

I would strongly recommend you don't alter the recovery partition in any way other wise it may become unreadable to the operation system it is designed to rescue.

---

