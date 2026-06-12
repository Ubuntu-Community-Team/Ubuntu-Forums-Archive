---
title: "Belkin F5D7000 Wireless version 1134"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by donnob on 2008-03-07
I have a Belkin F5D7000 Wireless Network Card, version 1134 that works fine on my computer when I use Windows XP but will not work with Ubuntu, version 7.10.

I found a suggested solution at... [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)

It says: Must manually set frequency to that of your router using sudo iwconfig <wlan0> channel <channel>. To find your router's frequency use iwlist <wlan0> scan. bcmw15a.inf can be found as part of R74092us.exe

That sounds like GREEK to me since I am brand new to Linux/Ubuntu.

I tried this...

sudo iwlist wlan0 scan

and got this after entering my password...

wlan0     interface doesn't support scanning

HELP!!!

Don

---

