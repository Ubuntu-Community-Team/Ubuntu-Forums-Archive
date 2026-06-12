---
title: "USB wifi: No connection after 12.04 -&gt; 14.04 upgrade"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by paapu on 2014-08-25
Dear All,
I upgraded from 12.04LTS to 14.04LTS and lost my internet connection.
My modem is wireless 4G/3G/2G: Sierra Wireless 4G LTE WLAN S
and I use it vie USB cable on my desktop.

It worked fine in 12.04LTS after adding the following lines to (someone told me to this and it worked on 12.04) 
 /lib/udev/rules.d/81-mm-sierra.rules
```

SUBSYSTEM=="tty", ATTRS{idVendor}=="1199", ATTRS{idProduct}=="68a3",ENV{ID_MM_CANDIDATE}="0"
SUBSYSTEM=="net", ATTRS{idVendor}=="1199", ATTRS{idProduct}=="68a3", ENV{DEVTYPE}="net"

```

My upgrade to ubuntu 14.04LTS went fine without complaints but resulted loss of internet connection.
Please help, attached the output from the wireless_script.

Terveisin, Markus

---

### Post by Malcolm_Gaissert on 2014-08-25
The problem may be that an internal WiFi card that does not work is still in the desktop? If it is, Linux is blocking that one and not allowing the USB one to function even though you make see it in the Network Manager, then turn off the computer and remove it. Windows 8.1 will recognized the situation and us the USB WiFi device.

Good luck

---

### Post by paapu on 2014-08-25
Hei,
To my knowledge there should not be any internal WiFi card in the desktop. I guess it should have been somehow listed in the attached wireless-info.txt file. 
Terveisin, Markus

---

### Post by paapu on 2014-10-27
The problem is now solved. I did not change my hardware but  
1) ubuntu 14.04 was updated
2) I changed my internet provider (from DNA to TeleFinland).
It now works out of the box.
Terveisin, Markus

---

