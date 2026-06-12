---
title: "Mounting (/etc/exports)"
date: 2010-10-28
forum: New to Ubuntu
---

### Post by theunionstreet on 2010-10-28
Hello,
   I have a server up and running on Ubuntu Server 10.10. Everything is working great but I want to be able to mount my network as a drive so I can simply drag and drop files in I'm away from home. Any ideas?

Thanks,
Adam

---

### Post by cariboo on 2010-10-28
I'm not exactly sure what it is you want to do, but I have a couple of system that mount nfs shares using fstab. this is what the entry looks like:

```
willy:/media/music	/media/music	nfs	rw,hard,intr	0	0
```

In the above example, willy is the name of the server, I aliased the ip address to the name in /etc/hosts. Using the above example the share is mounted at boot, and always accessible.

---

### Post by theunionstreet on 2010-10-28
Let's say i'm at school with my laptop (running mac os x). Is there a way to just go up to Go->Connect to Server... and then connect to my home server (and just have it show up on my desktop like a network drive) and drop files on it. I want to be able to do this without using a WinSCP-like kind of program. Currently I can't figure it out but I can SSH to it and I can view it via Apache through my browser no problem.

---

