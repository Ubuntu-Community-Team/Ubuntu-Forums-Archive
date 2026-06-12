---
title: "Setting WEP key at boot time."
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by xmastree on 2006-10-24
Hi, I have an orinoco gold wifi card in my Toshiba laptop. It works fine, but I don't know how to automatically enter the WEP key.
Currently I'm doing it with:
```
sudo iwconfig ath0 essid xxxxxxxxxxxx key xxxxxxxxxx
sudo dhclient ath0
```
and it works fine.

What do I need to do to make this happen at boot, automatically?

---

### Post by yage on 2006-10-24
you can do this by editing /etc/network/interfaces

```
iface wlan0 inet dhcp
address 192.168.1.somethin (if you have a static ip adress)
netmask 255.255.255.0
gateway 192.168.1.1 (your gateway)
wireless-essid YOURESSID
wireless-key YOURCODE

```

This does the trick for me ;-)

---

### Post by xmastree on 2006-10-24
> **yage said:**
> This does the trick for me ;-)

Worked for me too! \\:D/

As I'm using dhcp I left out the address,netmask and gateway, and just went for:
```
auto ath0
iface ath0 inet dhcp
wireless-essid xxxxxxxxxxxxxx
wireless-key xxxxxxxxxx
```

Thanks :mrgreen:

---

