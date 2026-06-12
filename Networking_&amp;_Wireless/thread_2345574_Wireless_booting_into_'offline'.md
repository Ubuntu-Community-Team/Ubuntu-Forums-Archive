---
title: "Wireless booting into 'offline'?"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by Rogotin on 2016-12-05
Simple request here; I have an issue on my laptop where when Ubuntu boots from shutdown; the WiFi card is offline.

Ubuntu 16.04LTS

```

lo        no wireless extensions.

eno1      Ralink STA  
          
enp8s0    no wireless extensions.

```

I can fix this with ```
 ifconfig eno1 up && service network-manager restart 
``` but I can't seem to figure out how to go about either getting this to happen on every boot up; or where to start diagnosing why it is off by default on boot.

Some card information; HP Laptop.

```


08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
    Kernel driver in use: r8169
    Kernel modules: r8169
09:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
    DeviceName:  
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter
    Kernel driver in use: rt2860


```

Any information how I can go about tackling this problem would be magnificent; either how I can script it to power on; or where the power might be.

Thanks in advance.

---

