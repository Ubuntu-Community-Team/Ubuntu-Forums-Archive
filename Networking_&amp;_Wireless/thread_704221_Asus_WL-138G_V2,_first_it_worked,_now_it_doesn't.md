---
title: "Asus WL-138G V2, first it worked, now it doesn't"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2008-02-22
I've followed kevdog's guide on my install, and initally it worked. However the last few times I've gone to use it it's just not worked, and there's also a weird thing happening with my wired interface still being up, even though I've got it disabled in my rc.local.

Here's a few facts about my setup
[LIST]
[*]Gutsy 7.10
[*]Asus WL-138g V2
[*]Restricted driver is installed
[*]Wireless is eth0
[*]Wired is eth1
[*]Range and signla are good in XP (machine is dual boot)
[*]AP is using WPA1
[/LIST]

And here's my rc.local as best I can recall it
```
ifconfig eth1 down
ifconfig eth0 down
dhclient -r eth0
wpa_supplicant -w -Dwext -ieth0 -c/etc/wpa_supplicant.conf -dd
ifconfig eth0 up
iwconfig eth0 mode Managed
dhclient eth0
```

Have I combined the two instruction sets properly? Or have I done something stupid?

---

### Post by Cadmus on 2008-02-22
Would switching to an ndiswrapper rather than the restricted driver help me at all?

---

