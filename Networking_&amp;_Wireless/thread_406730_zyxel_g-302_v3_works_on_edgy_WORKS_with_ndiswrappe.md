---
title: "zyxel g-302 v3 works on edgy WORKS with ndiswrapper"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by m_bridge on 2007-04-11
Hi, today i got a Zyxel G-302 v3 Wireless PCI Card
the device initially shows up in *lspci* as Unknow device 8185

i followed the instructions for ndiswrapper
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

also this was useful
[http://ubuntuforums.org/showthread.php?t=9454]("http://ubuntuforums.org/showthread.php?t=9454")

it seems to work sweet!

with WEP configured, my /etc/network/interfaces looks like that:
```
iface wlan1 inet dhcp
wireless-essid xxxxxxxx
wireless-mode Managed
wireless-key xxxxxxxxxx #(this is the hex key)

```

*sudo ifup wlan1* brings up the interface without problems


i am currently on 2.6.17-11-generic #2 SMP

---

