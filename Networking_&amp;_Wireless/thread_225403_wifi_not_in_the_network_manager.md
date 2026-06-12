---
title: "wifi not in the network manager"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by Zephir on 2006-07-29
Hi people, ;) 

I can't get my wifi activated, here's the story:

I tried the howto on wifi, the [COLOR="Green"]prism2_usb[/COLOR] is on my machine, [COLOR="Green"]lsusb [/COLOR]tells me there's an wifidongle on it, but [COLOR="Green"]iwconfig [/COLOR]says 'no wireless extensions' and never came across the ath0 neither.

The next time I did a reboot I noticed that my machine errored in starting up network setting (failed), and give me a black screen. Sometimes rebooting in recovery mode without the ethernet cable plugged in helps, but that's no good isn't it.

my setup:
Compaq Evo600c portable (PIII) with dapper on it.
D-LINK DWL-G122 vC1
Philips Wifi Router
(and another WinXP portable too)

Anyone any ideas pls? thanks!!

btw
[COLOR="Green"]cat /etc/network/interfaces:[/COLOR]

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
iface wlan0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid WiFi

---

