---
title: "errors in installing ndiswrapper"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by landegger on 2008-08-23
Following the instruction for installing ndiswrapper, but having errors please advise.  I am new to ubuntu.

Hearty Heron
PC



george@desktop:~$ cd Desktop/ndiswrapper-1.53
george@desktop:~/Desktop/ndiswrapper-1.53$ ls
AUTHORS    INSTALL           ndiswrapper.8     net8185n.cat  utils
ChangeLog  loadndisdriver.8  ndiswrapper.spec  README
driver     Makefile          net8185.inf       rtl8185.sys
george@desktop:~/Desktop/ndiswrapper-1.53$ make install
make -C driver install
make[1]: Entering directory `/home/george/Desktop/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-19-generic M=/home/george/Desktop/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
echo /lib/modules/2.6.24-19-generic/misc
/lib/modules/2.6.24-19-generic/misc
mkdir -p /lib/modules/2.6.24-19-generic/misc
mkdir: cannot create directory `/lib/modules/2.6.24-19-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/george/Desktop/ndiswrapper-1.53/driver'
make: *** [install] Error 2
george@desktop:~/Desktop/ndiswrapper-1.53$

---

### Post by Fergle on 2008-09-03
Make the command:
```
sudo make install
```

---

