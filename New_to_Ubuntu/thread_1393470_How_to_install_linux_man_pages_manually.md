---
title: "How to install linux man pages manually?"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by jestinjoy on 2010-01-29
I tried some unix system program in Ubuntu 9.04(Which I installed using a CD). When I tried man mq_open, it says man page is not installed. I dont have Internet connectivity to my laptop.I have Ubuntu 9.04 cd with me. I want to know how could I install that man page manually.

---

### Post by blazemore on 2010-01-29
man pages are usually installed along with the package manager.
You can try running
```
sudo mandb
```

but other than that, it's likely no documentation was provided.

---

### Post by sisco311 on 2010-01-29
```
sudo apt-get install manpages-dev
```

---

### Post by jestinjoy on 2010-01-29
I have no net connection to my laptop. Then how could I do that

---

### Post by mechro on 2010-01-29
You can get the .deb file for manpages and manpages-dev from here...

[http://packages.ubuntu.com/karmic/doc/](http://packages.ubuntu.com/karmic/doc/)

Download it to your internet connected computer and transfer it to your laptop. Either add it to your apt source list or just right-click  and use Gdebi installer.

---

### Post by jestinjoy on 2010-02-05
Thanx. It worked:popcorn:

---

