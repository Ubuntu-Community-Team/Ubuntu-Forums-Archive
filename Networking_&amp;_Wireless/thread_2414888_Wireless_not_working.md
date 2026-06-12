---
title: "Wireless not working"
date: 2019-03-16
forum: Networking &amp; Wireless
---

### Post by thaimann on 2019-03-16
installed Ubuntu  on a Hp Laptop.  But it didn't find the wireless device.
Windows 10 before the install said it was a Realtec RTL8821CE PCIe Adapter.  I googled the issue and they had me run a script but that was unsuccessful.

This is what they had me do:

sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone [https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh

lsusb returns:

cheryl@gemini:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b00a Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 05c8:03ba Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 04f3:2677 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lspci returns the folllowing

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter


There was a lot more returned, but I think that was the pertinent info.

---

### Post by wildmanne39 on 2019-03-16
*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

