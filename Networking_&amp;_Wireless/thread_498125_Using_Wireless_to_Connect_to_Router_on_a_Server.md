---
title: "Using Wireless to Connect to Router on a Server"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by GuitarRocker2562 on 2007-07-11
Well, i installed a ubuntu server and I can't to connect to the internet with my WG111v2 USB dongle, i looked at my /etc/networking/interfaces file and it's not there, I dont think the USB port is bad, what can I do to get it working?

---

### Post by sj3fk3 on 2007-07-11
> **GuitarRocker2562 said:**
> Well, i installed a ubuntu server and I can't to connect to the internet with my WG111v2 USB dongle, i looked at my /etc/networking/interfaces file and it's not there, I dont think the USB port is bad, what can I do to get it working?

Start with finding out if the dongle is detected and supported. Does iwconfig say anything useful? If not have a look at dmesg and see if it says anything about finding a wireless adapter etc.

---

