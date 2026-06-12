---
title: "Sprint LG Fusic"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by plaen on 2007-08-15
I've got an LG fusic which i use for my internet, however i have been unable to find any usb drivers to use the phone as a modem. Sprint does have the instructions to install drivers for the pc cards, however not any for using a phone as a modem, i've checked lg's website, but they did not have any drivers for Ubuntu. Any suggestions?

---

### Post by plaen on 2007-08-16
I figured out how to make it work, install kppp like sprint says, however since your not using a pc card, you can skip all of the steps to configure the drivers, if you look in the hardware information, it will list a lg vx4400 series, if you click on that there will be a location for the device, mine was /dev/ttyACM0, set kppp to use that, and it will be able to connect, now only if i can change the way the device times out, it will end the connection if i'm not using the internet

---

