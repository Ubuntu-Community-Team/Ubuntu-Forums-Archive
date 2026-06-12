---
title: "PS3 Ubuntu Resolution issues"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Rike Maverty on 2009-01-25
Hey everybody

COMPLETE Lixux/Ubuntu novice here.  Just trying to dink around with it on my PS3.

So I installed Ubuntu 7.10 last night on my PS3, but haven't been able to get the resolution up to 720p.  When I tried to add```
video=ps3fb:mode:3
``` to etc/kboot.conf, it told me that it couldn't edit the file because it is a read-only file system.  What?!?!?

Any and all help is appreciated -- please remember that what might seem like basic knowledge to you is probably way over my head, so detailed explanations and step-by-step instructions are helpful!

I'm learning, though!

---

### Post by anjilslaire on 2009-01-25
```

sudo gedit etc/kboot.conf

```

or 

```

sudo kate etc/kboot.conf

```

as appropriate

---

### Post by Rike Maverty on 2009-01-25
Thanks for your help.

When I try sudo gedit, it says "Cannot open display"
With sudo kate, it says "command not found".

I was able to access the etc/kboot.conf file using sudo nano, but when I try to save the changes, it tells me that the filesystem is read-only.  I don't see how this is possible if I correctly installed Ubuntu onto my PS3's HDD.

It also mentions "read-only" a lot when booting up Ubuntu from kboot.  I just can't wrap my head around it.

Thanks again!

---

