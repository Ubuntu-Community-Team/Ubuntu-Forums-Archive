---
title: "Wireless help"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by 289531.EXE on 2010-10-03
$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device

Is there a way to fix this error so I can get the interface flags?

---

### Post by Hippytaff on 2010-10-03
whats the output for

```

lspci
[/code0

or
[code]
lsusb

```

if your using an usb wiresless effot

---

### Post by 289531.EXE on 2010-10-03
$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)




$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


this is what I get

---

### Post by Hippytaff on 2010-10-03
and this
```

sudo lshw -C network

```

```

iwconfig

```

---

### Post by 289531.EXE on 2010-10-03
*-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: **:**:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=10.0.1.6 latency=128 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:20 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: **:**:**:**:**:**
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:3000(size=256) memory:b0109400-b01094ff

---

### Post by btindie on 2010-10-03
From that it looks like you wireless interface is called *eth1* and not *wlan0*.
```
sudo ifconfig eth1 down
```
use
```
sudo ifconfig -a
```
to see all interfaces or
```
sudo iwconfig
```
to see all wireless interfaces.

---

### Post by Hippytaff on 2010-10-03
> From that it looks like you wireless interface is called *eth1* and not *wlan0*.

well spotted :-D

---

### Post by Hippytaff on 2010-10-03
mine is also eth1 - working fine though

---

### Post by btindie on 2010-10-03
I don't know if this is something Lucid does? Maybe in /etc/udev/rules.d/70-persistent-net.rules ??
 
I did notice recently when I install some virtual machines it did rename some NIC's based on the rules in the above file. You can check that with ```
sudo dmesg | grep udev
```
I got > udev : renamed network interface eth0 to eth1

---

