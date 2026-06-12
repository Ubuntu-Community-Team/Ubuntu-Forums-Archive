---
title: "error building partition for md raid - Gparted"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by oehq on 2009-04-28
error building partition for md raid

```
GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ext3, 931.51 GB) on /dev/sdb  00:00:21    ( ERROR )
     	
create empty partition  00:00:11    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 1953520064
size: 1953520002 (931.51 GB)
set partition type on /dev/sdb1  00:00:10    ( SUCCESS )
     	
new partition type: ext3
create new ext3 file system  00:00:00    ( ERROR )
     	
mkfs.ext3 -L "" /dev/sdb1
     	
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!

========================================

```

How to i clear this??
I started to make a md raid and failed ... wanted to start over cant get the gparted to work

any Ideas

Thanks

---

