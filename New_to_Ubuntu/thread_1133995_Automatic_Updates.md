---
title: "Automatic Updates"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Howgil on 2009-04-23
Running Ubuntu 8.04.2.  Clicked on Update Available Icon and Install Updates as I have done many times before.  System froze part way through update.  Restarted computer.  Tried to update again.  Received following msg:

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem
E: _cache->open()failed,please report

I've tried in Terminal to enter the right command, but keep getting "syntax error near unexpected token'('.

Obviously, I'm not entering the right command or commands.  Please help.

System Info:

Intel p4, 1.70 gig, 1 gig RAM
Dual boot with Win XP3

Thanks.

---

### Post by anjilslaire on 2009-04-23
```

sudo dpkg **--configure** -a

```

I believe

---

### Post by tofiluk on 2009-04-23
what exactly are the things that you typed in the terminal?

> **Howgil said:**
> Running Ubuntu 8.04.2.  Clicked on Update Available Icon and Install Updates as I have done many times before.  System froze part way through update.  Restarted computer.  Tried to update again.  Received following msg:

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem
E: _cache->open()failed,please report

I've tried in Terminal to enter the right command, but keep getting "syntax error near unexpected token'('.

Obviously, I'm not entering the right command or commands.  Please help.

System Info:

Intel p4, 1.70 gig, 1 gig RAM
Dual boot with Win XP3

Thanks.

---

### Post by tofiluk on 2009-04-23
> **anjilslaire said:**
> ```

sudo dpkg **--configure** -a

```

I believe

this is the point that im trying to say. hahahaha...

---

### Post by Howgil on 2009-04-23
I entered:

sudo dpkg --configure -a

Got the following:

dpkg: error processing xulrunner -1.9 (--configure):
Package is in a very bad inconsistent state - you should reinstall it before reconfiguration.
dpkg: dependency problems prevent configuration of xulrunner -1.9-gnome-support:
xul runner -1.9-gnome-support depends on xulrunner-1.9 (=1.9.0.9+nobinonly-0ubuntu).8.04.1); however
Version of xulrunner-1.9 on system is 1.9.0.8+nobinonly-0ubuntu0.8.04.1
dpkg: error processing xulrunner-1.9-gnome-support (-- configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
xulrunner-1.9
xulrunner-1.9-gnome-support

Ideas?

Thanks.

---

