---
title: "fstab entry not working"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Android565 on 2009-04-12
I'm trying to add a partition to fstab so I don't have to mount it manually but it isn't mounting, my entry looks like this:

```
/dev/sda4	/media/disk	vfat	iocharset=utf8,gid=1000,uid=1000,umask=447	0	0

```

Any ideas?

---

### Post by Flareside on 2009-04-12
Make it like this:

```
/dev/sda4	/media/disk	vfat	force 0 0
```

And also make sure that the directory /media/disk exists.

---

### Post by taurus on 2009-04-12
You do have the mount point /media/disk right?

```
ls -la /media
```

---

