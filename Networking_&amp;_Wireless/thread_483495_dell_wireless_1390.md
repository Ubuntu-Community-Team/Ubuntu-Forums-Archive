---
title: "dell wireless 1390"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by sidprak on 2007-06-24
i am trying to get my wireless internet working with a dell wireless 1390 wlan card.

I installed ndiswrapper and installed the windows driver for the card.  When i go to System>Administration>Windows Wireless Drivers, i see that the drivers have been installed, but it says that the hardware is not present, when it is connected to the computer.  Is there any way to get the wireless to work??

Thanks!!

---

### Post by jpeddicord on 2007-06-25
This is a shot in the dark, but try running this:
```
sudo modprobe ndiswrapper
sudo depmod
```

If you are lucky, the card will reappear in the tool.

---

