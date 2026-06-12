---
title: "iwlist ath0 scan: &quot;no scan results&quot; with Atheros chipset and madwifi in Sharp MP30"
date: 2005-04-12
forum: Networking &amp; Wireless
---

### Post by pingswept on 2005-04-12
I'm having some trouble getting the Atheros chipset
built into my Sharp MP30 laptop working. I'm running
Hoary Hedgehog 5.04. The modules
appear to load correctly (dmesg and lsmod included
below). I can set all of the parameters (IP, ESSID,
WEP key, channel, AP MAC) with iwconfig and ifconfig
with no errors.

However, when I try iwlist ath0 scan, I get "no scan
results." There is a working Linksys WRT54G a few feet
away, and at least 5 other APs in the neighborhood. I
have tried switching from b to g and WEP to no WEP.

This section of dmesg looks like a list of version
numbers:
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)

Suggestions about what to do next? Is there some way that I can get the madwifi driver to give me debugging info?

Thanks,
Pingswept

relevant parts of dmesg:
--------------------------
ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.12.14 (AR5210, AR5211, AR5212)
wlan: 0.8.4.5 (EXPERIMENTAL)
ath_rate_onoe: 1.0
ath_pci: 0.9.4.12 (EXPERIMENTAL)
ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
PCI: setting IRQ 3 as level-triggered
ACPI: PCI interrupt 0000:00:06.0[A] -> GSI 3 (level,
low) -> IRQ 3
ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps
9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
ath0: mac 5.9 phy 4.3 radio 0.0
ath0: 802.11 address: 00:0e:9b:7a:b9:42
ath0: Use hw queue 0 for WME_AC_BE traffic
ath0: Use hw queue 1 for WME_AC_BK traffic
ath0: Use hw queue 2 for WME_AC_VI traffic
ath0: Use hw queue 3 for WME_AC_VO traffic
ath0: Atheros 5212: mem=0xe8000000, irq=3

lsmod shows the modules loaded:
--------------------------------
ath_pci                55584  0
ath_rate_onoe           8840  1 ath_pci
wlan                  106588  3 ath_pci,ath_rate_onoe
ath_hal               133328  2 ath_pci

results of lspci -v:
----------------------------
0000:00:06.0 Ethernet controller: Atheros
Communications, Inc. AR5212 802.11abg NIC (rev 01)
Subsystem: AMBIT Microsystem Corp.: Unknown device
0411
Flags: bus master, medium devsel, latency 168, IRQ 3
Memory at e8000000 (32-bit, non-prefetchable)
[size=64K]
Capabilities: [44] Power Management version 2

---

### Post by pingswept on 2005-06-01
Hello self,

I eventually figured out the answer to this puzzle. The MP30 has a hardwired button (<Fn> F1) that turns on and off the wireless radio. Mine was off.

Pingswept

---

