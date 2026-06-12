---
title: "missing wireless connection"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by pichulines on 2007-05-01
Hi folks,

After installing Feisty on my laptop most of hardware work fine but the wireless card. I have a broadcom 4311 chip so I installed bcm43xx-fwcutter. After reboot the wireless led turned on and network manager showed the available wireless networks.

In the list are included lot of networks except mine. I have a Dlink (dsl-g624t) router that works fine with winXP partition and also it worked fine with Edgy. I cannot connect other networks because they require password. I have tried to reconfigure my router with password (WEP) and without authentication but no success. The router is close to laptop and it cannot scan for the access point.

I have also tried to set my network manually (setting essid, with dhcp and also with static ip..) but no result. 

Any idea would be appreciated.

---

### Post by pichulines on 2007-05-04
Finally I have solved the problem. FwCutter doesn't work for me, although I could scan networks with it, I couldn't detect my Access Point.

With ndiswrapper had some problems at the beginning, but finally I folowed this [tutorial]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29") to install it . I must say that firstly I tried Vista drivers without success, and secondly the XP ones. These worked.

Now I'm testing the connections, because I'm afraid that the roaming mode doesn't work correctly, but setting manually the wireless network params it goes.

---

