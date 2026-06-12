---
title: "Wired internet does not work on first startup"
date: 2017-03-15
forum: Networking &amp; Wireless
---

### Post by thyrsson-anders-gmail on 2017-03-15
I am running Ubuntu 16.04 LTS x64 (Kernel 4.4.0-66-generic) and I am having some trouble with my network card. When I start my computer after it have been turned off only my wireless connection is available (network cable plugged in). If I then restart the computer, not shutdown and then start it again, the wired connection is active / started and working.

I ran "sudo lshw" both before and after reboot and found that "*-pci:0" first have nothing attached to it but after reboot I can see: *-network beskrivning: Ethernet interface

Please advise on how I can sort this out so that my wired connection works startup.

lshw - After startup

```
* -pci: 0
       Description: PCI bridge
       Product: 5 Series / 3400 Series Chipset PCI Express Root Port 1
       Manufacturer: Intel Corporation
       Physical ID: 1c
       Bus info: pci @ 0000: 00: 1c.0
       Version: 05
       width: 32 bits
       clock: 33MHz
       Abilities: pci PCIExpress msi pm normal_decode cap_list
       Configuration: Power = PCIe port
       Resources: IRQ 16 ioport: 4000 (size = 4096) Memory: d1d00000-d24fffff ioport: d0400000 (size = 8388608)
lshw - After restart

* -pci: 0
        Description: PCI bridge
        Product: 5 Series / 3400 Series Chipset PCI Express Root Port 1
        Manufacturer: Intel Corporation
        Physical ID: 1c
        Bus info: pci @ 0000: 00: 1c.0
        Version: 05
        width: 32 bits
        clock: 33MHz
        Abilities: pci PCIExpress msi pm normal_decode bus_master cap_list
        Configuration: Power = PCIe port
        Resources: IRQ 16 ioport: 4000 (size = 8192) Memory: d1e00000-d25fffff ioport: d0400000 (size = 9437184)
      * -Network
            Description: Ethernet interface
            Product: RTL8101 / 2 / 6E PCI Express Fast / Gigabit Ethernet controller
            manufacturer: Realtek Semiconductor Co., Ltd.
            physical id: 0
            Bus info: pci @ 0000: 01: 00.0
            logical name: enp1s0
            Version: 05
            Serial Number: dc: 0e: a1: 4b: 01: 79
            Size: 100Mbit / s
            capacity: 100Mbit / s
            width: 64 bits
            clock: 33MHz
            abilities pm msi PCIExpress msix VPD bus_master cap_list Ethernet physical tp mii 10BT 10BT-ex-ex-100BT 100BT autonegotiation
            configuration: autonegotiation = on broadcast = yes driver = r8169 driver version = 2.3LK-NAPI duplex = full firmware = rtl_nic / rtl8105e-1.fw ip = 192.168.1.200 latency = 0 link = yes multicast = yes port = MII speed = 100Mbit / p
            Resources: IRQ 24 ioport: 4000
```

---

### Post by TheFu on 2017-03-15
I vaguely remember an issue with Realtek NICs not correctly initializing if the wrong driver / options were used.  Perhaps searching for that would provide some leads?
"ubuntu RTL8101" would be the search term.

---

