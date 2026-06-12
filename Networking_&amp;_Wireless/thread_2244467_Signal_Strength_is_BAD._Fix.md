---
title: "Signal Strength is BAD. Fix?"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by imsaine on 2014-09-16
OK, this is** really annoying**. _**(NOTE:**_ I'm using my notebook)

I'm connected to the internet but it disconnects so often and it's bugging me!
I used Windows for a while but I can't stand it,** CONSTANT UPDATES FORCING ME TO RESTART**, it's horrible.

Ubuntu is great but I have issues with wireless, as stated above. 
It disconnects, asks for a password (annoying!), but sometimes I'm unable to reconnect.
Range is BAD. I can't use it in the kitchen without having to disconnect multiple times!

How can I fix this?


I'm not sure but will this help?

----------------------------------------------
##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

---

### Post by praseodym on 2014-09-16
Please show the outputs of
```

lsmod
ifconfig -a
iwconfig
iwlist chan
sudo iwlist scan
cat /etc/resolv.conf
```
Try deactivating IPv6 in the network profile and using WPA2-AES (CCMP) encryption. Check the router manual for changing the encryption.

---

