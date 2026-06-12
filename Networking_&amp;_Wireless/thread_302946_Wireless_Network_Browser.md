---
title: "Wireless Network Browser"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by Mirky on 2006-11-19
I'm running Xubuntu and need a wireless network browser
  (I need coffee)
I would like to know of one that works with XFCE.
I see Wifi-radar in (add/remove applications) I see others
but they are for K or G

---

### Post by Jussi Kukkonen on 2006-11-19
Do you know that they all do work with xfce (they just might need a lot of libraries)?

---

### Post by spd106 on 2006-11-19
**sudo iwlist wlan0 scan** from a terminal will give you a list of nearby APs.

---

### Post by Matt Yun on 2006-11-19
apt-get install network-manager-gnome

Not only does this package provide a system tray applet that displays available wireless networks, but it allows connection to WPA networks so you don't have to worry about configuring wpa_supplicant.

Here is a thread on [HOWTO: NetworkManager with WPA 1&2 Support]("http://www.ubuntuforums.org/showthread.php?p=703020").

---

