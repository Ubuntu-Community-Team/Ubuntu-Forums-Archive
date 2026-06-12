---
title: "no wireless at startup"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by jordanau on 2006-08-04
i cannot get my wifi to work at boot. I believe I have messed up my /etc/network/interfaces file:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth2 inet dhcp

auto eth2
wireless-essid Ben
wireless-key ----------------
auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


auto eth0

```

---

### Post by wieman01 on 2006-08-04
"ath0" or "wlan0" are your wireless card(s). It's strange you would have 2. I seems that you have installed both the Atheros driver and ndiswrapper. That's odd. Try this and pay attention to the sequence:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
[B]wireless-essid Ben
wireless-key ----------------[/B]

auto wlan0
iface wlan0 inet dhcp

If this doesn't work in your case, try this:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
[B]wireless-essid Ben
wireless-key ----------------[/B]

I cannot tell which of these two devices is your wireless adapter. Wouldn't be surprised if you had the device configured twice. Shouldn't do any harm though.

---

### Post by jordanau on 2006-08-05
eth2 is my wireless adapter. Broadcom 43xx drivers do that. I am not using ath0, wlan0 or ndiswrapper.

---

### Post by wieman01 on 2006-08-05
> **jordanau said:**
> eth2 is my wireless adapter. Broadcom 43xx drivers do that. I am not using ath0, wlan0 or ndiswrapper.

The try this:

> auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp
wireless-essid Ben
wireless-key ----------------

:-)

---

