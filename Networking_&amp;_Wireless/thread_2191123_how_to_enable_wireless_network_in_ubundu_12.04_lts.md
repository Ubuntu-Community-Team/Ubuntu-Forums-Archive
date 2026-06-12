---
title: "how to enable wireless network in ubundu 12.04 lts"
date: 2013-12-01
forum: Networking &amp; Wireless
---

### Post by enian48 on 2013-12-01
hi:(
   im using ubundu 12.04. Etthernet is working but wireless in not working. plsss help me

my lspci info...

Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
07:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

---

### Post by praseodym on 2013-12-01
Please install this driver:
```

sudo apt-get install linux-headers-$(uname -r) linux-headers-generic build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/29/20/5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz
sudo tar xvf 5641297-Ralink_3290sta-2.6.0.0_dkms.tar.gz -C /usr/src/
sudo dkms add -m Ralink_3290sta -v 2.6.0.0
sudo dkms build -m Ralink_3290sta -v 2.6.0.0
sudo dkms install -m Ralink_3290sta -v 2.6.0.0 
sudo cp /usr/src/Ralink_3290sta/src/common/rt3290.bin /lib/firmware 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist-rt2800pci.conf
```
Reboot.

---

