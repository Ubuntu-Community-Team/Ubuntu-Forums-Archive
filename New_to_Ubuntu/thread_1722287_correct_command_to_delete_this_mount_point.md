---
title: "correct command to delete this mount point"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2011-04-05
i made the mount point

sudo mkdir /mnt/sda3

then used sudo mount -t ext4 /dev/sda3 /mnt/sda3

need to completely delete it /tks

---

### Post by falko on 2011-04-05
```
umount /dev/sda3
rm -fr /mnt/sda3
```

---

### Post by rburkartjo on 2011-04-06
falko tks

---

