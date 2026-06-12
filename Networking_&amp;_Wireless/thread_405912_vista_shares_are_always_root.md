---
title: "vista shares are always root"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by dsula on 2007-04-10
Hi,

I'm sharing a vista folder and I would like to access this through ubuntu. So far I got everything working fine except that ubuntu shows files on the vista share to be "root" owned. In other words I can only write to my share as root. How can I change the ownership of the share ? I understand this is probably something that needs to be done on the vista side, but since I don't know where else to ask, I post it here. I'd appreciate any help.

Regards,
dsula

---

### Post by bnuytten on 2007-04-21
```
mount -t cifs -o 'username=Administrator,password=blahblah' //172.16.0.3/WinShare /mnt/tmp/
```

Any questions? ;-)

---

