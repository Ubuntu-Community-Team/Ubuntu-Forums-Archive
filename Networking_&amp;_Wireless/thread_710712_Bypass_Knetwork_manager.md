---
title: "Bypass Knetwork manager"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by csall on 2008-02-28
I have finally gotten my bcm4318 wireless card up and running. However, I would to be able to bypass using Knetwork manager, I have no use for it. I want only to connect to my wireless. I would like to be able to edit my /etc/network/interfaces file to automatically boot up my wireless card and the proper settings. This how have previously achieved this:

auto wlan0
iface inet dhcp
wireless-essid GRUNDLE
wireless-enc 1234567890

However, this does not work it does not connect at all. I have also tried using several command line prompts as well:

sudo iwconfig wlan0 essid GRUNDLE
sudo iwconfig wlan0 enc 1234567890
sudo iwconfig mode managed
sudo iwconfig ap 12:34:56:67:90:12

even with trying to force it the access point i still get no connection. The only way i cannot to the internet is to use Knetworkmanager, select connect to other wireless network fill in my info and make sure i select WEP 40/104 Hex.

I think somewhere in those iwconfig commands I need something that specifically sets it to a 40/104 hex key. I've never had to that before the regular set essid command has always worked. 

Thank in advance for your help!

---

