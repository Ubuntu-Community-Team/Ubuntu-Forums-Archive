---
title: "Mount external disk so that everyone can read/write"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by primaxx on 2009-12-14
Hello forum,

I want to mount an external USB-disk and make it read/writable to every user registered on the system.

This is what I have now, but I think this is wrong somehow, because I have to be sudo-user to see the content on the disk:```
# #/dev/sdb1
/dev/sdb1	/media/USB-Disk	vfat	rw,uid=1000,gid=100,utf8,dmask=027,fmask=137	0	2
```

Can anyone please help me here?

Thank you :)

---

### Post by dvlchd3 on 2009-12-14
set umask=0

This is essentially giving a+rwx or 777 permissions.  If you do not want execution, add the noexec option. (Making it 766 or 776, not sure...)

With execution:
```

# #/dev/sdb1
/dev/sdb1	/media/USB-Disk	vfat	rw,uid=1000,gid=100,utf8,dmask=027,fmask=137,umask=0	0	2

```

Without execution:
```

# #/dev/sdb1
/dev/sdb1	/media/USB-Disk	vfat	rw,uid=1000,gid=100,utf8,dmask=027,fmask=137,noexec,umask=0	0	2

```

---

### Post by primaxx on 2009-12-14
> **dvlchd3 said:**
> set umask=0

This is essentially giving a+rwx or 777 permissions.  If you do not want execution, add the noexec option. (Making it 766 or 776, not sure...)

With execution:
```

# #/dev/sdb1
/dev/sdb1	/media/USB-Disk	vfat	rw,uid=1000,gid=100,utf8,dmask=027,fmask=137,umask=0	0	2

```

Without execution:
```

# #/dev/sdb1
/dev/sdb1	/media/USB-Disk	vfat	rw,uid=1000,gid=100,utf8,dmask=027,fmask=137,noexec,umask=0	0	2

```

Woah, that was quick!

Thank you very, very much! :)

---

