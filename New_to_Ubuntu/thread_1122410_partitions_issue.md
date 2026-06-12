---
title: "partitions issue"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by vibrant007 on 2009-04-11
I have an existing windows OS (windows XP PRO) on my laptop. I have partitioned my 200GB scsi drive on my Toshiba satellite to have multiple Operating Systems. The Ubuntu installer window does not recognize any of my partitions and only gives me the choice of taking over my whole drive. I have partitioned everything with NTFS. I Need help with this bug! Has this been repaired?

---

### Post by Xender1 on 2009-04-11
could you leave your drive unpartioned except for you windows partition. and then using the livecd just choose guided resize and use freed space or just manual and then drag from there? so dont partition prior to attempting the install.

---

### Post by lavinog on 2009-04-11
> **vibrant007 said:**
> I have partitioned everything with NTFS. I Need help with this bug! Has this been repaired?
If you don't have free space available for a linux partition, you will have to remove, or resize an existing partition.
You can't install ubuntu on to a NTFS partition.
Also you can't have more than 4 primary partitions, Ubuntu will require a minimum of 2 (the root partition and a linux-swap)
To have more than 4 partitions, some of them will have to be extended/logical partitions.

---

