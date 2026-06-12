---
title: "WPA-PSK security in Feisty Fawn with Netgear wg111v2 usb"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by Ghost_Dog on 2007-12-18
Could anyone tell me how I could enable the WPA-PSK dropdown menu in
the wireless options or any other way to allow for me to connect to wireless networks
with WPA-PSK encryption.

---

### Post by spd106 on 2007-12-19
Network Manager (in roaming mode) will attempt to find the encryption type from the essid broadcast signal of your AP. So it will provide you with what it finds. Alternatively you can select the encryption type by using the Connect to other Wireless Network... option.

Manual configuration of WPA is not supported by the default gui tools in Ubuntu 7.04, so you'll have to upgrade to 7.10 or find another wireless manager if you need a gui.

If you're happy editing text files then see the Wireless Security sticky by wieman01 for details.

---

### Post by wieman01 on 2007-12-20
> **Ghost_Dog said:**
> Could anyone tell me how I could enable the WPA-PSK dropdown menu in
the wireless options or any other way to allow for me to connect to wireless networks
with WPA-PSK encryption.
If WPA is not supported by the driver, the WPA option won't appear. So probably need to replace the driver using "ndiswrapper" or compile the latest version yourself.

What hardware have you got?

---

### Post by Ghost_Dog on 2007-12-20
From typing **lsusb | grep NetGear** it comes up with NetGear, Inc. WG111 WiFi (v2).
The wireless worked straight out of the box but I had to change the security to WEP because the wireless card wouldn't support WPA-PSK. I'm also pretty happy with feisty fawn so I don't think I'll want to upgrade until the next version.

---

