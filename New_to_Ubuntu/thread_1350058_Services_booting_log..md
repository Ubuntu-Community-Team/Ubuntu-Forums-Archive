---
title: "Services booting log."
date: 2009-12-08
forum: New to Ubuntu
---

### Post by nomad980 on 2009-12-08
I was wondering if there was a way to see if there were any errors with the services that are loading during boot? I read about bootlogd but that is disabled because it is causing issues/doesn't work.

---

### Post by wojox on 2009-12-09
```
dmesg > ~/boot.messages
```

**man dmesg**

> 
dmesg is used to examine or control the kernel ring buffer.

The program helps users to print out their bootup messages. Instead of copying the messages by hand, the
user need only:
dmesg > boot.messages
and mail the boot.messages file to whoever can debug their problem. 


---

### Post by nomad980 on 2009-12-10
Thanks, sadly that isn't showing me the services and if they are getting started or failing. I am trying to figure out why ushare and sabnzbd seem to never start up properly.

---

