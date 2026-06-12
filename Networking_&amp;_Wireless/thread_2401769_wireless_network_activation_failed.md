---
title: "wireless network activation failed"
date: 2018-09-22
forum: Networking &amp; Wireless
---

### Post by vishnudinesh2011 on 2018-09-22
I am not able to connect to my WiFi. Every time I try to connect a pop-up notification comes saying "Wireless activation failed". I have recently installed Ubuntu 18.04LTS. 
My pastebin link is : [http://paste.ubuntu.com/p/9DSwqrkyGw/](http://paste.ubuntu.com/p/9DSwqrkyGw/)

---

### Post by jeremy31 on 2018-09-22
Do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Reboot

Did you install the driver from [https://github.com/lwfinger/rtlwifi_new?](https://github.com/lwfinger/rtlwifi_new?)

---

### Post by vishnudinesh2011 on 2018-09-23
yes i installed it from the github

---

