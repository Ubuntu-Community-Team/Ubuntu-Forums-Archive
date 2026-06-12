---
title: "ASUS X540L wireless adapter quit working"
date: 2021-04-27
forum: Networking &amp; Wireless
---

### Post by t5404tmz on 2021-04-27
[https://paste.ubuntu.com/p/zF3RzSwtZB/](https://paste.ubuntu.com/p/zF3RzSwtZB/)

I need help getting my wifi working again.  ASUS X540L laptop

---

### Post by chili555 on 2021-04-27
I see nothing whatever in your paste that suggests that your wireless is not working perfectly. Please explain.

Also, please run and post:

```
ping -c3 www.ubuntu.com
ping -c3 8.8.8.8
ping -c3 192.168.0.1
```

---

### Post by t5404tmz on 2021-04-27
[https://paste.ubuntu.com/p/zF3RzSwtZB/](https://paste.ubuntu.com/p/zF3RzSwtZB/)

Sorry about that... I pasted the wrong file for my other laptop that is working.  I corrected the original post.

ping command on the bad laptop gets the following error:

ping: [www.ubuntu.com:](www.ubuntu.com:) Temporary failure in name resolution

---

### Post by chili555 on 2021-04-27
We see no wireless device, either PCI nor USB. Is there a setting in the BIOS/EFI to enable/disable wireless?

May we see:

```
lspci -nnk
sudo dmesg | grep -i sdio
```

---

### Post by t5404tmz on 2021-04-27
I think there is just a Fn + F2 toggle for wifi which doesn't do anything.  I don't see anything in bios.

```
sudo dmesg | grep -i sdio
```     
produced no output


```
master@master-X540LA:~$ lspci -nnk

00:00.0 Host bridge [0600]: Intel Corporation Broadwell-U Host Bridge -OPI [8086:1604] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Broadwell-U Host Bridge -OPI [1043:10d0]
    Kernel driver in use: bdw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 5500 [8086:1616] (rev 09)
    Subsystem: ASUSTeK Computer Inc. HD Graphics 5500 [1043:10d0]
    Kernel driver in use: i915
    Kernel modules: i915
00:03.0 Audio device [0403]: Intel Corporation Broadwell-U Audio Controller [8086:160c] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Broadwell-U Audio Controller [1043:10d0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:04.0 Signal processing controller [1180]: Intel Corporation Broadwell-U Processor Thermal Subsystem [8086:1603] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Broadwell-U Processor Thermal Subsystem [1043:10d0]
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device
00:14.0 USB controller [0c03]: Intel Corporation Wildcat Point-LP USB xHCI Controller [8086:9cb1] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP USB xHCI Controller [1043:201f]
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
00:16.0 Communication controller [0780]: Intel Corporation Wildcat Point-LP MEI Controller #1 [8086:9cba] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP MEI Controller [1043:10d0]
    Kernel driver in use: mei_me
    Kernel modules: mei_me
00:1b.0 Audio device [0403]: Intel Corporation Wildcat Point-LP High Definition Audio Controller [8086:9ca0] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP High Definition Audio Controller [1043:10d0]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 [8086:9c90] (rev e3)
    Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 [8086:9c94] (rev e3)
    Kernel driver in use: pcieport
00:1f.0 ISA bridge [0601]: Intel Corporation Wildcat Point-LP LPC Controller [8086:9cc3] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP LPC Controller [1043:10d0]
    Kernel driver in use: lpc_ich
    Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] [8086:9c83] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP SATA Controller [AHCI Mode] [1043:10d0]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Wildcat Point-LP SMBus Controller [8086:9ca2] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP SMBus Controller [1043:10d0]
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
00:1f.6 Signal processing controller [1180]: Intel Corporation Wildcat Point-LP Thermal Management Controller [8086:9ca4] (rev 03)
    Subsystem: ASUSTeK Computer Inc. Wildcat Point-LP Thermal Management Controller [1043:10d0]
    Kernel driver in use: intel_pch_thermal
    Kernel modules: intel_pch_thermal
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5286 PCI Express Card Reader [10ec:5286] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTS5286 PCI Express Card Reader [10ec:5286]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. RTL810xE PCI Express Fast Ethernet controller [1043:200f]
    Kernel driver in use: r8169
    Kernel modules: r8169

```

---

### Post by chili555 on 2021-04-27
Sorry. We still see no wireless device at all. I suspect that it is electronically defective; otherwise known as *dead*.

---

### Post by t5404tmz on 2021-04-27
Yeah, I thought so.  Thanks for confirming.  I'll close this ticket.

---

