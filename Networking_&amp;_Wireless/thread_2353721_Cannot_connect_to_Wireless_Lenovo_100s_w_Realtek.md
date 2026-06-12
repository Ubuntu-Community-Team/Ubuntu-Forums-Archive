---
title: "Cannot connect to Wireless Lenovo 100s w/ Realtek"
date: 2017-02-24
forum: Networking &amp; Wireless
---

### Post by shaanx on 2017-02-24
So after struggling to even get Ubuntu installed, I managed to get it running and now i cannot connect to wireless networks, except, strangely iPhone 6+ in personal hotspot. My home router is an Airport Express and I tested it at work on an unknown router. I get the constant "bad password" prompt in Network Manager. I've tried things in wpa_supplicant that I have seen on various forums but to no avail. Just to get a fresh start I reinstalled 16.04.2 LTS to make anything I screwed around with worked. I am assuming it must be a driver issue or something along those lines as I have a separate and  fully functional 16.04 laptop that connects fine. 

here is a pastebin of the info script: [http://pastebin.ubuntu.com/24058780/](http://pastebin.ubuntu.com/24058780/)

any suggestions would be greatly appreciated !

---

### Post by wildmanne39 on 2017-02-25
Hello, please tell us what network are you trying to connect too, and is this an internal device?
Thanks

---

### Post by shaanx on 2017-02-25
thanks for the reply,
It is an Apple Airport Express that I am trying to connect to, 802.11n/dual band etc. yes it is the internal card,I am working around it by using a usb dongle currently.

---

### Post by wildmanne39 on 2017-02-25
I mean the name of the network so I can check it in the file you posted to pastebin.

---

### Post by shaanx on 2017-02-25
oh sorry, it is "Shaan's Wi-Fi Network"

---

### Post by wildmanne39 on 2017-02-25
Your device is trying to connect to another network, you have so may within range, please go into your router and set the channel to 5 then your encryption to WPA2 only not messed mode, then save the settings.

Go into network manager and change the settings to match the screnshots.
Reboot

---

