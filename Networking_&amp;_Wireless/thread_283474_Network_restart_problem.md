---
title: "Network restart problem"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by MiCc83 on 2006-10-24
Hi,

I'm a beginner user of Kubuntu and i've a problem with a WiFi dchp network connection with an open AP.
If i do :

```
sudo iwconfig eth1 essid accesspoint
sudo /etc/init.d/networking restart
```

with a interfaces file made in this way:

```
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp
```

The first time it works, but if i disconnect and i redo a networking restart there's no way to make the connection restart because to a dhcp error (something like no way to release ip) until i shutdown and restart system.

It's very strange also because if i do the same with another wpa2 AP using static ip no problem to reconnect.

Sorry for my very bad english... and thx for every help.

Ale

---

### Post by MiCc83 on 2006-10-24
Up, please.

No idea ?

---

