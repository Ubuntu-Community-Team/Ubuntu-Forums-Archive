---
title: "Mount other partitions with ro/rw access by default"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by bugsvoid on 2010-04-21
Hello all,

I have a dual boot system having Win7 + Ubuntu 9.10. It has 2 NTFS partitions & 2 ext3 partitions.

When I boot in ubuntu, these partitions (other than the root partition) appear in the nautilus when I open my computer. When I double-click & open these partitions, they are opened in read-only mode by default. How do I change this behavior? I want some partitions to be mounted as rw as default where as some partitions should be mounted as ro. The fstab does not have entries for these partitions. I assume that these are loaded at runtime. So where can I set the access mode for these partitions?

Regards.

---

### Post by Bob Bertrands on 2010-04-21
You can simply edit the /etc/fstab file.

execute in your terminal sudo blkid, search for the uuid of the desired partition and add this to fstab like this:

```
UUID=1FD0-4F64    /media/#the name you give your disk#        auto    rw        0    0
```

---

### Post by Mark Phelps on 2010-04-22
Do NOT mount your Win7 boot partition read-write.  

While the mounting is unlikely to cause any problems, if you change anything in there, your Win7 OS is unlikely to be able to boot again.  

Would be best to leave that partition as read-only.

---

### Post by bugsvoid on 2010-04-26
> **Mark Phelps said:**
> Do NOT mount your Win7 boot partition read-write.  

Yes. That is exactly what I want to do. Somehow, my NTFS partitions are mounted as rw where as my ext3 partitions are mounted as ro by nautilus. I want the opposite of this. 

I check fstab but there is no entry for any of these partitions in fstab. Hence I am curious how the access mode is decided for the partitions if they are not mentioned in fstab.

---

