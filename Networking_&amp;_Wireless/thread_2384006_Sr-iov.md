---
title: "Sr-iov"
date: 2018-02-01
forum: Networking &amp; Wireless
---

### Post by michaelkr2 on 2018-02-01
I am trying to enable SR-IOV on Ubuntu 16.04.3, can you have a look and suggest what can be wrong?

intel_iommu=on is passed to kernel:

**dmesg |grep -i iomm**
> 
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-101-generic.efi.signed root=UUID=bbfa2d78-f19c-4cb4-9661-8ab21d5397c2 ro intel_iommu=on
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-101-generic.efi.signed root=UUID=bbfa2d78-f19c-4cb4-9661-8ab21d5397c2 ro intel_iommu=on
[    0.000000] DMAR: IOMMU enabled
[    0.042277] DMAR-IR: IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.630416] iommu: Adding device 0000:00:00.0 to group 0
[    0.630429] iommu: Adding device 0000:00:01.0 to group 1
[    0.630435] iommu: Adding device 0000:00:01.1 to group 1
[    0.630444] iommu: Adding device 0000:00:14.0 to group 2
[    0.630450] iommu: Adding device 0000:00:14.2 to group 2
[    0.630459] iommu: Adding device 0000:00:15.0 to group 3
[    0.630465] iommu: Adding device 0000:00:15.1 to group 3
[    0.630472] iommu: Adding device 0000:00:16.0 to group 4
[    0.630478] iommu: Adding device 0000:00:17.0 to group 5
[    0.630497] iommu: Adding device 0000:00:1d.0 to group 6
[    0.630505] iommu: Adding device 0000:00:1e.0 to group 7
[    0.630514] iommu: Adding device 0000:00:1f.0 to group 8
[    0.630521] iommu: Adding device 0000:00:1f.2 to group 8
[    0.630526] iommu: Adding device 0000:00:1f.4 to group 8
[    0.630531] iommu: Adding device 0000:01:00.0 to group 1
[    0.630535] iommu: Adding device 0000:02:00.0 to group 1
[    0.630539] iommu: Adding device 0000:02:00.1 to group 1
[    0.630555] iommu: Adding device 0000:03:00.0 to group 6
[    0.630559] iommu: Adding device 0000:04:00.0 to group 6

modules are loaded:
**lsmod |grep ixg**
> ixgbevf                65536  0
ixgbe                 315392  0

modules are updated to latest versions:
[B]ixgbe:        5.3.5
ixgbevf:     2.16.4[/B]

in BIOS I have SRIOV and VT-d enabled.

What I don't see is SRIOV capability in my network card:
**lspci -s 02:00.1 -vnn**
> 02:00.1 Ethernet controller [0200]: Intel Corporation 82599ES 10-Gigabit SFI/SFP+ Network Connection [8086:10fb] (rev 01)
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at df980000 (64-bit, non-prefetchable) [size=512K]
    I/O ports at d000 [size=32]
    Memory at dfb00000 (64-bit, non-prefetchable) [size=16K]
    Expansion ROM at df900000 [disabled] [size=512K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable+ 64bit+
    Capabilities: [70] MSI-X: Enable+ Count=64 Masked-
    Capabilities: [a0] Express Endpoint, MSI 00
    Capabilities: [e0] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Device Serial Number 00-22-68-ff-ff-9b-59-04
    Kernel driver in use: ixgbe
    Kernel modules: ixgbe

and kernel is failing when trying to initialize:
> [    4.232728] ixgbe 0000:02:00.0: Enabling SR-IOV VFs using the max_vfs module parameter is deprecated.
[    4.233143] ixgbe 0000:02:00.0: Please use the pci sysfs interface instead. Ex:
[    4.233549] ixgbe 0000:02:00.0: echo '8' > /sys/bus/pci/devices/0000:02:00.0/sriov_numvfs
[    4.233946] ixgbe 0000:02:00.0 0000:02:00.0 (uninitialized): Failed to enable PCI sriov: -38

ethtool is not showing ixgbevf for network card:
**ethtool -i enp2s0f0**
> driver: ixgbe
version: 5.3.5
firmware-version: 0x800004e0
expansion-rom-version: 
bus-info: 0000:02:00.0
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: yes

Any hints appreciated!

---

