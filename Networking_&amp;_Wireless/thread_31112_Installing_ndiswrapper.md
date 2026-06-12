---
title: "Installing ndiswrapper"
date: 2005-05-01
forum: Networking &amp; Wireless
---

### Post by Minnie000 on 2005-05-01
I've tried this a number of different ways and cannot get ndiswrapper installed.
I've installed the kernel headers and source from synaptics and downloaded the source for ndiswrapper.
Here's the error.

```
Can't find kernel sources in /lib/modules/2.6.10-5-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[2]: *** [prereq_check] Error 1
make[2]: Leaving directory `/usr/src/ndiswrapper-1.1/driver'
make[1]: *** [build-modules] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.1'
make: *** [binary] Error 2
``` 

Can somebody please help?  Thanks!!

---

### Post by Xerampelinae on 2005-05-02
```
 ln -s /usr/src/linux-source-2.6.10-5.386 /lib/modules/2.6.10-5-386/build
```

or something like that...

---

### Post by Hieronymus on 2005-05-02
Goto the Synaptic Packages Manager (system>>administration>>synaptic packages manager) search for "linux" and it will find the linux-headers-your_arch. select to install and install. now it should work just fine.

---

