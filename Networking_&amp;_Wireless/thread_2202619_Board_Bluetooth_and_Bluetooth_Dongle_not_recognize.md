---
title: "Board Bluetooth and Bluetooth Dongle not recognized (hciconfig) on ASUS R202CA"
date: 2014-01-30
forum: Networking &amp; Wireless
---

### Post by der.haeusler on 2014-01-30
Hello,

yesterday my new headset arrived (Logitech G930 arrived). Unfortunately I did not get it to work by consulting the instructions I had found before on the internet.

I am using Lubuntu 13.10 on an ASUS R202CA. The netbook is 1 month old, which is why it's the first bluetooth device I am trying to use with it.

"Adapter" and "Device" are greyed out in the Blueman-Manager GUI and this is what I have found out so far:

sudo lsusb:
```
Bus 002 Device 003: ID 0bda:5605 Realtek Semiconductor Corp. Bus 002 Device 004: ID 046d:0a1f Logitech, Inc. G930
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 03eb:883c Atmel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
the headset's dongle is listed. the other device from logitech (Unifying Receiver) is a wireless mouse.

hciconfig --all:
nothing at all

rfkill list:
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

I searched the web the whole evening, flashed the bios etc., but cannot figure out what is causing it not to work.
Any idea?

Thanks in advanced!
Chris

---

