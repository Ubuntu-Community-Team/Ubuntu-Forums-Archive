---
title: "WUSB54G disconnect after while, KUBUNTU"
date: 2007-01-29
forum: Networking &amp; Wireless
---

### Post by henrik_h on 2007-01-29
Hey 
I have successfully installed wusb54g using ndiswrapper. This is how:
1) Installed ndiswrapper from packagemaneger.
2) downloaded Linksys v.4 windows-driver from [www.linksys.com](www.linksys.com)
3) Installed driver:
sudo ndiswrapper -i rt2500usb.inf
blacklist rt2570: sudo vi /etc/modprobe.d/blacklist
4) Write configuration for modprobe
ndiswrapper -m
5) Now everything works fine :) 
morbror@morbror-desktop:~/Packages/AdobeReader$ ndiswrapper -l
Installed ndis drivers:
rt2500usb               driver present, hardware present

Question:
The connection disapear after about ½ hour.

Can someone help me?

Henrik
(from Denmark)

---

