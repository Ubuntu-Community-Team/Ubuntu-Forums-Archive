---
title: "static wpa2 ip on nm-applet 0.6.5; resets to wpa after reboot"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by exodunix on 2007-11-22
It seems that after configuring nm-applet 0.6.5 for a static wpa2 ip address, it does not want to play nice. Each time I reboot my computer the nm-applet settings are configured for a wpa static ip, instead of wpa2.

---

### Post by kevdog on 2007-11-22
Why dont you just put your configuration in the /etc/network/interfaces file so you can save the settings??  If you then want to use the computer for a different AP, then re-enable roaming mode and the interfaces file settings will be ignored.

---

### Post by exodunix on 2007-11-23
i followed your advice, and all seemed well until I rebooted and the internet didn't work :|. had to ' sudo /etc/init.d/networking restart ' and it worked. doesn't really solve the problem either ;\, thank you though. seems im on the right track

---

