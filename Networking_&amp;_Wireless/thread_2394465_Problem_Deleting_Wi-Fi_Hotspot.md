---
title: "Problem Deleting Wi-Fi Hotspot"
date: 2018-06-16
forum: Networking &amp; Wireless
---

### Post by DBQ on 2018-06-16
Hi Everyone.

I cannot seem to delete a Wi-Fi AP that I created in Lubuntu 16.04 a while ago (I called it MyWifi). I tried all of the conventional ways (please see below).  It keeps launching automatically on every reboot.
Basically, at one point I needed to turn my laptop into a Wi-Fi access point and have create MyWifi.  I no longer need it.

However, every time I reboot, I see MyWifi showing up in the system tray and my laptop is being connected to it. Essentially my laptop is being automatically becomes an unwanted WiFi access point.
I have to manually disconnect after every reboot.

I tried the following:

1. In the Wifi app: Edit Connections -> and look through the list of known Wifi APs. MyWifi is not there.

2. In the terminal: ls /etc/NetworkManager/system-connections/

Again, no MyWifi anywhere.

How can I get rid of the MyWifi AP and stop it from turning my laptop into an AP on every reboot?

Thank you for any help.

---

### Post by #&amp;thj^% on 2018-06-16
You may or may not need to be root for this:
```
cd /etc/NetworkManager/system-connections
``` 
See if the Wi-Fi AP is listed and if it is >>use:
```
sudo rm {wireless_hotspot_name}

```
**EDIT I see you have looked in " ls /etc/NetworkManager/system-connections/"**
This is odd to me :confused:
You can, if a better solution is not offered then use:
```
sudo ap-hotspot stop
```

---

### Post by DBQ on 2018-06-16
Thank you, but I have already tried this.

My issue is that there is no wireless_hotspot_name in that directory.

My WiFi AP seems to be somewhat of a ghost: it does not appear anywhere in system configuration yet, is resurrected upon every reboot.

---

### Post by #&amp;thj^% on 2018-06-16
> **DBQ said:**
> Thank you, but I have already tried this.

My issue is that there is no wireless_hotspot_name in that directory.

My WiFi AP seems to be somewhat of a ghost: it does not appear anywhere in system configuration yet, is resurrected upon every reboot.

Yes I edited my original post when I noticed that you have looked there. :)
Try this as a temp workaround.
```
sudo ap-hotspot stop
```
And if installed:
```
apt policy hostapd
```
Remove:
```
sudo apt remove --purge hostapd
```

---

### Post by DBQ on 2018-06-16
Thank you so much for following along with me!

I have tried this, but it tells me that hostapd is not installed...the plot thickens;)

---

### Post by jeremy31 on 2018-06-16
See the wireless script link in my signature and post results

---

