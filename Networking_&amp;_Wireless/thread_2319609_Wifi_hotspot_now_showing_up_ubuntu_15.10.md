---
title: "Wifi hotspot now showing up ubuntu 15.10"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by armon2 on 2016-04-06
Hi, so I am currently connected to the interwebs through an ethernet cable out of the modem that I have here in my apartment. However, when i try and create a wifi hotspot through network it doesnt create it. I go to network, click on wireless, click on use as a wifi hotspot, it creates a ssid and wep key for me. But yet, there is no wifi showing up on any other devices in the house, and to top it all off. It doesnt configure the wifi hotspot, it eventually says wireless disconnected or whatever and remains as an ethernet connection with no wifi hotspot to show on nay device...

---

### Post by gordintoronto on 2016-04-06
What is your wireless hardware? It should show up when you enter one of these commands: lspci or lsusb

Actually, if you are in an apartment, network manager should show you several SSIDs if your Wi-Fi device is supported. You might need to pull the Ethernet cable to get there.

Oh, and I suspect you meant "Wifi hotspot *not* showing up..."

---

