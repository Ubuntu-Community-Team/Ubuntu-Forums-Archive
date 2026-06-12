---
title: "Unable to find wlan0"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by Jimmy_Tidey on 2014-05-15
I have a Lenovo Yoga laptop with a realtek wireless card which I had to install drivers for, when I converted it to ubuntu 12. 

Recently I had difficulty connecting to a particular wireless network (one that requires a certificate) and tried to reset the wifi interface with sudo ifdown wlan0. When I tried to start it again with sudo ifup wlan0 it says "Ignoring unknown interface wlan0=wlan0.", so I restarted the computer.

I'm now unable to find wlan0 anywhere, event if I boot into recovery mode and look at the network settings, only lo is listed. I can get back on with a wireless dongle, which lists itself as wlan1.

What have I done!?

---

### Post by varunendra on 2014-05-15
Welcome to the forums Jimmy,

Please follow the instructions in this post to create and show us a detailed diagnostics report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Jimmy_Tidey on 2014-05-15
sorry - didn't realise...[ATTACH]253173[/ATTACH]

---

### Post by Jimmy_Tidey on 2014-05-15
I really am completely stuck on this - my best theory at the moment is that my wifi device has actually died, and that it refusing to connect to certain networks was the beginning of the end. However, it is a new laptop... so I really hope that isn't what happened. Any further hints very much appreciated.

---

### Post by varunendra on 2014-05-15
Your device is a USB one and is still detected by Ubuntu -
```
Bus 001 Device 005: ID **0bda:1724** Realtek Semiconductor Corp.
```
However, the required driver doesn't seem to be loaded, which means either you didn't install it at all or perhaps your kernel got upgraded and now you need to reinstall it.

How did you install it the first time? The correct way is this one (post #6) : [http://ubuntuforums.org/showpost.php?p=12665885](http://ubuntuforums.org/showpost.php?p=12665885)

Either that entire process, or the process in post #8 of the same linked thread above will have to be repeated everytime the kernel is upgraded.

The author of the driver himself isn't sure whether it will compile correctly or not on kernel versions higher than 3.9 (see **[here]("https://lkml.org/lkml/2013/4/1/280")**), so please closely watch the installation process (messages in the terminal) and if you receive any errors during the installation, post them here.

---

