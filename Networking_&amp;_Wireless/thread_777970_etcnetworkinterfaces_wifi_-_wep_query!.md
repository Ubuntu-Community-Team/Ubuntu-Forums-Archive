---
title: "/etc/network/interfaces wifi - wep query?!"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by markeee on 2008-05-01
Hi guys, 

Just need a bit of help , :)

Just setup my Ubuntu 7.04 box to use a Linksys WUSB11v4 

using ndiswrapper and the windows driver-the device is picked up (checked lsusb output) and it is listed in iwconfig as wifi0 (ndiswrapper -l also lists  the device as having a driver installed!)

Just a bit stuck with regards to making it automatically connect to my wireless network, using WEP and my specified key

I had

iface wlan0 inet dhcp
wireless-essid 02wireless2BC067
wireless-key1 6551CDB1C
auto wlan0

But it seems to not be connecting, iwconfig says 'not associated' 

the essid and key1 don't need to be in quotes or anything do they?

Secondly how does it know wireless-key1 is a wep key and not infact WPA?

Thanks guys

mark

---

