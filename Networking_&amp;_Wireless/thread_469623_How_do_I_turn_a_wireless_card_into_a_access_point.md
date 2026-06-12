---
title: "How do I turn a wireless card into a access point"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2007-06-10
I have a device that I use online fairly rarely (NDS) that only supports wep encryption and would like to turn my spare usb wireless nic when plugged in into a AP for it. Then have all the traffic forwarded to my WPA2-PSK (AES) encrypted network. How would I go about this.

My usb wnic is a cheap 802.11b only atmel based card that is assigned wlan0 when plugged in.

All traffic should be forwarded to eth1 which is a bcm43xx card using ndiswrapper and already working as my standard internet connection.

If possible I would like wep encryption so that when I am online with the ds my neighbors can't use my connection also.

---

### Post by spd106 on 2007-06-10
It depends on what kind of chip you have in the card. Check the hostapd website for details on configuring an AP, [http://hostap.epitest.fi/](http://hostap.epitest.fi/).

---

