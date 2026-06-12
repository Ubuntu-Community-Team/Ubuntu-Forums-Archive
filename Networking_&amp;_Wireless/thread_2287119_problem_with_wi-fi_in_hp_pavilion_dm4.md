---
title: "problem with wi-fi in hp pavilion dm4"
date: 2015-07-16
forum: Networking &amp; Wireless
---

### Post by clayton-nog on 2015-07-16
Hi guys,

My Wireless Network is disconnecting suddenly and my wireless network disappears from the list of networks.

Then I have to disable and re-enable the wi -fi to work again.

Ubuntu 04.14 LTS
notebook HP Pavilion dm4 2175br

Please, help me :D

---

### Post by Bucky Ball on 2015-07-17
Welcome. Please open a terminal and copy/paste this:

```
sudo lshw -C network
```

Hit enter and post the output back here, thanks.

---

### Post by clayton-nog on 2015-07-17
here:

```

~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1030 [Rainbow Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: ac:72:89:c1:16:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-44-generic firmware=18.168.6.1 ip=192.168.1.107 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:47 memory:c2500000-c2501fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: eth0
       version: c0
       serial: 80:c1:6e:ab:60:f0
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:50 memory:c1400000-c143ffff ioport:2000(size=128)


```

I read some possible solutions : change the authentication for just WPA2 -AES , and also put the range at 20MHz , which I have done , but it is still disconnecting suddenly .

---

### Post by Bucky Ball on 2015-07-17
If you click Network Manager icon> Edit> edit the wireless connection> IPv6> set to 'Ignore'. 

Any different?

Are you using a static IP address and, if so, how did you set it up?

---

### Post by clayton-nog on 2015-07-17
I did it, same problem.

I am  using DHCP, my network is ok, I have another notebook with red hat enterprise and it works good.

I don't know what is causing that problem but there's others users with the same problem.

---

