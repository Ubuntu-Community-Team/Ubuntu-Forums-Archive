---
title: "Problem with Network 19.10"
date: 2020-03-09
forum: Networking &amp; Wireless
---

### Post by vladansusnjar1997 on 2020-03-09
**i can connect to the internet with my phone (phone hotspot), but i can't connect to the home internet. when i try to connect to home internet, it just spins ... (internet wlan logo with three dots) and (it works normally with the cable)**

---

### Post by CelticWarrior on 2020-03-09
Welcome.

We need to know your WiFi hardware (presumably this question is only about the WiFi). 
Is it an internal WiFi card? Please open a terminal, run the following command and post back the results:
```
lspci -knn | grep Net -A3
```
If using an USB dongle please post the relevant line of ```
lsusb
```


(Both commands list hardware in the respective bus, the first is targeted)

---

### Post by vladansusnjar1997 on 2020-03-09
03:00.0 Network controller [0280]: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter [168c:0042] (rev 31)
    Subsystem: Foxconn International, Inc. QCA9377 802.11ac Wireless Network Adapter [105b:e0a1]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci, wl
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411B PCI Express Card Reader [10ec:5287] (rev 01)

---

### Post by CelticWarrior on 2020-03-09
Your WiFi card should be correctly supported in Ubuntu 19.10. But it can have issues with firmware. Let's check. Please run ```
dmesg | grep ath10k
```

If you find a line similar to ```
Direct firmware load for (...) failed   with error -2
```
please run before anything else ```
sudo apt install --reinstall linux-firmware
```

---

### Post by vladansusnjar1997 on 2020-03-09
[    7.485876] ath10k_pci 0000:03:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    7.760062] ath10k_pci 0000:03:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 105b:e0a1
[    7.760064] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    7.760618] ath10k_pci 0000:03:00.0: firmware ver WLAN.TF.2.1-00021-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 42e41877
[    7.871323] ath10k_pci 0000:03:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[    7.946669] ath10k_pci 0000:03:00.0: unsupported HTC service id: 1536
[    7.964959] ath10k_pci 0000:03:00.0: htt-ver 3.56 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    8.091286] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[  730.088741] ath10k_pci 0000:03:00.0: unsupported HTC service id: 1536
[ 1193.578971] ath10k_pci 0000:03:00.0: unsupported HTC service id: 1536
[ 1731.112743] ath10k_pci 0000:03:00.0: unsupported HTC service id: 1536
[ 2806.911942] ath10k_pci 0000:03:00.0: unsupported HTC service id: 1536

**i cant find this line, can you help me , what now :D ?**

---

### Post by CelticWarrior on 2020-03-09
It seems there's nothing wrong with it, at least not something I could spot.

Have you tried in other networks? If the problem is only with yours I would check the router.


And, of course, using an alternative connection, make sure your system is fully updated.

---

