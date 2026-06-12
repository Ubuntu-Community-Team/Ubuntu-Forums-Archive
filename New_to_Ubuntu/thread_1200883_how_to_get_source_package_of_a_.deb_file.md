---
title: "how to get source package of a .deb file"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by mangologin on 2009-06-30
Hi friends,
Am a novice to linux trying out packagin and related stuff...I want to download the source package(want to see the .dsc , orig.tar.gz and other files present) for a particular .deb package which i downloaded ...(eg:)picasa_2.7.3736-15_i386.deb

I tried to use the following command :

apt-get source picasa_2.7.3736-15_i386.deb

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for picasa_2.7.3736-15_i386.deb


Am basically unable to get the source package...Please help

---

### Post by mcduck on 2009-06-30
apt-get won't be able to download source code for any package you have downloaded yourself, only for those you got from repositories..

(and then then command would use the package name, not the file name of the .deb package)

---

