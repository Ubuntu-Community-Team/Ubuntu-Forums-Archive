---
title: "Wireless Network disconnects periodically using Belkin"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by shoeshrimp on 2008-02-11
Hey Guys,

My wireless network USB Belkin dongle thingie (FD7050) works amazingly in Ubuntu - I was really impressed. I just plugged it in, and ubuntu went "yep, there's your internet". Fab. The only problem is that pretty much every time I go on the internet after 10-30mins the connection drops, and the wireless icon disappears from the "taskbar" (not sure what you call it) at the top. I can't get it reconnected even if I shuffle around USB ports. The only way is to restart, and then it's fine (for another 30mins). Does anyone have any ideas as to why? I'm using Ubuntu 7.10

---

### Post by tangibleorange on 2008-02-11
Does your wireless network use WPA?

Also do you know what chipset and driver your card is using? If you don't know, when you are connected to the internet, right click on the network icon and select "Connection Information", and post what is says next to "Driver".

---

### Post by shoeshrimp on 2008-02-11
> **tangibleorange said:**
> Does your wireless network use WPA?

Also do you know what chipset and driver your card is using? If you don't know, when you are connected to the internet, right click on the network icon and select "Connection Information", and post what is says next to "Driver".

Driver is: rt73usb, the chipset of the USB dongle is F5D77050B. It does use WPA, yes.

---

### Post by tangibleorange on 2008-02-11
Aha. I think the rt2x00 drivers have a bug which means that this happens with WPA. I had the same problem with my rt61pci driver. You might want to look into ndiswrapper. There is a great guide showing how to use it by wieman01:

[_Guide_]("http://ubuntuforums.org/showthread.php?t=564419")

---

