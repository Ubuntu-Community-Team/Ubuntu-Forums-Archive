---
title: "Cannot connect to wireless: Acer v5-591g Ubuntu 16.04"
date: 2016-05-29
forum: Networking &amp; Wireless
---

### Post by sarafs on 2016-05-29
iwconfig returns 

wlp7s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

enp8s0    no wireless extensions.


and lshw -C network returns

root@sara-Aspire-V5-591G:/home/sara# lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlp7s0
       version: 32
       serial: 48:e2:44:21:3e:e9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.4.0-22-generic firmware=WLAN.RM.2.0-00180-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:131 memory:94000000-941fffff

Tried fn-f3 to toggle wifi with no result. The Network Manager window reports the wireless SSID and the message "Out of Range".

---

### Post by sarafs on 2016-05-29
This was solved using [https://bbs.archlinux.org/viewtopic.php?id=208874](https://bbs.archlinux.org/viewtopic.php?id=208874). Thanks to julianp!

---

### Post by jeremy31 on 2016-05-29
If it was a firmware issue
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb
```
Should work

---

