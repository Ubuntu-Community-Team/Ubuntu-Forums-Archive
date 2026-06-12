---
title: "Can't set rate above 11 Mbit on D-Ling G520"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by wroopy on 2006-08-23
Hello!

I can't choose rates higher then 11 MBit on my Wireless card.  It seams to me that I'm stuck with 802.11b, even though the card should handle 802.11g.

How do I configure the card to use 54Mbit (i.e. 802.11g)?

Information regarding my system:

I'm using Dapper Drake 6.06.1 with kernel 2.6.15-26-k7 and restricted modules. 
Wireless Card: D-Link G520 , based on Atheros AR5112.

#lshw -C network
  *-network:2
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 11
       bus info: pci@00:11.0
       logical name: ath0
       version: 01
       serial: 00:13:46:94:b4:1b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.6.0 (EXPERIMENTAL) multicast=yes wireless=IEEE 802.11b
       resources: iomemory:fa000000-fa00ffff irq:10

#iwconfig ath0
ath0      IEEE 802.11b  ESSID:"APTest"
          Mode:Master  Frequency:2.412 GHz  Access Point: 00:13:46:94:B4:1B
          Bit Rate=11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=6/94  Signal level=-89 dBm  Noise level=-95 dBm
          Rx invalid nwid:1939  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:11   Missed beacon:0

When I load the module (modprobe ath-pci), I get the following information in /var/log/messages
[17304428.300000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17304428.320000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17304428.524000] ath_rate_sample: 1.2
[17304428.560000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17304428.560000] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17304431.148000] Build date: Jul 10 2006
[17304431.148000] Debugging version (IEEE80211)
[17304431.148000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17304431.148000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17304431.148000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17304431.148000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17304431.152000] ath0: mac 7.9 phy 4.5 radio 5.6
[17304431.152000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17304431.152000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17304431.152000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17304431.152000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17304431.152000] ath0: Use hw queue 8 for CAB traffic
[17304431.152000] ath0: Use hw queue 9 for beacons
[17304431.152000] Debugging version (ATH)
[17304431.152000] ath0: Atheros 5212: mem=0xfa000000, irq=10

/Andreas

---

### Post by funchords on 2006-08-23
Is APTest an 802.11g Access Point?

---

### Post by wroopy on 2006-08-23
The card is configured to be an access-point.

I can access it from my client-computer if I configure the computer for 802.11b. If I configure it to only use 802.11g, it can't connect.

/Andreas

---

### Post by funchords on 2006-08-23
Ah, 

try this then:

iwconfig ath0 rate auto


(you may then have to either
 iwconfig ath0 commit 
or bring up the card again using ifconfig)

---

### Post by wroopy on 2006-08-25
Hi!

Now I've tride iwconfig ath0 rate auto, but I still have the same problem.  Any other ideas?  
Could it be a malfunctioned card?  
Is teher any way of configuring the BIOS/Firmware of the card to disable 802.11b or configure 802.11g as default?

/Andreas

---

