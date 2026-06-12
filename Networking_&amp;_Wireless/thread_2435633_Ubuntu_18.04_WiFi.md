---
title: "Ubuntu 18.04 WiFi"
date: 2020-01-23
forum: Networking &amp; Wireless
---

### Post by death0 on 2020-01-23
[COLOR=#000000][FONT=HPSimplifiedLight]Hi,

I need to install these two packages:

sudo apt install ipw2100-fw[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight]sudo apt install ipw2200-fw

result:

E: Unable to locate package ipw2100-fw
E: Unable to locate package ipw2200-fw

How can I do that?[/FONT][/COLOR]

---

### Post by death0 on 2020-01-23
I'm on ubuntu 18.04, kernel 5.3, laptop HP EliteBook 9470m and wifi is "No Wi-Fi Adapter Found".
HP told me that I need to install packages ipw2100-fw and ipw2200-fw.
How can I do that?

---

### Post by chili555 on 2020-01-23
The firmware files are included by default in 18.04. You shouldn't need to install anything.

However, is the laptop 13-15 years old? No? I didn't think so. That's when the the Intel Pro/Wireless 2100 came out. I doubt that that is the wireless device you have. Let's find out what you do have. Please open a terminal Ctrl+Alt+t and run this command:```
lspci -nnk | grep 0280 -A3
```Post the result and we'll proceed.

---

### Post by death0 on 2020-01-23
Hi chili555, tks for the reply.

The laptop has approx. 8 years I think.

 I ran the command [COLOR=#000000][FONT=&quot]lspci -nnk | grep 0280 -A3 [/FONT][/COLOR]with no results.


From HP PartSurfer: [http://partsurfer.hp.com/search.aspx](http://partsurfer.hp.com/search.aspx) 


Wireless Interface
SPS-WLAN 802.11 ABGN 2x2 COMBO JP2 (NMA)

---

### Post by chili555 on 2020-01-23
> SPS-WLAN 802.11 ABGN 2x2 COMBO JP2 (NMA)That tells us nothing useful. Please try these commands:```
lspci -nnk
lsusb
```

---

### Post by death0 on 2020-01-23
lspci -nnk

```
$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
	Subsystem: Hewlett-Packard Company 3rd Gen Core processor DRAM Controller [103c:18df]
	Kernel driver in use: ivb_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller [103c:18df]
	Kernel driver in use: i915
	Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C210 Series Chipset Family USB xHCI Host Controller [103c:18df]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C216 Chipset Family MEI Controller [103c:18df]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) [8086:1502] (rev 04)
	Subsystem: Hewlett-Packard Company 82579LM Gigabit Network Connection (Lewisville) [103c:18df]
	Kernel driver in use: e1000e
	Kernel modules: e1000e
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C216 Chipset Family USB Enhanced Host Controller [103c:18df]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C216 Chipset Family High Definition Audio Controller [103c:18df]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C216 Chipset Family USB Enhanced Host Controller [103c:18df]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation QM77 Express Chipset LPC Controller [8086:1e55] (rev 04)
	Subsystem: Hewlett-Packard Company QM77 Express Chipset LPC Controller [103c:18df]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [103c:18df]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Hewlett-Packard Company 7 Series/C216 Chipset Family SMBus Controller [103c:18df]
	Kernel modules: i2c_i801
02:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
	Subsystem: Hewlett-Packard Company SD/MMC Host Controller [103c:18df]
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci_pci
02:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)
	Subsystem: Hewlett-Packard Company Standard SD Host Controller [103c:18df]
	Kernel modules: sdhci_pci
```

---

### Post by death0 on 2020-01-23
lsusb

$ lsusb
Bus 002 Device 003: ID 8087:07da Intel Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b346 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 004: ID 1058:25fe Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2020-01-23
You should power down the laptop and remove bottom cover, then remove and reinstall the wifi card.  First check BIOS settings to see if WLAN is disabled there.  I doubt you need the ipw firmware

---

### Post by johnsingam on 2020-01-24
> **jeremy31 said:**
> You should power down the laptop and remove bottom cover, then remove and reinstall the wifi card.  First check BIOS settings to see if WLAN is disabled there.  I doubt you need the ipw firmware

Yes, its the right solution to check the wifi.

---

### Post by death0 on 2020-01-24
Tks, I will check that

---

### Post by death0 on 2020-01-24
Not knowing why the wireless card was turned off in the BIOS. The only change I've made was to uninstall windows10 and install ubuntu...
Everything is ok now, many thanks

---

