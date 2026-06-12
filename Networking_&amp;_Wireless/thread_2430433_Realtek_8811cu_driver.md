---
title: "Realtek 8811cu driver"
date: 2019-11-01
forum: Networking &amp; Wireless
---

### Post by jicha on 2019-11-01
Hi,

I have a generic Chinese USB WiFi dongle with rtl8811cu chipset. I searched some discussions and guides and found out that this driver should work for me: [https://github.com/brektrou/rtl8821CU](https://github.com/brektrou/rtl8821CU)

I followed the steps and compiled and installed the driver (using the DKMS method). The driver is now installed but I still can not use the WiFi in network manager. What could be wrong? What should I do to identify and fix the problem?

Also the driver name says 9921CU but my dongle is 8811CU, so I'm not sure if I don't have to change something. But the readme doesn't mention anything regarding this.

Thank you.

---

### Post by chili555 on 2019-11-02
Please insert the device and run and post the result of the terminal command:```
lsusb
```

---

### Post by jeremy31 on 2019-11-02
Moved to Networking & Wireless

---

### Post by jicha on 2019-11-03
Here is the output:

> Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 001 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


The WiFi adapter from this list the [B]0bda:c811 Realtek Semiconductor Corp. 802.11ac NIC
[/B]
I identified the chipset using this page: [https://wikidevi.com/wiki/0bda](https://wikidevi.com/wiki/0bda)

---

### Post by chili555 on 2019-11-03
I believe that the driver you installed is correct for your device. Let's see some diagnostics; from the terminal:

```
sudo dkms status
sudo modprobe 8821cu && dmesg | grep -e rtl -e 8821
iwconfig
```

Please post the exact result of each.

---

### Post by jicha on 2019-11-03
Meanwhile I upgraded my computer to Ubuntu 19.10 and the WiFi adapter started to work automatically. I have no idea what was wrong before the upgrade, maybe a kernel version incompatibility? Anyway the problem is now solved and the above mentioned driver works perfectly for me. But I'll mark down these commands in case I will have to deal with a non working WiFi adapter again.

---

