---
title: "Ndiswrapper does not associate with Network"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by wgandhi on 2007-02-03
Hi All,

I am using the Edgy distribution with the latest updates installed. I have issues associating with the home wireless network. My home network uses WEP protection. 

I have tried two types of wireless USB hardware :
1) Dlink DWL G122 rev B1 (802.11 bg):
    a) Using the rt2570 native linux driver, the green activity light does not turn on. After uninstalling the driver (using rmmod) and re-installing using modprobe, and trying dhclient several times, it works. Once the network is connected, there are no problems but it takes a while to get there. Also this is unreliable. Also, iwlist rausb0 scan never shows any networks when the green light is not lit.
   b) Using ndiswrapper. ndiswrapper -l shows that hardware driver is installed and the hardware is present. However, the green light never turns on. iwlist wlan0 scan shows the essid but link quality is always 0/100 in the scan list. 

2) Dell TrueMobile Wireless 1180 , 802.11b:
Always tried using ndiswrapper. Same symptom as the Dlink USB dongle. Link quality is always 0/100 in the iwlist wlan0 scan..

I can use both the USB dongles under Win XP without any issues.
Any help is much appreciated.

-Wishwesh

---

### Post by phossal on 2007-02-04
What is your question?

---

