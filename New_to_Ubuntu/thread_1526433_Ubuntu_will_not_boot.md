---
title: "Ubuntu will not boot"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by rogeliodelarosa97 on 2010-07-08
hello i have finally partitioned using a gparted live cd and now once i boot up i get a message saying 

mount: mounting /dev/disk/by-uuid/2c2e7ba2-5c4448fa-b1a3-77a0f576907 on root
failed: invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /crop on /root/crop failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=botarg

please help!!!!!!!!!!!!!!!!!!! me i am a newbie so be descriptive

---

### Post by jtarin on 2010-07-08
Is this disk dedicated to Ubuntu? Do you remember your partition scheme?

---

### Post by tarps87 on 2010-07-08
Have you got a live cd? If so boot up using the live cd and then run the command
```
sudo fdisk -l
```

---

