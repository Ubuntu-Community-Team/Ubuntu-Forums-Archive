---
title: "How do I install a karmic package in jaunty?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-18
Hi there,

I would like to be able to install [this package]("https://launchpad.net/ubuntu/karmic/+source/fglrx-installer/2:8.660-0ubuntu1") on my jaunty laptop to fix [this bug.]("https://bugs.launchpad.net/bugs/423711")

How do I do this?

---

### Post by zvacet on 2009-09-18
Edit source list with 

```
gksudo gedit /etc/apt/sources.list
```

add line

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

save and close file.

```
sudo apt-get update
```

Install package you need and after that edit your source list again and make karmic repo look like this

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted

That is good to do because it is not good idea to have mixed repos.

---

