---
title: "wireless network dies"
date: 2004-12-17
forum: Networking &amp; Wireless
---

### Post by andy_sp1ke on 2004-12-17
My wireless network cuts out after a period of a few minutes inactivity ( i think!) i have currently been continoulsy on webpages surfing around and its ok...but a few minutes idle on IRC and it stops.

Its a toshiba laptop with celeron chip running warty with the normal 386 kernal installed. The NIC is a DLINK G650 air plus which says its HW ver 2 and Firmware ver 3.1.6 and its connecting to a linksys router with no WEP on it which is infracstrutcure on channel 6. 

the card appears in the device mananger asa Atheros Communicatiosn Inc AR5212 802.11abg and IWCONFIG picks it up as ath0. When i run IWCONFIG to set it up i entered just this

IWCONFIG ath0 essid linksys
iwconfig mode managed

and rebooted and it basically worked. each time iwconfig would reveal that the essid id was set and the gnome wireless link monitor would pick up signal strength but not actually be connected as it said accesspoint was 00 00 00 00 00. however at boot now the lights flash and it starts and it finds the accesspoint and i can browse. When it cuts out though it removes the details on the access point and i have to reboot to get it going again. Is there a better way controlling it and is there some software to allow me to browse for wireless networks? a real idiots guide would be appreciated!!

Andy

---

### Post by hypersonic5 on 2004-12-19
I have the same exact problem and I came here to find a solution. My computer is not a laptop like yours but a desktop machine. I also use a D-Link wireless card. Just like you described, the wireless network cuts off abruptly after a couple of minutes of inactivity. I have no idea how to solve it. This is probably the only problem that is keeping me from adopting Linux full time.

Any help would be appreciated.

---

### Post by Averatec5400 on 2004-12-19
[QUOTE=hypersonic5]I have the same exact problem and I came here to find a solution. My computer is not a laptop like yours but a desktop machine. I also use a D-Link wireless card. Just like you described, the wireless network cuts off abruptly after a couple of minutes of inactivity. I have no idea how to solve it. This is probably the only problem that is keeping me from adopting Linux full time.

Any help would be appreciated.[/QUOTE]
 if you are using ndiswrapper (as I see the first poster is) try the windows 2000 driver instead, they are in my short experience more "compatible" than the xp drivers.

You might also try an older version of the driver (still try the windows 2000 instead of XP)

The XP driver did that on my ralink rt2500, 2000 works flawless, posting from it now.

It could also be power saver issue, but I don't know how to resolve that if that is the case.

---

### Post by hypersonic5 on 2004-12-19
I don't know which driver I am using. Ubuntu configured it for me automatically during install. How would I be able to change the driver just in case? My chipset is a TI ACX100.

---

