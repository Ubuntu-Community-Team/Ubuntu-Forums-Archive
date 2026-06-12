---
title: "WPA Supplicant"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by jideuu on 2007-10-07
I'm trying to get WPA Supplicant to connect to my wireless card but it wont connect to the driver.

Here's what my 'wpa_supplicant.conf' file contains:
```
# WPA-PSK/TKIP

ctrl_interface=/var/run/wpa_supplicant

network={
	ssid="Belkin_G_Plus_MIMO_ADSL"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="MY PSK"
}
```

And when I type **sudo wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf** in the terminal, this appears (repeatedly):
```
Trying to associate with 00:17:3f:4b:d6:0a (SSID='Belkin_G_Plus_MIMO_ADSL' freq=2412 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.

```

---

### Post by kevdog on 2007-10-07
Try -Dwext instead -Dndiswrapper

---

### Post by jideuu on 2007-10-07
Great, thanks.

Is there anyway of getting Ubuntu to run **sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf** automatically on start up?

---

### Post by kevdog on 2007-10-07
Look at this thread:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Keep your settings however for now, you might need them later :)

---

