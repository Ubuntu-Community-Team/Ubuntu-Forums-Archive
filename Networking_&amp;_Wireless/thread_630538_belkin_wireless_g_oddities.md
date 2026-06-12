---
title: "belkin wireless g oddities"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by sds50 on 2007-12-03
I've been trying to get a belkin wireless g+ usb network adapter working on a desktop pc running a new install of ubuntu (7.10).

The adapter was detected automatically, and the local network appeared in network manager. Entering details (WPA-PSK) caused the connection to be made correctly and I was online - then about a minute later the signal quality dropped to 0 (although nm thought that it was still connected). This was accompanied by a whole load of dmesg errors:

rt2x00usb_vendor_request: Error - Vendor Request 0x007 failed for offset 0x3090 with error -110.

After playing for a while, I got nowhere. I switched to the Ralink rt73 driver, This seemed to work absolutely fine. However, now if I reboot the computer with the dongle plugged in, the mouse stops working. This appears to happen whether the rt73 module is loaded or not - so I'm not sure what is up :-s. The mouse still appears in lsusb

"Bus 001 Device 002: ID 045e:0059 Microsoft Corp. Wireless IntelliMouse Explorer" (eugh)

If anyone has any idea how to get either the original driver working (the rt73usb one, as it allows network manager to make changing network details somewhat easier), or knows what is up with my mouse it would be really appreciated.

---

### Post by sds50 on 2007-12-19
Never mind, sorted to some degree.

USB issues disappeared if the dongle was attached via a USB hub - must be something to do with power draw or similar. Anyway, it started to work once taht was done....

---

