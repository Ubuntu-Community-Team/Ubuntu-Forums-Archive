---
title: "Ubuntu must not like WUSB5S4GC very much..."
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by DJSpazz on 2008-04-07
[http://ubuntuforums.org/showthread.php?t=748071](http://ubuntuforums.org/showthread.php?t=748071)
I'm posting it in this forum because, upon taking a closer look at the hardware forum, it looks like a better place to put it...
Is there no way to get my Wireless Adapter working?
(Oh and it would nice if a mod would move my old thread here instead of me posting a link. xD)

---

### Post by dstew on 2008-04-08
I don't know about those scripts, but we can try to get it working by hand (meaning command line + brains).

To be sure which chipset you have, do **lsusb** and post the output. Also, let's see the current status of your ndiswrapper with```
ndiswrapper -l
ndiswrapper -v
```and the current status of your networks with```
ifconfig
iwconfig
```For good measure, check your kernel version```
uname -r
```This is just a starting point. Please post the outputs.

---

