---
title: "only one software management tool allowed to be running at same time"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by sportscrazed2 on 2009-05-08
this stupid error keeps coming up when trying to install a deb file even though i just restarted so nothing else is running.  i never had this problem in intrepid what can be going on?

---

### Post by taurus on 2009-05-08
Look at the output of this command to see if you can detect adept or apt.  If you do, then you can't use dpkg to install anything else until you either kill that process first or wait for it to finish doing whatever it is doing in the background.

```
ps -A
```

---

### Post by sportscrazed2 on 2009-05-08
nope.and.now.my.space.bar.has.stopped.working.yet.again.man.jaunty.is.driving.me.crazy

---

### Post by sportscrazed2 on 2009-05-08
ok ran sudo dpkg --configure -a to fix it if anyone else gets this problem

---

