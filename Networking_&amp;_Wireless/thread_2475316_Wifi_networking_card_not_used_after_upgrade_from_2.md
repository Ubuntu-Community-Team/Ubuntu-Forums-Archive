---
title: "Wifi networking card not used after upgrade from 21.10 to 22.04"
date: 2022-05-22
forum: Networking &amp; Wireless
---

### Post by iarnold on 2022-05-22
Hi,

I upgraded my Ubuntu 21.10 to 22.04 just the other day and lost Wifi connection on my laptop.

Output of `lshw -C network`

  *-network DISABLED
       description: Ethernet interface
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 78
       serial: 74:70:fd:1a:10:35
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=iwlwifi driverversion=5.15.0-30-generic firmware=36.ca7b901d.0 8265-36.ucode latency=0 link=no multicast=yes
       resources: irq:140 memory:b3200000-b3201fff

Suggestions please to get me loose from that cabled connection again.

Tia,

Arnold

---

### Post by chili555 on 2022-05-22
Please run and post the result of:

```
rfkill list all
sudo dmesg | grep -e iwl -e wlp
```

---

