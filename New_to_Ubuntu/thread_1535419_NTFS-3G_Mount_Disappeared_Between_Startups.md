---
title: "NTFS-3G Mount Disappeared Between Startups"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by avast on 2010-07-20
Hey everyone,

It seems that sometimes my ntfs-3g mount disappears between restarts... this is kind of annoying because I put source code on that partition and then the dependencies get screwed up a little. Does anyone know of a solution?

Thanks ahead of time!

---

### Post by sisco311 on 2010-07-21
Hi, 

Please open a terminal (Applications -> Accessories) and post the output of:
```
sudo blkid -c /dev/null
```
and
```
cat /etc/fstab
```

---

### Post by avast on 2010-07-21
I actually managed to fix it, I think, using this:

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Thanks anyway!

---

