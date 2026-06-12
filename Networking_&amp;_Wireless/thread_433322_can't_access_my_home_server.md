---
title: "can't access my home server"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by stevieb on 2007-05-04
hello,

i have a dapper server at 192.168.1.10 that offers a directory as an NFS share to any computer on 192.168.1.*

i cannot get to this share from my dapper laptop with wireless networking, only when connected with a wire.

in addition, vncviewer only connects when my connection is wired, and i can only get to the printer attached to this computer with a wired connection.

any ideas?  what info do i need to post?

thanks,

-steve

---

### Post by stevieb on 2007-05-05
this seems weird to me, but after running these two commands:

```
ip a show
ip r show
```

everything works.  why?  what did those commands do?

-steve

---

