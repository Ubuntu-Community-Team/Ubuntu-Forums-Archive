---
title: "Error question"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by The Eight-Bit Link on 2009-11-30
What does this mean? I tried to install gettext for some tool for gedit
PS:   Is there a much easier way to install gedit?
In function 'open',
    inlined from 'msgdomain_list_print' at write-catalog.c:223:
/usr/include/bits/fcntl2.h:51: error: call to '__open_missing_mode' declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[3]: *** [write-catalog.lo] Error 1
make[3]: Leaving directory `/home/jd/gettext-0.17/gettext-tools/src'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/jd/gettext-0.17/gettext-tools/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jd/gettext-0.17/gettext-tools'
make: *** [install-recursive] Error 1

---

### Post by KIAaze on 2009-11-30
> **The Eight-Bit Link said:**
> 
PS:   Is there a much easier way to install gedit?


```
sudo apt-get install gedit
```
?

By the way, I believe gedit is installed by default under Ubuntu. It's the default text editor.

What tool are you trying to install for gedit?

---

### Post by The Eight-Bit Link on 2009-11-30
its 9.10 xubuntu so it's stripped down.
When I try to get the package it says
E: Couldn't find package gedit

---

### Post by KIAaze on 2009-11-30
Could you please post the contents of /etc/apt/sources.list ?

---

### Post by Geoff918 on 2009-11-30
Mousepad is the default editor in Xfce.

I don't think it would be difficult to retrieve gedit, though. Shoudl be in the repos

[http://packages.ubuntu.com/karmic/gedit](http://packages.ubuntu.com/karmic/gedit)

that has d/l link (for 9.10 or equivalent) you can do a search for earlier distros if you're on one of them.

---

