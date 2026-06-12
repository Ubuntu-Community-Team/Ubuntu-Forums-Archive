---
title: "Netatalk and permissions for .AppleDB"
date: 2015-02-17
forum: Networking &amp; Wireless
---

### Post by wripet on 2015-02-17
I am using netatalk on a ubuntu server and access its AFP-shares from a Mac. Everytime I access the server, those DB-files are being created in .AppleDB, .AppleDouble, and so on, there are plenty of those directories. I know it is part of the way netatalk works, but why are the permissions of those directories set so strangely? I access them as the user main, but the .AppleDB directories for instance are created with the owner root. How can I change this? My current AppleVolumes.default has an entry like

```
/media/Disk "Share" allow:main dperm:0777 fperm:0777
```

Thanks!

---

