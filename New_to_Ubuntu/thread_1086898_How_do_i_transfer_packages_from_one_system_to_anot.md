---
title: "How do i transfer packages from one system to another"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-03-04
hi,

one of my machines has access to internet(using apt-get).. so i download some packages using it.. now i want to take those packages to other system(which does not have internet access) and install them there.....

how do i do that...
please help

---

### Post by Titan8990 on 2009-03-04
Using the dpkg command. Make sure you grab all the dependencies too.

Example:


sudo dpkg -i mydeb.deb

---

### Post by taurus on 2009-03-04
[http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html](http://onlyubuntu.blogspot.com/2007/04/create-backup-of-installed-packages.html)

---

### Post by albandy on 2009-03-04
the packages are downloaded to /var/cache/apt/archives
to install a package "sudo dpkg -i package-file.deb"

---

### Post by anubhavrocks on 2009-03-04
You can also set up some thing like apt-cacher.

---

### Post by avtolle on 2009-03-04
Take a look at AptonCD: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) which does, I believe (I've not used it) what you want to do.

---

