---
title: "upgrade to 15.04 cuts wifi to my Thinkpad"
date: 2016-02-11
forum: Networking &amp; Wireless
---

### Post by saintj0n on 2016-02-11
Hello,
I just upgraded to 15.04 and wifi works while on the live cd but not when running the new install.  It doesn't see any of the 6 APs around my house.  I'm sure it is a driver issue and this is what lshw shows:

           *-network
                description: Wireless interface
                product: Centrino Advanced-N 6205 [Taylor Peak]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 34
                serial: a0:88:b4:e2:e8:c4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.19.0-15-generic firmware=18.168.6.1 ip=192.168.1.242 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:27 memory:f2500000-f2501fff

I have a T420 Thinkpad Lenovo laptop and no external hardware connected.  Any ideas?

---

### Post by Bucky Ball on 2016-02-11
*Thread moved to **Networking & Wireless**.*

Forget 15.04. No longer supported. Please install a supported release, 14.04 LTS or 15.10 (12.04 LTS is also still supported) and see if you have the same issue. If so, edit your thread to correspond with the supported release you are using.

Thanks and good luck.

---

