---
title: "need old esd.conf code for ubuntu 8.04"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by carrierpilot1357 on 2009-04-18
I changed etc/esound/esd.conf completely to try and get znes sound to work and now I cant use the volume change button on my keyboard. can anyone paste the original file code on here for me so I can fix it? I cant find it anywhere on the web.:(

---

### Post by Yashiro on 2009-04-18
```
[esd]
# autospawning is not recommended, since it can't really be done
# right.  If you want your login session to be using a sound daemon,
# you should start it from the session controller, not some random
# app inside.
auto_spawn=0
spawn_options=-terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
That's a default esd.conf.

---

### Post by carrierpilot1357 on 2009-04-18
thanks alot!

---

