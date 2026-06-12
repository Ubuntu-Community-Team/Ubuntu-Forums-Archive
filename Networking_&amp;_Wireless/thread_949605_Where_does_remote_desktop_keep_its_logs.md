---
title: "Where does remote desktop keep its logs?"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by guitarMan666 on 2008-10-16
Someone accessed m VNC server today (luckily i was logged in remotely at the time as well) I need to know where from so i can eliminate pranks or practical jokes on the part of some of may more tech savvy friends.

I keep it unsecured because of limitations in the viewing software i use (needless to say that will be changing).  All I've been able to figure out is that they are NOT kept in /var/log.  I would like an answer as quickly as possible.  It SERIOUSLY freaked me out (since it may also mean someone broke into my house to do this if I am the only entry in the log).
Thanks!

---

### Post by iponeverything on 2008-10-16
look here:

```
cd ~/.vnc
```

or maybe here:
```

/var/log/x11vnc.log

```


if all else fails:
```

lsof |grep vnc|grep log
```

---

### Post by guitarMan666 on 2008-10-16
All of those failed.  I guess vino doesn't keep a log of users.  Are there any more general network activity logs that might indicate who accesed my computer and at what time?

---

