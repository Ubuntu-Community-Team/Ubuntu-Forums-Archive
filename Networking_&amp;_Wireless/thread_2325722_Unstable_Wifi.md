---
title: "Unstable Wifi"
date: 2016-05-24
forum: Networking &amp; Wireless
---

### Post by nshiell on 2016-05-24
I have Kubuntu 16.04 isntalled on my Desktop PC
I have put in a Broadcom PCIe wifi network adapter and installed the closed drivers, it connects ok but the signal is quite unstable
I then tried a USB dongle, that is the same, connects but the connection drops out, I even tried connecting the dongle to a USB cable to try it in a different location around my desk, same result.

My MacBook is fine with the connection as is my smartphone

Any Ideas what cases this?

---

### Post by pqwoerituytrueiwoq on 2016-05-24
```
lsusb && lspci
```
does the chip use the same class of wifi as the smart phone (A, B, G, N 150,N 300, AC)
difference frequencies have different ranges
maybe your phone is causing interference, leave it on the other side of the room or turn it off (worth a try)

---

### Post by nshiell on 2016-05-24
@pqwoerituytrueiwoq
Thanks for your response, I have tried it with my phone downstairs :)
Right now I am just using my USB dongle, I have removed the drivers for the PCIe card

**lsusb && lspci**
```
Bus 002 Device 014: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 2013:025f PCTV Systems 
Bus 001 Device 008: ID 05ac:0250 Apple, Inc. Aluminium Keyboard (ISO)
Bus 001 Device 006: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 005: ID 1532:002f Razer USA, Ltd 
Bus 001 Device 003: ID 2109:2811 VIA Labs, Inc. Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
03:00.0 Network controller: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
07:00.0 USB controller: Texas Instruments TUSB73x0 SuperSpeed USB 3.0 xHCI Host Controller (rev 02)

```

---

### Post by pqwoerituytrueiwoq on 2016-05-25
```
03:00.0 Network controller: Broadcom Corporation **BCM4360** 802.11ac Wireless Network Adapter
Bus 002 Device 014: ID 0bda:8179 Realtek Semiconductor Corp. **RTL8188EUS** 802.11n Wireless Network Adapter
```
the best way to find issues with a chip and linux is to google the chip name and linux or ubuntu in the same query, i put the chip names in bold, the stuff i found was the age of 12.04, i need to get ready for work so time have the time to look deeper
What is the distance from the router and the number any type of walls/floors (drywall, concrete, etc.)

make sure the case of the computer's case is not between the antenna and the router

---

