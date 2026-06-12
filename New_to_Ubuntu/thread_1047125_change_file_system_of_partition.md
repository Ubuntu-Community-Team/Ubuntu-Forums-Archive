---
title: "change file system of partition"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mdewet on 2009-01-22
I have a 200 GB hard drive for all my data that is currently FAT32..is there a way to change it to NTFS or ext3 without having to move all the data to another drive and completely reformat the drive?

---

### Post by Michael.Godawski on 2009-01-22
hi,

I don't think so.
I guess there is no other way to change the type of the partition as to re-partition the drive.

---

### Post by Elfy on 2009-01-22
If you have windows then you can change the drive to ntfs.

[http://technet.microsoft.com/en-us/library/bb456984.aspx](http://technet.microsoft.com/en-us/library/bb456984.aspx)

---

### Post by Michael.Godawski on 2009-01-22
> If you have windows then you can change the drive to ntfs.

[http://technet.microsoft.com/en-us/l.../bb456984.aspx]("http://technet.microsoft.com/en-us/library/bb456984.aspx")Learning something new every day....

Is the transformation of the partitions type possible in Linux, too?
Or  is a windows machine required?

---

### Post by Elfy on 2009-01-22
Not sure tbh - just remembered the other from the dark days :)

---

### Post by hyper_ch on 2009-01-22
you could shrink it
then crate a partition with the new desired filesystem
then move the files in there
then deleted the original partitiona nd expand the other one.

---

### Post by mcduck on 2009-01-22
> **Michael.Godawski said:**
> Learning something new every day....

Is the transformation of the partitions type possible in Linux, too?
Or  is a windows machine required?

That's pretty much a special case. Windows includes a tool that allows converting from FAT to NTFS. There's no way to convert back from NTFS to FAT, and the result is not exactly same as if the partition was originally formatted as NTFS. (+ you still get a warning that you might loose all your data during the conversion ;))

In Linux you can convert between Ext2 and Ext3, as they are pretty much the same apart from journaling included in Ext3. I've understood that Ext4 would be similar in this aspect.

Apart from those 2 exceptions it's safe to say that changing file system will always destroy all data on that partition.

---

