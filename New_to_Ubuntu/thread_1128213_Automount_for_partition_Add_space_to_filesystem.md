---
title: "Automount for partition? Add space to filesystem?"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by LesterPalooza on 2009-04-17
When I format a NTFS format partition (from Windows) to ext3, will this partition be automatically mounted everytime I startup Ubuntu?

I'm using GParted Partition Editor.

Additionally, is there anyway I can add this ext3 partition to the filesystem as additional "space"?

---

### Post by taurus on 2009-04-17
It will not automount for you unless you add an entry in /etc/fstab to have it mounted each time you boot Ubuntu.

Which partition is it?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

