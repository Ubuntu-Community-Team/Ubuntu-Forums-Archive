---
title: "How to install Linuxant ALSA on 10.10"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by huss11 on 2011-08-16
I accidentally deleted my sound drivers on ubuntu called Alsa drivers linuxant and I dont know how to reinstall it, heres everything you need to know about my computer : [http://www.alsa-project.org/db/?f=679ef49d52485ecc6608800783e0e2ef7f99e206](http://www.alsa-project.org/db/?f=679ef49d52485ecc6608800783e0e2ef7f99e206)

---

### Post by anieruddha on 2011-08-16
download latest stable from [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download).
then 

tar -xvf alsa-driver-xxxxx.gz
cd alsa-driver-xxxxx

Run this as root user
./configure && make && make install

---

