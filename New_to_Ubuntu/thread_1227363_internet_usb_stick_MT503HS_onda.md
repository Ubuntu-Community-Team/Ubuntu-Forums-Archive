---
title: "internet usb stick MT503HS onda"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by shaheru on 2009-07-30
Hello,
I would like to access internet with an internet usb stick MT503HS from Alice mobile.
Following the installation guide, I launch "make" from the directory and obtain this errror message:


valerio@valerio:linuxdriveronda1.0.1$ ls
install.sh  Makefile  onda.c  uninstall.sh
valerio@valerio:linuxdriveronda1.0.1$ make
make -C /lib/modules/2.6.24-24-generic/build M=/home/valerio/software/Software Alice MOBILE/linuxdriveronda1.0.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
make[1]: *** No rule to make target `Alice'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make: *** [modules] Error 2
valerio@valerio:linuxdriveronda1.0.1$ 

I don' t if I have to install other things to be able to run this "make" to be able to use this interent usb key.

Tank you for your answer!

---

### Post by mikechant on 2009-07-31
I guess you probably need quotes around the path name because it has spaces in it:
```
make -C /lib/modules/2.6.24-24-generic/build M="/home/valerio/software/Software Alice MOBILE/linuxdriveronda1.0.1" modules
```

---

