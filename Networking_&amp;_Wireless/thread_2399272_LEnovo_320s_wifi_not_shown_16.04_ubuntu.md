---
title: "LEnovo 320s wifi not shown 16.04 ubuntu"
date: 2018-08-23
forum: Networking &amp; Wireless
---

### Post by caneraydinbey on 2018-08-23
Connected Wifi shows very low signal and wifi network shows only a little wifi addresses


I have 16.04 ubuntu.


Yesterday it completely disconnected and could not reconnect to any wifi. Then somehow i managed to connect again.


Now i am connected to a wifi which is 2 meters away but it shows very low signal despite my mobile can connect with full power. And i can only see 3 wifi addresses to choose despite there are ten's of.


Those are the info:


~: sudo lshw -class network
*-network 
description: Wireless interface
product: Qualcomm Atheros
vendor: Qualcomm Atheros
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlp3s0
version: 31
serial: 58:00:e3:f1:10:15
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath10k_pci driverversion=4.15.0-32-generic firmware=WLAN.TF.1.0-00267-1 ip=192.168.0.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11
resources: irq:127 memory:a4000000-a41fffff
~: 

~: lspci -knn | grep Net -A3
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
Subsystem: Lenovo Device [17aa:0901]
Kernel driver in use: ath10k_pci
Kernel modules: ath10k_pci




I think i dont have driver here?


Subsystem: Lenovo Device [17aa:0901]




it should show some driver of network?


What should i do?


I just installed and did once update.


When i go to additional drivers, i can only see nvidia.





~: lspci | grep Wireless




this does not bring anything

It keeps disconnectin. i have to restart always :(

---

### Post by oldos2er on 2018-08-23
Duplicate closed.

---

