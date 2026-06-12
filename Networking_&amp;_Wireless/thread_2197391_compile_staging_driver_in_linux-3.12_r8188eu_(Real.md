---
title: "compile staging driver in linux-3.12: r8188eu (Realtek rtl8188eu ID 0bda:8179)"
date: 2014-01-03
forum: Networking &amp; Wireless
---

### Post by blaublatt on 2014-01-03
hi

i'm trying to get my TP-Link TL-WN725N-v2 to work with ubuntu 13.10 (kernel 3.12.0)

after finding [http://forum.ubuntuusers.de/topic/problem-mit-usb-adapter-tp-link-tl-wn725n-v2/#post-5536902](http://forum.ubuntuusers.de/topic/problem-mit-usb-adapter-tp-link-tl-wn725n-v2/#post-5536902) (in german) I tried installling the 8188eu driver with the instructions of various forums and github repos, but couldn't get it to work properly. (signal drops suddenly and timeout issues)
In one github issue on [https://github.com/lwfinger/rtl8188eu/issues](https://github.com/lwfinger/rtl8188eu/issues) (dont know exactly which one it was) it says the driver is now in the linux kernel as of version 3.12.
I checked the sources and found it in the staging dir (CONFIG_R8188EU=m) and activated it to compile as a module.

now how do i compile it?

problem is there is no linux-source-3.12 only a linux-source-3.11(which is obviously not what i want) 
how do i install linux-source-3.12 (its not inside apt  yet)

```
$uname -a
Linux lemen-l1 3.12.0-031200-generic #201311031935 SMP  Mon Nov 4 00:36:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by mörgæs on 2014-01-05
Hi, welcome to the fora.

Moving to Networking, hoping you will get more response here.

---

### Post by varunendra on 2014-01-05
> **blaublatt said:**
> it says the driver is now in the linux kernel as of version 3.12.
....
problem is there is no linux-source-3.12 only a linux-source-3.11(which is obviously not what i want)

You can directly download the latest available kernels and related headers in the form of .deb package from here : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

If installing the desired kernel (or a newer version) doesn't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by praseodym on 2014-01-05
Hi,

these are the githubs for:

12.04/12.10 (kernel 3.2 and 3.5)

git clone git://github.com/liwei/rpi-rtl8188eu.git

12.04/13.04 (Kernel 3.8) maybe also 3.11 (and 3.12?!)

[https://github.com/lwfinger/rtl8188eu](https://github.com/lwfinger/rtl8188eu)

---

### Post by chili555 on 2014-01-05
Once you get linux-headers and build-essential installed, I've outlined the process here: [http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o](http://askubuntu.com/questions/377470/tp-link-wn725n-unable-to-get-drivers-to-work-with-13-04-after-upgrade-worked-o)

---

