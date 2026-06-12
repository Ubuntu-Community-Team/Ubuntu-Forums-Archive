---
title: "Confused about the 2TB limit"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by busydoingnothing on 2010-03-27
I'm doing some research on setting up my software RAID-5, and came across discussion of the 2TB limit. I'm somewhat confused now...

I have 3x 1TB drives that I want to set up in a RAID-5, with LVM2 on top, XFS filesystem. The disks themselves have an MSDOS partition label. When I combine them all into a RAID-5, I'll end up with 2TB's. 

Let's say I add another 1TB drive to expand it to 3TB. Will I be able to have one large 3TB volume? Is that 2TB limit on the MSDOS partition a limit of the *physical drive*? In other words, if I'm combining 1TB drives to create a RAID, will I be able to expand my RAID-5 to be larger than 2TB without an issue? Or should I stop now, change the partition tables of each physical disk to GPT, and start over fresh? Starting over isn't a problem, since I haven't written anything to the RAID.

---

### Post by srs5694 on 2010-03-27
The 2 TiB limit is based on the Master Boot Record (MBR) partitioning system. As such, if you're using *software* RAID, you can link together as many sub-2TiB disks that use MBR as you like, since Linux software RAID arrays are built from partitions on the underlying disks, rather than the other way around with hardware RAID. Even if your disks total more than 2TiB, you should be fine with software RAID. If you should decide to add an over-2TiB disk in the future, though, you may need to use the GUID Partition Table (GPT) scheme on it.

---

### Post by busydoingnothing on 2010-03-28
Thanks for the reply! It looks like I'll be safe then, since my drives are all 1TB. If I expand in the future, I'll be expanding with 1TB anyway. If I'm looking to expand with larger drives, then I'll have to rebuild the array anyway.

---

### Post by drdos2006 on 2010-03-28
Check this out for more info.

[http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars/](http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars/)

regards

---

### Post by srs5694 on 2010-03-28
> **drdos2006 said:**
> Check this out for more info.

[http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars/](http://arstechnica.com/microsoft/news/2010/03/why-new-hard-disks-might-not-be-much-fun-for-xp-users.ars/)

That link is about the change from 512-byte to 4096-byte sectors in some recent (and probably in many more future) hard disks. Although this is an important issue, it has little to do with the question about RAID configuration that busydoingnothing posed. Are you sure you posted the right link?

---

