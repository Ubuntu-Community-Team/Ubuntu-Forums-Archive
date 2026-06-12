---
title: "Wireless quit on me"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by pee_gee_l on 2007-05-23
Hi guys,
I'm running Ubuntu 6.10 on my work laptop.
I used to be able to connect to my home wireless network without any problems. Last week I connected to a wired network at another place, and ever since I get no signal from my wireless card on my home network.
I'm pretty new to Ubuntu, having only delt with windows in the past...
When I run lspci I get this output for my wireless card:

02:08.0 Ethernet controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)

My network has WEP encryption with a shared network key. It worked no problem before.
Hope you can help!

---

### Post by Kobalt on 2007-05-23
There must be a little hiccup into your network config. Can you please post (removing your ESSID and WEP key) the output of this : ```
cat /etc/network/interfaces
```

---

### Post by pee_gee_l on 2007-05-23
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0





iface eth1 inet dhcp
wireless-essid XXXX
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX

auto eth1

Thanks for helping me out :)

---

### Post by Kobalt on 2007-05-27
Which one is your wireless interface : eth1 or wlan0 ? You can find out with the command line *iwconfig*
Because your wireless settings (SSID & key) are under eth1, and not wlan0...

---

### Post by pee_gee_l on 2007-05-27
eth1 is the wireless interface, that I'm sure of.
haha I discovered a switch for my wireless card on my laptop that was off. I turned it on, I can get signal now but I'm still unable to connect to the network.

---

### Post by pee_gee_l on 2007-06-04
Ok, so I also had some complications because of my shared network key but I fixed it! I'm no longer bound to work at the end of my ethernet cable :)
Thank you

---

