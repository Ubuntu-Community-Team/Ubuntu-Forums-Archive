---
title: "Atheros 5418 Wireless not working"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by cvasilak on 2008-01-05
Hi there, i am running ubuntu gutsy with the generic kernel supplied
cvasilak@euphoria:~$ uname -a
Linux euphoria 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

on a macbook core 2 duo machine. The machine comes with an atheros 5418 chipset. I have downloaded the latest svn version of madwifi drivers. Installation is done successfully, the interface ath0 brings up. I set the essid to my network. I then to dhclient but it can't acquire an IP address. It seems that it cannot associate with the access point.

root@euphoria:/home/cvasilak# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:564  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@euphoria:/home/cvasilak# lspci
03:00.0 Network controller: Atheros Communications, Inc. AR5418 802.11a/b/g/n Wireless PCI Express Adapter (rev 01)

root@euphoria:/home/cvasilak# dmesg

[ 1407.056000] ath_hal: 0.9.30.13 (AR5210, AR5211, AR5212, AR5416, RF5111, RF5112, RF2413, RF5413, RF2133)
[ 1407.072000] wlan: svn r3114
[ 1407.080000] ath_pci: svn r3114
[ 1407.080000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[ 1407.080000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[ 1407.208000] ath_pci: switching rfkill capability off
[ 1407.220000] ath_rate_sample: 1.2 (svn r3114)
[ 1407.220000] ath_pci: switching per-packet transmit power control off
[ 1407.220000] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 1407.220000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 1407.220000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 1407.220000] wifi0: mac 12.10 phy 8.1 radio 12.0
[ 1407.220000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 1407.220000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 1407.220000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 1407.220000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 1407.220000] wifi0: Use hw queue 8 for CAB traffic
[ 1407.220000] wifi0: Use hw queue 9 for beacons
[ 1407.236000] wifi0: Atheros 5418: mem=0x98100000, irq=17

---

