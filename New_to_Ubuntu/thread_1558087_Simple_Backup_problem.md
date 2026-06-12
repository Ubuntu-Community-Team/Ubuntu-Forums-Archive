---
title: "Simple Backup problem"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by Todd in Berlin on 2010-08-21
Hi, 

Simple Backup ran automatically, but unfortunately I did not have the target external disk hooked up, and I did not have the "abort if target not found" box checked.

So the backup in some kind of compressed version is somewhere on my partition which includes the Home folder. I have tried to find it with Disk Usage Analyzer, but no luck. 

**Using 10.04, 64 bit.** I know about the G-Parted stuff and have used it before, but it would feel like loosening my belt to feel I had not gained any weight.

Also, it seems that temporary downloads such as You Tube videos also are filling up space, though it seems that they cleaned up automatically.

Thanks!!):P

---

### Post by phillw on 2010-08-21
Hi,

the most likely place it would be is under ```
/media
``` as that is default for mounting external drives.

Regards,

Phill.

---

### Post by Todd in Berlin on 2010-08-21
Thanks, Phill. I had already looked there (file system / media)  and what is mounted is the current hard drive and two which are directly about the updates, but cannot be accessed (permissions) or deleted. They might contain just a tiny bit of stuff related to the back up (i.e. so that one can restore files, etc.) But also the contents of the current hard drive is equal in size to the full contents of /media.

---

### Post by Todd in Berlin on 2010-08-25
Partition with Home Folder still filling up and I can't find anything.....

Suppose I will start another thread.

Thanks.

---

