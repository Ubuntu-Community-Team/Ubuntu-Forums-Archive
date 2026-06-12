---
title: "How To: IEEE8021X &amp;amp;amp; Protect EAP w/ Ethernet"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by Skrypt on 2007-08-23
After much persistence and a little help, I managed to get it to work. I've attached my work.

This is how I setup my ethernet on Ubuntu 7.04 with GNOME for IEEE802.1X Authentification & Protected EAP on a DHCP network here, on campus, at the University of Florida.

First, disable your eth0 in your network manager.

Find out if you have wpa_supplicant installed (by default it is since 6.10).
```
$ wpa_supplicant -v
```
This returns for me:
wpa_supplicant v0.5.5
Copyright (c) 2003-2006, Jouni Malinen <jkmaline@cc.hut.fi> and contributors
Next, edit the following files as I have and be sure to change the username and password to your own.
```

$ sudo gedit /etc/wpa_supplicant.conf
```
```
# The below line not be changed otherwise we refuse to work
ctrl_interface=/var/run/wpa_supplicant

# Ensure that only root can read the WPA configuration
ctrl_interface_group=root

# Let wpa_supplicant take care of scanning and AP selection
ap_scan=0

network={
 key_mgmt=IEEE8021X
 eap=PEAP
 pairwise=CCMP TKIP
 identity="YOUR_USERNAME"
 password="YOUR_PASSWORD"
 phase2="auth=mschap2"
 priority=2
}
```
This file might not exist. Create it.
.... and then ....
Find out where your ethernet is / specify the correct ethernet. If you're unsure, use:
```
ifconfig
```
```
$ gksudo gedit /etc/network/interfaces
```
```

auto eth0
iface eth0 inet dhcp
wpa-driver wired
wpa-eap PEAP
wpa-key-mgmt IEEE8021X
wpa-identity YOUR_USERNAME
wpa-password YOUR_PASSWORD
wpa-conf /etc/wpa_supplicant.conf

auto lo
iface lo inet loopback

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

```

Finally, restart your computer.

Thanks to all those who helped and offered their assistance. I couldn't have done it without you. =-)

---

