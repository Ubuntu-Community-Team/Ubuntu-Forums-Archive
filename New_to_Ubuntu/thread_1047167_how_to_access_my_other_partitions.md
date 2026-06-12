---
title: "how to access my other partitions?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-01-22
besides my ext3 partition, i have 3 fat32 partitions that would showup in nautilus in ubuntu.

but theyre not showing up in xubuntu file manager, i think its called thaurus or something :)

how can i access them?

---

### Post by Bachstelze on 2009-01-22
The Wiki has all you need. ;)

[https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions](https://help.ubuntu.com/community/MountingWindowsPartitions#For%20FAT32%20and%20FAT16%20Partitions)

---

### Post by faraz_k86 on 2009-01-25
k thanks, ive read through the wiki and edited fstab accordingly.

but when i mount the partitions with sudo mount -a they get mounted in /media/drivec/

that is, to access the partitions, i have to go to that specific folder.

how do i make it such that all partitions when mounted appear on the desktop, just like ubuntu?

---

### Post by faraz_k86 on 2009-01-26
bump.. :)                   .

---

### Post by taurus on 2009-01-26
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

