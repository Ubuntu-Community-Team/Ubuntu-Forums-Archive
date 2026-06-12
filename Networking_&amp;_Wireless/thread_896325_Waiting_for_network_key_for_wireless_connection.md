---
title: "Waiting for network key for wireless connection"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Justin7b on 2008-08-21
Sorry for asking a newbie question. I'm dual booting WIN2K and Ubuntu 8.04. Previously,my DLink wireless usb adapter DWL-G122 was working fine with automatic driver detection and WPA Personal encryption. Then I changed it to TP-Link TL-WN321G and again everything works beautifully.Now that I switched it back to the DLink adapter as I wanted to use my DLink adapter for another computer, the wireless connection simply fail to connect - it keeps searching for network key.

I've tested the adapter to be Ok when I reboot to WIN2K.Apparently,both these adapters use the same rt73 driver(?).

Please help.

---

### Post by tangibleorange on 2008-08-21
ok i believe this may be a problem with network manager, so we will try and connect from the terminal:

```
gksu gedit /etc/network/interfaces
```

make sure these lines are in the file. if not, add them (I assume you are using WPA1 (TKIP)). remember to replace the stuff in quotes with your info:
```
auto wlan0
iface wlan0 inet dhcp

pre-up ifconfig wlan0 up 
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up ifconfig wlan0 down
pre-up iwconfig wlan0 essid "myssid"
pre-up iwconfig wlan0 mode Managed
pre-up iwpriv wlan0 set AuthMode=WPAPSK
pre-up iwpriv wlan0 set EncrypType=TKIP
pre-up iwpriv wlan0 set WPAPSK="mypskkeystring"
pre-up ifconfig wlan0 up 
```

then save and quit. then reboot, and see what happens! even if the network icon says you are not connected, try loading a page in firefox.

---

