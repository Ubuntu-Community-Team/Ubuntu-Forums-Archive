---
title: "[SOLVED] D-Link Atheros AR5212 configuration in feisty running Xen"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by azelter on 2007-08-24
I'm running 32-bit feisty using the current Xen kernel (Xen 3.0-i386 / Ubuntu, kernel 2.6.19-4-generic) and am trying to get my D-link wireless card configured.
I downloaded madwifi-0.9.3.2.tar.gz as I understand that this is the driver I need for my card, which reports itself as follows using lspci -v:
02:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Unknown device 1948:3ab6
        Flags: bus master, medium devsel, latency 168, IRQ 21
        Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2

I successfully compiled and installed madwifi by doing:
make KERNELPATH=/usr/src/xen-headers-2.6.19-4-generic
make install KERNELPATH=/usr/src/xen-headers-2.6.19-4-generic

and then after doing modprobe ath-pci I can see ath0 using iwconfig:
ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have not gone further in my configuration as yet although all looks promising so far. However, I am confused on one point. This card should support 11g rates, yet the output of iwconfig suggests that it will only support 11b rates. If I do dmesg I get the following, relating to ath0:
[35701.598745] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[35701.605130] wlan: 0.8.4.2 (0.9.3.2)
[35701.608580] ath_pci: 0.9.4.5 (0.9.3.2)
[35701.609573] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[35701.609584] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[35702.041443] ath_rate_sample: 1.2 (0.9.3.2)
[35702.043277] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[35702.043284] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[35702.043292] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[35702.043298] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[35702.043301] wifi0: mac 5.9 phy 4.3 radio 4.6
[35702.043306] wifi0: Use hw queue 1 for WME_AC_BE traffic
[35702.043309] wifi0: Use hw queue 0 for WME_AC_BK traffic
[35702.043311] wifi0: Use hw queue 2 for WME_AC_VI traffic
[35702.043313] wifi0: Use hw queue 3 for WME_AC_VO traffic
[35702.043315] wifi0: Use hw queue 8 for CAB traffic
[35702.043317] wifi0: Use hw queue 9 for beacons
[35702.066484] wifi0: Atheros 5212: mem=0xe2000000, irq=21

This also suggests my PC knows the card supports 11g. So why does iwconfig say 11b only?
Any ideas?
Thanks!
Alex

---

### Post by nosrednaekim on 2007-08-24
From what i've noticed,
either 1), since it is not associated with an AP, it just says the mode is b. once it is associated, it will switch to g.(or whatever mode the router is in)
or 2) your device is either not detected correctly or the wireless switch(if any) is off.

Its far more likely to be the former. Try connecting and see what happens to iwconfig.

EDIT:

And BTW, thanks for your very detailed report! That helps us very much.

---

### Post by azelter on 2007-08-24
Yes you are right. After connecting to the network the card is reported as IEEE 802.11g.
Thanks!

---

### Post by nosrednaekim on 2007-08-25
now, unfortunately, I had the latter problem I mentioned :)

Gutsy fixed it though.

---

