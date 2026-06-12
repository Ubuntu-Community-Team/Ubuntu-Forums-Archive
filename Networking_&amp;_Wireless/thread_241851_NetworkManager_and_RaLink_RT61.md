---
title: "NetworkManager and RaLink RT61"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by cruizer on 2006-08-22
are they compatible? i haven't had success getting my notebook's RT61 wifi to work with networkmanager. but it works OK with ubuntu's built in network config tool. it's just I'd like to use NetworkManager so that i can easily slide into other networks when I bring my notebook out of the house.

anybody who's had success getting networkmanager to work with RT61? i have a feeling it doesn't recognize the "ra0" interface name...

---

### Post by BrendanM on 2006-11-16
There is a list of hardware supported by NetworkManager here: [http://live.gnome.org/NetworkManagerHardware](http://live.gnome.org/NetworkManagerHardware)

It looks to me like it *does* support the rt61 card, but only if you're using the rt2x00 driver from serial monkey. That driver is broken in Edgy Eft (whole other issue) so the only way to get the card to work is with proprietary ralink drivers. That's what I'm doing and it works well, but NetworkManager doesn't seem to work.

I'm using a different program called Wifi-radar which works pretty well. You might give that a shot.

---

