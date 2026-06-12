---
title: "Apt-get install not working"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by Axilus on 2010-03-16
Hey,

I am currently trying to install emerillon onto Ubuntu 9.10 however everything seems to be going well until I get these error messages.

```
 Depends: libethos-1.0-0 (>=0.1.0-0) but it is not installable
 Depends: libethos-ui-1.0-0 (>=0.2.1-0+git206-1~karmic0) but it is not installable
```

Does any one know how to fix this?

Cheers

---

### Post by n0dix on 2010-03-16
here's an interesting [link]("http://blog.cyphermox.net/2009/10/debianubuntu-package-for-emerillon.html").

---

### Post by GO%)$@*1 on 2010-03-16
OK you might not be able to install the dependencies from apt (or at all)... but here are a few things you can try...

```
sudo apt-get --fix-broken
sudo apt-get --build-dep
sudo apt-get check
```

---

### Post by mc4man on 2010-03-17
I'm thinking that  you're trying to install from this ppa..?
[https://launchpad.net/~mathieu-tl/+archive/emerillon/+packages](https://launchpad.net/~mathieu-tl/+archive/emerillon/+packages)

If so, while there is a karmic build of emerillon, none of the deps needed have been built or still available in the ppa. So the karmic build is somewhat worthless. 

The ppa seems at this point to be geared towards lucid with all the packages built.

---

### Post by Axilus on 2010-04-28
Thank you for the link, the download worked with no problems.

---

