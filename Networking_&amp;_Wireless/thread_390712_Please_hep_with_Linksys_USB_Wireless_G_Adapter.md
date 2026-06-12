---
title: "Please hep with Linksys USB Wireless G Adapter"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by kolslorr on 2007-03-22
I really need some help here...

I upgraded from Edgy to Feisty last night, and things went well until I reboot. Found the additional network manager icon on the task bar, but it is unable to connect to any network.

I am a complete noob when it comes to linux networking, do not know how to troubleshoot this.. This is how my "interfaces" text file looks like.. 

```
auto lo
iface lo inet loopback

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

iface rausb1 inet static
wireless-essid hillstreet
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1

auto rausb1

iface wmaster0 inet static
wireless-essid hillstreet
address 192.168.1.77
netmask 255.255.255.0
gateway 192.168.1.1

iface rausb0 inet static
wireless-essid hillstreet
address 192.168.1.77
netmask 255.255.255.0
gateway 192.168.1.1
```

I completely do not understand what are all these, can someone please explain to me? Also, I only have a USB Linksys wireless adaptor, why do i see so many additional interfaces in the list? 

Help help.. I do not know what to do... have to use xp now... :(

---

### Post by kolslorr on 2007-03-22
This is a sad forum...

---

