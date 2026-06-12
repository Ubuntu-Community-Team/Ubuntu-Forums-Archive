---
title: "Ubuntu 14.04 wifi disconnected - offline"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by unstable_quokka on 2014-11-13
Hi all, I think I have a similar issue. Here's my Wireless Script's output:



[COLOR=#000000]```
[/COLOR]########## wireless info START ##########


Report from: 13 Nov 2014 18:20 CET +0100


Booted last: 13 Nov 2014 12:09 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


24:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1461]
	Kernel driver in use: ath9k


25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:167e]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 008: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 003: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath3k                  13318  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6743625 (6.7 MB)  TX bytes:1574570 (1.5 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:265710282 (265.7 MB)  TX bytes:15937675 (15.9 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"FASTWEB-1-gvs108iyyv27"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search labs.pbs.com


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Connessione Ethernet 1] ---------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.101
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


- Device: wlan0  [FASTWEB-1-gvs108iyyv27] --------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NETGEAR_A.S.Roma:Infra, <MAC 'NETGEAR_A.S.Roma' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    InfostradaWiFi-005976: Infra, <MAC 'InfostradaWiFi-005976' [AC7]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    InfostradaWiFi-003588: Infra, <MAC 'InfostradaWiFi-003588' [AC5]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    TNCAP24F45F:     Infra, <MAC 'TNCAP24F45F' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    TP-LINK_65EC5E:  Infra, <MAC 'TP-LINK_65EC5E' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    TeleTu_74888B184854: Infra, <MAC 'TeleTu_74888B184854' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    InfostradaWiFi-305873: Infra, <MAC 'InfostradaWiFi-305873' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    FLILLO:          Infra, <MAC 'FLILLO' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    TNCAP355D33:     Infra, <MAC 'TNCAP355D33' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    *FASTWEB-1-gvs108iyyv27: Infra, <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.112
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Isfol-Convegni]] (600 root)
[connection] id=Isfol-Convegni | type=802-11-wireless
[802-11-wireless] ssid=Isfol-Convegni | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Mirza Kadic]] (600 root)
[connection] id=Mirza Kadic | type=802-11-wireless
[802-11-wireless] ssid=Mirza Kadic | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AIRTIES_RT-204]] (600 root)
[connection] id=AIRTIES_RT-204 | type=802-11-wireless
[802-11-wireless] ssid=AIRTIES_RT-204 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AirTies_Air5341]] (600 root)
[connection] id=AirTies_Air5341 | type=802-11-wireless
[802-11-wireless] ssid=AirTies_Air5341 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Arduino Yun-90A2DAF02BF3]] (600 root)
[connection] id=Arduino Yun-90A2DAF02BF3 | type=802-11-wireless
[802-11-wireless] ssid=Arduino Yun-90A2DAF02BF3 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Telenor WiFi]] (600 root)
[connection] id=Telenor WiFi | type=802-11-wireless
[802-11-wireless] ssid=Telenor WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/FASTWEB-1-gvs108iyyv27]] (600 root)
[connection] id=FASTWEB-1-gvs108iyyv27 | type=802-11-wireless
[802-11-wireless] ssid=FASTWEB-1-gvs108iyyv27 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Isfol-P1]] (600 root)
[connection] id=Isfol-P1 | type=802-11-wireless
[802-11-wireless] ssid=Isfol-P1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OmbreRosse]] (600 root)
[connection] id=OmbreRosse | type=802-11-wireless
[802-11-wireless] ssid=OmbreRosse | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TNCAPB581D1]] (600 root)
[connection] id=TNCAPB581D1 | type=802-11-wireless
[802-11-wireless] ssid=TNCAPB581D1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


country IT:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"FASTWEB-1-gvs108iyyv27"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000058f480c8c
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'NETGEAR_A.S.Roma' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR_A.S.Roma"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000026e2a1f70
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001733902181
                    Extra: Last beacon: 440ms ago
          Cell 04 - Address: <MAC 'TP-LINK_65EC5E' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_65EC5E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000557cabff57
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'InfostradaWiFi-003588' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"InfostradaWiFi-003588"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000076f725a1e
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FLILLO' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"FLILLO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008029ab157
                    Extra: Last beacon: 1440ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'InfostradaWiFi-005976' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"InfostradaWiFi-005976"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000043fea8d4eec
                    Extra: Last beacon: 1024ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TeleTu_74888B184854' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"TeleTu_74888B184854"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     661F5D1CDD236CFF7BE3FA5
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


loop
lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1


[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.5/0000:25:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:24:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[12650.982043] wlan0: authenticate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>
[12650.998001] wlan0: send auth to <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[12650.999986] wlan0: authenticated
[12651.000919] wlan0: associate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[12651.043432] wlan0: RX AssocResp from <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (capab=0x411 status=0 aid=5)
[12651.043487] wlan0: associated
[12651.043517] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12651.048526] ath: EEPROM regdomain: 0x817c
[12651.048531] ath: EEPROM indicates we should expect a country code
[12651.048534] ath: doing EEPROM country->regdmn map search
[12651.048536] ath: country maps to regdmn code: 0x37
[12651.048538] ath: Country alpha2 being used: IT
[12651.048540] ath: Regpair used: 0x37
[12651.048543] ath: regdomain 0x817c dynamically updated by country IE
[14017.052892] wlan0: deauthenticating from <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> by local choice (reason=3)
[14024.422712] wlan0: authenticate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>
[14024.439035] wlan0: send auth to <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[14024.440998] wlan0: authenticated
[14024.443154] wlan0: associate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[14024.457947] wlan0: RX AssocResp from <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (capab=0x411 status=0 aid=5)
[14024.458006] wlan0: associated
[14024.458039] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14024.461695] ath: EEPROM regdomain: 0x817c
[14024.461699] ath: EEPROM indicates we should expect a country code
[14024.461701] ath: doing EEPROM country->regdmn map search
[14024.461703] ath: country maps to regdmn code: 0x37
[14024.461704] ath: Country alpha2 being used: IT
[14024.461706] ath: Regpair used: 0x37
[14024.461708] ath: regdomain 0x817c dynamically updated by country IE
[15523.143415] wlan0: deauthenticating from <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> by local choice (reason=3)
[16596.313484] wlan0: authenticate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]>
[16596.334892] wlan0: send auth to <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[16596.336892] wlan0: authenticated
[16596.339696] wlan0: associate with <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (try 1/3)
[16596.345451] wlan0: RX AssocResp from <MAC 'FASTWEB-1-gvs108iyyv27' [AC1]> (capab=0x411 status=0 aid=1)
[16596.345535] wlan0: associated
[16596.345546] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[16596.349562] ath: EEPROM regdomain: 0x817c
[16596.349566] ath: EEPROM indicates we should expect a country code
[16596.349568] ath: doing EEPROM country->regdmn map search
[16596.349570] ath: country maps to regdmn code: 0x37
[16596.349572] ath: Country alpha2 being used: IT
[16596.349573] ath: Regpair used: 0x37
[16596.349576] ath: regdomain 0x817c dynamically updated by country IE


########## wireless info END ############[COLOR=#000000]
```[/COLOR]

---

### Post by slickymaster on 2014-11-14
Moved to a thread of its own.

Hi unstable_quokka, welcome to the forums. Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

