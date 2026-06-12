---
title: "Wifi Will Not Connect"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by joey-elijah on 2009-02-25
I have a USB dongle that i use via Ndiswrapper with its Windows driver and it was working fine.
 
 It can see the available networks, i can choose to select and enter my WAP/WEP password but it just never connects; the status icon just spins around and around.
 
 I can connect with ease in Windows 7, on my EeePC (running ibex) and (before my power cable died yesterday) in OS X.
 
 What's up with Ubuntu? Is there a way to get it to connect? I assume it's having issue getting the required DCHP/IP from the router?

---

### Post by Patricrawley on 2009-03-03
Try this out, I used to have a similar issue of getting disconnected and then not being able to reconnect.
```
sudo rmmod ndiswrapper
```
Physically unplug the USB dongle and plug it back in
```
sudo modprobe ndiswrapper
```

---

