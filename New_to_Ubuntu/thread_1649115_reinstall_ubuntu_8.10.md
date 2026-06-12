---
title: "reinstall ubuntu 8.10?"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by operaytor on 2010-12-19
I had to reinstall ubuntu 8.10 and now I cannot get all the packages I 
need because of the support problem. My question is, is there any 
other sources which can be modified in the sources.list file to get back
all the packages. Also, is it possible to download all the packages as a
dvd/s image/s?

---

### Post by sandyd on 2010-12-19
> **operaytor said:**
> I had to reinstall ubuntu 8.10 and now I cannot get all the packages I 
need because of the support problem. My question is, is there any 
other sources which can be modified in the sources.list file to get back
all the packages. Also, is it possible to download all the packages as a
dvd/s image/s?
```

sudo nano /etc/apt/sources.list
```
Replace  all
[http://archive.ubuntu.com](http://archive.ubuntu.com)
with
[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)

---

### Post by beew on 2010-12-19
Why don't you just upgrade to 10.04 or 10.10? By "upgrade" I don't mean necessarily using the upgrade process in update manager to upgrade the OS, but simply getting a more up to date version (maybe via a fresh install). There is a reason why 8.10 is no longer supported.

---

### Post by waynefoutz on 2010-12-19
8.10 is dead. It's no longer supported and the repositories have been taken down.

---

