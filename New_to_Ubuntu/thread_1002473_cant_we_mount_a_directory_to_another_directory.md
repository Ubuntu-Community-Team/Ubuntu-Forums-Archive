---
title: "cant we mount a directory to another directory?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-05
Hi
Thank you for reading my post.
is it possible to mount a directory to another directory?
for example, what will be fstab entry to mount  /dev/sda5/all  to /media/all?

Thanks

---

### Post by sisco311 on 2008-12-05
> **legolas_w said:**
> Hi
Thank you for reading my post.
is it possible to mount a directory to another directory?
for example, what will be fstab entry to mount  /dev/sda5/all  to /media/all?

Thanks

yes, but /dev/sda5 must be mounted first:
```
/dev/sda5        /mnt/sda5     type    options    0    0 
/mnt/sda5/all    /media/all    none    bind
```

---

