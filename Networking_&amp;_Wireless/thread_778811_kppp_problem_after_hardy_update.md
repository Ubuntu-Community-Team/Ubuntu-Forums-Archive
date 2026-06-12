---
title: "kppp problem after hardy update"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by rider_sss on 2008-05-02
I updated yesterday to hardy and kppp seems to be experiencing problems because my internet conection broke down. 

I use a sierra wireless ac 875u GRPS wireless device.

If I try to start kppp via the terminal I get the following:

```
seba@seba-laptop:~$ sudo kppp
[sudo] password for seba: 
Error: "/tmp/kde-sebaWPaeYc" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-seba9rOVpo" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-seba9rOVpo" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-sebaWPaeYc" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-seba" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-sebaWPaeYc" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-seba" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-seba" is owned by uid 1000 instead of uid 0.
Opener: received SetSecret
Opener: received SetSecret
Opener: received OpenLock

Opener: received OpenDevice
```

Somebody any idea ?? 

Thank you

---

### Post by dstew on 2008-05-02
Instead of sudo, use kdesudo.

---

