---
title: "Broadcom BCM4311/Ubuntu 13.04/Dell Latitude D620"
date: 2014-09-13
forum: Networking &amp; Wireless
---

### Post by chockopocko on 2014-09-13
After installing a bunch of software updates, I restarted my computer. It was then that my wireless internet connection stopped working. The software package *linux-firmware-nonfree* had my wireless working before.

```
sudo modprobe wl
``` returns
```
FATAL: module wl not found
```

Under Network on the top bar, under Wireless it says "device not ready (firmware missing)". 

Any help fixing my wifi would be much appreciated.

---

### Post by varunendra on 2014-09-14
The broadcom firmware has been removed (actually just disabled) from the linux-firmware-nonfree package.

Please see this bug report : [https://bugs.launchpad.net/bugs/1367882](https://bugs.launchpad.net/bugs/1367882)

The current way to install it (with a working internet connection through cable or other means) is -
```
sudo apt-get install firmware-b43-installer
```

Or, if there is no working internet connection, the manual way, something like : [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)

---

### Post by praseodym on 2014-09-14
Sure its 13.04? This one is outdated, as is 13.10. Please install 14.04 LTS

---

### Post by sheldon-corey on 2014-09-15
13.04 is not LTS but still supported by that package (firmware-b43-installer -- which goes back to 12.04 support wise)

---

