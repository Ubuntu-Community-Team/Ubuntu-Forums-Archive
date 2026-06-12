---
title: "CIFS: Can't change umask on NAS"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by klss on 2008-09-12
Hi folks.

I am running umask 000 on my local machine (Ubuntu Hardy).

I don't manage to get it configured on my NAS. It keeps generating new files with 022 (rw-r-r).

My mount string in fstab:

```
//192.XXX.X.XXX/root /media/netcenter cifs password=XXXX,uid=1000,gid=1000,rw,iocharset=utf8,codepage=cp850,dir_mode=0777,file_mode=0777,rsize=8192,wsize=8192,noauto 0 0
```

THX for your support.

---

