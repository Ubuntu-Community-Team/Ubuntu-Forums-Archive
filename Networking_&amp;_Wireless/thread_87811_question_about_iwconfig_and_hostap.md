---
title: "question about iwconfig and hostap"
date: 2005-11-08
forum: Networking &amp; Wireless
---

### Post by herot on 2005-11-08
i am using a smc2532w-b wireless card... i managed to get it working 
by installing the hostap drivers and editing the /etc/pcmcia/hostap_cs.conf file.

however when i try to change some settings using iwconfig, i get this:
```
root@minislash:/home/herot# iwconfig wlan0 txpower 18
Warning: Driver for device wlan0 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.

```
does anyone know how to upgrade the Wireless Extension to version 18??

---

### Post by slux on 2005-11-11
AFAIK the hostap drivers are quite flaky and don't seem to support much configuration from iwconfig. Would the orinoco driver be an option for you?

---

### Post by herot on 2005-11-14
its a prism 2.5 chipset... i want to use aircrack, airodump, void11, and the like...

---

### Post by slux on 2005-11-14
Ah, right prism. Use linux-wlan-ng for it. I haven't done any sniffing or such with it so I can't vouch for that but sure beats trying to fight with hostap for basic functionality.

---

