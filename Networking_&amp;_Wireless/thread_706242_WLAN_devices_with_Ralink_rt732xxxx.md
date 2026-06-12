---
title: "WLAN devices with Ralink rt73/2xxxx"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by unix-pete on 2008-02-24
Hi fellows,

setting up such a device, as e.g. D-Link DWL-G122 Rev. C without authentication is not an issue.

The OS detects the device, loads the proper modules, but the assosiation to an AP, which is protected with WPA2 / AES either fails or the connectionrt breaks down after a while.

To get these devices working, use ndiswrapper along with the Windows XP drivers and blacklist the Ralink drivers (rt73usb,  rt2x00usb, 2500usb).

After a reboot everything works. 

Happy Comuting and Cheers

Pete

---

### Post by wieman01 on 2008-02-24
I thought you only need to blacklist 'rt73usb'...

---

