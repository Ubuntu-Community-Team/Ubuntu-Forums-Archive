---
title: "Problem with Kubuntu 7.04 and IPW3945"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by timking on 2007-04-23
New Dell Inspiron 1505
Intel Pro Wireless 3945
Nvidia GeForce Go 7300
Fresh Kubuntu 7.04 installation, dual boot with XP Pro (yes, I ditched Vista)

The system doesn't recognize the wireless card at startup. which delays startup ~40 seconds.  It works fine after I manually connect with wlassistant.  I noted the same problem when I ran the Edgy Eft Live CD on the same machine.  Is this a driver issue, or a system startup issue?

Thanks,
Tim King

---

### Post by chili555 on 2007-04-24
The problem may be related to your */etc/network/interfaces* file. If many stray interfaces are shown; ath0, eth2, etc., then networking churns through all of them trying to connect. Also, the interface you want to use needs to be designated 'auto.' Here is mine for comparison:```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```Try amending your file as above, reboot and let us know.

---

### Post by timking on 2007-04-24
It boots up much faster, but still does automatically connect to my wireless network.  Here is my current interfaces file:
```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
wireless-essid XXXX
wireless-key XXXXXXXXXX

```

---

