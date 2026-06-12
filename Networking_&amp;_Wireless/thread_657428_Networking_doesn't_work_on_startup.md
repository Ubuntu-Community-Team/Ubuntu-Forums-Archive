---
title: "Networking doesn't work on startup"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by bruno321 on 2008-01-03
Hi. Each time I boot up networking doesn't work. Well, generally it doesn't, but I seem to recall that sometimes it does. I have to do 'sudo /etc/init.d networking restart' in order to get it working.

Anyway, it's kind of annoying. So I'd like to solve it properly. 

/etc/network/interfaces reads:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet static
address 192.168.1.4
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.253
wireless-essid *************
wireless-key ***********

```

I've tried putting a script on /.kde/Autostart but it needs to be run at root. I *could* do this:*sudo -S /execute/script < /file/with/password* as I found on this forum, but it isn't the best solution :(

Thanks.

---

