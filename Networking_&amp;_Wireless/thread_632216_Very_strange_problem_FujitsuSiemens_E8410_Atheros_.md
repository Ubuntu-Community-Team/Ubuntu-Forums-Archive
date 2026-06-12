---
title: "Very strange problem FujitsuSiemens E8410 Atheros internal pci card"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by Bakyt Niyazov on 2007-12-05
Hello!

I've just installed Kubuntu Gutsy Gibbon on my new laptop FujitsuSiemens Lifebook E8410

everything went fine! Now I'm trying (for about 4 hours) to configure wireless.

Kubuntu identified my card as Atheros AR5006EG.

here is my **lshw -C network**
> 
  *-network
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:17:42:84:b1:94
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=192.168.1.100 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0


and **dmesg** snippet
> 
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
wlan: 0.8.4.2 (svn r3005)
ath_pci: 0.9.4.5 (svn r3005)
ACPI: PCI Interrupt 0000:14:00.0[A] -> GSI 19 (level, low) -> IRQ 18
PCI: Setting latency timer of device 0000:14:00.0 to 64
MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
ACPI: PCI interrupt for device 0000:14:00.0 disabled


did you notice (**MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)**)

and **lspci -v**

> 
14:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
	Subsystem: Atheros Communications, Inc. Unknown device 3067
	Flags: fast devsel, IRQ 18
	Memory at fe200000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>


I've tried both -ng and "not ng" :)

I've successfully installed the latest (svn) MadWifi-ng drivers and loaded the ath_pci module using modprobe.

Installation was successful.

Then
> 
bakytn@bakytn-laptop: ~$ [b]wlanconfig ath0 create wlandev wifi0 wlanmode 
wlanconfig: ioctl: No such device


What should I do :(

Please please help me!!! :confused:

Any other information wil, sure, be provided.

Best regards.
Ubuntu - forever!

---

### Post by Bakyt Niyazov on 2007-12-06
anybody?

---

### Post by rustybronco on 2007-12-06
[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

"Notes:	Had to change order of module insertion. Works when order is:modprobe wlan_scan_sta,modprobe wlan_wep,modprobe ath_pci"

don't know if it will help at all.
> did you notice (MadWifi: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)) usually because of the incorrect chipset i.e. t.i. broadcom ect. [http://madwifi.org/wiki/UserDocs/Troubleshooting#WhatdoesHALstatus13mean](http://madwifi.org/wiki/UserDocs/Troubleshooting#WhatdoesHALstatus13mean)

---

### Post by Bakyt Niyazov on 2007-12-06
Huh... I've successfully 
got it working through **ndiswrapper**

Everything is working perfectly. I'm so happy.

**rustybronco**
Thank you for your response!

---

### Post by rustybronco on 2007-12-06
Glad to hear it, seems to be a challenge for that chipset.
Did you install ndiswrapper through synaptic or from source? it may help others.

---

