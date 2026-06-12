---
title: "ZyDAS USB wireless dongle: refuses to connect in Intrepid despite being detected"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by Phil Airtime on 2008-11-30
I have a "Safecom" branded USB wireless dongle ([this thing](http://safecom.cn/code/sub/category.asp?prdid=321&subcatid=41)) which uses the ZyDAS chipset and zd1211rw drivers. The code which appears in lsusb is 0ace:1215. 

It's able to connect to the internet via my WPA-protected network in Intrepid on the first boot. After showing the "A wireless network is available" speech bubble and allowing me to enter my key, it works as expected, getting the IP address from the router's DHCP server and showing the four signal strength bars. Web pages load as normal. However, on subsequent boots I have no such luck. 

The network is detected and Ubuntu tries to automatically connect, but never gets past the first of the two green dots on the NetworkManager icon and eventually asks for the WPA key again... and again... and again... you get the idea. The key is already filled in on the offending box, with lots of hexadecimal figures which I presume is my key in encrypted form. Clicking OK, or entering my key again in plaintext and clicking OK, results in a wait of around 30 seconds and another showing of the blasted box.

It's not a WPA fault--if I turn off encryption and try the same, it simply sits on the first green dot for about 30 seconds before giving a "disconnected from the network" message. 

I've tried manually inputting the settings for my network, but that doesn't seem to make it work. My wireless signal is detected at 85-100%. 

Does anyone know what I'm doing wrong? Since I haven't done anything out of the ordinary, it seems awfully like a bug.

---

### Post by Phil Airtime on 2008-11-30
Did someone drop a pin?

---

