---
title: "Having troubles mounting my windows partition"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by andpal222 on 2011-01-24
Hi,

Recently, my Windows XP partition crashed and we suspect it is because of a registry problem. I spent countless hours trying to fix the problem but was unable to and resorted to the "repair windows option". This did not help at all either. So what i have decided to do rather then wasting my time was to mount my windows partition to ubuntu, then copy files from Ubuntu to blank CD's and then just reinstall windows all together.

However, i am having troubles mounting my Windows partition and have tried a variety of methods and am still unable to. I have used ntfs config, and MountManager and both say that the partition is mounted but i do not see it in the file manager.

please, any help would be greatly appreciated

---

### Post by [Snc] on 2011-01-24
> **andpal222 said:**
> Hi,

Recently, my Windows XP partition crashed and we suspect it is because of a registry problem. I spent countless hours trying to fix the problem but was unable to and resorted to the "repair windows option". This did not help at all either. So what i have decided to do rather then wasting my time was to mount my windows partition to ubuntu, then copy files from Ubuntu to blank CD's and then just reinstall windows all together.

However, i am having troubles mounting my Windows partition and have tried a variety of methods and am still unable to. I have used ntfs config, and MountManager and both say that the partition is mounted but i do not see it in the file manager.

please, any help would be greatly appreciated

here is the default howto for NTFS and Ubuntu 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

but if the partition is already mounted, you can find here
```
/media
```
it should be a folder like for example "EF23-873A"

---

### Post by andpal222 on 2011-01-24
> **'[Snc] said:**
> here is the default howto for NTFS and Ubuntu 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

but if the partition is already mounted, you can find here
```
/media
```
it should be a folder like for example "EF23-873A"


ok, so in the file browser, i went to the file system, and i found a folder labeled "Media". Inside this folder there are two folder : "sda1" and "windows". But both folders are empty

---

### Post by andpal222 on 2011-01-24
> **andpal222 said:**
> ok, so in the file browser, i went to the file system, and i found a folder labeled "Media". Inside this folder there are two folder : "sda1" and "windows". But both folders are empty

After looking around for a bit, i found the entire partition on the host folder. Thanks for the quick help!

---

### Post by Mark Phelps on 2011-01-25
In general, the way that "windows" get mounted to \host is when you install Ubuntu INSIDE Windows using Wubi.  IF you did this, which I suspect, when you erase Windows, you will erase Ubuntu as well!

One way to tell is to open a terminal in Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one).  That will list the partitions on your drive.  If they are all NTFS or none of them are Ext3, or Ext4, then you have a Wubi installation.

---

### Post by andpal222 on 2011-01-26
> **Mark Phelps said:**
> In general, the way that "windows" get mounted to \host is when you install Ubuntu INSIDE Windows using Wubi.  IF you did this, which I suspect, when you erase Windows, you will erase Ubuntu as well!

One way to tell is to open a terminal in Ubuntu and enter "sudo fdisl -lu" (that's a lowercase L, not a one).  That will list the partitions on your drive.  If they are all NTFS or none of them are Ext3, or Ext4, then you have a Wubi installation.

Thanks Mark, thing is that this is more of a back up computer that is several years old and doesn't see much use anymore. I recovered my important data but my windows partition is so messed up that the only option was to do a clean install. I plan on installing ubuntu 11.04 when it comes out.

---

