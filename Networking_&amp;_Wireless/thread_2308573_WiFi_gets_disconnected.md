---
title: "WiFi gets disconnected"
date: 2016-01-04
forum: Networking &amp; Wireless
---

### Post by ashwary2 on 2016-01-04
I'm using Ubuntu 14.04.3 LTS, and I have rtl8723be wifi card. I was losing internet connectivity on WiFi, so I installed a driver with dkms, as suggested by someone, by following this link - [http://askubuntu.com/questions/629679/rtl8723ae-unstable-on-ubuntu-14-04/](http://askubuntu.com/questions/629679/rtl8723ae-unstable-on-ubuntu-14-04/)

There is some improvement, but WiFi gets disconnected after, say, 45-50 minutes of use, and I can get to work by disabling and re-enabling WiFi. 

I have also tried this, which i guess, turns off power saver. Didn't work.

```
sudo -i
echo "options rtl8723be  fwlps=0"  >  /etc/modprobe.d/rtl8723be.conf
exit
```

I don't want this to happen because, firstly, I leave my laptop turned on overnight to download stuff, and I want WiFi to stay connected all the time. Secondly, it's annoying when it happens while I'm working.

Please let me know if you need more information. 

P.S.- I'm a beginner.

---

