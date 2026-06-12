---
title: "laptop - network config for different locations"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by aljosa.mohorovic on 2007-08-06
everything related with hardware works and network manager also works when i have network cable plugged in.

when i start laptop without cable plugged in it waits ~2 minutes when boot reaches /etc/init.d/network because i have auto eth0 and auto eth1 in /etc/network/interfaces and if i remove auto part from interfaces network manager gets confused and nothing works.

any ideas/tips how to solve this?

Aljosa

---

### Post by Jose Consuervo on 2007-08-06
I am not completely clear on what is happening. Is your computer booting? Also is eth1 your wireless card? or is it some other ethernet adapter.

---

### Post by aljosa.mohorovic on 2007-08-07
eth1 is wireless.

my laptop boots but if i have auto eth0 eth1 in /etc/network/interfaces it takes ~2 minutes to pass /etc/init.d/networking  since it tries to get info from dhcp server and since no cable is plugged in it takes 2 minutes to give up on network configuration.

this can all be avoided if "auto" options are removed from /etc/network/interfaces but then NetworkManager can't detect wireless and some other things don't work automatically.

---

