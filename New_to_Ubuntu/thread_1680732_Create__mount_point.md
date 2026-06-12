---
title: "Create  mount point"
date: 2011-02-03
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-02-03
Initially i don't have cd drive. After installing OS i had a work with CD drive, so that i connected CD drive. but  after connectin, it shows that "unable to mount".

how could i create mount point for cd drive?

Kindly reply............

---

### Post by HermanAB on 2011-02-03
Have a look at the kernel error messages with 'dmesg'.  Also look at /dev:

$ dmesg
$ ls /dev

and look for /dev/cdrom.  

Report here what you found and someone may be able to assist.

---

