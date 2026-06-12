---
title: "black screen after unsuccesfull wifi install"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by Zephir on 2006-07-29
Hi all,

Guess this is another beginner-problem! I tried to install my d-link wifi-usb (DWL-G122) but the thing doesn't work :( 

I tried the howto on wifi, the [COLOR="Blue"]prism2_usb[/COLOR] is on my machine, [COLOR="Blue"]lsusb[/COLOR] tells me there's an wifidongle on it, but [COLOR="Blue"]iwconfig[/COLOR] says '[COLOR="Blue"]no wireless extensions[/COLOR]' and never came across the [COLOR="Blue"]ath0[/COLOR] neither.

The next time I did a reboot I noticed that my machine errored in starting up network setting (failed), and give me a black screen. Sometimes rebooting in [COLOR="Blue"]recovery mode[/COLOR] without the ethernet cable plugged in helps, but that's no good isn't it.

my setup:
Compaq Evo600c portable (PIII) with dapper on it.
D-LINK DWL-G122 vC1
Philips Wifi Router
(and another WinXP portable too)

Anyone any ideas pls? :confused:   thanks!!

btw
[COLOR="Blue"]**cat /etc/network/interfaces:**[/COLOR]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid WiFi


But what does it mean?

---

