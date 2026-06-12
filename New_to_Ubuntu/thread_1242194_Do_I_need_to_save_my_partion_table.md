---
title: "Do I need to save my partion table?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-16
Do I need to save my partion table or would saving my partitions suffice?

I have only 1 hard drive with 3 primary partitions (/, swap, home).  Grub is on the MBR; the MBR is on /.

The reason I ask:

[http://www.partimage.org/Partimage-manual_Backup-partition-tab](http://www.partimage.org/Partimage-manual_Backup-partition-tab)

The information at this specific url confuses me.  It seems like this specific url is refering to "extended" partitions.  I have no "extended" partitions.

Based upon my setup, do you think I should save my partition table?  Where would I save it; perhaps mnt?

Thanks.

---

### Post by drs305 on 2009-08-16
Your link dropped a couple of letters. Here is the page:
[http://www.partimage.org/Partimage-manual_Backup-partition-table]("http://www.partimage.org/Partimage-manual_Backup-partition-table")

I used partimage for years and never accomplished these steps specifically for partimage. I saved the partition table regularly with my own separate backups. Since I always restored images to their original location, I didn't need to mess with the partition table. However, having a copy of the partition table isn't a bad thing to have, regardless of whether you use partimage or not.

You can save it wherever you wish - it's just a small file.

---

### Post by cat2005 on 2009-08-17
> **drs305 said:**
> Your link dropped a couple of letters. Here is the page:
[http://www.partimage.org/Partimage-manual_Backup-partition-table](http://www.partimage.org/Partimage-manual_Backup-partition-table)

I used partimage for years and never accomplished these steps specifically for partimage. I saved the partition table regularly with my own separate backups. Since I always restored images to their original location, I didn't need to mess with the partition table. However, having a copy of the partition table isn't a bad thing to have, regardless of whether you use partimage or not.

You can save it wherever you wish - it's just a small file.


If my partition table is in the MBR, and the MBR is on sda1, then wouldn't I already get the partition table while saving sda1?

---

### Post by drs305 on 2009-08-17
> **cat2005 said:**
> If my partition table is in the MBR, and the MBR is on sda1, then wouldn't I already get the partition table while saving sda1?

When you restore with partimage, you have to designate a partition. If the partition table was damaged, you may not have a partition to choose to restore your backup to. If you could restore the table, you would be able to restore the image to it's original location. 

Partimage has an option to restore the MBR from an image file, but I think this would be from a separate file. I don't believe it can go inside your backup and extract a partition table. I haven't used that feature so perhaps another user can provide a definitive answer.

---

