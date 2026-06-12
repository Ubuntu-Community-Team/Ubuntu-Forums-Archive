---
title: "Slow network speeds and frequent disconnects wifi AR928X"
date: 2013-12-25
forum: Networking &amp; Wireless
---

### Post by philipibb on 2013-12-25
I've been trying to rectify this for several months on Linux Mint with no luck. I recently installed 13.04 in hopes of fixing this issue, but it reared its ugly head again. I have an HP desktop, which I have dual-booted with windows 7. I have no issues on Windows 7 with wireless. With Ubuntu- I start off with 30 Mps DL speeds, then I'll either notice no connectivity (the network-manager indicator shows still connected), or severely throttled speeds around 1 Mbps. I've tried a whole host of fixes browsing this site and others- but nothing works yet. Appreciate any help. 

Here are some helpful outputs. Notice the varying Bit-rates I get when doing iwlist scan

```
 Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

```
wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 20:AA:4B:AC:08:2D   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3440  Invalid misc:1230   Missed beacon:0
```

lsmod
```

ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
radeon               1402449  3 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
microcode              23518  0 
mac80211              596969  1 ath9k
cfg80211              479757  3 ath,ath9k,mac80211

```

```
 
description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:00:db:6e:c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.11.0-14-generic firmware=N/A ip=192.168.1.144 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:febf0000-febfffff
```
iwlist scan

```

wlan0     Scan completed :
          Cell 01 - Address: 20:AA:4B:16:E7:F4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Lula Has No Soul"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ddb86d89
                    Extra: Last beacon: 51704ms ago
                    IE: Unknown: 00104C756C6120486173204E6F20536F756C
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010339A3ED5DAF8169699FFE8CECCF62B7110210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30331042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

---

### Post by praseodym on 2013-12-31
Deactivate the hardware encryption of the driver:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

