---
title: "performous"
date: 2009-06-28
forum: New to Ubuntu
---

### Post by bjhome on 2009-06-28
Can anybody tell me anything about 'performous download' it is a karaoke game similar to singstar for microsoft.
how do i know which one to download there are 3 to choose from
ubuntu 8.10 debi386 or
ubuntu 8.10 debami64 or
tar.bz2[/B]

---

### Post by lisati on 2009-06-28
One of the deb files will probably be easiest - choose the 32 or 64 according to whether you're using 32-bit or 64-bit Ubuntu.

---

### Post by Amilo1718 on 2009-06-28
1. do you have a 32 or a 64 bit system?
2. how do you want to install it?

---

### Post by bjhome on 2009-06-28
how can i tell whether i have 32 or 64 bit.where do i get this info from?

---

### Post by Amilo1718 on 2009-06-28
```
lshw
``` can tell you that

---

### Post by bjhome on 2009-06-28
i have 32 bit so does that mean i use the ubuntu 8.10 debi386.

---

### Post by Amilo1718 on 2009-06-28
or you can use the synaptic package manager ;)

---

### Post by bjhome on 2009-06-28
i have got an Error: Dependency is not satisfiable:libavcodec51

---

### Post by MasterProg on 2009-06-28
That means that package is not compatible with your version of Ubuntu or with Ubuntu itself.

Why don't you just
```
sudo apt-get install performous
```

---

