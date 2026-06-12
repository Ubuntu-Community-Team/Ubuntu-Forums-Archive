---
title: "updates proplem of GNOME 3"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Mr.ALDO on 2011-05-13
so, when I updated to ubtuntu 11.4 I didn't like the interface very much but it was at least working well as it is supposed to and then came the new update that installed the new gnome 3 interface I liked it but now the updates doesn't install the new themes and panels.....that is the error
"

The following packages have unmet dependencies:

gnome-shell: Depends: gir1.2-mutter-3.0 (>= 3.0.0) but it is not installed
             Depends: libcamel1.2-19 (< 2.33) but 2.32.2-0ubuntu2 is installed
             Depends: libffi5 (>= 3.0.4) but 3.0.9-3ubuntu1 is installed
             Depends: libnspr4 (>= 4.7.0~1.9b1) but 4.8.7-0ubuntu1 is installed
             Depends: libnss3 (>= 3.12.2~rc1) but 3.12.9+ckbi-1.82-0ubuntu2 is installed
             Depends: libsqlite3-0 (>= 3.7.3) but 3.7.4-2ubuntu5 is installed
             Depends: libxfixes3 (>= 1:4.0.1) but 1:4.0.5-1ubuntu1 is installed
             Depends: gnome-themes-standard (>= 2.91) but it is not installed
"
so what should I do ?? the new GNOME is cool when I reviewed it online but can't stand it without themes it sucks...
sorry for my bad English :)
thanks for help :)

---

### Post by Mr.ALDO on 2011-05-14
any help ???

---

### Post by wildmanne39 on 2011-05-14
> **Mr.ALDO said:**
> any help ???

Hi, if you search on here there is a thread that deals with the extra themes that do not come with gnome 3 I have it marked I think but I have so many I will have to look through them you can probably find it faster.:D

---

### Post by wildmanne39 on 2011-05-14
> **Mr.ALDO said:**
> any help ???

Hi, I found the link.
[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

---

### Post by akand074 on 2011-05-14
Open up a Terminal window and try:

```
sudo apt-get install -f
```to try to fix your dependencies issue. You can also check out [this]("http://ubuntuforums.org/showthread.php?t=1742343") thread for common Gnome 3 issues/fixes.

---

### Post by Mr.ALDO on 2011-05-19
> **akand074 said:**
> Open up a Terminal window and try:

```
sudo apt-get install -f
```to try to fix your dependencies issue. You can also check out [this]("http://ubuntuforums.org/showthread.php?t=1742343") thread for common Gnome 3 issues/fixes.

aha I want to know how to fix the dependencies ? :)

---

