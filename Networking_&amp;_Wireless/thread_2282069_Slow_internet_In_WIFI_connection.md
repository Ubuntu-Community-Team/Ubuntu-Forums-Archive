---
title: "Slow internet In WIFI connection"
date: 2015-06-11
forum: Networking &amp; Wireless
---

### Post by tibin2 on 2015-06-11
I am using ubuntu 14.04 LTS(32 bit) along with windows 7 in my Lenovo G550. But when i am connecting wifi in ubuntu the Internet is extremely slow as compared with windows 7. Please help me to clear it out. I am attaching the network details

 *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:82:51:ea:4e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) ip=192.168.13.250 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f4500000-f4503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 70:5a:b6:57:3e:4e
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:48 memory:f4600000-f460ffff



Regards

---

### Post by Bucky Ball on 2015-06-11
Welcome. I'm presuming you need this:

> (12.04 - 12.10) if you need a LP-PHY version (e.g BCM4312), use:

```
sudo apt-get update
sudo apt-get install firmware-b43-lpphy-installer
```

... from [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#A12.04_.28Precise_Pangolin.29_-_14.04_.28Trusty_Tahr.29"). I think wl0 is the wrong driver and it may need to be blacklisted. I'm no wireless guru. :)

If you're lucky, it may just start working once installed. If not, reboot. If still not working, post back with the same output you provided in post 1, but between code tags, thanks (see last link in my signature).

---

