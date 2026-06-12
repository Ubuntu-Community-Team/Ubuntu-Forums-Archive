---
title: "Force BSSID with many APs of same ESSID"
date: 2008-09-01
forum: Networking &amp; Wireless
---

### Post by doomestic on 2008-09-01
Hello. 

I am relatively new to ubuntu. I have a situation where there are two open wireless APs with the same ESSID, but one with a much stronger signal, but I need to connect to the AP with the weaker signal. I have a D-Link DWL-520 with an atheros chipset. In windows there is just no way to force connect it to the weaker BSSID because the drivers supplied do not support it.

In linux I had success with various live CD distros before connecting to the weaker AP using wireless assisstant, a wireless manager for KDE. Finally I installed ubuntu, but the default wireless manager failed to connect to the specific BSSID, and just looked for the AP with the stronger signal and same ESSID. 

I uninstalled it, and tried Wicd, and I got the same result. Is there a certain way to force the original wireless manager that comes with Ubuntu or wicd to connect to a specific BSSID, or a way using wlanconfig / madwifi?

Is there any way possible to force the wireless card to connect to a specific BSSID sharing the same ESSID with another AP with a stronger signal, but obviously a different BSSID? 

Thank you.

---

### Post by forger on 2008-09-01
You can set a specific access point to connect to if you disable "Roaming mode" at System > Administration > Network (> Unlock) > select Wireless and click on Properties - configure it properly there.

---

### Post by doomestic on 2008-09-01
I tried that. There is no option to specify what BSSID I can connect to. All it has is a list of ESSIDs. Still can't connect to the weaker signal. 

I have Wicd installed instead of the default wireless manager.

---

### Post by forger on 2008-09-01
I'm not much of a wiz at wireless networking, but have you tried the network manager editor?

Should be one of these commands:
```
nm-editor
gksu nm-editor
```

Again, never tried it, but it seems to be possible to attach it to a specific bssid

[https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor](https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor)

---

### Post by doomestic on 2008-09-01
I could swear I tried this before, but for some reason I tried it now and it worked :D 

Thanks a lot.

---

