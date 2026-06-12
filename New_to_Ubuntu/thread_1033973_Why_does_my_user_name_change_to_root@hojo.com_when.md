---
title: "Why does my user name change to root@hojo.com when I use sudo -i"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by amvmr on 2009-01-07
Why does my user name change to [email]root@hojo.com[/email] when I use sudo -i?

First time installer but as I recall when I used [email]hojo@hojo.com[/email]$ sudo -i before I got [email]hojo@hojo.com[/email]# but reciently something changed and now [email]hojo@hojo.com[/email] sudo -i changes to [email]root@hojo.com[/email]. This seems suspect?

---

### Post by Bucky Ball on 2009-01-07
su = superuser; do = do

sudo = superuser do

This changes you to root for the command, not permanently (safer that way). :)

... and no, nothing suspect. That is the way it should be. Don't know what was happening before ...

---

### Post by Frak on 2009-01-07
It should be OK. It shouldn't have any ill-effects on use.

---

### Post by iaculallad on 2009-01-07
For complete info on sudo's switches, issue the command below on your terminal:

```
man sudo
```

---

