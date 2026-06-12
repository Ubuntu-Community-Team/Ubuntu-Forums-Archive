---
title: "wifi will not work on my hp 15 laptop after i update ubuntu"
date: 2019-11-22
forum: Networking &amp; Wireless
---

### Post by dreamstar87 on 2019-11-22
i am having wifi problems with my hp laptop. i recently installed ubuntu  19.10 so i can practice Linux because im new to it. while installing  ubuntu it detected my wifi and it connected. After ubuntu installed and  updated itself i rebooted my laptop, and after that it would not detect  any wifi signals. i dont know whats wrong 
 ```
$ lspci -knn |grep Net -A3
    01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    DeviceName: Realtek Focus RTL8188EE bgn 1x1 PCI-e HMC WW
    Subsystem: Hewlett-Packard Company RTL8188EE mini-PCIe card [103c:197d]
    Kernel driver in use: rtl8188ee

```
 
```
 iwconfig
lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
eno1      no wireless extensions. 
```

---

### Post by mörgæs on 2019-11-23
Hi, welcome to the fora.

Your problem has a better chance for finding a solution in the networking forum. If you click 'report' you can ask a moderator to move it.

---

### Post by uRock on 2019-11-23
> **mörgæs said:**
> Hi, welcome to the fora.

Your problem has a better chance for finding a solution in the networking forum. If you click 'report' you can ask a moderator to move it.

Moved to ***Networking & Wireless***.

---

### Post by praseodym on 2019-11-23
Please run the wireless script from the sticky thread and show the output

---

