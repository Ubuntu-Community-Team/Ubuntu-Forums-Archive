---
title: "has anyone a for dummies description of INIT 1-6 runlevels?"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by honeybear on 2010-10-03
It is bit complicated. An init 2 is also repeated at halt or reboot. 

How to start a program at startup ? You send them into /etc/rcX.d with X a number of init?

---

### Post by lkraemer on 2010-10-05
REF:
[http://osfreaks.wordpress.com/2009/06/28/linux-run-levels/](http://osfreaks.wordpress.com/2009/06/28/linux-run-levels/)
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

[http://www.debian-administration.org/article/28/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/28/Making_scripts_run_at_boot_time_with_Debian)

[http://en.wikipedia.org/wiki/Run_level](http://en.wikipedia.org/wiki/Run_level)
[http://en.wikipedia.org/wiki/Init](http://en.wikipedia.org/wiki/Init)
[http://docs.hp.com/en/B2355-60103/init.1M.html](http://docs.hp.com/en/B2355-60103/init.1M.html)

lk

---

### Post by honeybear on 2010-10-05
> **lkraemer said:**
> REF:
[http://osfreaks.wordpress.com/2009/06/28/linux-run-levels/](http://osfreaks.wordpress.com/2009/06/28/linux-run-levels/)
[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

[http://www.debian-administration.org/article/28/Making_scripts_run_at_boot_time_with_Debian](http://www.debian-administration.org/article/28/Making_scripts_run_at_boot_time_with_Debian)

[http://en.wikipedia.org/wiki/Run_level](http://en.wikipedia.org/wiki/Run_level)
[http://en.wikipedia.org/wiki/Init](http://en.wikipedia.org/wiki/Init)
[http://docs.hp.com/en/B2355-60103/init.1M.html](http://docs.hp.com/en/B2355-60103/init.1M.html)

lk


well do you know if it possibel to start a script at boot (like rc2.d) and not to run it at shutdown or halt or reboot ?

thx

---

### Post by bodhi.zazen on 2010-10-05
init levels are depreciated, Ubuntu uses Upstart.

Before upstart init2 was the same as 3,4 and 5.

From your post it sounds as if you want to write an upstart (init) script.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

So yes, in general it is "trivial" to write an upstart script that will behave the way you wish.

---

