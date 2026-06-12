---
title: "rt2570 drivers wont compile on ubuntu 7.10"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by colinireland on 2007-12-15
I am getting an error message when I try to install the rt2570 drivers.

# cd ~/Desktop/rt2570-k2wrlz-1.3.0/Module
# make
# make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.o
/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.c: In function ‘usb_rtusb_probe’:
/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.c:1829: error: ‘dev_base’ undeclared (first use in this function)
/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.c:1829: error: (Each undeclared identifier is reported only once
/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.c:1829: error: for each function it appears in.)
/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.c:1829: error: ‘struct net_device’ has no member named ‘next’
make[2]: *** [/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module/rtusb_main.o] Error 1
make[1]: *** [_module_/home/colin/Desktop/rt2570-k2wrlz-1.3.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
rt2570.ko failed to build!
make: *** [module] Error 1
# ~/Desktop/rt2570-k2wrlz-1.3.0/Module# 

I have seen that there are alot of people with various problems installing these drivers but I have not found any posts that can help me. If any one knows how to sort this out I would greatly appreciate it

Colin

---

### Post by rustybronco on 2007-12-15
Try this post [http://ubuntuforums.org/showpost.php?p=3609183&postcount=1](http://ubuntuforums.org/showpost.php?p=3609183&postcount=1)

---

### Post by colinireland on 2007-12-16
worked a treat.
Thanks for the help

---

### Post by rustybronco on 2007-12-17
Yes that one works just about all the time, glad it did again.

---

