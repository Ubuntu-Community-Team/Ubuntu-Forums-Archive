---
title: "Why can't I install build-essential from cdrom?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by itguy1985 on 2011-05-16
Don't have an internet connection until I compile driver, but when I try to install build package it say there are unmet dependencies. Why wouldn't the dependencies be on the disk too? It let install make and gcc-4.5 so I know the apt-cdrom is working.

---

### Post by wojox on 2011-05-16
Because the packages have [packages.]("http://packages.ubuntu.com/natty/build-essential")

---

### Post by Sef on 2011-05-16
> Don't have an internet connection until I compile driver, but when I try to install build package it say there are unmet dependencies. Why wouldn't the dependencies be on the disk too? It let install make and gcc-4.5 so I know the apt-cdrom is working.

It might be on the alternate cd, but if not, then you would have to find a computer with internet access and go to the [packages site]("http://packages.ubuntu.com"), and download everything needed and the dependencies too.

---

### Post by itguy1985 on 2011-05-17
got it working thanks.

---

