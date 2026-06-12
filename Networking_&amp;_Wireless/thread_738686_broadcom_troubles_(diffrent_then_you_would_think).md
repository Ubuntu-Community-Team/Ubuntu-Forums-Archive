---
title: "broadcom troubles (diffrent then you would think)"
date: 2008-03-28
forum: Networking &amp; Wireless
---

### Post by twist2b on 2008-03-28
Apperently I have the drivers installed. Its detected and everything. I only have Feisty to!

craig@craig-laptop:~$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
Password:
driver bcmwl5 is already installed
craig@craig-laptop:~$ 


I tried installing windows drivers.... seems I didn't have to,

I have a 
"Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card"
So, any ideas on whats wrong? I try to connect to a network and its not connecting. I have a strange router. Its called D-Link. So I dont know it its good and thats the problem. I ididnt add any information besides the SSID.

Ideas?

---

### Post by Gina on 2008-03-29
I got the bcm4306 rev.3 chipset working in Feisty but it wasn't all that easy.  With Gutsy is was a doddle - the Restricted Drivers Manager came up and asked if I wanted to install firmware - I just checked the box and it downloaded the files and installed the firmware.  I was then able to set essid etc. in System > Administration > Network and it worked fine.

I can recommend Gutsy but the latest Hardy is not yet ready and there's a problem with some Broadcom chipsets still.  We're hoping things will be fixed in time for the Hardy release in a few weeks time.

There's still info on getting Broadcom chipsets working in Feisty on my Ubuntu website (see sig).  As I recall I needed ndiswrapper and the Windows driver.

---

### Post by articpenguin on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

try there

---

