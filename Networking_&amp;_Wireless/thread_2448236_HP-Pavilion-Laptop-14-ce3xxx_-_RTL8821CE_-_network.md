---
title: "HP-Pavilion-Laptop-14-ce3xxx - RTL8821CE - network not working"
date: 2020-08-04
forum: Networking &amp; Wireless
---

### Post by guym1414 on 2020-08-04
after install the RTL8821CE-dkms , the wifi still not seems to working , any help ?
 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
 apt-cache search rtl8821ce rtl8821ce-dkms - DKMS source for the Realtek 8821C PCIe WiFi driver

---

### Post by chili555 on 2020-08-05
Please run:

```
lspci -nnk | grep 0280 -A3

rfkill list all

```
Please post the result.

---

