---
title: "D-LINK DWL G-122 c1"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by joaomario@edgy on 2006-11-20
Hi folks,


This wireless card gets recognized on my computer, but it simply won't work. I'd like to know if I need to install the windows drivers on Edgy with ndiswrapper, or if I am not doing the configuration as I should.

I did the iwconfig for ESSID + WEP KEY + AP, etc, then restarted it with ifconfig wlan0 up. When I do the dhclient command, it says the signal is being sent on fallback, and I don't see the "Act" led to actually act on the device.

---

### Post by FrodoB on 2006-11-20
The driver that recognizes your device will not work. See this document and follow carefully and it will work:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29#preview)

---

### Post by joaomario@edgy on 2006-11-21
Thanks Frodo...

This is one very good tutorial. I was able to install the driver properly and now I am close to get internet. I've posted another thread, so now there are some matters on configuring it to work in the network.

---

### Post by unarmedninja on 2006-11-22
this card also works with ndiswrapper as well. just blacklist those two modules from that tutorial frodo mentioned then use the windows drivers from the cd (DR71WU.INF and DR71WU.SYS). this might be easier than compiling linux drivers.

---

### Post by joaomario@edgy on 2006-11-22
Yesterday I finally got it!!! Thenks everybody, now there is a minor problem; the connection keeps falling and then the only way to get it up again is disabling/enabling the device. When I do the dhclient command, it says "4000 secondos to restart...". 

How can I do to get it working without interruptions?


Thanks...

---

### Post by FrodoB on 2006-11-22
The 4000 seconds is coming from your DHCP server You need to configure the time of the lease on your router or access point, whichever is serving DHCP.

---

