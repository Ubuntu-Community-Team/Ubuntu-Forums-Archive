---
title: "unstable ubuntu"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by EvilBro on 2009-07-06
lately I am experiencing a lot of programs segfaulting on me. I already did a memcheck and it gave no errors. In the logs I see things like this:

Jul  6 21:29:58 evilbro-desktop kernel: [ 3755.883303] nm-applet[3348]: segfault at 357fdfff ip 357fdfff sp bf8f8d5c error 4 in SYSV00000000 (deleted)[b6d76000+60000]
Jul  6 21:31:28 evilbro-desktop kernel: [ 3846.141585] evolution[6134]: segfault at ddffcbff ip b6aa3902 sp bf982850 error 5 in libgobject-2.0.so.0.2000.1[b6a7e000+3c000]

I was wondering the following things:

1. What is the (deleted) about?
2. Errors seems to be often in things like libgobject. Is there a way to use apt-get to reinstall this package?

---

### Post by Tibuda on 2009-07-06
> **EvilBro said:**
> 2. Errors seems to be often in things like libgobject. Is there a way to use apt-get to reinstall this package?
libgobject is on the libglib2.0-0 package. Try
```
sudo apt-get install --reinstall libglib2.0-0
```

---

### Post by EvilBro on 2009-07-07
> **danielrmt said:**
> libgobject is on the libglib2.0-0 package.
I was wondering how I could discover this myself? (In case I ever want/need to in the future.)

---

