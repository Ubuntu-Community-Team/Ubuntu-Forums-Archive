---
title: "Stuck permanently in Flight Mode"
date: 2019-07-10
forum: Networking &amp; Wireless
---

### Post by oluwafenyi on 2019-07-10
Hey, I'm a newcomer to Ubuntu and since I was on windows I've always had a problem with the physical WiFi switch which is broken. I bought a usb WiFi adapter to fix that but so far after switching to linux, I've followed the instructions to install the driver and the device shows up on the top bar as PCI WiFi but I'm unable to turn it on, is there anyway to fix this?

---

### Post by TheFu on 2019-07-10
I'd check **rfkill**, see if it is hardlocked or softlocked.
Also, if you don't want to use the internal wifi adaptor, be certain it is disabled in the BIOS.

```
$ sudo rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
4: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
```
is what you want, probably.

---

### Post by jeremy31 on 2019-07-10
One way to fix is to remove the internal wifi

---

