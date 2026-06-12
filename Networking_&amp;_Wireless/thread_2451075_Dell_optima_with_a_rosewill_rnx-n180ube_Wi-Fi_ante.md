---
title: "Dell optima with a rosewill rnx-n180ube Wi-Fi antenna won't connect."
date: 2020-09-26
forum: Networking &amp; Wireless
---

### Post by nekroskoma on 2020-09-26
I have an old Dell Optima that I just installed Ubuntu 20.04 on, after updating it through Ethernet installing the drivers when I attempt to connect to the Wi-Fi it will continuously connect and then ask me for the password and then try to connect again and then asked me for the password. It'll keep doing this until it finally gives up and it will never connect. I have no idea why it's doing this I've installed the drivers through the official channels and I've tried to compile the drivers from rosewill but they will not compile correctly. When I try to compile the driver it gives me 'make compile driver error 2'.

---

### Post by morrownr on 2020-09-26
Hey, I have one of the those Rosewill RNX-N180UBE wifi adapters. It is the only wifi device that I have that won't work under linux. It used to work well but since around 16.04, it has not worked well.

It uses a Realtek 8191su chipset. I have chased down the details and supposedly it is internally supported by, I think, the rtl8187 driver, but that driver is broken as the device will just cycle on and off. If you have a link to anything that might help us bring it back to life, please pass it on.

If you need a device that works right now, I can suggest some.

Edit: I just checked. It appears that Rosewill has released 3 versions of the RNX-N180UBE over time and all 3 have different chipsets. Mine, evidently, is a v1. What version is yours and what chipset is in it? It might help you run the script in the Sticky at the top.

---

### Post by CelticWarrior on 2020-09-28
RTL8191SU works perfectly fine OOB. 

Yes, please run the wireless script and post results.

---

