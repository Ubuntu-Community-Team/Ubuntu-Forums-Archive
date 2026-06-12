---
title: "Samba share disk usage limit"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Tim.R on 2006-08-12
Currently I've got a shared folder "/home/shared/" which has global read/write permission.  It's shared using samba, with guest login enabled (where guest is linked to nobody:nogroup).  I assume this isn't too unsafe, considering I've disallowed the following of symbolic links, so they presumably will only be able to access that folder.

I was wondering if it's possible to set a maximum size of this folder (say 500MB or so) to limit the amount of incoming data allowed.

Also, as a side issues, is it possible to change the text that's displayed when you log in to a shell, for instance in SSH?  The Ubuntu warranty one isn't all that friendly.

---

