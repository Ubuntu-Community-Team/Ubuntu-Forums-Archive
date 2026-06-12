---
title: "Internet connection listed but unable to connect to anything"
date: 2017-04-16
forum: Networking &amp; Wireless
---

### Post by topkek on 2017-04-16
I recently did my first Ubuntu install ever, and more specifically, Ubuntu 17.04. After I finished installing I tried to access the internet only to be greeted by "Server not found". After some digging I tried manually changing the IPv4 settings, that didn't work. I checked "Connection Information" for it to show 1 GiB internet and no security. All the IPv4 settings were correct, and I added Google's DNS's (8.8.8.8, 8.8.4.4). I later tried to use terminal and imputed "ping -c 5 Google.com", receiving the message "ping: Google.com: Name or Service not know". When I boot into Windows, my ethernet connection is perfectly fine and works 100% of the time. Nothing is working and I can't download anything to diagnose it. What can I do?

Specifications:
MotherBoard: ASUS M5A78L-M USB3.0
CPU: AMD FX-4300
GPU: EVGA NVidia GTX 960 SSC
RAM: 16GB
HDD(Windows): 1TB
SSD(Ubuntu): 120GB
FlashDrive with Ubuntu .iso: 8GB
NO CD/ROM bays
NO WiFi Capabilities
Using Ethernet port

---

### Post by wildmanne39 on 2017-04-16
*Thread moved to **Networking & Wireless**.*

You only have an ethernet connection, no wifi that needs fixed?

---

### Post by topkek on 2017-04-16
@Moderators
Fixed, Started working randomly

---

### Post by wildmanne39 on 2017-04-16
For the changes to take effect that you made it would require restarting network manager or rebooting the computer.

---

