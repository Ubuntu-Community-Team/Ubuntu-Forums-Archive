---
title: "Wireless connenction drops constantly on xubuntu 15.10"
date: 2016-01-06
forum: Networking &amp; Wireless
---

### Post by nigro.orlando on 2016-01-06
Hi!
my xubuntu 15.10 has issues with the wireless. When I start the computer it finds the connection and it works ok. After a while it drops and then can't find it again. I have to restart the connections several time before it finds it again but then it won't connect to it. The only way to connects again is the reboot the whole system.

I tried this command from a search on google: 
```

sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "options iwlwifi 11n_disable=1"

```

and it worked while I was at my parents home with their wireless but know that I'm home again it keeps dropping and it's impossible to use.
Maybe this information can help:

```
*-network               
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 93
       serial: a0:88:69:77:23:ba
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-22-generic firmware=25.30.13.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:34 memory:d1600000-d1601fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 10
       serial: f8:a9:63:3d:48:60
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.040.00-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:28 ioport:3000(size=256) memory:d1504000-d1504fff memory:d1500000-d1503fff


```

---

