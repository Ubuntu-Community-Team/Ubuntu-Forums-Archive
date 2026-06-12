---
title: "All of my data are gone after I mount a non empty directory to an empty partition."
date: 2008-12-05
forum: New to Ubuntu
---

### Post by legolas_w on 2008-12-05
Hi
what will happen when we mount a directory which has some data to a partition which has no data?
I have just done that and I realized all of my data which was inside that directory is gone.

I mounted /dev/sdb3 to /opt by changing the fstab and reloading it.

I tried to comment the line and execute sudo mount -a to unload the mount point with no luck.

---

### Post by nakama85 on 2008-12-05
> **legolas_w said:**
> Hi
what will happen when we mount a directory which has some data to a partition which has no data?
I have just done that and I realized all of my data which was inside that directory is gone.

I mounted /dev/sdb3 to /opt by changing the fstab and reloading it.

I tried to comment the line and execute sudo mount -a to unload the mount point with no luck.

to unmount I think you need to enter something like this in terminal
```
sudo umount /dev/sdb3
```

remember you should always create a new dir to mount to.

---

