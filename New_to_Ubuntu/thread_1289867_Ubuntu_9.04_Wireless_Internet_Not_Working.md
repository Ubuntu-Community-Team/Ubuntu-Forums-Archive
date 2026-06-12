---
title: "Ubuntu 9.04 Wireless Internet Not Working?"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by marcelluspye on 2009-10-12
I have recently installed Ubuntu 9.04 on an old computer, and also have Windows XP installed. I am unable to connect to the internet via WiFi connection (WEP 40/128-Bit Passphrase protected), but only in Ubuntu, on that computer. If I boot Windows I can connect, and if I get on my Dell Netbook w/ 8.04 installed with the same settings I can connect, but Ubuntu on that computer will not allow me to connect. What must I do to solve this problem?

---

### Post by PrePenguin on 2009-10-12
Try sudo apt-get install ubuntu-restricted-extras and see if a driver is in the program manager for you to load.. If not try disabling the lan in the bios for sometimes they bump heads in ubuntu with a resource conflict. Is it showing your wireless card with available networks too i guess would be the first thing to ask?

---

### Post by scared0o0rabbit on 2009-10-12
If you can see the networks, but just can't get connected to them you might try using wicd instead of the default network manager that comes with ubuntu.  I had a similar problem and that fixed it for me.

---

### Post by mapes12 on 2009-10-13
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

---

