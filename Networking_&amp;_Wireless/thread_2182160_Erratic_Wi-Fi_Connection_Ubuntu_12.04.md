---
title: "Erratic Wi-Fi Connection Ubuntu 12.04"
date: 2013-10-20
forum: Networking &amp; Wireless
---

### Post by Daniel_Ocando on 2013-10-20
Hello everyone!

I have a **Samsung** **NP550P5CL** Laptop with **Ubuntu 12.04** alongside Windows 8 installed on it, with a **intel (R) centrino (R) advanced-N 6235** for the **Wi-Fi connection**. For the first few days my Wi-Fi connection worked flawlessly, but after I shuted down my laptop, although it can connect to any wireless network it began to worked erratically, until it reached a point when it cannot show a webpage anymore.

- I already tried ignoring the IPV6 settings in the Wi-Fi profile.
- I already tried using Wicd, but it still has the same problems. It can find and connect to any wireless network but seems to have DNS problems once in a while, until it reaches a point when it cannot longer reach any webpage.
- I've also noticed that the problem seems to get worst when I have my laptop with little battery life and I'm not plugged recharging it!

Please help me! I'd really like to make the transition from Windows (shows no problems whatsoever with the Wi-Fi) to Linux and Ubuntu.

---

### Post by wildmanne39 on 2013-10-20
*Thread moved to **Networking & Wireless**.*

---

### Post by Daniel_Ocando on 2013-10-21
Ok. So after doing some experimenting and fooling around, I discovered that the problem has to do with the power management configuration of the wireless card. If the laptop is plugged in to the wall, the Wi-Fi works perfectly. But every time I unplug the power cable it start to work erraticly, until the point where it cannot connect to any webpage.

I've already tried to modify the rc.local file as suggested on this thread: [http://askubuntu.com/questions/162524/wireless-card-power-management](http://askubuntu.com/questions/162524/wireless-card-power-management)

If you have any other alternatives I could try, I'd be more than happy to read them! :)

---

### Post by wildmanne39 on 2013-10-21
Hi, totally remove that file and try it this way:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default power management behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off 
```
above exit0, then save gedit, close and reboot.
Thanks

---

