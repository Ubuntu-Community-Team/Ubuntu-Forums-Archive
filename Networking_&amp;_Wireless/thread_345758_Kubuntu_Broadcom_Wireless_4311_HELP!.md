---
title: "Kubuntu Broadcom Wireless 4311 HELP!"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by darkzone on 2007-01-24
Ok so I started off with Ubuntu installed but it was a total mess to get ndiswrapper working and such so I installed Kubuntu. Ndiswrapper worked fine and the driver installed but it keeps showing up as eth1. It needs to be wan0 right? Its also saying that its a broadcom dell 3900 or something like that. Any ideas guys? I have a compaq V3019us. If you need any more info or anything just let me know.

---

### Post by Floppyjoe on 2007-01-24
[http://www.ubuntuforums.org/showthread.php?t=338332&highlight=wlan0](http://www.ubuntuforums.org/showthread.php?t=338332&highlight=wlan0)

---

### Post by darkzone on 2007-01-24
wlan0     IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


This is what i am getting. something is ****'d up :(

---

### Post by Floppyjoe on 2007-01-24
you may need to adjust your /etc/network/interfaces file again.

```
sudo gedit /etc/network/interfaces
```

to get something like this:

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp


#auto eth1
#iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid WarGames
wireless-channel 7
wireless-mode managed
#wpa-driver wext
#wpa-conf /etc/wpa_supplicant.conf


Where you put in your router name and channel instead of what I have there.

---

### Post by discord on 2007-01-25
works for me follow instructions here

[https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983](https://launchpad.net/ubuntu/+source/ndiswrapper/+bug/59983)

---

