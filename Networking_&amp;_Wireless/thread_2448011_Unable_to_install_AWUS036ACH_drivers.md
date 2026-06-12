---
title: "Unable to install AWUS036ACH drivers"
date: 2020-07-30
forum: Networking &amp; Wireless
---

### Post by hunterxh7 on 2020-07-30
Hello Team,
I am trying to install Alfa AWUS036ACH USB wireless adapter to Ubuntu 20.04.1 LTS but I am unable to get it working.
My wireless-info.txt contents can be displayed via
[https://pastebin.com/1TVNhzgk](https://pastebin.com/1TVNhzgk)
This is what I get in "Additional Drivers" tab.

---

### Post by hunterxh7 on 2020-07-30
anonymous@anonymous:~$ sudo dkms autoinstall
[sudo] password for anonymous: 
anonymous@anonymous:~$ sudo modprobe -v 8812au
anonymous@anonymous:~$ lsusb; uname -r
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0408:5365 Quanta Computer, Inc. HP TrueVision HD Camera
Bus 001 Device 003: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 0bda:b009 Realtek Semiconductor Corp. 802.11n WLAN Adapter
Bus 001 Device 002: ID 0bda:8812 Realtek Semiconductor Corp. RTL8812AU 802.11a/b/g/n/ac 2T2R DB WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
5.4.0-42-generic
anonymous@anonymous:~$ lspci -nnk | grep -iA3 net
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723DE 802.11b/g/n PCIe Adapter [10ec:d723]
    DeviceName: Realtek Wireless LAN + BT
    Subsystem: Hewlett-Packard Company RTL8723DE 802.11b/g/n PCIe Adapter [103c:8319]
    Kernel driver in use: rtw_pci
anonymous@anonymous:~$

---

