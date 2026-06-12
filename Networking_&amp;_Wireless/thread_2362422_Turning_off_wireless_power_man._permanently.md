---
title: "Turning off wireless power man. permanently"
date: 2017-05-28
forum: Networking &amp; Wireless
---

### Post by BrianSwatton on 2017-05-28
I have partly solved a wireless problem on my easynote laptop that I've had since installing 16.04.  Without fail, the wireless would work for about 5-10 mins, when it would drop out and not return until reboot.  dmesg would show lots of connection retries.

iwconfig shows that the power management is on. If I use :

  sudo iwconfig <iface> power off

It works reliably and continually then, until logout or reboot, when power management gets turned back on again.  I haven't found anything in settings manager or editor to make a permanent setting.

I guess I could add a script to set this, but is there a "proper" way to address this?  Perhaps turning off power management to fix this isn't the proper way anyway, but I'm not too concerned about power usage in this situation.

---

### Post by Hadaka on 2017-05-28
Hi, please open a terminal ctrl/alt t then copy and paste..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
To Confirm..
```
iwconfig
```
Thanks.

---

### Post by BrianSwatton on 2017-05-29
Thank you very much, That's sorted it,

---

### Post by Hadaka on 2017-05-29
Glad that worked for you !
Thank you for marking your thread solved.

---

