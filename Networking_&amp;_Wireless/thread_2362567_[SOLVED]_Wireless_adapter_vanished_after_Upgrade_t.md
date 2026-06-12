---
title: "[SOLVED] Wireless adapter vanished after Upgrade to 17.04"
date: 2017-05-30
forum: Networking &amp; Wireless
---

### Post by timfinley on 2017-05-30
This is an ACER Aspire V5, very old computer. I've had Ubuntu running on it since before Ubuntu had Unity. I've had issues in the past with the wireless driver, but I had always at least detected the device. This time, it seems to have vanished. 

I was also having issues with my ethernet connection, but I have resolved that issue. [A Link to my wireless-info.txt]("http://paste.ubuntu.com/24715715/")

Regards,

EDIT:

I simply commented out the offending drivers in /etc/udev/rules.d/70-persistent-net.rules

I recognized the r8712u because I had struggled with it in the past. I might have mistakenly installed the ath9k driver as well. 


```
# PCI device 0x10ec:0x8168 (r8169)SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="1c:87:2c:77:b4:a0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="b4:75:0e:79:e5:b4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="70:5a:b6:df:a4:eb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x168c:0x002a (ath9k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="70:f1:a1:43:90:8e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="20:6a:8a:82:86:17", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x168c:0x0034 (ath9k)
#SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:ed:b9:60:c4:7b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
```

---

### Post by chili555 on 2017-05-30
> ##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
Verrrry interesting! And by interesting, I mean that ole Chili doesn't like this one bit. Your wireless driver isn't r8712u AND ath9k or are you using two or three wireless devices at once??

Anything you'd like to tell us?

My largely default 17.04 system doesn't have or need any rules.d files at all.

---

### Post by timfinley on 2017-05-30
> **chili555 said:**
> Verrrry interesting! And by interesting, I mean that ole Chili doesn't like this one bit. Your wireless driver isn't r8712u AND ath9k or are you using two or three wireless devices at once??

Anything you'd like to tell us?

My largely default 17.04 system doesn't have or need any rules.d files at all.

This is probably some legacy settings from past installs. Should i simply delete the rules.d file?

---

### Post by chili555 on 2017-05-30
> **timfinley said:**
> This is probably some legacy settings from past installs. Should i simply delete the rules.d file?Yes, please. Then reboot and show us:```
lspci -nnk
```Thanks.

---

### Post by timfinley on 2017-05-30
Thanks for pointing that conflict out. See my edit above. 

Here's the output anyway:

```
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)	Subsystem: Acer Incorporated [ALI] 2nd Generation Core Processor Family DRAM Controller [1025:072a]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
	Subsystem: Acer Incorporated [ALI] 2nd Generation Core Processor Family Integrated Graphics Controller [1025:072a]
	Kernel driver in use: i915
	Kernel modules: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C210 Series Chipset Family USB xHCI Host Controller [1025:072a]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family MEI Controller [1025:072a]
	Kernel driver in use: mei_me
	Kernel modules: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family USB Enhanced Host Controller [1025:072a]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family High Definition Audio Controller [1025:072a]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C216 Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family USB Enhanced Host Controller [1025:072a]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation 7 Series Chipset Family LPC Controller [8086:1e5e] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series Chipset Family LPC Controller [1025:072a]
	Kernel driver in use: lpc_ich
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [1025:072a]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Acer Incorporated [ALI] 7 Series/C216 Chipset Family SMBus Controller [1025:072a]
	Kernel modules: i2c_i801
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
	Subsystem: Acer Incorporated [ALI] RTL8411 PCI Express Card Reader [1025:0724]
	Kernel driver in use: rtsx_pci
	Kernel modules: rtsx_pci
02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:0724]
	Kernel driver in use: r8169
	Kernel modules: r8169
03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter [105b:e052]
	Kernel driver in use: ath9k
	Kernel modules: ath9k



```

---

### Post by chili555 on 2017-05-30
> 03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. AR9462 Wireless Network Adapter [105b:e052]
	Kernel driver in use: ath9k
	Kernel modules: ath9kThere is your wireless device. Is it working as expected? When you detach the ethernet cable and click the Network Manager icon, does it see networks? Can you click yours and connect?> I simply commented out the offending drivers in /etc/udev/rules.d/70-persistent-net.rules
Meaning what? That you didn't simply remove the file as I recommended? Why?

---

