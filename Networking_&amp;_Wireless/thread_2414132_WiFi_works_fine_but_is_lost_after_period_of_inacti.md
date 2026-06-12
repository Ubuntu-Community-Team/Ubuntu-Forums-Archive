---
title: "WiFi works fine but is lost after period of inactivity"
date: 2019-03-06
forum: Networking &amp; Wireless
---

### Post by veanidon on 2019-03-06
I have a Dell Inspiron 15 3000 (AMD A6 processors) with an Intel Dual Band Wireless - AC 3165 network card. The machine is dual bootable with Ubuntu 18.10 and Windows 10. The Wifi is configured and successfully connects to the network. On Ubuntu the WiFi works well as long as I keep working but after a short period of inactivity the WiFi  is lost and an attempt to reconnect gives 'No Wi-Fi Adaptor Found'. Upon reboot the WiFi works fine again until the next period of inactivity. This happens on both battery and when on mains power. This looks like the problem relates to the energy saving feature that shuts off the WiFi when inactive to save power. In Windows 10 this feature can be turned off but I cannot find a way to do this in Ubuntu. Does anyone know a way of disabling the power saving feature with WiFi possibly as a command line command(s). Out of interest Bluetooth works fine and does not have this problem. Any thoughts would be welcome !!!!

---

### Post by kc1di on 2019-03-06
[Here is how]("https://askubuntu.com/questions/85214/how-can-i-prevent-iwconfig-power-management-from-being-turned-on") to turn off the power manager for you wireless card. (note use Answer 21). Good Luck.

---

### Post by veanidon on 2019-03-06
Thanks Dave, Answer 21 looks to have done the trick! Cheers

---

### Post by kc1di on 2019-03-07
Glad it worked for you - Enjoy :) 
Take a moment and mark the thread as solved.

---

