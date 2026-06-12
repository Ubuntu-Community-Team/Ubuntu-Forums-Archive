---
title: "Wireless not working - Atheros 5212 Chipset"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by Kamakazie! on 2008-10-18
Hi all,
I installed a TP-Link TL-WN650G PCI network card with an AR5212 chipset in and the restricted modules loaded up fine. The problem is, the network manger shows no wiereless connections and there is no "ath1" listed in iwconfig.


lsmod:
```
 lsmod|grep ath
ath_pci               101024  0 
wlan                  207728  1 ath_pci
ath_hal               192592  1 ath_pci

```

dmesg:
```
[14939.522857] input,hidraw3: USB HID v1.11 Device [HID 046a:0021] on usb-0000:00:13.2-2
[16762.835175] ath_pci: driver unloaded
[16762.836412] wlan: driver unloaded
[16762.837804] ath_hal: driver unloaded
[16773.832632] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[16773.840628] wlan: 0.9.4
[16773.843832] ath_pci: 0.9.4
[16773.843870] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 22 (level, low) -> IRQ 18
[16773.843887] ath_pci: cannot reserve PCI memory region
[16773.843894] ACPI: PCI interrupt for device 0000:03:00.0 disabled

```

lspci:
```
00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
03:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
03:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

modinfo ath_pci:
```
filename:       /lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko
license:        Dual BSD/GPL
version:        0.9.4
description:    Support for Atheros 802.11 wireless LAN cards.
author:         Errno Consulting, Sam Leffler
srcversion:     D3FD3BD11169A96DBCFF8DE
alias:          pci:v0000168Cd00009013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000001Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000019sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000018sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000017sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000016sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000015sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000101Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00001014sv*sd*bc*sc*i*
alias:          pci:v000010B7d00000013sv*sd*bc*sc*i*
alias:          pci:v0000A727d00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000013sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000012sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000007sv*sd*bc*sc*i*
depends:        ath_hal,wlan
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           countrycode:Override default country code (int)
parm:           maxvaps:Maximum VAPs (int)
parm:           outdoor:Enable/disable outdoor use (int)
parm:           xchanmode:Enable/disable extended channel mode (int)
parm:           rfkill:Enable/disable RFKILL capability (int)
parm:           autocreate:Create ath device in [sta|ap|wds|adhoc|ahdemo|monitor] mode. defaults to sta, use 'none' to disable (charp)
parm:           ratectl:Rate control algorithm [amrr|minstrel|onoe|sample], defaults to 'sample' (charp)
parm:           ath_debug:Load-time debug output enable (int)

```

sudo lshw -C Network:
```
 sudo lshw -C Network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:16:17:9b:26:05
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network:0 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: RTL-8110SC/8169SC Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth0
       version: 10
       serial: 00:16:17:9b:26:06
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s

```

I hope that is enough info for some help.
Thanks all.

---

### Post by Kamakazie! on 2008-10-19
:confused:

Oh this is on 8.04.

---

### Post by Kamakazie! on 2008-10-20
Heeeeeeeeeeelp!!!!

:)

---

### Post by melojo on 2008-10-20
what does iwconfig give you

nevermind didn't read your post thoroughly

---

### Post by Kamakazie! on 2008-10-27
Please?
Somebody?

---

### Post by Kamakazie! on 2008-10-30
Fresh install of 8.10 sorted the issue.

---

### Post by squalleitor on 2008-10-31
fresh install of 8.10 and my atheros wlan still refuses to work...

---

