---
title: "How to add usb-adsl modem to Newtwork Manager"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by klx on 2007-07-31
Hi,

I have Ubuntu 7.04 and DLink DSL200 usb modem. I have already installed and configured drivers eciadsl-usermode-0.11.

After system boot I manualy run my modem:

```
root@klx-laptop:~# eciadsl-start
...
[EciAdsl 5/5] Setting up route table...

Waiting for tap0...
root@klx-laptop:~# dhclient tap0
```

after this I have access to internal network of my provider, but to get access to Internet I need to setup VPN. I want to do this using Network Manager, but it don't see my usb-adsl modem.

How to add my adsl modem to Network Manager list of devices??? in this list I have only my ethernet card, wifi-adapter and dial-up modem.

this is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp
```

Maybe I need to add tap0 interface to this file, but I don't know how to do this..

---

