---
title: "Strange: to connect my ssid, must first connect my neigbour's essid"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by mr_delphi on 2007-04-20
in the past, everything is ok: ndiswrapper+wapsupplicant
now in feisty old settings never work

my current setting is network-manager+ndiswrapper+wpa personal
i can always see all the ssid nearby, but i must first connect my neighbour's ssid (or at least attempt connecting, his is unecrypted) then disconnect it and connect my own...and it takes forever.


if i put everything into the interface file: like MY ssid, psk, ... in a correct fashion as described here, after restart, the network-manager does not work, but wlan0 still connects to my neighbour's ssid. 

He is using dlink router, mine is linksys

Somebody saves me. If one day my neighbour moves out, i can't use internet!!!

---

### Post by gspathoulas on 2007-04-21
Hello,

I have a similar problem.

I installed Feisty and everything seems to work great except from the network manager.

I have a Compaq Presario r3000 with a built in Broadcom 4303 b card.

I installed ndiswrapper and used the windows driver, and everything seems to work fine.

But when network manager tries to connect nothing happens.

If I disable the roaming mode and use dhcp or static ip my wireless network disappears from the manager and I see only wired network.

If I enable  roaming mode then I see my network. But when I connect to it I have no internet.

They only way to make it work is :

Choose connect to another network.
Give a random SSID name. (The new network is created in the manager, and is selected)
And then reselect my original SSID. 
This way I get internet until my next shutdown.

Anybody has any idea about that ???

Thank you

---

### Post by mr_delphi on 2007-04-21
I finally solved the problem. My interface file is now like this. (using this, I have to uninstall network manager. I also deleted the file \etc\default\wpasupplicant)

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
#wpa-conf managed
wpa-ssid XXXXXXXX
wpa-ap-scan 2
wpa-proto WPA 
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

my setting: wpa personal + ndiswrapper

---

