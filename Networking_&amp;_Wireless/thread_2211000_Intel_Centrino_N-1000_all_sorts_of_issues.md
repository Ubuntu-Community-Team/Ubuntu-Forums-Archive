---
title: "Intel Centrino N-1000 all sorts of issues"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by mongr31 on 2014-03-13
For some reason my laptop which has been running Saucy without problems since the day it was released just started having issues like crazy last night. My wifi just drops like crazy. It'll say it's connected, but I won't be able to ping anything on my LAN. At first I thought it was my router, but I booted up to Windows and my wifi is working like a champ on there.

It seems to drop out after just a few minutes of browsing, and to get it working again, I have to hit the WiFi button on my keyboard to disable it and then hit it again to start it back up again. That'll fix it for another few minutes, until I have to repeat the process. I searched around as much as I could without going crazy, and tried to do these commands:

```

sudo ifconfig wlan0 down
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
sudo ifconfig wlan0 up


```

But it says: "FATAL: Module iwlwifi is in use." when I try to do the 2nd command. I can run the rest fine, but it doesn't seem to fix it. Any ideas?

---

### Post by mongr31 on 2014-03-13
Adding "options iwlwifi 11n_disable=2" to my /etc/modprobe.d/iwlwifi.conf seemed to do the trick.

---

### Post by mörgæs on 2014-03-13
Good, please mark the thread 'solved'.

---

