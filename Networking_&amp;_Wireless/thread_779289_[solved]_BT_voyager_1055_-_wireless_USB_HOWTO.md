---
title: "[solved] BT voyager 1055 - wireless USB HOWTO"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by crackshot1980 on 2008-05-02
Hi,

I've managed to configure the BT voyager 1055 wireless USB dongle that comes with the basic BT Home hub package.

I can't claim the credit for making it work - just for following the instructions! 

use the [rndis_wlan driver]("http://linuxwireless.org/en/users/Drivers/rndis_wlan") here, [download and follow the instructions]("http://linuxwireless.org/en/users/Download").

It's pretty simple - after installing, I restarted and voila, the USB dongle worked!

I've used the [community howto for wireless]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo") to configure the USB stick from there.

with the /etc/network/interfaces file as follows.
```
iface wlan0 inet dhcp
wireless-channel 11
wireless-mode managed
wireless-key 0123456789
wireless-essid BTHomeHub-A123

auto wlan0

```

Good luck, fellow Tuxers!

---

