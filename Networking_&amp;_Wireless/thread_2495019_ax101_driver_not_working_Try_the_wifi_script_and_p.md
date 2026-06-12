---
title: "ax101 driver not working? Try the wifi script and power down"
date: 2024-02-04
forum: Networking &amp; Wireless
---

### Post by patricia.p on 2024-02-04
I was going to ask for help in getting the Intel N100 Wifi card recognised in Ubuntu 23.10 but after running the forum script the problem was sorted.
```
Distributor ID:    Ubuntu
Description:    Ubuntu 23.10
Release:    23.10
Codename:    mantic
Linux 6.7.1-060701-generic
```

Before running the script I ran lspci -nn

```
patricia@beelink:~$ lspci -nnk 
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:461c]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
00:02.0 VGA compatible controller [0300]: Intel Corporation Alder Lake-N [UHD Graphics] [8086:46d1]
    DeviceName: Onboard - Video
    Subsystem: Intel Corporation Alder Lake-N [UHD Graphics] [8086:7270]
    Kernel driver in use: i915
    Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:54ed]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
00:14.2 RAM memory [0500]: Intel Corporation Device [8086:54ef]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
00:14.3 Network controller [0280]: Intel Corporation CNVi: Wi-Fi [8086:54f0]
    DeviceName: Onboard - Ethernet
    Subsystem: Intel Corporation Device [8086:0244]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
00:15.0 Serial bus controller [0c80]: Intel Corporation Device [8086:54e8]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:15.1 Serial bus controller [0c80]: Intel Corporation Device [8086:54e9]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:54e0]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:17.0 SATA controller [0106]: Intel Corporation Device [8086:54d3]
    DeviceName: Onboard - SATA
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:19.0 Serial bus controller [0c80]: Intel Corporation Device [8086:54c5]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:19.1 Serial bus controller [0c80]: Intel Corporation Device [8086:54c6]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:54be]
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: pcieport
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:54b2]
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: pcieport
00:1e.0 Communication controller [0780]: Intel Corporation Device [8086:54a8]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1e.3 Serial bus controller [0c80]: Intel Corporation Device [8086:54ab]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:5481]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:54c8]
    DeviceName: Onboard - Sound
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:54a3]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device [8086:54a4]
    DeviceName: Onboard - Other
    Subsystem: Intel Corporation Device [8086:7270]
    Kernel driver in use: intel-spi
    Kernel modules: spi_intel_pci
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
    Kernel driver in use: r8169
    Kernel modules: r8169
02:00.0 Non-Volatile memory controller [0108]: MAXIO Technology (Hangzhou) Ltd. NVMe SSD Controller MAP1202 [1e4b:1202] (rev 01)
    Subsystem: MAXIO Technology (Hangzhou) Ltd. NVMe SSD Controller MAP1202 [1e4b:1202]
    Kernel driver in use: nvme
```
After running the script, I powered off and removed the ethernet cable. Reconnected ethernet.
I was able to enable wifi and add SSID and password using the forum wiki. 
```
[patricia@beelink:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:461c]
00:02.0 VGA compatible controller [0300]: Intel Corporation Alder Lake-N [UHD Graphics] [8086:46d1]
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:54ed]
00:14.2 RAM memory [0500]: Intel Corporation Device [8086:54ef]
00:14.3 Network controller [0280]: Intel Corporation CNVi: Wi-Fi [8086:54f0]
00:15.0 Serial bus controller [0c80]: Intel Corporation Device [8086:54e8]
00:15.1 Serial bus controller [0c80]: Intel Corporation Device [8086:54e9]
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:54e0]
00:17.0 SATA controller [0106]: Intel Corporation Device [8086:54d3]
00:19.0 Serial bus controller [0c80]: Intel Corporation Device [8086:54c5]
00:19.1 Serial bus controller [0c80]: Intel Corporation Device [8086:54c6]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:54be]
00:1d.0 PCI bridge [0604]: Intel Corporation Device [8086:54b2]
00:1e.0 Communication controller [0780]: Intel Corporation Device [8086:54a8]
00:1e.3 Serial bus controller [0c80]: Intel Corporation Device [8086:54ab]
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:5481]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:54c8]
00:1f.4 SMBus [0c05]: Intel Corporation Device [8086:54a3]
00:1f.5 Serial bus controller [0c80]: Intel Corporation Device [8086:54a4]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
02:00.0 Non-Volatile memory controller [0108]: MAXIO Technology (Hangzhou) Ltd. NVMe SSD Controller MAP1202 [1e4b:1202] (rev 01)
patricia@beelink:~$ 
```

The difference is that in the first lspci output: Subsystem: Intel Corporation Device [8086:0244]
Not so in the second. 

Its working now, getting an address from DHCP

---

