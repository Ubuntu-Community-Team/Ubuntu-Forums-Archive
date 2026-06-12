---
title: "how can I boot to safe graphics mode automatically in 10.04?"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by jernord on 2010-06-04
Hi,
I have just installed 10.04 on a LG LS50a. It only seems to work properly when I boot it into safe mode. This is fine as I only need this machine for surfing and the like. How can set it to automatically boot to failsafe graphics mode? 

Many Thanks!
Jeremy

---

### Post by cariboo on 2010-06-04
Why not fix the problem instead of trying to work around it. have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1488699"), the solution to your problem is there

---

### Post by wojox on 2010-06-04
You could also try resetting the xorg.conf file:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

