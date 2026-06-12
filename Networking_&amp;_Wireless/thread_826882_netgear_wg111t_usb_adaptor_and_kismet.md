---
title: "netgear wg111t usb adaptor and kismet?"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by Washington Irving on 2008-06-12
I have just bought a wireless usb adaptor, netgear wg111t. Is it possible to set it up so that it works with kismet? It is listed as working with ndiswrapper on the supported wireless cards list but I hear that if I want to use kismet then that's not going to fly. Is there a way of using linux drivers with it?

---

### Post by openflame06 on 2008-06-21
hey Washington Irving

Your best bet would be to check out madwifi drivers.

[http://madwifi.org/wiki/Compatibility/Netgear](http://madwifi.org/wiki/Compatibility/Netgear)

It lists the models it supports. After you install madwifi kismet is able to use the madwifi drivers to push your device into monitor mode.

I'm currently using it with an atheros card, not much help to you I know, but the idea is madwifi works with kismet therefore, i'd expect it to work even if its a netgear device.

Also make sure you have got libpcap-devel installed before using kismet, if you installed kismet from the repos e.g. sudo aptitude install kismet it will not have downloaded this, and kismet will be unable to fetch packets (not what you want)

---

### Post by n_s_simpson on 2009-10-24
Did you get the WG111T into monitor mode?

---

