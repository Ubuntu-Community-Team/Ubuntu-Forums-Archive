---
title: "getting on internet with belkin n+ router"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by viper3500 on 2009-08-29
hi i am new to ubuntu and i have no idea how to get ubuntu to recognize my adapter. its model is f5d8055 please help

---

### Post by sandyd on 2009-08-29
are you talking a bout your router or your wireless card?

---

### Post by viper3500 on 2009-08-29
usb wireless adapter sorry

---

### Post by viper3500 on 2009-08-29
do you know what to do

---

### Post by mapes12 on 2009-08-30
Have you clicked on the Network Manager icon and enabled wireless then entered your SSID and passphrase? If you can't do this then we need to look at your USB wifi device. In Terminal ```
lsusb
``` and post the output back here.

---

### Post by ithinkitschad on 2009-08-30
Hey I've never had the problem, I got an older belkin that works great. But I found this. Maybe it will help.

> 
Well, that is very useful information. Took me days trying to figure out why the drivers worked in 8.10 but not 9.04. Now it works correctly :grin:

Anyway, i have a Belkin N+ USB adapter (F5D8055v1).
Steps to get it working for me:

1) Download drivers from Ralink ([http://www.ralinktech.com/ralink/Hom...ort/Linux.html]("http://www.ralinktech.com/ralink/Home/Support/Linux.html")). Right now, its 2009_0521_RT2870_Linux_STA_V2.1.2.0.tgz

2) Extract drivers. I extracted to /usr/src.

3) Delete existing rt2870sta driver. Refer to quote above for exact location

4) Edit os/linux/config.mk. Change values of 
HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

5) Edit os/linux/usb_main_dev.c

6) Look for line: {USB_DEVICE(0x050d,0x815c)}, /* Belkin F5D8053 */

7) Add new line below the above: {USB_DEVICE(0x050d,0x825a)}, /* Belkin F5D8055 */

8 ) Save and close file

9) sudo make && sudo make install

10) sudo modprobe rt2870sta
Network manager should now start scanning for wireless networks

To load module at startup...
11) edit /etc/modules. Add new line: rt2870sta

That it :grin:
Original post - [http://ubuntuforums.org/showthread.php?p=7510417#post7510417](http://ubuntuforums.org/showthread.php?p=7510417#post7510417)

Good luck g

---

