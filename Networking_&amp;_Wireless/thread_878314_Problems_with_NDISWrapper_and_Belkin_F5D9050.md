---
title: "Problems with NDISWrapper and Belkin F5D9050"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by eheldreth on 2008-08-02
I'm helping a friend set up Ubuntu on his desktop.  He already had a Belkin F5D9050 and I've read that others have gotten them to work.

I've installed ndiswrapper and the driver.  An lsusb shows the hardware and ndiswrapper -l shows that the hardware and driver are recognized.  However wlan0 still doesn't exist.  There are no errors in the logs or for modprobe.  I'm just not sure where to go from here.  I appreciate any help.

---

### Post by caljohnsmith on 2008-08-04
Please copy and paste the output of:
```
ndiswrapper -l
lsmod
ifconfig
iwconfig
sudo lshw -C network
```
My guess is even though ndiswrapper is installed, Ubuntu may be using one of its native drivers for you wireless card. Anyway, the above commands should give us the necessary clues of where to go with this.

---

