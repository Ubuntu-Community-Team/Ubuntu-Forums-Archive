---
title: "[SOLVED] Start wireless USB connection without logging in."
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by Wulfrunner on 2008-11-21
Hello,

I have recently acquired a d-link DWA-130 wireless USB adapter for my server. I had to manually get it going with Hardy, but Intrepid seems to support it natively (using the ralink rt2870 driver). It shows up in the restricted hardware manager so either it actually does or it found out that I compiled and installed the drivers and pretended that the ubuntu team did...

Here is my issue: I am not getting a network connection until I log in to my account using gdm. I am not sure what service is taking care of the wireless log-in process. I know that I can do the whole thing manually using wpa_supplicant, but I would like NetworkManager to take care of this for me.

How can I get the wireless link without logging in?

---

### Post by Wulfrunner on 2008-11-24
In order to get this working, I defined ra0 in /etc/network/interfaces:
iface ra0 inet static
address  192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

The /etc/wpa_supplicant.conf:
network={
ssid="nameofnetwork"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="mypresharedkey"
pairwise=TKIP
group=TKIP
}

Then I added this line to /etc/modules:
alias ra0 rt2870sta

And finally, made sure it was starting up with /etc/rc.local (there should be a better way?!):
ifup ra0

---

### Post by tanha on 2009-04-28
> **Wulfrunner said:**
> In order to get this working, I defined ra0 in /etc/network/interfaces:
iface ra0 inet static
address  192.168.1.200
netmask 255.255.255.0
gateway 192.168.1.1
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf

The /etc/wpa_supplicant.conf:
network={
ssid="nameofnetwork"
scan_ssid=0
proto=WPA
key_mgmt=WPA-PSK
psk="mypresharedkey"
pairwise=TKIP
group=TKIP
}

Then I added this line to /etc/modules:
alias ra0 rt2870sta

And finally, made sure it was starting up with /etc/rc.local (there should be a better way?!):
ifup ra0

Are you using x86 or x86_64? Are you using it in 802.11g or 802.11n mode?

---

