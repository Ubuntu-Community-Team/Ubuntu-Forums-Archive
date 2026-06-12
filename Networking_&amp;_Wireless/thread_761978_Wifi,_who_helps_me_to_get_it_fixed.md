---
title: "Wifi, who helps me to get it fixed"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by backupdevice on 2008-04-21
Ok,

I;ve got a RT2500 based linksys card, and a linksys router. Cant get a connection .

This is what i tried 

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

[http://sudan.ubuntuforums.com/showthread.php?t=318539](http://sudan.ubuntuforums.com/showthread.php?t=318539)

Also Ndiswrapper, but it states that the rt2500 driver is already loaded.

No luck. I want WPA and static ip

/etc/network/interfaces

auto wlan0
iface wlan0 inet static
address 192.168.168.40
gateway 192.168.168.230 
dns-nameservers 192.168.1.1
netmask 255.255.255.0
wpa-driver wired
wpa-ssid oebidoebi
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk 123456677788

iwconfig >shows not my AP
iwlist scan > Shows my AP

adm/networktools show my wlan0 with ip address. Networktools shows wlan0 with all the info that needs to be there.

Im really stuck, who can help me to get it done.

---

### Post by trwrt on 2008-04-21
Did you put the rt2500 driver in /etc/modprobe.d/blacklist-local?  Try unloading it and loading ndiswrapper by hand for a start.

sudo rmmod rt2500
sudo modprobe ndiswrapper

See if that does anything.  What does 'ndiswrapper -l' say?

---

