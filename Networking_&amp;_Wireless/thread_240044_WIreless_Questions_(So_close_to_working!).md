---
title: "WIreless Questions (So close to working!)"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by skattman83 on 2006-08-20
I got my Dell laptop's wireless card working using the native bcm43xx drivers.  The networks I'm using are encrypted with either peap or wpa.  I can connect to both using wpa_supplicant.  Is there a way to have more than one network listed in the wpa_supplicant.conf file?  Currently, I am commenting out whichever one I don't intend on using at that momemnt.  Also, I still have not figured out how to start wpa_supplicant on boot.  I still need to wait for the computer to boot, then run ```
wpa_supplicant -B -ieth1 -c/etc/wpa_supplicant.conf -Dwext
``` followed by ```
dhclient eth1
```  This works, however, I'd prefer it be automatic at boot.  I would prefer to just use this as is, without network-manager if possible, but if there is a way to get network manager (or wifi-radar) working easily using wpa_supplicant, I would try it.I do like the idea of a strength meter on my task bar.

---

### Post by skattman83 on 2006-08-20
I found this:> To have your wireless network come up automatically with wpasupplicant, edit /etc/network/interfaces to have the following 2 lines after the iface wlan0 entry:

pre-up wpa_supplicant -Bw -i wlan0 -c /etc/wpa_supplicant.conf -D zydas
post-down killall -q wpa_supplicant.  It looks like what I was looking for to auto start wpa_supplicant at boot.  I'll give it a try and post back.

---

### Post by skattman83 on 2006-08-22
That didn't do it.  I think network-manager-gnome may be the way to go, but it doesnt work for me.  I installed it, and it shows me two computer screens with an X.  When i click on it, it gives me the choices of enabling wired and wireless, both of which are enabled.  Is there a config file I need to edit somewhere?

---

