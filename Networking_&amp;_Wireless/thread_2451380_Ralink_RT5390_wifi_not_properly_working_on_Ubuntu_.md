---
title: "Ralink RT5390 wifi not properly working on Ubuntu 20.04"
date: 2020-10-03
forum: Networking &amp; Wireless
---

### Post by laxman6811 on 2020-10-03
I'm totally new to ubuntu, it's been 2 days since i have been using this, everything seems fine but have been facing issues with my wifi connections.
Wifi signals always are weak even at very small distance from wifi hotspot. When i bring hotspot close enough I get good signals but still the network speed is really slow, many times it would disconnect by itself, then I have to turn wifi off and on to re-establish the connection.

Need help with it, think this is the right place to get it solved.

[COLOR=#000000]sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

[/COLOR]
Found this but it didn't worked

I could provide whatever the logs needed

used below command, maybe it could be of some help

```
###### lspci -v #######
02:00.0 Network controller: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe
    DeviceName: Ralink 5390GN 802.11b/g/n 1x1 WiFi Adapter
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d3400000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2800pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller
```

---

