---
title: "Slow Internet on Ubuntu 14.04"
date: 2014-10-03
forum: Networking &amp; Wireless
---

### Post by mr-josephalabash on 2014-10-03
Like many people it seems like, wireless internet runs very slowly. Many pages don't load and have to be refreshed. I attached a wireless script. Thanks to any who try to help!

[ATTACH]256933[/ATTACH]

---

### Post by fly-by-night on 2014-10-04
Wireless can be dodgy for many reasons from my readings. In your case it must be really bad if you need to compress an already tiny txt file. :)

Are you far from router, through walls etc? Using a USB device with an extention cable (try without for more power)?
Try changing the Wifi channel on the router to something else.

Unfortunately the txt file contents mean little to me with my knowledge.

---

### Post by varunendra on 2014-10-05
Welcome to the forums mr-josephalabash!

Can you change the encryption in the router to pure WPA2-PSK with AES (CCMP)? It is currently using WPA/WPA2 mixed mode with TKIP which can be a problem with some drivers.

Additionally, seeing that yours is a Lenovo machine, not Acer, does it help if you blacklist the 'acer-wmi' driver that seems to be loading ? -
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

And set "IPv6" in the Network Manager to "Ignore".

Try one change at a time, and let us know if any of these helps the speed. If not, we still have a few more things to try.

---

