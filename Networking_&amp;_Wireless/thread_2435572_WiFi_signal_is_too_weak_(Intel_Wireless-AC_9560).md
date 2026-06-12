---
title: "WiFi signal is too weak (Intel Wireless-AC 9560)"
date: 2020-01-22
forum: Networking &amp; Wireless
---

### Post by dglez on 2020-01-22
Newbie Linux user here. I tried searching an answer for hours, but nothing worked. Many solutions were too complex for me to understand and I didn't know if they applied to my case, so I decided to come here and ask. I apologize in advance if this has been solved already.

Motherboard: Gigabyte Aorus Pro Wifi with **Intel Wireless-AC 9560**
BIOS version: F12a

Ubuntu 18.04.03
Kernel 5.3.0-26-generic

"Additional drivers" shows it's not using the device. It doesn't allow to choose the **iwlwifi driver backport**:
[IMG]https://i.ibb.co/ysFTvTB/Screenshot-from-2020-01-22-17-06-45.png[/IMG]

- I can connect via USB Ethernet with no problems.
- Most of the time it can't detect WiFi networks. When it does, these show minimum signal strength and can barely connect.  The router is within a reasonable distance and I live in a building full of many other WiFi networks, which it doesn't detect either (my laptop does).
- I can connect via WiFi if I share it from my smartphone, but still very weak signal. Once connected it works fine and I can actually access the Internet using WiFi.


**iwconfig**:
```
wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.


lo        no wireless extensions.


eno2      no wireless extensions.

```

I guess the Tx-Power=0 dBm has something to do with it, but I don't know how that works.

**/etc/network/interfaces**:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

**dmesg**:
```

iwlwifi 000:00:14.3: Applying debug destination EXTERNAL:DRAM
iwlwifi 000:00:14.3: FW already configured (0) - re-configuring
iwlwifi 000:00:14.3: BIOS contains WGDS but no WRDS

```

**lshw**:
```

*-network:0
description: Wireless interface
product: Wireless-AC 9560 [Jefferson Peak]
vendor: Intel Corporation
physical id: 14.3
bus info: pci@0000:00:14.3
logical name: wlo1
version: 10
serial: [not relevant]
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-26-generic firmware=46.6bf1df06.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
resources: irq:16 memory::55334000-55337fff

```

I always get a "System program problem detected" message after booting up the system. Don't know how to get more info about it though.

Thanks for your time :)

---

