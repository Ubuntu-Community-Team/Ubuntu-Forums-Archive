---
title: "Trouble installing ubuntu"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by argelfraster on 2008-12-25
Hey,
im trying to install ubuntu 8.10, but as soon as i start installing a get a message that says: The creation of swap space in partition #5 of SCSI3 (0,0,0) (sda) failed.
What do i do?:confused:

---

### Post by taurus on 2008-12-25
How many primary partitions do you have?  From the LiveCD, open a terminal and post the layout of your harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

