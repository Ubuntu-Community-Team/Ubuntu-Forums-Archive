---
title: "Realtek RTL8188EE Laptop Wi-Fi Does not Work on Ubuntu 14.04"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by guiles00 on 2014-04-19
Hi, im having some problems with wireless, it is very slow and intermittent. I read [http://ubuntuforums.org/showthread.php?t=2196571](http://ubuntuforums.org/showthread.php?t=2196571) and tried to make it work but for now i cant.
i ran wireless_script, here is the output.

If someone can help me i ll be bery appreciated.
```
 
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux guillermo-laptop 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Hewlett-Packard Company Device [103c:1960]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 003: ID 138a:0050 Validity Sensors, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:571a Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0458:002e KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"guiles"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:239   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 200.49.130.41
nameserver 200.42.4.204
nameserver 127.0.1.1
search fibertel.com.ar

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [guiles] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Guiles-Wifi:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA
    Julian Wi-Fi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    SEC_LinkShare_a5f2a6: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA2
    Fibertel WiFi573:Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA
    *guiles:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80 WPA
    LMJOTVM:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    Rosario:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             200.49.130.41
    DNS:             200.42.4.204

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"guiles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000014cc51711
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 00066775696C6573
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010001
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Guiles-Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f73fb5175
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000B4775696C65732D57696669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Bilbaos"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001213cd17183
                    Extra: Last beacon: 108ms ago
                    IE: Unknown: 000742696C62616F73
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180203F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Julian Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001010857b127
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000C4A756C69616E2057692D4669
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C43535630314A3830313532331054000800060050F204000110110011576972656C6573732D4720526F75746572100800020084
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"SEC_LinkShare_a5f2a6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000009ab19183
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 00145345435F4C696E6B53686172655F613566326136
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030107
                    IE: Unknown: 050400030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 200100
                    IE: Unknown: 23021100
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607080000000000000000000000000000000000000000
                    IE: Unknown: DD0E0012FB0100010103050000010000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F0240000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Speedy-74cc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009fe8031c6c
                    Extra: Last beacon: 1284ms ago
                    IE: Unknown: 000B5370656564792D37346363
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010020
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FABIAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014d695526b0
                    Extra: Last beacon: 604ms ago
                    IE: Unknown: 000646414249414E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"KIKA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ae04e6725
                    Extra: Last beacon: 832ms ago
                    IE: Unknown: 00044B494B41
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180200F4

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency=2.437 GHz (Channel 6)

##### lsmod #####

iwlwifi               147953  0 
rtl8188ee              84210  0 
rtl_pci                26314  1 rtl8188ee
rtlwifi                52835  2 rtl_pci,rtl8188ee
mac80211              545990  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              409394  3 iwlwifi,mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     1E6912E109D5A43B310FB34
alias:          pci:v00008086d0000095Asv*sd00005490bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005290bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005590bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005190bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005090bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005420bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000502Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005020bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009510bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009210bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009012bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00009010bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005202bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005002bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005200bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000500Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005000bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00001010bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005400bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005410bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005012bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005210bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005302bc*sc*i*
alias:          pci:v00008086d0000095Bsv*sd00005310bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd0000510Abc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005100bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005112bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005110bc*sc*i*
alias:          pci:v00008086d0000095Asv*sd00005010bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008570bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00008270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00008070bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000370bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000472bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000470bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000272bc*sc*i*
alias:          pci:v00008086d000008B4sv*sd00000270bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000062bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000060bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000172bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000170bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000072bc*sc*i*
alias:          pci:v00008086d000008B3sv*sd00000070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C02Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C26Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000C270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C760bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C770bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C06Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000C070bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004420bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004220bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000402Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004020bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00005070bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004360bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004370bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004560bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004570bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Cbc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A6Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004A70bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000486Ebc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004870bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004462bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000446Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004460bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004472bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004470bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004262bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd0000426Abc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004260bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004272bc*sc*i*
alias:          pci:v00008086d000008B2sv*sd00004270bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004162bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004062bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004160bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd0000406Abc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004060bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004170bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004072bc*sc*i*
alias:          pci:v00008086d000008B1sv*sd00004070bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000462bc*sc*i*
alias:          pci:v00008086d00000893sv*sd00000262bc*sc*i*
alias:          pci:v00008086d00000892sv*sd00000062bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000822bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000422bc*sc*i*
alias:          pci:v00008086d00000895sv*sd00000222bc*sc*i*
alias:          pci:v00008086d00000894sv*sd00000022bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00005260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004860bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000446Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004460bc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd0000426Abc*sc*i*
alias:          pci:v00008086d0000088Fsv*sd00004260bc*sc*i*
alias:          pci:v00008086d0000088Esv*sd0000406Abc*sc*i*
alias:          pci:v00008086d0000088Esv*sd00004060bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004462bc*sc*i*
alias:          pci:v00008086d00000888sv*sd00004262bc*sc*i*
alias:          pci:v00008086d00000887sv*sd00004062bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004822bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004422bc*sc*i*
alias:          pci:v00008086d00000891sv*sd00004222bc*sc*i*
alias:          pci:v00008086d00000890sv*sd00004022bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005027bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005025bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005017bc*sc*i*
alias:          pci:v00008086d00000897sv*sd00005015bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005007bc*sc*i*
alias:          pci:v00008086d00000896sv*sd00005005bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001027bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001025bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001017bc*sc*i*
alias:          pci:v00008086d000008AFsv*sd00001015bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001007bc*sc*i*
alias:          pci:v00008086d000008AEsv*sd00001005bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001317bc*sc*i*
alias:          pci:v00008086d00000886sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001327bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000885sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005226bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005225bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005221bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005207bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005206bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005205bc*sc*i*
alias:          pci:v00008086d00000091sv*sd00005201bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005216bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005215bc*sc*i*
alias:          pci:v00008086d00000090sv*sd00005211bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005317bc*sc*i*
alias:          pci:v00008086d0000008Bsv*sd00005315bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005327bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005325bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005307bc*sc*i*
alias:          pci:v00008086d0000008Asv*sd00005305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00004820bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C228bc*sc*i*
alias:          pci:v00008086d00000085sv*sd0000C220bc*sc*i*
alias:          pci:v00008086d00000082sv*sd0000C020bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001318bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001328bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001308bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001307bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001118bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001128bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001108bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     1B8E36556B30AA35325F55D
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

##### modules #####

lp

##### blacklist #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   18.237551] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   18.237619] rtl8188ee 0000:01:00.0: irq 45 for MSI/MSI-X
[   18.650688] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   18.650884] rtlwifi: wireless switch is on
[   24.059750] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.988926] wlan0: authenticate with <MAC address removed>
[   24.999063] wlan0: send auth to <MAC address removed> (try 1/3)
[   25.000651] wlan0: authenticated
[   25.000795] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   25.000798] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   25.000801] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   25.003535] wlan0: associate with <MAC address removed> (try 1/3)
[   25.005700] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[   25.005861] wlan0: associated
[   25.005869] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  188.486013] wlan0: Connection to AP <MAC address removed> lost
[  190.801145] wlan0: authenticate with <MAC address removed>
[  190.810682] wlan0: send auth to <MAC address removed> (try 1/3)
[  190.812418] wlan0: authenticated
[  190.812939] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  190.812943] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  190.812945] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  190.816414] wlan0: associate with <MAC address removed> (try 1/3)
[  190.818593] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  190.818790] wlan0: associated
[  190.818805] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  191.436171] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  194.111156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  199.706580] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  200.490290] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  203.549144] wlan0: authenticate with <MAC address removed>
[  203.549238] wlan0: send auth to <MAC address removed> (try 1/3)
[  203.550819] wlan0: authenticated
[  203.550835] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  203.550837] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  203.550839] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  203.552811] wlan0: associate with <MAC address removed> (try 1/3)
[  203.555030] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  203.555208] wlan0: associated
[  203.555228] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  207.554535] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  208.888503] wlan0: authenticate with <MAC address removed>
[  208.898511] wlan0: send auth to <MAC address removed> (try 1/3)
[  208.900083] wlan0: authenticated
[  208.900097] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  208.900099] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  208.900101] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  208.900251] wlan0: associate with <MAC address removed> (try 1/3)
[  208.902412] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  208.902590] wlan0: associated
[  212.901390] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  214.248129] wlan0: authenticate with <MAC address removed>
[  214.258048] wlan0: send auth to <MAC address removed> (try 1/3)
[  214.259667] wlan0: authenticated
[  214.259682] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  214.259684] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  214.259686] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  214.259788] wlan0: associate with <MAC address removed> (try 1/3)
[  214.261925] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  214.262086] wlan0: associated
[  218.268436] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  219.603617] wlan0: authenticate with <MAC address removed>
[  219.613587] wlan0: send auth to <MAC address removed> (try 1/3)
[  219.615103] wlan0: authenticated
[  219.615121] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  219.615124] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  219.615125] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  219.615280] wlan0: associate with <MAC address removed> (try 1/3)
[  219.617422] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  219.617596] wlan0: associated
[  223.615401] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  237.411455] wlan0: authenticate with <MAC address removed>
[  237.421300] wlan0: send auth to <MAC address removed> (try 1/3)
[  237.422862] wlan0: authenticated
[  237.422893] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  237.422898] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  237.422901] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  237.422992] wlan0: associate with <MAC address removed> (try 1/3)
[  237.426481] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  237.426684] wlan0: associated
[  239.046587] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  239.512872] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  239.996322] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  260.782733] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  268.858185] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  269.698377] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  301.560739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  304.673673] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  305.513805] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  343.594848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  344.080848] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  352.837814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  353.709912] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  355.853269] wlan0: authenticate with <MAC address removed>
[  355.853414] wlan0: send auth to <MAC address removed> (try 1/3)
[  355.854972] wlan0: authenticated
[  355.855009] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  355.855011] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  355.855012] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  355.856743] wlan0: associate with <MAC address removed> (try 1/3)
[  355.858909] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  355.859078] wlan0: associated
[  355.859106] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  359.866916] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  361.208794] wlan0: authenticate with <MAC address removed>
[  361.218595] wlan0: send auth to <MAC address removed> (try 1/3)
[  361.220207] wlan0: authenticated
[  361.220269] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  361.220275] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  361.220280] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  361.224253] wlan0: associate with <MAC address removed> (try 1/3)
[  361.226365] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  361.226532] wlan0: associated
[  365.232292] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  366.572259] wlan0: authenticate with <MAC address removed>
[  366.582124] wlan0: send auth to <MAC address removed> (try 1/3)
[  366.583730] wlan0: authenticated
[  366.583787] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  366.583804] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  366.583805] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  366.587769] wlan0: associate with <MAC address removed> (try 1/3)
[  366.590019] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  366.590188] wlan0: associated
[  370.588933] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  371.935843] wlan0: authenticate with <MAC address removed>
[  371.945661] wlan0: send auth to <MAC address removed> (try 1/3)
[  371.947301] wlan0: authenticated
[  371.947320] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  371.947325] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  371.947328] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  371.951307] wlan0: associate with <MAC address removed> (try 1/3)
[  371.955542] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  371.955713] wlan0: associated
[  375.957608] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[  389.755581] wlan0: authenticate with <MAC address removed>
[  389.765360] wlan0: send auth to <MAC address removed> (try 1/3)
[  389.766887] wlan0: authenticated
[  389.766908] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  389.766910] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  389.766913] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  389.766976] wlan0: associate with <MAC address removed> (try 1/3)
[  389.769327] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  389.769486] wlan0: associated
[  391.519998] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  391.989930] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  392.445777] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  430.140172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  430.666799] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  431.501343] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  432.049768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  459.059095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  462.964502] wlan0: authenticate with <MAC address removed>
[  462.964613] wlan0: send auth to <MAC address removed> (try 1/3)
[  462.967072] wlan0: authenticated
[  462.967362] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  462.967368] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  462.967372] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  462.971048] wlan0: associate with <MAC address removed> (try 1/3)
[  462.973181] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[  462.973357] wlan0: associated
[  462.973374] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1349.408050] wlan0: Connection to AP <MAC address removed> lost
[ 1357.022460] wlan0: authenticate with <MAC address removed>
[ 1357.032135] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1357.033677] wlan0: authenticated
[ 1357.033795] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1357.033798] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1357.033800] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1357.033895] wlan0: associate with <MAC address removed> (try 1/3)
[ 1357.035997] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1357.036155] wlan0: associated
[ 1357.036162] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1594.551730] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1599.865200] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1606.502011] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1607.335083] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1645.492940] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1645.960503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1728.723684] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1729.587105] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1767.633217] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1768.066043] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1784.087206] wlan0: authenticate with <MAC address removed>
[ 1784.097702] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1784.101500] wlan0: authenticated
[ 1784.101725] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 1784.101729] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1784.101731] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1784.102218] wlan0: associate with <MAC address removed> (try 1/3)
[ 1784.106581] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[ 1784.106756] wlan0: associated
[ 1784.106775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3786.405141] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3786.429601] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3787.696365] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3788.128641] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3788.998172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3797.073229] rtlwifi: wireless switch is on
[ 3799.867143] rtl8188ee 0000:01:00.0: no hotplug settings from platform
[ 3803.561343] wlan0: authenticate with <MAC address removed>
[ 3803.561456] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3803.563055] wlan0: authenticated
[ 3803.563170] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3803.563173] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3803.563175] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3803.565220] wlan0: associate with <MAC address removed> (try 1/3)
[ 3803.567365] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[ 3803.567524] wlan0: associated
[ 3803.567543] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3803.778595] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3804.411831] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3805.527002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3806.552436] wlan0: authenticate with <MAC address removed>
[ 3806.552540] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3806.555493] wlan0: authenticated
[ 3806.555628] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3806.555631] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3806.555633] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3806.559133] wlan0: associate with <MAC address removed> (try 1/3)
[ 3806.561188] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[ 3806.561353] wlan0: associated
[ 3806.561370] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3807.652316] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 3845.996884] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3846.613697] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3847.869641] wlan0: authenticate with <MAC address removed>
[ 3847.869761] wlan0: send auth to <MAC address removed> (try 1/3)
[ 3847.872428] wlan0: authenticated
[ 3847.872641] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 3847.872644] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3847.872647] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3847.874224] wlan0: associate with <MAC address removed> (try 1/3)
[ 3847.876414] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[ 3847.876584] wlan0: associated
[ 3847.876693] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4430.793966] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 4430.840578] wlan0: authenticate with <MAC address removed>
[ 4430.840725] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4430.842772] wlan0: authenticated
[ 4430.843094] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4430.843103] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4430.843108] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4430.844900] wlan0: associate with <MAC address removed> (try 1/3)
[ 4430.846992] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 4430.847174] wlan0: associated
[ 4430.847216] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4440.855154] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4442.006373] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4447.506890] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4448.341639] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4450.414179] wlan0: authenticate with <MAC address removed>
[ 4450.414282] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4450.416004] wlan0: authenticated
[ 4450.416023] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4450.416025] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4450.416027] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4450.417726] wlan0: associate with <MAC address removed> (try 1/3)
[ 4450.418240] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4450.419606] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4450.419793] wlan0: associated
[ 4450.419813] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4458.078807] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4459.371551] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4467.467666] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4477.361930] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4478.214220] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4480.277746] wlan0: authenticate with <MAC address removed>
[ 4480.277900] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4480.279902] wlan0: authenticated
[ 4480.280040] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4480.280047] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4480.280051] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4480.281367] wlan0: associate with <MAC address removed> (try 1/3)
[ 4480.283300] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4480.283478] wlan0: associated
[ 4480.283524] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4480.284008] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4595.166569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4595.999883] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4598.067752] wlan0: authenticate with <MAC address removed>
[ 4598.067857] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4598.069478] wlan0: authenticated
[ 4598.069516] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4598.069519] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4598.069521] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4598.070652] wlan0: associate with <MAC address removed> (try 1/3)
[ 4598.072604] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4598.072782] wlan0: associated
[ 4598.072819] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4616.118123] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 4617.673381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4631.980757] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4632.810258] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4634.871183] wlan0: authenticate with <MAC address removed>
[ 4634.871333] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4634.879262] wlan0: authenticated
[ 4634.879311] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4634.879316] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4634.879321] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4634.880764] wlan0: associate with <MAC address removed> (try 1/3)
[ 4634.882623] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4634.882804] wlan0: associated
[ 4634.883167] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4668.027300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4668.865179] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4670.923491] wlan0: authenticate with <MAC address removed>
[ 4670.923636] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4670.926210] wlan0: authenticated
[ 4670.926252] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4670.926259] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4670.926265] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4670.926402] wlan0: associate with <MAC address removed> (try 1/3)
[ 4670.932250] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4670.932425] wlan0: associated
[ 4670.932456] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4689.913760] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 4691.520598] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4704.683000] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4705.520352] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4707.599370] wlan0: authenticate with <MAC address removed>
[ 4707.599529] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4707.601498] wlan0: authenticated
[ 4707.601547] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4707.601554] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4707.601560] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4707.604178] wlan0: associate with <MAC address removed> (try 1/3)
[ 4707.606062] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4707.606237] wlan0: associated
[ 4707.606279] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4707.606533] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4730.152770] wlan0: authenticate with <MAC address removed>
[ 4730.162307] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4730.163949] wlan0: authenticated
[ 4730.164118] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4730.164123] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4730.167696] wlan0: associate with <MAC address removed> (try 1/3)
[ 4730.170798] wlan0: RX AssocResp from <MAC address removed> (capab=0x401 status=0 aid=4)
[ 4730.170953] wlan0: associated
[ 4781.418864] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 4781.429064] wlan0: authenticate with <MAC address removed>
[ 4781.429225] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4781.431150] wlan0: authenticated
[ 4781.431395] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4781.431401] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4781.431761] wlan0: associate with <MAC address removed> (try 1/3)
[ 4781.434609] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=12 aid=0)
[ 4781.434616] wlan0: <MAC address removed> denied association (code=12)
[ 4781.468508] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 4796.776280] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4800.389690] wlan0: authenticate with <MAC address removed>
[ 4800.389809] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4800.391394] wlan0: authenticated
[ 4800.391682] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 4800.391685] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 4800.391687] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 4800.394788] wlan0: associate with <MAC address removed> (try 1/3)
[ 4800.396943] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 4800.397106] wlan0: associated
[ 4800.397128] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6934.117401] wlan0: deauthenticated from <MAC address removed> (Reason: 7)
[ 6934.130040] wlan0: authenticate with <MAC address removed>
[ 6934.130151] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6934.131804] wlan0: authenticated
[ 6934.131939] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 6934.131942] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 6934.131945] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 6934.135072] wlan0: associate with <MAC address removed> (try 1/3)
[ 6934.137885] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 6934.138047] wlan0: associated
[ 6934.138068] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7408.932401] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7409.921397] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7410.402315] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7411.298670] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7414.648243] rtlwifi: wireless switch is on
[ 7417.558171] rtl8188ee 0000:01:00.0: no hotplug settings from platform
[ 7421.242942] wlan0: authenticate with <MAC address removed>
[ 7421.243056] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7421.246956] wlan0: authenticated
[ 7421.247159] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7421.247162] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7421.247164] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7421.248227] wlan0: associate with <MAC address removed> (try 1/3)
[ 7421.250295] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7421.250456] wlan0: associated
[ 7421.250476] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7421.416512] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7421.878507] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7422.722440] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7423.600010] wlan0: authenticate with <MAC address removed>
[ 7423.600127] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7423.603237] wlan0: authenticated
[ 7423.603410] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7423.603413] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7423.603415] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7423.605753] wlan0: associate with <MAC address removed> (try 1/3)
[ 7423.607833] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7423.608003] wlan0: associated
[ 7423.608023] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7956.123319] wlan0: Connection to AP <MAC address removed> lost
[ 7958.525709] wlan0: authenticate with <MAC address removed>
[ 7958.535220] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7958.536868] wlan0: authenticated
[ 7958.537146] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7958.537155] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7958.537160] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7958.540873] wlan0: associate with <MAC address removed> (try 1/3)
[ 7958.543002] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7958.543182] wlan0: associated
[ 7958.543191] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7962.541976] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 7963.881810] wlan0: authenticate with <MAC address removed>
[ 7963.890702] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7963.892229] wlan0: authenticated
[ 7963.892475] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7963.892480] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7963.892483] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7963.896388] wlan0: associate with <MAC address removed> (try 1/3)
[ 7963.898525] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7963.898705] wlan0: associated
[ 7967.899199] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 7969.241329] wlan0: authenticate with <MAC address removed>
[ 7969.250176] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7969.251751] wlan0: authenticated
[ 7969.251934] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7969.251939] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7969.251943] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7969.255896] wlan0: associate with <MAC address removed> (try 1/3)
[ 7969.257977] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7969.258144] wlan0: associated
[ 7972.249592] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7974.734954] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7975.236739] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7976.993839] wlan0: authenticate with <MAC address removed>
[ 7977.003371] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7977.006109] wlan0: authenticated
[ 7977.006317] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7977.006320] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7977.006322] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7977.009049] wlan0: associate with <MAC address removed> (try 1/3)
[ 7977.012425] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7977.012597] wlan0: associated
[ 7977.012605] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7981.016544] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 7981.030310] wlan0: authenticate with <MAC address removed>
[ 7981.030468] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7981.031995] wlan0: authenticated
[ 7981.032243] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7981.032250] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7981.032255] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7981.035609] wlan0: associate with <MAC address removed> (try 1/3)
[ 7981.040183] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7981.040367] wlan0: associated
[ 7985.296737] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 7986.453492] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7986.985468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7987.692592] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7988.274354] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7989.777910] wlan0: authenticate with <MAC address removed>
[ 7989.798211] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7989.999771] wlan0: send auth to <MAC address removed> (try 2/3)
[ 7990.002465] wlan0: authenticated
[ 7990.002504] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7990.002509] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7990.002512] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7990.005518] wlan0: associate with <MAC address removed> (try 1/3)
[ 7990.007481] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=12 aid=0)
[ 7990.007488] wlan0: <MAC address removed> denied association (code=12)
[ 7990.021750] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7990.021820] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 7990.955088] wlan0: authenticate with <MAC address removed>
[ 7990.964493] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7990.967690] wlan0: authenticated
[ 7990.967925] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7990.967933] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7990.967939] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7990.970173] wlan0: associate with <MAC address removed> (try 1/3)
[ 7990.972366] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7990.972536] wlan0: associated
[ 7990.972550] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7994.974270] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 7996.326787] wlan0: authenticate with <MAC address removed>
[ 7996.336722] wlan0: send auth to <MAC address removed> (try 1/3)
[ 7996.339540] wlan0: authenticated
[ 7996.339659] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 7996.339663] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7996.339665] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7996.341692] wlan0: associate with <MAC address removed> (try 1/3)
[ 7996.343842] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 7996.344006] wlan0: associated
[ 8000.340924] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 8013.394340] wlan0: authenticate with <MAC address removed>
[ 8013.783500] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8013.786188] wlan0: authenticated
[ 8013.786494] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8013.786503] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8013.786509] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8013.789134] wlan0: associate with <MAC address removed> (try 1/3)
[ 8013.791241] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8013.791413] wlan0: associated
[ 8017.793392] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 8031.609848] wlan0: authenticate with <MAC address removed>
[ 8031.619089] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8031.622028] wlan0: authenticated
[ 8031.622215] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8031.622219] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8031.622222] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8031.624841] wlan0: associate with <MAC address removed> (try 1/3)
[ 8031.627530] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8031.627693] wlan0: associated
[ 8035.625273] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 8039.085626] wlan0: authenticate with <MAC address removed>
[ 8039.475709] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8039.479011] wlan0: authenticated
[ 8039.479311] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8039.479320] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8039.479325] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8039.481989] wlan0: associate with <MAC address removed> (try 1/3)
[ 8039.486733] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8039.486910] wlan0: associated
[ 8043.491559] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 8057.294526] wlan0: authenticate with <MAC address removed>
[ 8057.304028] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8057.306714] wlan0: authenticated
[ 8057.306935] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8057.306943] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8057.306947] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8057.309700] wlan0: associate with <MAC address removed> (try 1/3)
[ 8057.311825] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8057.312006] wlan0: associated
[ 8061.318459] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[ 8064.101077] wlan0: authenticate with <MAC address removed>
[ 8064.493056] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8064.495865] wlan0: authenticated
[ 8064.496144] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8064.496153] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8064.496159] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8064.498415] wlan0: associate with <MAC address removed> (try 1/3)
[ 8064.500710] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8064.500884] wlan0: associated
[ 8110.308534] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 8113.128187] wlan0: authenticate with <MAC address removed>
[ 8113.517022] wlan0: send auth to <MAC address removed> (try 1/3)
[ 8113.518538] wlan0: authenticated
[ 8113.518673] rtl8188ee 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[ 8113.518677] rtl8188ee 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8113.518679] rtl8188ee 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8113.522662] wlan0: associate with <MAC address removed> (try 1/3)
[ 8113.526012] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=4)
[ 8113.526186] wlan0: associated
[ 8113.526223] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############
```

Thanks!

---

### Post by praseodym on 2014-04-19
Hi,

maybe a network-manager problem:

```
[  391.519998] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
```
But there is an Intel driver loaded (iwlwifi). Blacklist it and reload the Realtek one:
```

echo "blacklist iwlwifi" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -rfv rtl8188ee
sudo modprobe -v rtl8188ee
```

---

