---
title: "how get CDMA wirless modem driver for ubuntu 9.10"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by achu86 on 2009-11-06
I'm trying to configure CDMA wireless modem on ubuntu but it couldn't fined the modem driver. pleas tale me step-by-stem how to figure out.

---

### Post by friv_livs on 2009-11-06
Go to Applications->Accessories->Terminal, type the following in:
```
lshw
```

and post the output back here in code tags.

Have you googled for your driver?

---

### Post by theozzlives on 2009-11-06
All CDMA I've used just works. You left-click on Network Manager and select CDMA.

---

### Post by achu86 on 2009-11-06
achu@gtz-desktop:~$ lshw
WARNING: you should run this program as super-user.
achu-desktop               
    description: Computer
    width: 64 bits
    capabilities: vsyscall64 vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 2038MiB
     *-cpu
          product: Intel(R) Pentium(R) D CPU 3.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts pni dtes64 monitor ds_cpl est cid cx16 xtpr pdcm lahf_lm
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82Q963/Q965 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:24 memory:dfc00000-dfcfffff
        *-display:0
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:27 memory:dfe00000-dfefffff memory:c0000000-cfffffff(prefetchable) ioport:ecb8(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:dff00000-dfffffff
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:ff20(size=32)
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff00(size=32)
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:22 memory:dfdfbc00-dfdfbfff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:16 memory:dfdfc000-dfdfffff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:25 memory:dfb00000-dfbfffff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             configuration: driver=pcieport-driver
             resources: irq:26 memory:dfa00000-dfafffff
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 02
                serial: 00:1a:a0:ba:0c:fc
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=5754-v3.15 ip=172.23.17.179 latency=0 multicast=yes
                resources: irq:28 memory:dfaf0000-dfafffff
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff80(size=32)
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:ff60(size=32)
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:ff980800-ff980bff
        *-pci:3
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
             resources: ioport:d000(size=4096) memory:df900000-df9fffff
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k HSFi Modem
                vendor: Conexant Systems, Inc.
                physical id: 0
                bus info: pci@0000:04:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: memory:df9f0000-df9fffff ioport:dcf8(size=8)
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fec0(size=16) ioport:ecc0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:dfdfbb00-dfdfbbff ioport:ece0(size=32)
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe40(size=8) ioport:fe50(size=4) ioport:fe60(size=8) ioport:fe70(size=4) ioport:fed0(size=16) ioport:ecd0(size=16)
achu@gtz-desktop:~$ 

yes i has google my driver 3 hours but i can't fined 
i hope you will help me

---

### Post by friv_livs on 2009-11-06
It appears your wireless is not listed in lshw.

Do not post output, but run the following in terminal:

```
sudo lshw -C network
```and see if your wireless shows.

If it does, post the brand and model number from the output.
If not, post that wireless doesn't show in the output.

Can you find a windows driver from your PC manufacturer's website?

---

