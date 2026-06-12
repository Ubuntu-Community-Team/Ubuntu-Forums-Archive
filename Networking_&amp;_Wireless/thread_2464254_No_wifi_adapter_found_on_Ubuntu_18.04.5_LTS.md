---
title: "No wifi adapter found on Ubuntu 18.04.5 LTS"
date: 2021-06-27
forum: Networking &amp; Wireless
---

### Post by imayachita on 2021-06-27
Hi all,
I got this classic problem "No wifi adapter found". I'm using Ubuntu 18.04.5 LTS. Here is the output of ```
lspci -nnk
```

```
00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15d0]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:15d0]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Device [1022:15d1]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:15d1]
00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge [1022:1452]
00:01.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:15d3]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:01.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:15d3]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 00h-0fh) PCIe Dummy Host Bridge [1022:1452]
00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Device [1022:15db]
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 61)
    Subsystem: Lenovo FCH SMBus Controller [17aa:382a]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
    Subsystem: Lenovo FCH LPC Bridge [17aa:382b]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e8]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e9]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15ea]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15eb]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15ec]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15ed]
00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15ee]
00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:15ef]
01:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a809]
    Subsystem: Samsung Electronics Co Ltd Device [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822]
    Subsystem: Lenovo Device [17aa:c123]
    Kernel modules: wl
03:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Picasso [1002:15d8] (rev c4)
    Subsystem: Lenovo Device [17aa:3805]
03:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:15de]
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
03:00.2 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:15df]
    Subsystem: Lenovo Device [17aa:3802]
03:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e5]
    Subsystem: Lenovo Device [17aa:3803]
    Kernel driver in use: xhci_hcd
03:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e2]
    Subsystem: Lenovo Device [17aa:3807]
03:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Device [1022:15e3]
    Subsystem: Lenovo Device [17aa:3809]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

```

Command [HTML]sudo dmesg | grep -e r8169 -e enp[/HTML] results in:
```
[  522.738179] rndis_host 1-4:1.0 enp3s0f3u4: renamed from usb0
[  522.771871] IPv6: ADDRCONF(NETDEV_UP): enp3s0f3u4: link is not ready
```

Kernel is```
 4.15.0-147-generic

```

Thanks!

---

### Post by chili555 on 2021-06-27
Here you go!
> Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822]
    Subsystem: Lenovo Device [17aa:c123]
    Kernel modules: wlFirst, wl is a driver for Broadcom devices; you have a Realtek. Please remove it:

```
sudo apt-get purge bcmwl-kernel-source

```
Next, let's Google the pci.id 10ec:c822. I find this: [https://askubuntu.com/questions/1227732/ubuntu-16-04-6-wifi-not-being-detected-on-new-hp-laptop](https://askubuntu.com/questions/1227732/ubuntu-16-04-6-wifi-not-being-detected-on-new-hp-laptop)

I suggest that you try that procedure.

Post back if you need additional guidance.

---

