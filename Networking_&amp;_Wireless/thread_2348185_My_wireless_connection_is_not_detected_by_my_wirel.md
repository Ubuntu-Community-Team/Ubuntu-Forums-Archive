---
title: "My wireless connection is not detected by my wireless adapter"
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by chandramauli2 on 2017-01-01
Recently, I have upgraded to Ubuntu 12.04 I have also applied the changes in the additional driver. I can see few listed wifi connection but i'm unable to see my own home wireless connection. It is working fine on other devices but can't be detected in ubuntu.
Please help me out of this.

---

### Post by cariboo on 2017-01-01
Moved to Networking and wireless. We need more information, what type of wireless device are you using? Can ytou paste the output of:

```
sudo lshw -C network
```

You can copy and paste the command in a terminal, then copy and paste the output into your next post.

The output should look similar to this:

```
*-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: b8:ee:65:8a:1b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.9.0-11-generic firmware=N/A ip=192.168.0.106 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0700000-d077ffff memory:d0780000-d078ffff
```

---

