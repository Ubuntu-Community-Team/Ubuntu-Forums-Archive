---
title: "Disk Check In Ubuntu?"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-24
I have seen ubuntu checking my HDD while start up in some situations,But is there any way to do it manually and also defragment my HDD (i have 1 ext4 and 3 ntfs file systems)

---

### Post by ubername on 2009-05-24
> **ravi_buz said:**
> I have seen ubuntu checking my HDD while start up in some situations,But is there any way to do it manually and also defragment my HDD (i have 1 ext4 and 3 ntfs file systems)

I'm no expert but:

Defrag NTFS drives from windows. I don't know if you can from ubuntu, but even if you can I wouldn't

As far as I know you don't need to defrag linux type partitions (including ext4)

you can use 'fsck' to check a linux HDD but it should be unmounted, which probably means running  from a liveCD, or you can just wait for ubuntu to do it. 

You can change how often this runs:
[http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)

---

### Post by orky7 on 2009-05-24
in ext4 the HDD check at start-up is not going to happen, they created ext4 in such a way that u don't need HDD checks, and actually u don't need to  defrag linux partitions but u can do it if u want.

---

