---
title: "Ubuntu 17.10 - WiFi Driver not showing up on Additional Drivers"
date: 2018-02-16
forum: Networking &amp; Wireless
---

### Post by geoabe95 on 2018-02-16
Hi, 

I just installed Ubuntu 17.10 and the installation completed smoothly with only one small hiccup. I'm unable to find my WiFi driver under Additional Drivers. 

After reading on many threads, I tried the following commands: 

lspci -nnk | grep 0280 - A2

Result: 
08:00.0 Network Controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
09:00.0 Ethernet Controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)

rfkill list all

Result: 
0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no

Any help on the same would be greatly appreciated!

---

### Post by praseodym on 2018-02-17
Please run
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms broadcom-sta-dkms
```
Reboot

---

### Post by pokemon4e on 2018-04-19
I had the same issue with a Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01) and Ubuntu 17.10.
This fixed my problem. Thanks a million
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms broadcom-sta-dkms
```

---

