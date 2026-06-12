---
title: "mount cifs ISO-8859-1 problem"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by mindless1973 on 2008-11-27
Hi,

I try to mount an SMB share (based on a NAS box using SAMBA 3.0.4) with ISO 8859-1 charset:

-o iocharset=iso-8859-1

but unfortually, I get the following error message:

mount error 79 = Can not access a needed shared library
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

any help highly appreciated!

Thanks

bye
Marcus.

---

### Post by CHaoSlayeR on 2009-02-05
Hi there,

I also have this problem. There is no library mentioned in the man page so either the error message is wrong or the man page is incomplete.

On the other hand Dolphin from KDE4 displays all paths correctly and they are accessible too. So I wonder what Dolphin does to accomplish that.

Anyway, we need help on that!

C]-[aoZ

---

### Post by CHaoSlayeR on 2009-02-05
OK, the error message is misleading.

Try the following:
```
-o iocharset=iso8859-1
```

But in most cases (as long as the windows system is at least windows 2000 or newer) you should be good to go with utf8:
```
-o iocharset=utf8
```

This worked for me. :-)

C]-[aoZ

---

### Post by ladanz on 2010-05-31
-o iocharset=utf8

worked perfectly, thanks!

---

