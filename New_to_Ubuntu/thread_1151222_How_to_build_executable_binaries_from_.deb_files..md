---
title: "How to build executable binaries from .deb files."
date: 2009-05-06
forum: New to Ubuntu
---

### Post by firebirdworks on 2009-05-06
So here is the deal, I don't have the ability to install a piece of software that I need as root (as I can't login as root).

I would like to build a binary file that I can just copy to the computer and run without being root.

PS:  It is CentOS, if that makes a difference.

---

### Post by mick8985 on 2009-05-06
Just open the deb in archive manager the open data.tar.gz and extract the binary files you need, you'll need to put any libraries in correct relative folders.

---

### Post by mick8985 on 2009-05-06
dependencies could be an issue though

---

### Post by blueridgedog on 2009-05-06
Alternatively, you could ask the system admin (root account holder) to install the software and I submit that that is the intent of a multi user system.

---

