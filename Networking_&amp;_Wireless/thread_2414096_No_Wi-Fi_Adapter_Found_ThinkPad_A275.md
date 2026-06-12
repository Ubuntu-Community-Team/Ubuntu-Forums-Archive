---
title: "No Wi-Fi Adapter Found ThinkPad A275"
date: 2019-03-05
forum: Networking &amp; Wireless
---

### Post by fatn00b on 2019-03-05
Hello,
I am a new linux user (disgusted that Windows 10 has ads built in to the OS), and I've been having trouble getting my wireless connection to work. When I go to Settings->Wi-fi it just says "No Wi-Fi Adapter Found - Make sure you ave a Wi-Fi adapter plugged and turned on".

I'm using a dual boot with Windows 10, and wi-fi works with Windows. I've attached the results from the pinned wireless script.
Thanks!

---

### Post by pcfan1234 on 2019-03-06
Please show us the full output of lspci without any options. What adapter is detected in Windows?

---

### Post by dave157 on 2019-03-06
Spin up the live session of 18.04 see if it fines the ethernet.

---

### Post by kc1di on 2019-03-06
you most likely have a realtek wireless card and will need to preform the following:

```
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/lwfinger/rtlwifi_new
cd rtlwifi_new
make
sudo make install
sudo modprobe rtl8723be
``` (NOTE: replace rtl8723be with your card #) 

Also you should turn secure boot off.  

lspci command should tell you which card you have.

---

### Post by fatn00b on 2019-03-06
I confirmed that I have rtl8822be.
I made it all the way up to > sudo modprobe rtl8822be
but I got the following error message: > modprobe: FATAL: Module rtl8822be not found in directory /lib/modules/4.18.0-15-generic

---

### Post by jeremy31 on 2019-03-06
I don't think you have the rtl8822be as your device is USB with an ID of 0bda:b023, more likely to be rtl8823bu as the rtl8822be is a PCI device with an ID of 10ec:b822

---

### Post by fatn00b on 2019-03-06
Here's my lspci readout:
> 00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] (rev c8)
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:03.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge
00:03.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port
00:08.0 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 1578
00:09.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 157d
00:09.2 Audio device: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 20)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 49)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 49)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 4a)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0e)
01:00.1 Serial controller: Realtek Semiconductor Co., Ltd. Device 816a (rev 0e)
01:00.2 Serial controller: Realtek Semiconductor Co., Ltd. Device 816b (rev 0e)
01:00.3 IPMI Interface: Realtek Semiconductor Co., Ltd. Device 816c (rev 0e)
01:00.4 USB controller: Realtek Semiconductor Co., Ltd. Device 816d (rev 0e)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961
Does the penultimate line not mean that I have an RTL8822BE?

---

### Post by pcfan1234 on 2019-03-07
Please show
```
lspci -nnk
``` to get the Device ID for your Adapter.
It is connected to PCI(e), not USB.

---

### Post by jeremy31 on 2019-03-07
> **fatn00b said:**
> Here's my lspci readout:

Does the penultimate line not mean that I have an RTL8822BE?
Strange as that should use the kernel module r8822be, post result for ```
modinfo r8822be
```

---

### Post by fatn00b on 2019-03-07
Output from "lspci -nnk":
> 00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex [1022:1576]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Complex [1022:1576]
00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit [1022:1577]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) I/O Memory Management Unit [1022:1577]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wani [Radeon R5/R6/R7 Graphics] [1002:9874] (rev c8)
    Subsystem: Lenovo Carrizo [17aa:511f]
    Kernel driver in use: amdgpu
    Kernel modules: amdgpu
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
    Subsystem: Lenovo Kabini HDMI/DP Audio [17aa:511f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge [1022:157b]
00:02.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
    Kernel driver in use: pcieport
00:02.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
    Kernel driver in use: pcieport
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
    Kernel driver in use: pcieport
00:03.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Host Bridge [1022:157b]
00:03.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Root Port [1022:157c]
    Kernel driver in use: pcieport
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1578]
    Subsystem: Advanced Micro Devices, Inc. [AMD] Device [1022:1578]
00:09.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:157d]
00:09.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Audio Controller [1022:157a]
    Subsystem: Lenovo Device [17aa:511f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7914] (rev 20)
    Subsystem: Lenovo FCH USB XHCI Controller [17aa:511f]
    Kernel driver in use: xhci_hcd
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 49)
    Subsystem: Lenovo FCH SATA Controller [AHCI mode] [17aa:511f]
    Kernel driver in use: ahci
    Kernel modules: ahci
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7908] (rev 49)
    Subsystem: Lenovo FCH USB EHCI Controller [17aa:511f]
    Kernel driver in use: ehci-pci
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 4a)
    Subsystem: Lenovo FCH SMBus Controller [17aa:511f]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4, sp5100_tco
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 11)
    Subsystem: Lenovo FCH LPC Bridge [17aa:511f]
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 0 [1022:1570]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 1 [1022:1571]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 2 [1022:1572]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 3 [1022:1573]
    Kernel driver in use: k10temp
    Kernel modules: k10temp
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 4 [1022:1574]
    Kernel driver in use: fam15h_power
    Kernel modules: fam15h_power
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Family 15h (Models 60h-6fh) Processor Function 5 [1022:1575]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0e)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:511f]
    Kernel driver in use: r8169
    Kernel modules: r8169
01:00.1 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816a] (rev 0e)
    Subsystem: Lenovo Device [17aa:511f]
01:00.2 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816b] (rev 0e)
    Subsystem: Lenovo Device [17aa:511f]
01:00.3 IPMI Interface [0c07]: Realtek Semiconductor Co., Ltd. Device [10ec:816c] (rev 0e)
    Subsystem: Lenovo Device [17aa:511f]
    Kernel modules: ipmi_si
01:00.4 USB controller [0c03]: Realtek Semiconductor Co., Ltd. Device [10ec:816d] (rev 0e)
    Subsystem: Lenovo Device [17aa:511f]
    Kernel driver in use: ehci-pci
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader [10ec:522a] (rev 01)
    Subsystem: Lenovo RTS522A PCI Express Card Reader [17aa:511f]
    Kernel driver in use: rtsx_pci
    Kernel modules: rtsx_pci
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8822BE 802.11a/b/g/n/ac WiFi adapter [10ec:b822]
    Subsystem: Lenovo Device [17aa:b024]
    Kernel driver in use: r8822be
    Kernel modules: r8822be
04:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961 [144d:a804]
    Subsystem: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961 [144d:a801]
    Kernel driver in use: nvme
    Kernel modules: nvme

Output from "modinfo r8822be":
> filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/staging/rtlwifi/r8822be.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
firmware:       rtlwifi/rtl8822befw.bin
description:    Realtek 8822BE 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     FCBBD738FC5F4CEEBA19625
alias:          pci:v000010ECd0000B822sv*sd*bc*sc*i*
depends:        mac80211,cfg80211
staging:        Y
retpoline:      Y
intree:         Y
name:           r8822be
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug_level:int
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           dma64:Set to 1 to use DMA 64 (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug:Set debug level (0-5) (default 0)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

---

### Post by fatn00b on 2019-03-07
It somehow works, and I have no idea how. I think it might have been an automatic update or something. Thank you for your help, everyone, and I apologize to the future that the ultimate solution can't be recorded.

---

