---
title: "Mounting issue after upgrade"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by kernel tom on 2009-02-09
So I finally upgraded from 7.10 to 8.04 via the update manager.  I know, it took me a while but I wanted to wait until I wasn't using my computer for anything important.

I am running across the problem of not being able to mount my external hard drive as user, it wants me to be root... here is my fstab entry for this drive and I'm pretty sure its correct as it worked before the upgrade...


UUID=e9ce2da1-3674-4098-b37f-442d245e9286	/media/Media	ext3	rw,noauto,user,noexec	0	0

Also, my internal partitions no longer show up on my desktop which I liked and I'm not sure how to get that back either.

Thanks,
kt

---

### Post by adult swim on 2009-02-09
try running ```
sudo blkid
``` from a terminal and then compare the uuid that is shown for your external drive to the one that is in fstab.  are they the same?

---

### Post by kernel tom on 2009-02-09
Yes I forgot to mention I did check the UUIDs and they are the same

---

### Post by kernel tom on 2009-02-09
update: I can mount the drive using the terminal as user, but not by right clicking the drive and pressing "mount"

---

