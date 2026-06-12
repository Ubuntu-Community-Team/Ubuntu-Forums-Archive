---
title: "merging partitions with Gparted"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by myotis on 2010-11-30
I have two hard drives. both 300GB.

Ubuntu 10.10 is installed on /dev/sda

and the other hard drive /dev/sdb is divided into (ther is no data of any value on /sdb

/dev/sdb1        ntfs        158.33GiB
/dev/sdb2        extended    139.76gb
    unallocated  unallocated 1.00MiB
    /dev/sdb5    ntfs        139.76

Don't ask the details of how I got here, but it was because I am used to partition magic, and gParted obviously doesn't work the way I had expected.

I now realise that gParted has a rather more complex approach, which I don't really follow.

I wonder if anyone could help me with some step by step instructions on how I get this HD as one partition. 

I was leaving it as NTFS just to make it easily accessible to Windows, but happy to format it as something else if that is seen as a good idea.

Many thanks,

Graham

---

### Post by sikander3786 on 2010-11-30
See this for resizing help on gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

If the partitions you are going to resize/merge contain any useful data, make sure to backup that before proceeding.

---

### Post by bodhi.zazen on 2010-11-30
> **myotis said:**
> I have two hard drives. both 300GB.

Ubuntu 10.10 is installed on /dev/sda

and the other hard drive /dev/sdb is divided into (ther is no data of any value on /sdb

/dev/sdb1        ntfs        158.33GiB
/dev/sdb2        extended    139.76gb
    unallocated  unallocated 1.00MiB
    /dev/sdb5    ntfs        139.76

Don't ask the details of how I got here, but it was because I am used to partition magic, and gParted obviously doesn't work the way I had expected.

I now realise that gParted has a rather more complex approach, which I don't really follow.

I wonder if anyone could help me with some step by step instructions on how I get this HD as one partition. 

I was leaving it as NTFS just to make it easily accessible to Windows, but happy to format it as something else if that is seen as a good idea.

Many thanks,

Graham

If you have no data of any use on the drive

Fire up gparted

delete all the partitions -> apply changes

Make a new partition in the free space -> apply changes.

---

### Post by myotis on 2010-11-30
> **sikander3786 said:**
> See this for resizing help on gparted.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


Thanks, some useful instructions here.

Graham

---

### Post by myotis on 2010-11-30
> **bodhi.zazen said:**
> If you have no data of any use on the drive

Fire up gparted

delete all the partitions -> apply changes

Make a new partition in the free space -> apply changes.

Thanks, but the delete is greyed out, do I need to unmount the partitions first, and if I unmount them and turn them into one as per your instructions, will they remount automatically.

Thanks again,

Graham

---

### Post by sikander3786 on 2010-11-30
> **myotis said:**
> Thanks, but the delete is greyed out, do I need to unmount the partitions first, and if I unmount them and turn them into one as per your instructions, will they remount automatically.

Thanks again,

Graham
Yes you need to unmount the partitions prior to deleting them. Better if you do this from an Ubuntu or Gparted Live CD.

Yes the new partition will mount automatically once you click that but if you want to mount that automatically or startup, you need to define the mount in /etc/fstab or using the NTFS config tool.

As I see the partitions on your sdb are NTFS. Do you plan to use that drive as a data sharing drive between Windows and Ubuntu? If not, just format the new one to ext4 and not NTFS.

---

