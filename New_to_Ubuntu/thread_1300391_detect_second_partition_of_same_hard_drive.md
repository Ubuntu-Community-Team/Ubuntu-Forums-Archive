---
title: "detect second partition of same hard drive"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by ditch_windows on 2009-10-24
Hello, this is my first posting here, I've been using Ubuntu for 2 years on desktop computer. Just installed it recently on my laptop also, so I'm Windows free!
Question: during Ubuntu installation, did not pay much attention to partitioning, so my 80 GB hard drive is still split in 2 as it was under Windows. Ubuntu shows only half of the capacity; how do I detect now the second half? Thank you, hope this is not confusing...

---

### Post by shadow120 on 2009-10-24
```
sudo fdisk -l
```

run that from the terminal and it will tell you what your partitions are

you can install gparted and delete the second partition

---

### Post by laidback on 2009-10-25
You may well find Gparted is already installed, System>Admin.>Partition Editor. However, you may/will have problems if you try to adjust a partition that's mounted, which includes the partition that the OS is on. But Gparted is also on the Live CD so if you want to reorganise and merge your current partitions run Gparted from there.

There is also a web site for Gparted from where you can get a bootable version, Google for it. You download an ISO and burn that to a CD.

---

