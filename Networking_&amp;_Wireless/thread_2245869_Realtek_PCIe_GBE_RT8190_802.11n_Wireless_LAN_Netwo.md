---
title: "Realtek PCIe GBE RT8190 802.11n Wireless LAN Network Card Driver for Ubuntu 14.04 LTS"
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by Nire_Inicana on 2014-09-26
I installed Ubuntu 14.04 yesterday alongside Windows 8.1. I found out that there is no default driver for my Realtek PCIe GBE RT8190 802.11n Wireless LAN Network Card. I have no internet connected to my computer. My network card does work with my Windows 8.1 OS and I do have a driver for it for Windows 7 and it still works for Windows 8.1. I have tried to install ndiswrapper on my Ubuntu OS but one of the modules takes too many things to install (python 2.7, etc.). I have taken the liberty to already do all the things, in order, on the topic which says to read before posting. The log is in this link: [http://pastebin.com/kEMhzjTt](http://pastebin.com/kEMhzjTt). I would really appreciate if you can help me as soon as possible...

Edit: I posted the wrong log file so now it is fixed.

---

### Post by praseodym on 2014-09-26
Hi,

please (re)install ndiswrapper via:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms ndisgtk ndiswrapper-dkms
```
After that install the 64bit driver via that

---

### Post by Nire_Inicana on 2014-09-27
Ok, so I got help from this guy on the ubuntu irc chat and he helped me to follow these steps from this topic: [http://askubuntu.com/questions/53136/realtek-8190-wireless-doesnt-work](http://askubuntu.com/questions/53136/realtek-8190-wireless-doesnt-work) and I sucessfuly installed the driver but I cannot add Wifi in the Network settings page. Here is the updated wifi log: [http://pastebin.com/2k1dZiJs](http://pastebin.com/2k1dZiJs)

---

