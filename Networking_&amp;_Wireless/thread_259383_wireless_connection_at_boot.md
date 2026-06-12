---
title: "wireless connection at boot"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by julx on 2006-09-17
hi,

I've got a RT2500-based Belkin wifi card, and my /etc/network/interfaces is configured as follows:

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

#auto ra0
iface ra0 inet static
address 192.168.2.3
netmask 255.255.255.0
gateway 192.168.2.1
wireless-essid 3Com
wireless-channel 11
wireless-mode Managed
```


I have no problem to connect to internet using the wireless assistant, but when I configure /etc/network/interfaces to connect at boot (uncommenting "auto ra0"), I can only connect to my router, and not to internet (only Skype works!)...

Any suggestion?

Thanks
Jul

---

### Post by pak33m on 2006-09-18
Julx,

Take a look at my mini-HOWTO: 

[http://www.ubuntuforums.org/showthread.php?t=256893&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=256893&highlight=wireless)

It may or may not work for you.  This is what I did manually to get my wireless connection configured and to start everytime I rebooted.

---

