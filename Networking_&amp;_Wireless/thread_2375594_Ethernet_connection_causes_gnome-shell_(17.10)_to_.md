---
title: "Ethernet connection causes gnome-shell (17.10) to freeze for ~10 seconds, repeat"
date: 2017-10-25
forum: Networking &amp; Wireless
---

### Post by aeronutt on 2017-10-25
Running 17.10, fresh load.
Dell Precision 5510, with USB-C to ethernet adapter. (That is, the Dell Precision laptop has no Ethernet connector, just a USB-C connector to which I connect a USB-C to ethternet adapter).

When connect to Ethernet, the screen freezes for about 10sec, then is usable for about 30 seconds, repeat.

---

### Post by aeronutt on 2017-10-26
UPDATE. The above problem only occurs when there's no internet connection. I have a NAS system that rarely gets connected to the internet, so when I run backups, I connect to the NAS via ethernet and typically disable WiFi. Which causes the above problem.

If I leave WiFi enabled, no freezing occurs.

So it's something with networkmanager trying to find an internet connection via ethernet.

---

