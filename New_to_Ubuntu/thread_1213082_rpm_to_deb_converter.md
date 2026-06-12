---
title: "rpm to deb converter"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by navaneethan on 2009-07-14
Hi all i urgently need for rpm to deb converter

or deb to rpm converter

---

### Post by Ra-Hoor-Khuit on 2009-07-14
[http://kitenet.net/~joey/code/alien/]("http://www.howtoforge.com/converting_rpm_to_deb_with_alien")

---

### Post by SunnyRabbiera on 2009-07-14
Alien can do it, its commandline but it works.

---

### Post by RoestVrijStaal on 2009-07-14
I use alien for doing rpm to deb.
You can install it via synaptic.
You could better read the manual of alien by running ```
man alien
``` at the terminal.

---

### Post by Tibuda on 2009-07-14
alien is available as a [package]("apt:alien") in the ubuntu repos. after you install it, you run it from the terminal:
```
alien -k appname.rpm
```

---

### Post by SunnyRabbiera on 2009-07-14
> **danielrmt said:**
> alien is available as a [package]("apt:alien") in the ubuntu repos. after you install it, you run it from the terminal:
```
alien -k appname.rpm
```

actually in ubuntu its sudo alien appname.rpm, there is no real extra configuration rules to worry about as by default alien converts rpms into debs.

---

