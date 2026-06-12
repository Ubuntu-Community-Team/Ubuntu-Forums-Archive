---
title: "gutsy messes up my wireless"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by ZeldaFan on 2007-12-02
I have an intel 3945 internal wireless card on my laptop. Anyway, in feisty I could successfully connect to my internet wirelessly and anytime switch to another network, switch to LAN, or even reconnect to my existing connection by clicking on the icon in the upper right hand corner of my screen and choosing the appropriate type of connection. However after getting Gutsy, I can no longer do that. It connect successfully to me wireless connection, but I can't change the connection afterwards, without restarting or I completely lose the connection. How do I fix this?

---

### Post by ZeldaFan on 2007-12-02
Anyone know? I dont know if this helps or not, but I never actually upgraded from feisty to gutsy. I did a clean install of Gutsy. By /etc/network/interfaces file looked like this with feisty:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

this is what it looks like in gutsy:
```
auto lo
iface lo inet loopback
```

For some reason, I suspect that this is inciting the problem...Should I change my interfaces file to mirror my old feisty one? With both files I can still access the net, I just can't change what network I use with Gutsy.

---

