---
title: "Annoying WiFi connection problems"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by 5hadow5un on 2010-12-12
I am using a Linksys WUSB600N WiFi adapter.  It works just fine WinXP, worse with Lubuntu 10.10, even worse with Ubuntu 10.10.  What happens is that I can connect, even surf the web for a short period of time (very short, usually no more than a few minutes) before my connection is lost.  What was really odd was that when I first connected the adapter to my PC, I was running Lubuntu 10.10, it was recognized and I proceeded to download a 550MB+ iso file...which took under 10 minutes.  Now, I cannot seem to stay online under Ubuntu/Lubuntu...ideas?

---

### Post by kittkatt on 2011-05-05
I had a similar problem and found out that the reason for it was because the device was set in power-saving mode and would not wake after it sleeps.  This is why it works for a bit but then "dies".  I fixed it by setting the device to CAM (constantly awake mode).  This might work for you

---

### Post by sadaruwan12 on 2011-05-05
Or you can use the ndiswrapper to wrap the windows drivers on you linux system and use the WiFi I got my dongle working without any issue using this software.

It's available in the repository.

---

