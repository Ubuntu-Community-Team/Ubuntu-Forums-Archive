---
title: "dpkg vs apt-get"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by el_diablo on 2011-02-09
[SIZE=3]hi
i recently installed a package using dpkg,n I was able to delete it  using apt manager.
Can anyone plz tell me the difference between these two.can i delete package of apt from dpkg?which is better to use???[/SIZE]

---

### Post by mcduck on 2011-02-09
Both tools are part of the same package management system

Dpkg is what installs .deb packages and maintains information about the installed packages on your system.

Apt-get handles information about packages available in the Internet repositories, and downloading of the packages. It then uses dpkg to install them.

So when it comes to uninstalling something, there's no difference if you use apt-get, dpkg, Synaptic Package Manager or the Ubuntu Software Center. They all all parts of the same system.

(Installing a package is of course a bit different, since dpkg assumes you already have the package on your system, while apt-get assume you want it to download it for you.s)

---

