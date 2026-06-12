---
title: "Static IP?"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2007-04-02
I was wondering how I can set a static IP in Ubuntu/Kubuntu via CLI?

I opened **/etc/network/interfaces** and see the following:

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

```

---

### Post by Rui Pais on 2007-04-02
most easy is, on a terminal:
```
gksudo network-admin
```

click on the interface you want static
click Properties
change to Static (from DHCP) and enter your settings.

:)

---

### Post by CarlosinFL on 2007-04-02
That wont work - this is a CLI system only so I need to know what text file needs to be edited and how the format should be seated. CLI instructions are what I am looking for.

---

### Post by Rui Pais on 2007-04-02
then just do:
```
sudo nano /etc/network/interfaces
```

and edit the section for eth0 to:
> auto eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx

with xxx.xxx.xxx.xxx replaced by your settings, of course ;)

hth

---

### Post by sisco311 on 2007-04-02
my /etc/network/interfaces file:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.2.130
netmask 255.255.255.0
gateway 192.168.2.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


---

