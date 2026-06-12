---
title: "AR2413 Wireless Woe [Intrepid]"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by jaxxstorm on 2008-11-03
Hi all, I've finally given up on fixing this myself, and I'm hoping for helo from you guys.

I've been trying to get this Atheros chipset working on both Hardy and Ibex, and I got some success on Hardy using Madwifi, until I upgraded the Kernel and it broke again.

I decided to do a clean install of Ibex to see if I had any more luck, and installed the compat-wireless drivers which seemed to load ath5k fine.

Anyway, here are my outputs
**dmesg**
```
[  292.697200] cfg80211: Using static regulatory domain info
[  292.697217] cfg80211: Regulatory domain: US
[  292.697223] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  292.697232] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[  292.697240] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  292.697247] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  292.697254] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  292.697261] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  292.697268] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[  292.697275] cfg80211: Calling CRDA for country: US
[  292.777357] ath5k_pci 0000:08:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  292.777468] ath5k_pci 0000:08:04.0: registered as 'phy0'
[  292.867221] phy0: Selected rate control algorithm 'pid'
[  293.036279] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[  293.039316] udev: renamed network interface wlan0 to wlan1
[  297.141354] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  307.858463] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  307.858472] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  307.858478] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```

**sudo lshw -C network**
```
 *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:0e:c2:cc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=168 maxlatency=28 mingnt=10 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 02:e7:53:aa:e2:36
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
**lspci -v**
```
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0418
	Flags: bus master, medium devsel, latency 168, IRQ 21
	Memory at d0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ath5k_pci
	Kernel modules: ath5k

```

**sudo make load (compat wireless)**
```
Loading ipw2100...
Loading ipw2200...
Loading libertas_cs...
Loading usb8xxx...
Loading p54pci...
Loading p54usb...
Loading adm8211...
Loading zd1211rw...
Loading rtl8180...
Loading rtl8187...
Loading p54pci...
Loading p54usb...
Loading iwl3945...
Loading iwl4965...
Loading rtl8180...
Loading rtl8187...
Loading rtl8180...
Loading rtl8187...
Loading rt2400pci...
Loading rt2500pci...
Loading rt61pci...
Loading rt2500usb...
Loading rt73usb...
Loading rndis_wlan...
Loading at76_usb...
Module ath_pci not detected -- this is fine
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully

```

I can start pan0 using sudo pan0 up, but nothing happens in terms of network manager. Also, these drivers arent being loaded on startup, I have to manually load them everytime I boot into ubuntu

Please, please help!

---

### Post by jaxxstorm on 2008-11-03
I'll be bumping this until I get a reply by the way

:)

---

### Post by jaxxstorm on 2008-11-03
> **jaxxstorm said:**
> I'll be bumping this until I get a reply by the way

:)

Not particularly sure what I did right here, but it seems to be working now?

A peculiar thing, but I'm not complaining

---

