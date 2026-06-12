---
title: "Ubuntu 7.10 TP-Link WN550G - connection bounces up and down"
date: 2008-01-07
forum: Networking &amp; Wireless
---

### Post by rjmarshall on 2008-01-07
Hi,

I didn't see anything similar, so...

I just installed Ubuntu 7.10 on my desktop that has a TP-Link WN550G wireless PCI card.  I notice that the connection keeps going from 100% down to 1, or 2% and then back up again.  This doesn't seem to bother the browser or most other applications, but I use some Cisco VPN software (needed for work) and it loses the connection.  Once the connection is lost, the network ends up hosed and I have to reboot (restarting the network doesn't help) in order to clear the problem.

Does anyone know how to stop the link from bouncing up and down?

> Here's some additional information:

From /var/log/messages:

ath_hal: module license 'Proprietary' taints kernel.
ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
agpgart: Detected VIA KT400/KT400A/KT600 chipset
agpgart: AGP aperture is 128M @ 0xd0000000
wlan: 0.8.4.2 (0.9.3.2)
ath_pci: 0.9.4.5 (0.9.3.2)
-> GSI 17 (level, low) -> IRQ 16
ath_rate_sample: 1.2 (0.9.3.2)
wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
wifi0: H/W encryption support: WEP AES AES_CCM TKIP
wifi0: mac 7.8 phy 4.5 radio 5.6
wifi0: Use hw queue 1 for WME_AC_BE traffic
wifi0: Use hw queue 0 for WME_AC_BK traffic
wifi0: Use hw queue 2 for WME_AC_VI traffic
wifi0: Use hw queue 3 for WME_AC_VO traffic
wifi0: Use hw queue 8 for CAB traffic
wifi0: Use hw queue 9 for beacons
parport_pc 00:0b: reported by Plug and Play ACPI
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
wifi0: Atheros 5212: mem=0xea000000, irq=16

# lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: wifi0
       version: 01
       serial: 00:0a:eb:a6:d6:1b
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) ip=192.168.1.102 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

# iwlist ath0 scan

ath0      Scan completed :
          Cell 01 - Address: 00:18:F8:72:6F:DD
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=9/70  Signal level=-86 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100

# iwconfig ath0

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:72:6F:DD   
          Bit Rate:5 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:restricted
          Power Management:off
          Link Quality=1/70  Signal level=-66 dBm  Noise level=-67 dBm
          Rx invalid nwid:228  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks,

Rob

---

