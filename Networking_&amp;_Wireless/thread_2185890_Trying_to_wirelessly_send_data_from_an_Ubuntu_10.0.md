---
title: "Trying to wirelessly send data from an Ubuntu 10.04 laptop to a Windows 8 laptop"
date: 2013-11-04
forum: Networking &amp; Wireless
---

### Post by steven.bensics on 2013-11-04
I have an old dying laptop (can't detect battery, busted CD/DVD reader, screen is losing pixels and showing lines) that has Ubuntu 10.04; I have tonnes of videos and mp3s on there that I want to salvage. I have a newer laptop with Windows 8; I want to wirelessly send data from the old Ubuntu 10.04 laptop to the Windows 8 laptop (they are both connected to the internet right now through the same WiFi router). 

Is there an easy way to do this? Thanks!

---

### Post by cjhabs on 2013-11-04
> **steven.bensics said:**
> I have an old dying laptop (can't detect battery, busted CD/DVD reader, screen is losing pixels and showing lines) that has Ubuntu 10.04; I have tonnes of videos and mp3s on there that I want to salvage. I have a newer laptop with Windows 8; I want to wirelessly send data from the old Ubuntu 10.04 laptop to the Windows 8 laptop (they are both connected to the internet right now through the same WiFi router). 

Is there an easy way to do this? Thanks!

I would install WinSCP on the Windows laptop and use it to connect to the Ubuntu laptop and copy the files.
This way you can do everything from the new laptop - and it'll use ssh which should already be in place on the Ubuntu laptop.

---

