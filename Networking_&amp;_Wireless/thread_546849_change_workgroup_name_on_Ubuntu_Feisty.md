---
title: "change workgroup name on Ubuntu Feisty"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by cccc on 2007-09-09
hi

howto change workgroup name on Ubuntu Feisty ?

---

### Post by MetalRampage on 2007-09-09
edit the smb.conf in your /etc/samba directory, there's a line something like workgroup = mshome or something like that, just change mshome to whatever you want

---

### Post by Zorael on 2007-09-09
And if you don't seem to have an /etc/samba directory, you need to:
```
$ sudo apt-get install samba smbfs
```

---

### Post by tripokey on 2007-09-09
Or the easy way:
System -> Administration -> Shared Folders

---

