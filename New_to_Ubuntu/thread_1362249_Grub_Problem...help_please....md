---
title: "Grub Problem...help please..."
date: 2009-12-22
forum: New to Ubuntu
---

### Post by chewes on 2009-12-22
[SIZE=2]Hi there..I have installed Ubuntu 9.10..in different partition with the pre existing Window XP..But unfortunately..at the grub I never see the Window Xp choice..Please all may you help me to solve this....![/SIZE]

---

### Post by overdrank on 2009-12-22
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by running_rabbit07 on 2009-12-22
Please open a terminal and enter```
sudo fdisk -l
``` then copy and paste the results here.

The above command gets the partition numbering for adding to the boot menu.

---

### Post by running_rabbit07 on 2009-12-22
I have just done some reading and found that you should only have to run one command to fix this problem. ```
sudo update-grub2
```

---

### Post by running_rabbit07 on 2009-12-22
Please click thread tools then click solved, if your problem is fixed. Thank you.

---

