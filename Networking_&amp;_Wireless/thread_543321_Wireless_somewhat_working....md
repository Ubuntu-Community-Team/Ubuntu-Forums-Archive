---
title: "Wireless somewhat working..."
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by vitalejd on 2007-09-05
I got a new router and I put WPA encryption on it and it works in ubuntu.  However when I turn off the broadcast SSID function on the router settings ubuntu disconnects and it will not reconnect to the router.  What the heck is going on here?  

BTW...this worked with my older wireless router where I did not broadcast my SSID over a WEP encryption.

---

### Post by spd106 on 2007-09-05
Because there are several methods involved in WPA, the broadcast signal contains the information needed by the drivers/wpa_supplicant to find out the mode that is required to connect. It is possible to get around this by telling wpa_supplicant not scan for it, but AFAIK this hasn't been fully implemented across all drivers yet and network manager (nm-applet) support is a bit buggy. So it's still a bit hit and miss. 
See [http://lists.shmoo.com/pipermail/hostap/2004-August/007758.html](http://lists.shmoo.com/pipermail/hostap/2004-August/007758.html) (rather old) for more detail.

Hopefully it is coming in future updates. Until then there is no provable security benefit to turning of AP broadcast. It's not like WPA is as weak as WEP, where there might be a case for hiding the nework as much as possible.

---

### Post by erfahren on 2007-09-05
the best way I found to get WPA with Wifi is from this HowTo: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

going by that should solve the problems of the non-broadcasted SSID. I've also found it pretty convenient if re-installing Ubuntu as well. Everything is set in the /etc/network/interfaces file (I just have to go into the Network settings to set my DNS addresses).

---

