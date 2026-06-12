---
title: "Need help with wifi - new to ubuntu"
date: 2018-03-30
forum: Networking &amp; Wireless
---

### Post by aiden007700 on 2018-03-30
Hello, I am having problems with my WiFi on Ubuntu. After 4-6 minutes I cant access the internet even though it shows that im still connected. I have no problems with the WiFi on any other device at home/windows. I noticed that others have had this problem and I tried flowing the tips posted on the thread but now i am even more confused and worried that I might have caused more problems. 

For wifi my pc uses an Asus usb (not sure on the model but i belie it is the n10). 

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 1532:0060 Razer USA, Ltd 
Bus 001 Device 007: ID 1532:021e Razer USA, Ltd 
Bus 001 Device 009: ID 1532:0502 Razer USA, Ltd 
Bus 001 Device 006: ID 0b05:17ba ASUSTek Computer, Inc. N10 Nano 802.11n Network Adapter [Realtek RTL8192CU]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can some one walk me through what needs to be done?

---

### Post by wildmanne39 on 2018-03-30
*Thread moved to **Networking & Wireless, a more appropriate forum**.*

---

### Post by praseodym on 2018-03-30
Normally, there are two drivers loaded, so blacklist the wrong one
```

echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by chili555 on 2018-03-30
Please run and post:```
lsmod | grep rtl
cat /etc/NetworkManager/NetworkManager.conf
```

---

