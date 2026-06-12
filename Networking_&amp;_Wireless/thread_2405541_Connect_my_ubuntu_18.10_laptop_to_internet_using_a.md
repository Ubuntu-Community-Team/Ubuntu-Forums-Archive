---
title: "Connect my ubuntu 18.10 laptop to internet using android phone bluetooth tethering"
date: 2018-11-07
forum: Networking &amp; Wireless
---

### Post by lrmunoz on 2018-11-07
Hello,

I use the pdanet app on my LG V30 android phone to use bluetooth tethering. When I was using windows it was easy to connect to internet via phone bluetooth by using pdanet app on my LG V30 but I have not been able to find a way to connect my laptop to internet through bluetooth now that I switched to Ubuntu. 

Does anyone know a way to connect to the android bluetooth data connection? I found some descriptions but they  are from older versions of ubuntu using "network manager" but I cant find the equivalent current method to use bluetooth phone as a network connection. I would appreciate any help since I would prefer to use Ubuntu all the time.

Thanks!

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

To use the bluetooth tethering, the laptop/computer and android device should be paired. You can pair the two devices using blueman-applet on Ubuntu and bluetooth setting of android phone. Once the devices are paired, go to Network Manager where the bluetooth device should be shown as connection, enable/connect it. In case if it is not shown as connection, add the device to the manager and enable the connection.

Please check the box connect automatically to this network when available if you want to auto-connect. (I used the android's native bluetooth tethering app from the settings.)

Regards,
Mitesh

---

