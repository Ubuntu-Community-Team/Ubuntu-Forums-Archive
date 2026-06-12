---
title: "Union Mount"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by jerden on 2010-06-01
Hey guys I just got a new 1.5 terra byte HDD because I ran out of room on my other 1.5 terra byte HDD but I hate them being separate. I really would like the computer to see them as one. I was looking at UnionFS but was wondering is there any other options people have used on here to get that to work?

---

### Post by gmargo on 2010-06-01
LVM (Logical Volume Manager) is typically used for this sort of thing.[http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29)

The Union FS is typically used for LiveCDs or USBs, to mix read-write and read-only filesystems to transparently overlay changes to the read-only filesystem.  Not appropriate for two normal hard drives.
[http://en.wikipedia.org/wiki/UnionFS](http://en.wikipedia.org/wiki/UnionFS)

---

### Post by jerden on 2010-06-02
Cool thank you gmargo! Looks like I will be waiting a little while longer and getting a third HDD to make a RAID 5 array

---

### Post by bwinfrey on 2011-04-22
you can also mount using aufs:
sudo mount -t aufs -o dirs=/dir1/=rw:/dir2/=rw aufs /mnt/test

I am using this in a chrooted environment to combine two source directories.  I'm not exactly sure of the internals, but I notice that if I create a file/folder it will be on the first dir entry (/dir1 above) when unmounted.

-bw

---

