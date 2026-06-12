---
title: "smbfs codepage on fstab"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by guillemsola on 2008-02-07
Hi all,

I have a home NAS device that I mount with

> mount   -t   smbfs //192.168.1.3/PUBLIC    /mnt/NAS/ -o guest,iocharset=utf8,dmask=777,fmask=777,codepage=iso8859-15,uid=1000,

This way works great, but... I would like to do the same on fstab. 

> //192.168.1.3/PUBLIC      /mnt/NAS           smbfs   user,guest,codepage=iso8859-15,iocharset=utf8,uid=1000 0       0

This mounts the NAS disk but without codepage conversion so I can't see local characters.

Why It doesn't work? I read many manuals and seems that codepage is supported on fstab. Isn't it?

Thanks!

---

