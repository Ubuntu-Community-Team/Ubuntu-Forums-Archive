---
title: "nvidia module on 10.04.3 LTS w/ backported natty kernel"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by ptn107 on 2011-07-28
I've installed the provided back-ported natty kernel (along with headers) on 10.04.3 LTS via the following packages:

linux-image-generic-lts-backport-natty
linux-image-2.6.38-10-generic
linux-headers-generic-lts-backport-natty
linux-headers-2.6.38-10
linux-headers-2.6.38-10-generic

The problem is that I can't get the nvidia module to install for some reason, via dkms or manually.  These are all the proper Ubuntu provided packages so I assume this should have been before the back-ported kernel was released?  Anyone else have trouble or can help me out.  The build log output is here _[http://paste.ubuntu.com/653911/](http://paste.ubuntu.com/653911/)_

Right now I'm back to running the nvidia module (nvidia-current 195.36.24-0ubuntu1~10.04) on the latest stable LTS kernel 2.6.32-33 until anyone can help me find a solution.

---

### Post by ptn107 on 2011-08-02
bump

---

