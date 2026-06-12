---
title: "wlan0 not being recognized by iwconfig..."
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by luger on 2007-12-20
I have just completed a long move across the country and got my internet installed at my home. So I tried to get my desktop with Ubuntu going and it wasn't recognizing my PCI wireless device in either Ubuntu or Windows. So I didn't want to go through a long hassle again and I bought a USB network adapter made by Belkin (Belkin's F5D7050E model version 5000). I popped that in and it wasn't working. I added the driver from the device's CD using ndiswrapper (the driver was BLKWGU.inf).

ndiswrapper says the driver is present and recognizes the device. However, iwconfig only lists LO and ETH0 and nothing else. I've updated the interfaces file and wlan0 is there but it is not being recoginzed for whatever reason. The network manager icon is in manual mode and does not show wireless as an option right now for whatever reason.

Help me please, if you can.

---

### Post by victorbrca on 2007-12-20
Have you tried to go into network configuration and change the device to roaming, them:

```
sudo ifconfig eth1 up
sudo iwlist scanning
```



Vic.

---

