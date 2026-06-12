---
title: "Wlan0: no connection to wireless router at boot"
date: 2005-08-02
forum: Networking &amp; Wireless
---

### Post by Titusxx on 2005-08-02
I'm having some troubles with my wifi connection.
When the pc boots the wlan0 network interface comes up but I have no connection to my router and I do not get an IP address.
After boot I just have to do:
sudo iwconfig wlan0 essid " essid "
sudo dhclient wlan0
Than it all works.
In my interfaces file I have the following:
auto wlan0
iface wlan0 inet dhcp
wireless_essid "essid" (does the essid have to be inbetween quotation marks?)
wireless_key thekey (in HEX)
Any suggestions?

---

### Post by odin on 2005-08-02
see if you have the wireless-tools package installed.

---

### Post by Titusxx on 2005-08-07
Yep, wireless-tools are installed.

---

### Post by Titusxx on 2005-08-07
I've got it working.
interfaces file:
auto wlan0
iface wlan0 inet dhcp
pre-up iwconfig wlan0 essid "Name router"
pre-up iwconfig wlan0 key s:wep key
pre-up iwconfig wlan0 key open

And this did it for me. The pre-up solved all my problems.

---

