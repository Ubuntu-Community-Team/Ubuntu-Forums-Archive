---
title: "Can't change WiFi MAC address after installing the 8192cu driver"
date: 2015-05-05
forum: Networking &amp; Wireless
---

### Post by formule_rally23 on 2015-05-05
Hi everyone,
I'm using Ubuntu 14.04.02 64 Bits LTS and recently, I bought a TP-Link TL-WN822N v3.0 using a Realtek 8192 chipset, I needed to install the 8192cu Driver, and I followed the instructions on this link: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) and it worked fine, but my problem is that I can't change the mac address of my WiFi Card neither using macchanger or by manually typing:

sudo ifconfig wlan0 down
sudo ifconfig wlan0 hw ether xx:xx:xx:xx:xx:xx
sudo ifconfig wlan0 up

[FONT=arial]I've also tried to edit the connection by adding a cloned mac address but it wouldn't work, I'm really stuck with this, I hope that someone will help me to get it work.
Best regards,
[/FONT]

---

