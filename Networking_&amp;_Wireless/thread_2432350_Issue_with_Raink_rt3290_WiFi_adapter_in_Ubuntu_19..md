---
title: "Issue with Raink rt3290 WiFi adapter in Ubuntu 19.10"
date: 2019-12-01
forum: Networking &amp; Wireless
---

### Post by jsarthak on 2019-12-01
I'm a new ubuntu user. I've just dual booted Ubuntu 19.10 with Windows 10. There's no problem of wifi in windows. But in Ubuntu, whenever I turn on wifi by clicking on top right section > WiFi Off > Turn On, nothing happens. In Settings > WiFi, there it says "No WiFi Adapter found. Make sure you have a WiFi adapter plugged and turned on".

I've Ralink rt3290 WiFi Adapter. I tried many solution provided on askubuntn and ubuntuforms. None of them work. I tried installing third party drivers, but none of them worked.

```
sudo lshw -C network
```

gives the following output:

```
*-network DISABLED
   description: Wireless interface
   product: RT3290 Wireless 802.11n 1T/1R PCIe
   vendor: Ralink corp.
   physical id: 0
   bus info: pci@0000:0a:00.0
   logical name: wlp10s0f0
   version: 00
   serial: 90:48:9a:2b:1c:9f
   width: 32 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
   configuration: broadcast=yes driver=rt2800pci driverversion=5.3.0-23-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
   resources: irq:16 memory:b5510000-b551ffff
```

Also,

```
sudo rfkill list all
```

gives the following output:

```
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Also,

```
sudo lspci
```

gives the following output:

```
0a:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
0a:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth
```

---

### Post by daf182 on 2020-05-01
Hi, for me wifi adapter is added for this type though it works unreliably. I described it here: [https://answers.launchpad.net/ubuntu/+question/690368](https://answers.launchpad.net/ubuntu/+question/690368)

Do you experience such behavior ?

---

