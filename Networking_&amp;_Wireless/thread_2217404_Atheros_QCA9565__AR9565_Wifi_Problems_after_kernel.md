---
title: "Atheros QCA9565 / AR9565 Wifi Problems after kernel upgrade"
date: 2014-04-17
forum: Networking &amp; Wireless
---

### Post by hkphooey on 2014-04-17
Hi,

Figured this one out for myself, but thought I'd post it here in case it helps anyone. I have a Dell laptop with an atheros wifi chip. It uses the ath9k driver. 

```
:~$ lsmod | grep ath
ath9k                 136257  0 
ath9k_common           13619  1 ath9k
ath9k_hw              429197  2 ath9k_common,ath9k
ath3k                  13110  0 
dm_multipath           22402  0 
ath                    19187  3 ath9k_common,ath9k,ath9k_hw
mac80211              517444  1 ath9k
scsi_dh                14458  1 dm_multipath
bluetooth             323656  23 bnep,ath3k,btusb,rfcomm
cfg80211              401762  3 ath,ath9k,mac80211
```

and 
```
:~$ sudo lshw -c Network
[sudo] password for slave: 
  *-network               
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 70:18:8b:05:42:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-18-generic firmware=N/A ip=10.11.12.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn

```

This was working fine until I updated my machine and got kernel 3.11.0-19. I tried a load of things, and eventually discovered that if I booted back into 3.11.0-18, then it all worked again. So I booted into 3.11.0-18, removed the 3.11.0-19 kernel and then pinned the kernel at 18. 
```
sudo apt-get remove linux-headers-3.11.0-19 linux-headers-3.11.0-19-generic linux-image-3.11.0-19-generic linux-image-extra-3.11.0-19-generic
sudo apt-mark hold linux-image-3.11.0-18

```
All is now groovy.

---

