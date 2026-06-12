---
title: "Cisco (Atheros) controller"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by Sterke-Jerke on 2006-11-03
During the initial installation of my Edgy system my Cisco Aeronet card worked OK.

But after the restart, ath0 would not come "up" 
So I am sure the card can work. Does any one now how to fix this? Perhaps add a module to modules.conf?


If I do a lspci i see the card correclty:

02:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC ( rev 01)

From /var/log/installer/syslog:

Oct 31 20:23:57 main-menu[2924]: INFO: Menu item 'ethdetect' selected
Oct 31 20:24:00 kernel: [17179799.440000] ath_hal: module license 'Proprietary' taints kernel.
Oct 31 20:24:00 kernel: [17179799.448000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
Oct 31 20:24:00 kernel: [17179799.484000] wlan: 0.8.4.2 (0.9.2)
Oct 31 20:24:00 kernel: [17179799.488000] ath_rate_sample: 1.2 (0.9.2)
Oct 31 20:24:00 kernel: [17179799.836000] ath_pci: 0.9.4.5 (0.9.2)
Oct 31 20:24:00 kernel: [17179799.836000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Oct 31 20:24:00 kernel: [17179799.836000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [C142] -> GSI 11 (level, low) -> IRQ 11
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: mac 5.6 phy 4.1 radio 3.6
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 1 for WME_AC_BE traffic
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 0 for WME_AC_BK traffic
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 2 for WME_AC_VI traffic
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 3 for WME_AC_VO traffic
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 8 for CAB traffic
Oct 31 20:24:01 kernel: [17179800.076000] wifi0: Use hw queue 9 for beacons
Oct 31 20:24:01 kernel: [17179800.104000] wifi0: Atheros 5212: mem=0x12000000, irq=11

---

