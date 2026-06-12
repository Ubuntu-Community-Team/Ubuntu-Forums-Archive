---
title: "WiFi cannot find any wireless network to connect"
date: 2019-12-07
forum: Networking &amp; Wireless
---

### Post by maplex123 on 2019-12-07
Hello,

I've recently tried to install Ubuntu on a Surface Go and can't seem to get it working.
The problem is that most solutions require connections to the internet and my device can only connect via wireless networks.

The output of sudo lshw -c network:

  *-network DISABLED        
       description: Wireless interface
       product: QCA6174 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 32
       serial: d8:c4:97:96:de:d7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.0.0-23-generic firmware=WLAN.RM.4.4.1-00079-QCARMSWPZ-1 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:144 memory:b1400000-b15fffff

Thank you for your help.

---

### Post by maplex123 on 2019-12-11
bump

---

### Post by chili555 on 2019-12-12
DISABLED usually means that the wireless switch or key combination is set to turn off the wireless radio. Please check.

---

