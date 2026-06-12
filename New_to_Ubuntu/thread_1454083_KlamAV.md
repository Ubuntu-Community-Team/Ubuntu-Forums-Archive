---
title: "KlamAV"
date: 2010-04-14
forum: New to Ubuntu
---

### Post by vivek40 on 2010-04-14
hii.. a few days back I had installed Klam AV on my system .. but yesterday I had uninstalled it.. however when i open the system monitor i can still see a process called clmad (username clamav) using a memoy of 90.5MB... why is it so and can someone please help with that

---

### Post by 3rdalbum on 2010-04-14
> **vivek40 said:**
> hii.. a few days back I had installed Klam AV on my system .. but yesterday I had uninstalled it.. however when i open the system monitor i can still see a process called clmad (username clamav) using a memoy of 90.5MB... why is it so and can someone please help with that

KlamAV is a "frontend" to Clamd; in other words, KlamAV gives you a graphical user interface to control the real virus scanner which is called Clamd.

When you installed KlamAV, it also automatically installed Clamd; but when you removed KlamAV it didn't remove Clamd (this is by design, because the system doesn't know if you still want Clamd for manual use, or if you've since installed another program that needs Clamd).

Clamd is provided by the "clamav-daemon" package, so you can safely remove that if you don't want it.

I don't know if 90 mebibytes is a big memory allocation for this program, if that's what you're asking.

---

