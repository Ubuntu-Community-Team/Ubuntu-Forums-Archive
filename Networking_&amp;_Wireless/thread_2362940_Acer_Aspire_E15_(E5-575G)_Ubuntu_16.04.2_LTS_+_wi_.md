---
title: "Acer Aspire E15 (E5-575G) Ubuntu 16.04.2 LTS + wi fi 2.4Ghz, 5Ghz. QCA9377"
date: 2017-06-04
forum: Networking &amp; Wireless
---

### Post by aurum0301 on 2017-06-04
Hi.
```
andrew@andrew-pc:~$ lspci -knn | grep Net -A3
03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
    Subsystem: Lite-On Communications Inc Device [11ad:08a6]
    Kernel driver in use: ath10k_pci
    Kernel modules: ath10k_pci
```

Its works only with 5 ghz wi-fi and does not see 2.4ghz :(

---

### Post by jeremy31 on 2017-06-04
I haven't heard that before, is your wifi router set to auto channel?  I would change it to a fixed channel below channel 12 and see if it will find the wifi then

---

### Post by aurum0301 on 2017-06-04
> **jeremy31 said:**
> I haven't heard that before, is your wifi router set to auto channel?  I would change it to a fixed channel below channel 12 and see if it will find the wifi then

1. Auto channel.
2. ZyXEL Keenetic DSL (2.4ghz) ssid_1, repeater Xiaomi Router Mini (2.4ghz, 5ghz) ssid_2.

---

### Post by aurum0301 on 2017-06-04
Ok, I changed the channel from auto to 5 and laptop saw three points :)
Thank you.

---

### Post by jeremy31 on 2017-06-04
There is a code written to the chip at the factory and the linux module will restrict what wifi channels are available based on the code

---

