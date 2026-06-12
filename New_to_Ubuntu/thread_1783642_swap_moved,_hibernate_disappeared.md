---
title: "swap moved, hibernate disappeared"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by bestron on 2011-06-16
When I installed ubuntu 11.04, I've chosen Delete 10.10 and install that created a new swap separated from the 10.10 swap, so I removed the new one as the size of the old swap was the right for me, after that I've found that the hivernate had disappeared from the power menu
I now have 1.5 GB of swap and I have 4 GB of RAM and that was working fine for me with 10.10 ..
any help?

---

### Post by plucky on 2011-06-16
> **bestron said:**
> When I installed ubuntu 11.04, I've chosen Delete 10.10 and install that created a new swap separated from the 10.10 swap, so I removed the new one as the size of the old swap was the right for me, after that I've found that the hivernate had disappeared from the power menu
I now have 1.5 GB of swap and I have 4 GB of RAM and that was working fine for me with 10.10 ..
any help?

Does your swap work?

Please post output of ```
free -m
sudo blkid
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
```

---

### Post by mikewhatever on 2011-06-16
When hibernating, the content of RAM is copied into swap, and there is no way to do that with your setup (4>1.5).

---

### Post by wildmanne39 on 2011-06-16
> **bestron said:**
> When I installed ubuntu 11.04, I've chosen Delete 10.10 and install that created a new swap separated from the 10.10 swap, so I removed the new one as the size of the old swap was the right for me, after that I've found that the hivernate had disappeared from the power menu
I now have 1.5 GB of swap and I have 4 GB of RAM and that was working fine for me with 10.10 ..
any help?
Hi, I agree it could be to small or maybe you did not turn it on, open gparted and see if the swap is on.

---

