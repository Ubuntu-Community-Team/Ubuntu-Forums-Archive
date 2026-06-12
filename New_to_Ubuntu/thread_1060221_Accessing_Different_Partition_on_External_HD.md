---
title: "Accessing Different Partition on External HD"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by darkH0rse on 2009-02-04
I have an external hard driver (500gb) that is partitioned into two parts. One part is for Ubuntu, and the other is for backup as well as my library of songs. When I try to access these songs from the places explorer, I dont have any trouble. But when I want to get a folder or file from the other partition from within an application, the drive is not listed. How can I reach these files from within applications?

---

### Post by taurus on 2009-02-04
Did you mount the other partition?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```
Which partition you are trying to access?

---

### Post by darkH0rse on 2009-02-04
yeah, its mounted

---

