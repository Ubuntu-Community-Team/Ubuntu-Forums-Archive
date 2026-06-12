---
title: "apt-file syntax question: how to find a program?"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by ginestre on 2010-02-08
Can anyone tell what I've missed on this command, and why it isn't working?

```
apt-file /etc/apt/sources.list find includepdf.*
```


I'm trying to find the file includepdf from wherever in the repositories it is lurking, for my lyx/TEX installation. It is in some TEX package somewhere- but which? I believe this apt-file thingie is the right command, and I think the syntax above is right. But it ain't working!

TIA, as always.

---

### Post by nhasian on 2010-02-08
its not installed by default, but when i did an apt-cache search it said:

> $ apt-cache search apt-file
apt-file - search for files within Debian packages (command-line interface)

after its installed, did you try:

```
man apt-file
```

also i found:

[http://www.debuntu.org/how-to-find-missing-packages-with-apt-file](http://www.debuntu.org/how-to-find-missing-packages-with-apt-file)

---

### Post by ginestre on 2010-02-08
thanks for the reply, nhasian. Yes, I've both installed apt-file and updated its lists. The page you poinbted me tois useful, but I still get a null result when I run the search with this (corrected) enquiry

apt-file -v find includepdf.*

Does that just mean the file doesn't exist anywhere, or am I missing something?

---

