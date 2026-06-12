---
title: "Is there command to repair/update/fix a program (gnome-power-manager)"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by omnica on 2009-11-09
Hi there. I'm new and was having some problems with the power management on my laptop.

I have two problems, the first is the battery always states discharging at (0.0) regardless if it's plugged in or not. 
The second problem is that it will not wake up from a suspended state. If I close the lid or go into suspend it will sleep as it should, but when I power it on again the power turns off after about 5 seconds, and the computer does not restore upon the next boot.

I believe gnome-power-manager deals with both of these issues and am guessing that it may need care, is there a command that will allow me to repair it?
Thank you

---

### Post by lavinog on 2009-11-09
Run the update manager and check for updates first.

There are still a lot of outstanding bugs reguarding suspend.
Many times it is caused by kernel driver such as video drivers, and not gnome-power-manager.

It might help to post the output of **lspci** and **lshw** (from a terminal)

---

### Post by omnica on 2009-11-10
Thanks [lavinog]("http://ubuntuforums.org/member.php?u=118273").
I'm all up to date with updates.
Here are the outputs:


> matt@L:~$ **lspci**
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:04.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
01:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
01:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
01:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)






> 
matt@L:~$ **lshw**
WARNING: you should run this program as super-user.
PCI (sysfs)  
l                         
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3016MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:fde00000-fdefffff memory:d0000000-dfffffff(prefetchable) ioport:c080(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:fdf00000-fdffffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:c400(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:c480(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:fe0ff800-fe0ffbff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:20 memory:fe0f8000-fe0fbfff
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 ioport:e000(size=4096) memory:feb00000-febfffff
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 01
                serial: 00:19:db:ec:9e:e0
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list rom ethernet physical
                configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
                resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:febc0000-febdffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:fea00000-feafffff
           *-network
                description: Wireless interface
                product: AR5001 Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wmaster0
                version: 01
                serial: 00:15:af:4f:d8:74
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath5k ip=192.168.1.103 latency=0 multicast=yes wireless=IEEE 802.11bg
                resources: irq:18 memory:feaf0000-feafffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:c800(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:c880(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:cc00(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:fe0ffc00-fe0fffff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d000(size=4096) memory:fe100000-fe9fffff ioport:fb000000(size=33554432)
           *-pcmcia
                description: CardBus bridge
                product: OZ711SP1 Memory CardBus Controller
                vendor: O2 Micro, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=195
                resources: irq:22 memory:fe100000-fe100fff ioport:d000(size=256) ioport:d400(size=256) memory:c0000000-c3ffffff(prefetchable) memory:c4000000-c7ffffff
           *-generic
                description: SD Host controller
                product: Integrated MMC/SD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.2
                bus info: pci@0000:01:04.2
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:22 memory:fe103000-fe1030ff
           *-storage UNCLAIMED
                description: Mass storage controller
                product: Integrated MS/xD Controller
                vendor: O2 Micro, Inc.
                physical id: 4.3
                bus info: pci@0000:01:04.3
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage cap_list
                configuration: latency=64
                resources: memory:fe101000-fe101fff
           *-firewire
                description: FireWire (IEEE 1394)
                product: Firewire (IEEE 1394)
                vendor: O2 Micro, Inc.
                physical id: 4.4
                bus info: pci@0000:01:04.4
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=ohci1394 latency=64
                resources: irq:22 memory:fe102000-fe102fff memory:fe1fe800-fe1fefff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16) ioport:ff90(size=16)

> 

---

### Post by lavinog on 2009-11-10
```
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```
I found this for another user today...it looks like a problem with intel gpu chipset driver.
bug report for your suspend issues: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/385445)

---

### Post by lavinog on 2009-11-10
This doesn't address the batter charge issue though...I am suspecting a ACPI bug though.
You might be able to find a info file in /proc/acpi/battery somewhere

try 
```
cat /proc/acpi/battery/BAT?/state
```
or 
```
cat $(find /proc/acpi/battery -name 'state')

```

---

