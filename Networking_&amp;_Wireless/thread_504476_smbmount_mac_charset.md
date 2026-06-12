---
title: "smbmount mac charset"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by timas on 2007-07-19
Howdy,

I'm having issues with smbmount not displaying certain folders with bullets in the foldername.. I finally found something about charsets and codepage that /might/ be in the right direction but I can't find the correct solution, or at least all my attempted combinations don't work.
```

smbmount //10.0.0.79/hoehle /mnt/samba -o username=xyz,uid=1000,gid=1000,file_mode=0640,codepage=cp437,iocharset=utf8

codepage=utf8,iocharset=utf8
codepage=iso8859-1
codepage=cp437, utf16
codepage=cp852,iocharset=utf8
codepage=cp437,iocharset=utf8 

```

anyone have an idea?

Thanks!

---

