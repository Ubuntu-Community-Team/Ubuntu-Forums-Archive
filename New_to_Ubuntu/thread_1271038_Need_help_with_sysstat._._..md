---
title: "Need help with sysstat. . ."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-09-20
Hi!  I am trying to get sysstat setup on my server so that I don't have to use:

```
top d 1 | tee /home/travis/top.log
```

But I can't seem to make sense of the man pages, or the website.  What I want to achieve is a log file somewhere that lists the CPU usage, memory usage, system load, and basic things like that for every minute of system operation.  How might I go about doing this?  Any advice would be greatly appreciated.

Thanks in advance!

---

### Post by RealPSL on 2009-09-20
Did you install the sysstat package with ```
apt-get install sysstat
```? It will automatically start logging after that. You would then use the sar command e.g. ```
sar -u sar01
``` would give you information about CPU usage for that day.

---

