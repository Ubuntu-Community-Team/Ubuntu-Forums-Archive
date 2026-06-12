---
title: "Need help with wifi on Lenovo H50-00, Ubuntu 16.04"
date: 2019-03-20
forum: Networking &amp; Wireless
---

### Post by hildalev2 on 2019-03-20
Hi everyone!

I am a newbie and trying to understand what I need to get wifi to work on a desktop computer in Ubuntu. I have a wifi adapter that I failed to get working, but I now also read that you can do it with a driver without an adapter, but maybe I understood it wrong. And I couldn't find the driver.

Hope that somebody can help me with this :confused:.

---

### Post by jeremy31 on 2019-03-20
See the wireless script link in my signature and post results

---

### Post by hildalev2 on 2019-03-20
Sadly, the only thing that was in the file after I ran it, was: 
########## wireless info START ##########

and nothing else.

I don't know if this would help:

  *-network                
        description: Ethernet interface
        product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: enp2s0
        version: 05
        serial: b8:ae:ed:20:a3:f3
        size: 10Mbit/s
        capacity: 100Mbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
        resources: irq:89 ioport:d000(size=256) memory:b0304000-b0304fff memory:b0300000-b0303fff

---

### Post by jeremy31 on 2019-03-20
Post results for ```
lspci -nnk | grep -iA3 net; lsusb; rfkill list
```

---

### Post by hildalev2 on 2019-03-20
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
 	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:368d]
 	Kernel driver in use: r8169
 	Kernel modules: r8169
 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
 Bus 001 Device 008: ID 046d:c502 Logitech, Inc. Cordless Mouse & iTouch Keys
 Bus 001 Device 007: ID 1058:1230 Western Digital Technologies, Inc. My Book (WDBFJK0030HBK)
 Bus 001 Device 006: ID 041e:4097 Creative Technology, Ltd  
 Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
 Bus 001 Device 004: ID 17ef:602e Lenovo 
 Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
 Bus 001 Device 009: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-03-20
How is this wifi adapter connected?

---

### Post by hildalev2 on 2019-03-20
Through usb hub. But I guess the computer doesn't see it.

---

### Post by jeremy31 on 2019-03-20
An unpowered USB hub might be an issue if too many devices are connected

---

### Post by hildalev2 on 2019-03-20
Changed the usb port from the hub to the one in front of the computer, the result is practically the same:

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:368d]
    Kernel driver in use: r8169
    Kernel modules: r8169
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 009: ID 046d:c502 Logitech, Inc. Cordless Mouse & iTouch Keys
Bus 001 Device 008: ID 1058:1230 Western Digital Technologies, Inc. My Book (WDBFJK0030HBK)
Bus 001 Device 007: ID 041e:4097 Creative Technology, Ltd
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 005: ID 17ef:602e Lenovo
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 2357:0109
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2019-03-20
```
sudo apt-get install linux-headers-generic git build-essential
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
```

Check ```
mokutil --sb-state
```
If it returns secure boot enabled, you will have to get into BIOS settings to disable Secure Boot
Reboot

---

