---
title: "Stale NFS Handle"
date: 2014-01-07
forum: Networking &amp; Wireless
---

### Post by AmbiguousOutlier on 2014-01-07
I've made a mistake somewhere but I can't figure it out. 

I added; **/mnt/fs02/movies orange(rw,sync,no_root_squash)** to /etc/exports on tomato

On tomato I then ran; **sudo service nfs-kernel-server restart**

And added **TOMATO:/mnt/fs02/movies /mnt/fs02/movies nfs rsize=8192,wsize=8192,timeo=14,intr** to /etc/fstab on orange

On orange I then ran;
```

sudo mkdir /mnt/fs02/movies
sudo mount -a
ls /mnt/fs02/movies

```

Which returns the following error; **ls: cannot access /mnt/fs02/movies: Stale NFS file handle**

I have several other nfs shares and I've literally just copied previous entries and adjusted them. Can anyone see what I've done wrong?

---

