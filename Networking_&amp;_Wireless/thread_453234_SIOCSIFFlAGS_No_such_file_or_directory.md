---
title: "SIOCSIFFlAGS: No such file or directory"
date: 2007-05-24
forum: Networking &amp; Wireless
---

### Post by capogiro2002 on 2007-05-24
I've the error SIOCSIFFLAGS: No such file or directory when I launch the command: ifconfig eth1 up.

eth1=wirless integrated card

So I can't connect to wireless network.

HELP ME PLEASE!!!

---

### Post by spd106 on 2007-05-25
Check that the interface has the correct name with these commands
```
 cat /proc/net/wireless
```
```
cat /proc/net/dev
```

The /etc/iftab will allow you to assign persistent names to interfaces

---

