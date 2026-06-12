---
title: "Cant connect to wireless AP"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by Good Old Jacob on 2007-06-09
My AP has a cloaked essid and uses open WEP. My wireless card is a prism54 that worked fine with gentoo. The network seems to come up if I configure it with the network manager, but I can't even ping my AP. Any help would be greatly appreciated. :-({|=

Edit: iwconfig shows wlan0 with the correct essid, but for AP it has Access Point: Not-Associated

---

### Post by upfwnv03 on 2007-06-10
My AP also showed loss of association. In searching the forums I found this thread.
[http://ubuntuforums.org/showthread.php?t=463118](http://ubuntuforums.org/showthread.php?t=463118)
Granted its for the Ath0 device, but with a small change on my AP to WPA2. I was able to connect using wlan0 and have experienced no trouble since doing so.
The WICD application seems much friendlier than the Gnome NetworkManager app.

---

### Post by Good Old Jacob on 2007-06-10
It's not actually my AP, so I can't change it to WPA2.

---

### Post by Good Old Jacob on 2007-06-10
Well, I talked the owner into uncloaking the AP until I switch back to gentoo. I can connect just fine now.

---

### Post by Good Old Jacob on 2007-06-19
For what it's worth, as I am switching my laptop back to Gentoo, I can set things up manually. This even works when the AP is cloaked. Thanks for the help upfwnv03. :KS

```
ifdown wlan0
iwconfig wlan0 essid MyESSID
iwconfig wlan0 key s:MyPassphrase
iwconfig wlan0 ap 00:0F:...... // Needed this to work from a livecd i.e., a fresh environment
ifup wlan0
```

* /etc/network/interfaces contains

```
auto wlan0
iface wlan0 inet dhcp
```

---

