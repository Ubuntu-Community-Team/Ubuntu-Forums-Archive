---
title: "EE no devices detected after changing graphics card"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by sparker1 on 2010-02-12
Hello, I have Ubuntu Karmic and the system was working well.....until I messed with it. I changed graphics cards from a NVIDIA GeForce 8400Gs to an Asus AX300SE-T i.e. an ATI Radeon X300SE. I get an "EE no devices detected-no screens found" at boot. I have saved all the logs if anyone wants them. I have to go to low graphics mode option for boot but it actually has excellent resolution when the desktop loads. If I go to a console and use
 lshw -c display
 the ATI card shows up as installed.  When I go to "system-administration" the Nvidia x server settings are still there and I think that might be the problem. Do they They need to be uninstalled somehow??

---

### Post by gordintoronto on 2010-02-12
Yes, you should have removed the nVidia proprietary driver before you removed the card.

---

