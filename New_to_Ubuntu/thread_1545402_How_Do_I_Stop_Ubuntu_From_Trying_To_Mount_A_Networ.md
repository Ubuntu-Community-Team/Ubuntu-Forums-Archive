---
title: "How Do I Stop Ubuntu From Trying To Mount A Network Drive At Startup?"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by justinmiller87 on 2010-08-03
See the following:

```
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /media/media [829] terminated with status 32
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /media/media [842] terminated with status 32
Skipping /shared at user request
mount error(101): Network is unreachable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
mountall: mount /media/media [858] terminated with status 32
```

Now, I've since solved the problem of getting it to mount using gvfs. But in the process of trying to get it to mount, after upgrading to 10.04, I now see this at every boot. What do I need to do to remove the attempt to mount my network drive at startup and just let gvfs-mount do its thing as it already is upon logging in?

---

