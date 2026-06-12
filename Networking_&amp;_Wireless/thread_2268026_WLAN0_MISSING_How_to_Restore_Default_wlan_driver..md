---
title: "WLAN0 MISSING: How to Restore Default wlan driver."
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by Symaster on 2015-03-05
i have dual boot installed windows8.1 and ubuntu, and i installed the Ralink rt290 drivers for my ubuntu through windows driver installer,
 and now the wlan0 is not showing in ifconfig. 
i tried running:

$ lshw -c network
but the it show that the driver for my wlan is unclaimed

```
*-network               
       description: Ethernet interface
       product: QCA8171 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: e0:3f:49:c2:a2:df
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:60 memory:f7900000-f793ffff ioport:e000(size=128)


  *-network UNCLAIMED
       description: Network controller
       product: RT3290 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7810000-f781ffff
```


so how do i restore my default wlan driver settings.
please do help me.

---

### Post by Symaster on 2015-03-06
Someone Please help, im dying without wifi

---

### Post by Bucky Ball on 2015-03-06
*Thread moved to **Networking & Wireless**.*

Welcome. Your card is fully supported without adding drivers manually if you are using the 3.13 kernel and up (14.04 LTS and up). Try these two commands:

```
sudo modprobe -v rt2800pci
dmesg | grep rt2
```

Whatever you did with the Windows driver may have muddied the waters, though. Did you attempt to get the wireless working prior to using Windows whatever? Please describe exactly what you did. If you installed ndiswrapper and tried with that, problematic. It is rarely used and not needed for your device now. Ubuntu is not like Win generally: you don't need to install drivers for every bit of hardware, most are already in the kernel and much hardware works 'out of the box'. 

Please provide the output of this file:

```
nano /etc/modules
```

Which release are you using?

PS: Please use [code] tags for terminal output (see last link in my signature). Thanks. I have added them to one section of your first post.

---

