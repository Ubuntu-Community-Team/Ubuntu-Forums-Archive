---
title: "Networking"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by Kchymet on 2009-12-17
Ok, so Ubuntu randomly stopped working last night, so I installed karmic again as a Dual-Boot with my broken karmic today. I can't seem to figure out how to connect to a wireless network though. I have all my information, but when I enter it and select "Connect Automatically" my laptop will not connect.

My network SSID does NOT appear in a list or anything like the help guide says it will, and I can only connect to the internet with an extra ethernet cable I was lucky enough to find. My router is a Linksys WRT54G

---

### Post by 3rdalbum on 2009-12-17
So your local SSIDs don't appear when you click on the Network Manager applet? Sounds like your wireless card doesn't have a driver.

Reload the package list in Synaptic and check the Hardware Drivers program to see if you are offered a driver.

If you aren't, then please post the output of the 'lspci' command (that's a lowercade L)

---

