---
title: "wireless trouble"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by shaunybo on 2007-11-05
i have installed the rt73 driver for my belkin F5D7050 usb adaptor but still the light does not come on how do i, check if it is installed or does anyone know how to help me out? im new to ubuntu

---

### Post by spd106 on 2007-11-06
Might be a good idea to look at this help page [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73)

If the card is properly installed you should see it appear in System -> Admin -> Network and there will be an icon in the notification area to select a wireless network from a list.

If you still aren't having much success try opening a terminal and run the following command and you should be presented with configuration information.
```
sudo lshw -class network
```

---

