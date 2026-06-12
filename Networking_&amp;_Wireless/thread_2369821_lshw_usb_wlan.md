---
title: "lshw usb wlan"
date: 2017-08-27
forum: Networking &amp; Wireless
---

### Post by louis144 on 2017-08-27
does show lswh information about an usb wlan adapter?

---

### Post by jeremy31 on 2017-08-27
It should if it can be identified as a wifi device but it might need a driver to be shown there.  We could help more if you posted results for ```
lsusb; rfkill list all
```
Welcome to the forums

---

### Post by louis144 on 2017-08-27
I would like to use it to detect the chipset of an asus usb wifi adapter on a windows 10 host.So i would use lshw on an ubuntu live cd: but this means there is no driver!

---

### Post by jeremy31 on 2017-08-27
Normally we use lsusb and then search for the ID that is returned and sometimes the actual chipset is listed in lsusb results.
You should be able to get some info from the Device Manager in Windows, through Device Properties and then either Driver Details or look through the info under the Details tab as the Hardware ID will be the similar to what we find in lsusb

---

### Post by chili555 on 2017-08-27
Here is the rough idea. Run:```
lsusb
```Find the device ID like this example:```
Bus 002 Device 003: ID [COLOR="#FF0000"]148f:5370[/COLOR] Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04d9:a055 Holtek Semiconductor, Inc. Keyboard
Bus 001 Device 003: ID 04d9:a100 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```We Google the ID string and see this:  [https://wiki.debian.org/rt2800usb](https://wiki.debian.org/rt2800usb)> USB: 148F:5370 Ralink Technology, Corp. RT5370 Wireless AdapterHow exactly that relates to Windows, we do not know. Most of us do not speak Windish.

---

