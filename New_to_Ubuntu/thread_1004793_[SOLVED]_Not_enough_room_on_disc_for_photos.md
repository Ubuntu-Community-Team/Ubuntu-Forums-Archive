---
title: "[SOLVED] Not enough room on disc for photos????"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by wavemaker on 2008-12-07
Gooday all, as the title suggests, I have tried to download some holiday photos from a disc onto my machine. However the process stalls and a message saying that there is not enough room on the disc appears.Could one of you fine people tell me how I find out how much disc space I have used and if I can add more space to the partition I am using. I think the drive is 150 gig. I only want this OS on the disc so I can get rid of anything else if needs be. Thanks in advance. James.

---

### Post by lovelyvik293 on 2008-12-07
OPen the System->administration->system monitor and go to the file sytem tab and you can see the use of your disk.

---

### Post by gettinoriginal on 2008-12-07
Try this, hope it helps

[http://ph.ubuntuforums.com/showthread.php?p=6259849](http://ph.ubuntuforums.com/showthread.php?p=6259849)

---

### Post by wavemaker on 2008-12-07
Thanks for the responses. It would appear that somehow or other I have installed an a very small partition. Don't really know what to do about that other than format the drive and re-install making sure I use the whole partition.

---

### Post by laffinet on 2008-12-07
NoNoNo.

You don't have to reinstall. All you need to do is change the partition size. To do so, boot into the liveCD & use gparted (under System -> Administration) and increase the partition size.

You have to use a liveCD because you can not change partitions that are mounted (eg root and home for your running system).

---

### Post by jimmy the saint on 2008-12-07
ADVISORY!!  Should you take laffinet's advice, backup your important data!!  That should go without saying, but nearly every day someone posts who did not and lost data. Also, please share with us your partition scheme.  What are the partitions and how big are they.  You dont have to worry about a command, you can just tell us.

---

### Post by handydan918 on 2008-12-07
> **jimmy the saint said:**
>   What are the partitions and how big are they.  You dont have to worry about a command, you can just tell us.

However, in the interest of ease, if the OP should wish to cut and paste a command, this one may serve.

```
sudo fdisk -l
```

---

### Post by wavemaker on 2008-12-08
Gooday again. Being a bit of an impatient sod I just jumped in and re-installed. It is all up and running at the moment. Got the photos downloaded. Thank you all for your fast and knowledgeable help. James.

---

