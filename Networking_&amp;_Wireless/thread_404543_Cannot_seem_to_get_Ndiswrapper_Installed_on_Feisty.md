---
title: "Cannot seem to get Ndiswrapper Installed on Feisty Fawn"
date: 2007-04-08
forum: Networking &amp; Wireless
---

### Post by Fenrirwulf on 2007-04-08
I tried to install using Synaptic and then when I try to run ndiswrapper -l to see the drivers I get a message saying that no version of ndiswrapper can be found. I uninstalled them and then installed version 1.41.

fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ sudo make
make -C driver
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
Building modules, stage 2.
MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C utils
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ sudo make install
make -C driver install
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C /lib/modules/2.6.20-14-generic/build SUBDIRS=/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-14-generic'
Building modules, stage 2.
MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-14-generic'
echo /lib/modules/2.6.20-14-generic/misc
/lib/modules/2.6.20-14-generic/misc
mkdir -p /lib/modules/2.6.20-14-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.20-14-generic/misc
/sbin/depmod -a 2.6.20-14-generic -b /
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/driver'
make -C utils install
make[1]: Entering directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/fenrirwulf/Desktop/ndiswrapper-1.41/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$ ndiswrapper -l
ls: /etc/ndiswrapper: No such file or directory
fenrirwulf@Fenris:~/Desktop/ndiswrapper-1.41$


I'm not sure what to do now. Any help would be appreciated. I am a Linux newb and only have a little experience with Freespire prior to this. Thanks!

---

### Post by Floppyjoe on 2007-04-08
This is a link to a tutorial on installing the latest ndiswrapper:
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

