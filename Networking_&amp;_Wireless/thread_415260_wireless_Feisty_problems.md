---
title: "wireless Feisty problems"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by rock lobster on 2007-04-20
I have just installed Feisty Fawn on my Laptop (Hp ze4800) My wireless card consists BCM4306 802.11b/g Wireless LAN. I have a linksys wireless B Router with WAP 128bit encryption enabled. The thing is i can see the laptop trying to connect to the wireless network but just never connects at all. I have also installed ndiswrapper but that has not worked either. im out of ideas and i dont have much experience with wireless on linux. Please help thank you

---

### Post by Kobalt on 2007-04-20
Try to install the *ndisgtk* package and fire it up under System -> Administration -> Windows Wireless Drivers, it will install your card using windows drivers in a graphical way. 
You will then be able to use your card properly with WPA encryption through Network-Manager.

---

### Post by rock lobster on 2007-04-20
I tried installing that sadly it did not work. It says that my device is not present. any ideas i know i have gotten Ndiswrapper to work in the past but for some reason not since 6.06.

---

