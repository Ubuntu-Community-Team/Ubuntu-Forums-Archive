---
title: "UPSTART confusion"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by kalimojo on 2011-07-06
im running 11.04 . i am very confused about upstart and sysvinit. my system seems to have both installed. does 11.04 still use sysvinit style scripts or is it totally converted to upstart ?

---

### Post by dFlyer on 2011-07-06
I believe everything has been converted to upstart, but maybe someone with more knowledge and give a better answer.

---

### Post by sisco311 on 2011-07-06
> **kalimojo said:**
> im running 11.04 . i am very confused about upstart and sysvinit. my system seems to have both installed. does 11.04 still use sysvinit style scripts or is it totally converted to upstart ?

Only Upstart is installed, but Upstart is able to run sysvinit scripts unmodified.

A lot of services use native Upstart jobs, but some services still use system V style init scripts.

The [Wikipedia]("http://en.wikipedia.org/wiki/Upstart") page is quite accurate.

---

### Post by kalimojo on 2011-07-07
does that mean rcconf is still supported ?

---

