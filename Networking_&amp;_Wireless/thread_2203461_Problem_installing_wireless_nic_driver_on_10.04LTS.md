---
title: "Problem installing wireless nic driver on 10.04LTS"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by Yuping_Dong on 2014-02-03
Hi Everyone,

I am a real newbie to Linux.
I was trying to follow the instructions to using Ubuntu 10.04LTS to measure the wireless signal channels.
It requires to use the author's modified kernel. So I followed every step.
Now I cannot turn on the wireless NIC.
Below are some commands I tried and the returned results.
I am very sorry for just typing code. I have the ubuntu server installed without a graphical interface, so I cannot do copy/paste from a terminal.

ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

lspci | grep -i wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

lshw -C network
network UNCLAIMED
  description: Network Controller
  product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
  vendor: Intel Corporation
  physical id: 0
  bus info: pci@0000:03:00.0
  version: 00
  width: 64 bits
  clock: 33MHz
  capabilities: bus_master cap_list
  configuration: latency=0
  resources: memory:f9ffe000-f9ffffff
(and the ethernet nic)

lsmod | grep iwlwifi  returns nothing.
I went in /lib/firmware, the drivers are there. 
iwlwifi-5000-2.ucode
iwlwifi-5000-5.ucode are there.

Any comments will be highly appreciated!!

Yuping

---

### Post by praseodym on 2014-02-03
Hi,

does LAN work to update the driver? Please check:
```

sudo modprobe -v iwlwifi
dmesg | grep iwl
```

---

