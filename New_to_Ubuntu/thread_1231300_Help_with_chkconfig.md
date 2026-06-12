---
title: "Help with chkconfig"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by SteelCore on 2009-08-04
I doing a lab exercise with chkconfig on Ubuntu
before I started the umountfs runlevels were as follows:
```
umountfs                  0:on  1:off  2:off  3:off  4:off  5:off  6:off
```
then I swiched the 0 level off using:
```
chkconfig --level 0 umountfs off
```
the problem is that I'm not able to switch the value to on again

---

### Post by wizard10000 on 2009-08-04
> **SteelCore said:**
> I doing a lab exercise with chkconfig on Ubuntu
before I started the umountfs runlevels were as follows:
```
umountfs                  0:on  1:off  2:off  3:off  4:off  5:off  6:off
```
then I swiched the 0 level off using:
```
chkconfig --level 0 umountfs off
```
the problem is that I'm not able to switch the value to on again

There's a much easier way to do this.  Rather than use chkconfig try using sysv-rc-conf.  Much nicer interface.

---

