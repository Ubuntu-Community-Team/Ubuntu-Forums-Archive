---
title: "Drive Partition"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by darkH0rse on 2009-01-31
I'm trying to install Ubuntu on an external hard drive. The install screen allows you to adjust how much of that drive you want devoted to Ubuntu. But if I partition only some of the drive, will the entire drive be erased in order to partition one section? Do I need to make a partition using Disk Manager in XP and then install within that partition? How can I partition it without the other contents being erased?

---

### Post by nandemonai on 2009-01-31
Use GParted on the live cd to resize the existing partitions and create a new one after. Then use that partition for the install.

Just be sure to back it all up beforehand in case anything goes wrong.

---

### Post by 73ckn797 on 2009-01-31
If the HD already has an OS installed you will have to resize that partition to a smaller size to make room for the new partition.

Ubuntu will not overwrite another partition unless you choose to "use entire disk". You are in control.

---

