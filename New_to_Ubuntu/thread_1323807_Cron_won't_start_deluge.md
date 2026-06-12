---
title: "Cron won't start deluge"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by laffinet on 2009-11-12
Ahhh, this is driving me nuts. I used to start deluge from cron, but can't seem to be able to do it anymore.

This is my line in crontab:

```
40 17 * * * export DISPLAY=:0 && /usr/bin/deluge
```

I tried all kinds of combinations, DISPLAY:=0, DISPLAY:=0.0, deluge, /usr/bin/deluge, nothing works.

What's going on ?

---

### Post by DaithiF on 2009-11-12
works for me, is cron actually running?
```
/etc/init.d/cron status
```, or if you're on 9.10:
```
service cron status
```

and if so, then maybe add some logging to your crontab line:
```
40 17 * * * export DISPLAY=:0 && /usr/bin/deluge > /home/yourname/deluge.cron.log 2>&1

```
and see what turns up in the log file

---

### Post by coggins on 2009-11-12
Solution for me was in another thread:

[http://ubuntuforums.org/showthread.php?t=1293371](http://ubuntuforums.org/showthread.php?t=1293371)

---

### Post by laffinet on 2009-11-12
Success !

```
service cron status
```

returned

```
cron start/running, process 1233
```

so I guess cron was running.

I disabled acl by creating .xprofile and adding *xhost +local:*

Had to reboot (I guess restarting X would have sufficed) and then it worked.

Thanks a lot !

---

