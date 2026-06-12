---
title: "sudo apt-get install -f"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by thunderstruck959 on 2009-07-15
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 190416 files and directories currently installed.)
Preparing to replace sun-java6-jdk 6-13-1 (using .../sun-java6-jdk_6-14-0ubuntu1.9.04_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6-14-0ubuntu1.9.04_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java6-bin 6-13-1 (using .../sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java6-jre 6-13-1 (using .../sun-java6-jre_6-14-0ubuntu1.9.04_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-14-0ubuntu1.9.04_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jdk_6-14-0ubuntu1.9.04_i386.deb
 /var/cache/apt/archives/sun-java6-bin_6-14-0ubuntu1.9.04_i386.deb
 /var/cache/apt/archives/sun-java6-jre_6-14-0ubuntu1.9.04_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


This is what I got when I went into the terminal  to see if I could install java, I know java is broken, because I just went in the synaptic package manager, and it said to use the broken filter to locate it, or something along those lines, problem is, I can't, do not know how to fix it, and would like some help:/

---

### Post by philinux on 2009-07-15
Make sure synaptic is not running at the same time. Or reboot the try your command again.

---

### Post by thunderstruck959 on 2009-07-15
thanks, I was about 10 minutes away from re-installing ubuntu but figured i'd give this a shot, working great now, thanks again:D

---

