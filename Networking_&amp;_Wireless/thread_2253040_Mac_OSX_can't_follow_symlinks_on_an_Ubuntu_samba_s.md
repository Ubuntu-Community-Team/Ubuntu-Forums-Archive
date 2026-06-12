---
title: "Mac OSX can't follow symlinks on an Ubuntu samba share"
date: 2014-11-16
forum: Networking &amp; Wireless
---

### Post by gyrex on 2014-11-16
Hi guys,

For some reason, Mac OSX won't follow symlinks on a samba share I've created on Ubuntu 14.04. Windows can follow the symlinks fine, but OSX finder won't...

I added these lines to /etc/samba/smb.conf

```
[global]

follow symlinks = yes
wide links = yes
unix extensions = no
```

Any ideas?

---

