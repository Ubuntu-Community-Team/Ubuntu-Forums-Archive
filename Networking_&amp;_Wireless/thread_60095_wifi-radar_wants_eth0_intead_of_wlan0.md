---
title: "wifi-radar wants eth0 intead of wlan0"
date: 2005-08-26
forum: Networking &amp; Wireless
---

### Post by kneewobbler1 on 2005-08-26
Let me apologize if this has been brought up before somewhere, but I looked real hard for the better part of the day, and didn't find anything similar.

I got my laptop with a Linksys wpc54g pcmcia working under UHH, thanks to linuxant driverloader. (tried ndiswrapper beforehand, that also got me connected by the way).
All roses, except for "wireless roaming". My problem is, wifi-radar (the latest ubuntu .deb), only looks for eth0, but should find wlan0.
"sudo iwlist wlan0 scan" nicely shows my two 802.11b/g wep-enabled networks.

I tried to tweak '/etc/network/interfaces', but that doesn't help. I can't find a command line switch for wifi-radar or a config file to direct it towards wlan0.
This prevents me from switching networks.
"sudo gtkwifi run-in-window" also fails, probably for the same reason (the app freezes).
Do I need to alias my eth0 somewhere?
For completeness' sake, my laptop only has one network slot, wlan0.

Any suggestions are greatly welcomed!

---

### Post by Chrissss on 2005-10-08
You've got to edit /etc/wifi-radar.conf, it should look like this

```
[DEFAULT]
scan_timeout = 5
auto_profile_order = any
speak_up = False
ifup_required = False
interface = wlan0
commit_required = False

[yourssid]
mode =
key = whatever
use_dhcp = yes
security =
channel =
```

CU
 Chr

---

