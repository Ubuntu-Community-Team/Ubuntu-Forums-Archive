---
title: "Set Wireless Config w/o root access"
date: 2006-09-26
forum: Networking &amp; Wireless
---

### Post by ineluki12 on 2006-09-26
Hello,
I just got my *&^% Broadcom wireless card working ](*,) , and now I'd like to automate things a bit. My current idea is to create a single Bash script for each wireless network I use. I would like the script to execute the following commands:
```

iwconfig eth1 key open [KEY]
iwconfig eth1 essid [SSID]
dhclient eth1

```
Problem is, these commands require root privilages, so they all have to be sudo'd. Is there a way to allow user-privilaged scripts to set the wireless settings? I'm trying to avoid scripting root access, as that's a big security risk.

Thanks!

---

