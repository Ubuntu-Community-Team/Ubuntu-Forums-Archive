---
title: "installing python 3 - synaptic won't update"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by imtheshade on 2009-07-20
Hi! I installed ubuntu ultimate edition and I am trying to install python 3 on it but synaptic won't update..  I get this error message:


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

```
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz: 404 Not Found
http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-backports/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://repoubuntusoftware.info/dists/feisty/all/binary-i386/Packages.gz: 404 Not Found
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: 404 Not Found [IP: 91.189.88.31 80]
```

P.S.: my internet connection works just fine, I am posting this from ubuntu, using firefox.

---

### Post by bandgeek on 2009-07-20
If I'm correct Ultimate Edition has it's own repositories?

---

### Post by OffAxis on 2009-07-20
That install disc of yours is a little dated...
It's looking for a feisty repository, and feisty may have run it's course (it was released May of 2007).
Try upgrading to version 2.2, which is jaunty based.

---

### Post by imtheshade on 2009-07-21
How do I upgrade it ?

---

### Post by OffAxis on 2009-07-21
The kindest (and probably fastest) way would be to download a new liveDVD from the torrents, burn the iso, and install new.

[http://ultimateedition.info/ultimate-edition-2-2/](http://ultimateedition.info/ultimate-edition-2-2/)

---

### Post by imtheshade on 2009-07-24
Fixed. I installed ultimate edition 2.2 and now I can find and install python 3

---

