---
title: "Wireless DISABLED"
date: 2007-11-15
forum: Networking &amp; Wireless
---

### Post by bobdeep on 2007-11-15
I'm running 7.10 and can't get the wireless to work
I've tried to go through the wirelesstroubleshootingguide and honestly am a bit lost.

What I've done so far:

sudo lshw -class network
  *-network:1 DISABLED
       description: Wireless interface
       product: AR5211 802.11ab NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:90:96:59:e7:fa
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.2) latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11a

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I've looked at other similar threads and I'll try to answer some of the common questions:

1. Is the switch for the wireless card on (laptop)? - Yes
2. Have you tried the FN + Fx key combination? - Yes

I'd appreciate any help and suggestions

---

### Post by bobdeep on 2007-11-15
apart from the disabled notice is everything as it should be?
Should I try a newer madwifi release? (I'm assuming this is madwifi since it uses the proprietary HAL)

Or the ath5k?

---

