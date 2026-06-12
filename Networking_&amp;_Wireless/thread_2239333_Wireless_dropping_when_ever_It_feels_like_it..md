---
title: "Wireless dropping when ever It feels like it."
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by Langney on 2014-08-13
Hi this could be every 5 minutes to every 2 minutes. Not sure whats going on. Here Is the report though. Maybe someone here can figure whats wrong. Thanks 

```

########## wireless info START ##########

Report from: 13 Aug 2014 12:23 BST +0100

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 003: ID 04d9:a061 Holtek Semiconductor, Inc. 
Bus 005 Device 002: ID 152e:2507 LG (HLDS) PL-2507 IDE Controller
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID ffc0:0040  
Bus 003 Device 004: ID 0846:9010 NetGear, Inc. WNDA3100v1 802.11abgn [Atheros AR9170+AR9104]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

11: phy11: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

carl9170               91161  0 
ath                    28698  1 carl9170
mac80211              626557  1 carl9170
cfg80211              484040  3 ath,mac80211,carl9170
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  1 asus_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr MAC addr eth0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:90922 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136023778 (136.0 MB)  TX bytes:1560536 (1.5 MB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            carl9170
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    SKY7D431:        Infra, <MAC addr SKY7D431>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA2
    PlusnetWireless78BC69: Infra, <MAC addr PlusnetWireless78BC69>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    SKY53955:        Infra, <MAC addr SKY53955>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    BTHub3-K5P8:     Infra, <MAC addr BTHub3-K5P8>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 5180 MHz, Rate 54 Mb/s, Strength 97
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    TALKTALKC696AC:  Infra, <MAC addr TALKTALKC696AC>, Freq 2432 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BTHub4-H5FZ:     Infra, <MAC addr BTHub4-H5FZ>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC address>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption keyn
                    ESSID:"BTHub4-H5FZ"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000190bfbff41
                    Extra: Last beacon: 3668ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr SKY7D431>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption keyn
                    ESSID:"SKY7D431"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000eed5a3d9f4
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption keyn
                    ESSID:"TNCAPA3F6F9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr BTHub3-K5P8>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption keyn
                    ESSID:"BTHub3-K5P8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000030640ac98
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTWifi-X>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption keyn
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000306401777
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 06 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption keyff
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000030640d5fe
                    Extra: Last beacon: 0ms ago
          Cell 07 - Address: <MAC addr BTHub4-H5FZ>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption keyn
                    ESSID:"BTHub4-H5FZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000190bf07392
                    Extra: Last beacon: 4948ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr BTWifi-with-FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption keyff
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000190bf0a1b3
                    Extra: Last beacon: 4924ms ago
          Cell 09 - Address: <MAC addr TALKTALKC696AC>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption keyn
                    ESSID:"TALKTALKC696AC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000232ba1de0
                    Extra: Last beacon: 4544ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC addr PlusnetWireless78BC69>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption keyn
                    ESSID:"PlusnetWireless78BC69"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001bba8667265
                    Extra: Last beacon: 4300ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC addr SKY53955>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption keyn
                    ESSID:"SKY53955"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001195883186
                    Extra: Last beacon: 3948ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption keyn
                    ESSID:"SKY1E33D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001445922d183
                    Extra: Last beacon: 3820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption keyn
                    ESSID:"BTHub3-TQJR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b029dd89d4
                    Extra: Last beacon: 3784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC addr BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption keyff
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b029de639d
                    Extra: Last beacon: 3780ms ago
          Cell 15 - Address: <MAC addr BTWifi-with-FON>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption keyff
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:6 Mb/s; 9 Mb/s

##### module infos #####

[carl9170]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     F69F7AA6A1CF9E52DDE89FD
alias:          usb:v1B75p9170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p02B4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0249d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0026d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3417d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0326d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0804d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0ACEp1221d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vCACEp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,ath,cfg80211
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        09:4B:30:96:4E:E6:CE:B2:C5:672:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512
parm:           nohwcryptisable hardware crypto offload. (bool)
parm:           nohtisable MPDU aggregation. (int)

[ath]
filename:       /lib/modules/3.13.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        09:4B:30:96:4E:E6:CE:B2:C5:672:52:22:6B:47:71:2C:FD:8A:F6
sig_hashalgo:   sha512

##### module parameters #####

[carl9170]
noht: 0
nohwcrypt: N

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (carl9170)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.283062] type=1400 audit(1407922704.222:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
[   10.283194] type=1400 audit(1407922704.222:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=439 comm="apparmor_parser"
[   10.283432] type=1400 audit(1407922704.222:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=438 comm="apparmor_parser"
[   10.283569] type=1400 audit(1407922704.222:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=439 comm="apparmor_parser"
[   11.237102] usb 3-3: firmware API: 1.9.6 2012-07-07
[   11.577853] ath: EEPROM regdomain: 0x0
[   11.577855] ath: EEPROM indicates default country code should be used
[   11.577855] ath: doing EEPROM country->regdmn map search
[   11.577857] ath: country maps to regdmn code: 0x3a
[   11.577857] ath: Country alpha2 being used: US
[   11.577858] ath: Regpair used: 0x3a
[   11.767660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   11.767877] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.282299] wlan0: authenticate with <MAC address>
[   17.357773] wlan0: send auth to <MAC address> (try 1/3)
[   17.358726] wlan0: authenticated
[   17.358796] wlan0: waiting for beacon from <MAC address>
[   17.422638] wlan0: associate with <MAC address> (try 1/3)
[   17.423469] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[   17.427288] wlan0: associated
[   17.427306] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1055.830751] usb 3-3: firmware upload failed (-22).
[ 1056.835416] wlan0: authenticate with <MAC addr BTHub4-H5FZ>
[ 1056.835478] wlan0: direct probe to <MAC addr BTHub4-H5FZ> (try 1/3)
[ 1057.290625] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 1057.629654] ath: EEPROM regdomain: 0x0
[ 1057.629657] ath: EEPROM indicates default country code should be used
[ 1057.629659] ath: doing EEPROM country->regdmn map search
[ 1057.629661] ath: country maps to regdmn code: 0x3a
[ 1057.629663] ath: Country alpha2 being used: US
[ 1057.629664] ath: Regpair used: 0x3a
[ 1057.809582] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1057.809782] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1063.057275] wlan0: authenticate with <MAC address>
[ 1063.134226] wlan0: send auth to <MAC address> (try 1/3)
[ 1063.135202] wlan0: authenticated
[ 1063.135272] wlan0: waiting for beacon from <MAC address>
[ 1063.178953] wlan0: associate with <MAC address> (try 1/3)
[ 1063.179865] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 1063.184066] wlan0: associated
[ 1063.184119] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1139.219576] usb 3-3: firmware upload failed (-22).
[ 1140.239755] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 1140.684266] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 1141.024597] ath: EEPROM regdomain: 0x0
[ 1141.024604] ath: EEPROM indicates default country code should be used
[ 1141.024607] ath: doing EEPROM country->regdmn map search
[ 1141.024611] ath: country maps to regdmn code: 0x3a
[ 1141.024614] ath: Country alpha2 being used: US
[ 1141.024617] ath: Regpair used: 0x3a
[ 1141.206774] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1141.206964] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1151.599026] wlan0: authenticate with <MAC address>
[ 1151.674874] wlan0: send auth to <MAC address> (try 1/3)
[ 1151.676173] wlan0: send auth to <MAC address> (try 2/3)
[ 1151.677806] wlan0: send auth to <MAC address> (try 3/3)
[ 1151.678891] wlan0: authentication with <MAC address> timed out
[ 1151.784128] wlan0: authenticate with <MAC address>
[ 1151.860319] wlan0: send auth to <MAC address> (try 1/3)
[ 1151.861049] wlan0: authenticated
[ 1151.863969] wlan0: associate with <MAC address> (try 1/3)
[ 1151.864826] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 1151.868716] wlan0: associated
[ 1151.868770] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2990.834451] wlan0: deauthenticated from <MAC address> (Reason: 6)
[ 3006.065991] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3623.399421] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 3623.738698] ath: EEPROM regdomain: 0x0
[ 3623.738705] ath: EEPROM indicates default country code should be used
[ 3623.738708] ath: doing EEPROM country->regdmn map search
[ 3623.738712] ath: country maps to regdmn code: 0x3a
[ 3623.738715] ath: Country alpha2 being used: US
[ 3623.738718] ath: Regpair used: 0x3a
[ 3623.922472] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3623.922634] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3634.307754] wlan0: authenticate with <MAC address>
[ 3634.389607] wlan0: send auth to <MAC address> (try 1/3)
[ 3634.390133] wlan0: authenticated
[ 3634.390217] wlan0: waiting for beacon from <MAC address>
[ 3634.493598] wlan0: associate with <MAC address> (try 1/3)
[ 3634.494550] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 3634.498488] wlan0: associated
[ 3634.498508] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3634.586921] wlan0: authenticate with <MAC addr BTHub4-H5FZ>
[ 3634.665646] wlan0: send auth to <MAC addr BTHub4-H5FZ> (try 1/3)
[ 3634.667327] wlan0: authenticated
[ 3634.669395] wlan0: associate with <MAC addr BTHub4-H5FZ> (try 1/3)
[ 3634.672902] wlan0: RX AssocResp from <MAC addr BTHub4-H5FZ> (capab=0x431 status=0 aid=30)
[ 3634.677066] wlan0: associated
[ 4240.149881] usb 3-3: firmware upload failed (-110).
[ 4240.173883] wlan0: deauthenticating from <MAC addr BTHub4-H5FZ> by local choice (reason=3)
[ 4241.569806] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 4241.916569] ath: EEPROM regdomain: 0x0
[ 4241.916576] ath: EEPROM indicates default country code should be used
[ 4241.916579] ath: doing EEPROM country->regdmn map search
[ 4241.916583] ath: country maps to regdmn code: 0x3a
[ 4241.916586] ath: Country alpha2 being used: US
[ 4241.916589] ath: Regpair used: 0x3a
[ 4242.101840] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4242.102059] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4252.518331] wlan0: authenticate with <MAC address>
[ 4252.597213] wlan0: send auth to <MAC address> (try 1/3)
[ 4252.598326] wlan0: authenticated
[ 4252.601537] wlan0: associate with <MAC address> (try 1/3)
[ 4252.602465] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4252.606178] wlan0: associated
[ 4252.606199] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4252.616620] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[ 4252.695354] wlan0: authenticate with <MAC address>
[ 4252.771596] wlan0: send auth to <MAC address> (try 1/3)
[ 4252.772338] wlan0: authenticated
[ 4252.777424] wlan0: associate with <MAC address> (try 1/3)
[ 4252.778412] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4252.782242] wlan0: associated
[ 4434.837856] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 4440.195606] wlan0: authenticate with <MAC address>
[ 4440.270956] wlan0: send auth to <MAC address> (try 1/3)
[ 4440.271607] wlan0: authenticated
[ 4440.272630] wlan0: associate with <MAC address> (try 1/3)
[ 4440.273498] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4440.277256] wlan0: associated
[ 4890.887527] usb 3-3: firmware upload failed (-22).
[ 4891.919359] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 4892.500346] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 4892.840360] ath: EEPROM regdomain: 0x0
[ 4892.840363] ath: EEPROM indicates default country code should be used
[ 4892.840364] ath: doing EEPROM country->regdmn map search
[ 4892.840365] ath: country maps to regdmn code: 0x3a
[ 4892.840366] ath: Country alpha2 being used: US
[ 4892.840368] ath: Regpair used: 0x3a
[ 4893.035433] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4893.035861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4903.446649] wlan0: authenticate with <MAC address>
[ 4903.526312] wlan0: send auth to <MAC address> (try 1/3)
[ 4903.527248] wlan0: authenticated
[ 4903.528155] wlan0: associate with <MAC address> (try 1/3)
[ 4903.529091] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4903.532893] wlan0: associated
[ 4903.532921] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4903.551281] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[ 4903.630949] wlan0: authenticate with <MAC address>
[ 4903.707121] wlan0: send auth to <MAC address> (try 1/3)
[ 4903.708101] wlan0: authenticated
[ 4903.712078] wlan0: associate with <MAC address> (try 1/3)
[ 4903.712946] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4903.716661] wlan0: associated
[ 4974.328305] usb 3-3: firmware upload failed (-22).
[ 4975.360467] wlan0: authenticate with <MAC addr BTHub4-H5FZ>
[ 4975.360510] wlan0: direct probe to <MAC addr BTHub4-H5FZ> (try 1/3)
[ 4975.865030] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 4976.206842] ath: EEPROM regdomain: 0x0
[ 4976.206845] ath: EEPROM indicates default country code should be used
[ 4976.206846] ath: doing EEPROM country->regdmn map search
[ 4976.206847] ath: country maps to regdmn code: 0x3a
[ 4976.206848] ath: Country alpha2 being used: US
[ 4976.206849] ath: Regpair used: 0x3a
[ 4976.391766] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4976.392466] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4981.646646] wlan0: authenticate with <MAC address>
[ 4981.723087] wlan0: send auth to <MAC address> (try 1/3)
[ 4981.724037] wlan0: authenticated
[ 4981.728109] wlan0: associate with <MAC address> (try 1/3)
[ 4981.729089] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 4981.732909] wlan0: associated
[ 4981.732959] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5304.055462] usb 3-3: firmware upload failed (-22).
[ 5305.067068] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 5305.555406] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 5305.894569] ath: EEPROM regdomain: 0x0
[ 5305.894576] ath: EEPROM indicates default country code should be used
[ 5305.894579] ath: doing EEPROM country->regdmn map search
[ 5305.894583] ath: country maps to regdmn code: 0x3a
[ 5305.894586] ath: Country alpha2 being used: US
[ 5305.894589] ath: Regpair used: 0x3a
[ 5306.067977] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5306.068205] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5311.317681] wlan0: authenticate with <MAC address>
[ 5311.394446] wlan0: send auth to <MAC address> (try 1/3)
[ 5311.395730] wlan0: authenticated
[ 5311.395980] wlan0: waiting for beacon from <MAC address>
[ 5311.463645] wlan0: associate with <MAC address> (try 1/3)
[ 5311.567441] wlan0: associate with <MAC address> (try 2/3)
[ 5311.671354] wlan0: associate with <MAC address> (try 3/3)
[ 5311.775285] wlan0: association with <MAC address> timed out
[ 5312.164559] wlan0: authenticate with <MAC addr BTHub4-H5FZ>
[ 5312.242908] wlan0: send auth to <MAC addr BTHub4-H5FZ> (try 1/3)
[ 5312.247556] wlan0: authenticated
[ 5312.250677] wlan0: associate with <MAC addr BTHub4-H5FZ> (try 1/3)
[ 5312.257038] wlan0: RX AssocResp from <MAC addr BTHub4-H5FZ> (capab=0x431 status=0 aid=30)
[ 5312.260888] wlan0: associated
[ 5312.260915] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5385.868228] usb 3-3: firmware upload failed (-22).
[ 5386.883788] wlan0: deauthenticating from <MAC addr BTHub4-H5FZ> by local choice (reason=3)
[ 5387.346426] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 5387.693467] ath: EEPROM regdomain: 0x0
[ 5387.693474] ath: EEPROM indicates default country code should be used
[ 5387.693476] ath: doing EEPROM country->regdmn map search
[ 5387.693480] ath: country maps to regdmn code: 0x3a
[ 5387.693484] ath: Country alpha2 being used: US
[ 5387.693486] ath: Regpair used: 0x3a
[ 5387.880636] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5387.880798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5398.299565] wlan0: authenticate with <MAC address>
[ 5398.377258] wlan0: send auth to <MAC address> (try 1/3)
[ 5398.378835] wlan0: authenticated
[ 5398.382388] wlan0: associate with <MAC address> (try 1/3)
[ 5398.383290] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 5398.387107] wlan0: associated
[ 5398.387125] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5398.399636] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[ 5398.478802] wlan0: authenticate with <MAC address>
[ 5398.554870] wlan0: send auth to <MAC address> (try 1/3)
[ 5398.556788] wlan0: authenticated
[ 5398.558186] wlan0: associate with <MAC address> (try 1/3)
[ 5398.559151] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 5398.563378] wlan0: associated
[ 5834.824923] wlan0: deauthenticated from <MAC address> (Reason: 6)
[ 5835.229494] wlan0: authenticate with <MAC addr BTHub4-H5FZ>
[ 5835.308931] wlan0: send auth to <MAC addr BTHub4-H5FZ> (try 1/3)
[ 5835.310603] wlan0: authenticated
[ 5835.312760] wlan0: associate with <MAC addr BTHub4-H5FZ> (try 1/3)
[ 5835.316362] wlan0: RX AssocResp from <MAC addr BTHub4-H5FZ> (capab=0x431 status=0 aid=30)
[ 5835.320591] wlan0: associated
[ 5958.496364] usb 3-3: firmware upload failed (-22).
[ 5959.511909] wlan0: deauthenticating from <MAC addr BTHub4-H5FZ> by local choice (reason=3)
[ 5959.940287] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 5960.278840] ath: EEPROM regdomain: 0x0
[ 5960.278842] ath: EEPROM indicates default country code should be used
[ 5960.278843] ath: doing EEPROM country->regdmn map search
[ 5960.278844] ath: country maps to regdmn code: 0x3a
[ 5960.278845] ath: Country alpha2 being used: US
[ 5960.278846] ath: Regpair used: 0x3a
[ 5960.464016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5960.464289] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5970.898382] wlan0: authenticate with <MAC address>
[ 5970.974988] wlan0: send auth to <MAC address> (try 1/3)
[ 5970.975523] wlan0: authenticated
[ 5970.975604] wlan0: associating with AP with corrupt beacon
[ 5970.978490] wlan0: associate with <MAC address> (try 1/3)
[ 5970.979459] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 5970.983204] wlan0: associated
[ 5970.983220] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5971.003145] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[ 5971.081979] wlan0: authenticate with <MAC address>
[ 5971.157982] wlan0: send auth to <MAC address> (try 1/3)
[ 5971.158569] wlan0: authenticated
[ 5971.159273] wlan0: associating with AP with corrupt beacon
[ 5971.162286] wlan0: associate with <MAC address> (try 1/3)
[ 5971.163190] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 5971.167260] wlan0: associated
[ 6034.894779] usb 3-3: firmware upload failed (-22).
[ 6035.915043] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 6036.351571] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 6036.712676] ath: EEPROM regdomain: 0x0
[ 6036.712683] ath: EEPROM indicates default country code should be used
[ 6036.712686] ath: doing EEPROM country->regdmn map search
[ 6036.712690] ath: country maps to regdmn code: 0x3a
[ 6036.712693] ath: Country alpha2 being used: US
[ 6036.712696] ath: Regpair used: 0x3a
[ 6036.902069] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6036.902243] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6047.294455] wlan0: authenticate with <MAC address>
[ 6047.374263] wlan0: send auth to <MAC address> (try 1/3)
[ 6047.375224] wlan0: authenticated
[ 6047.379338] wlan0: associate with <MAC address> (try 1/3)
[ 6047.380343] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 6047.384623] wlan0: associated
[ 6047.384658] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6047.400907] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[ 6047.480060] wlan0: authenticate with <MAC address>
[ 6047.555025] wlan0: send auth to <MAC address> (try 1/3)
[ 6047.556294] wlan0: authenticated
[ 6047.563487] wlan0: associate with <MAC address> (try 1/3)
[ 6047.564396] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 6047.568333] wlan0: associated
[ 6114.489897] usb 3-3: firmware upload failed (-22).
[ 6115.502065] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[ 6115.938645] usb 3-3: firmware API: 1.9.6 2012-07-07
[ 6116.277310] ath: EEPROM regdomain: 0x0
[ 6116.277313] ath: EEPROM indicates default country code should be used
[ 6116.277314] ath: doing EEPROM country->regdmn map search
[ 6116.277316] ath: country maps to regdmn code: 0x3a
[ 6116.277317] ath: Country alpha2 being used: US
[ 6116.277319] ath: Regpair used: 0x3a
[ 6116.453866] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6116.454027] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6126.863515] wlan0: authenticate with <MAC address>
[ 6126.941382] wlan0: send auth to <MAC address> (try 1/3)
[ 6126.942405] wlan0: authenticated
[ 6126.942489] wlan0: waiting for beacon from <MAC address>
[ 6127.034309] wlan0: associate with <MAC address> (try 1/3)
[ 6127.138240] wlan0: associate with <MAC address> (try 2/3)
[ 6127.242189] wlan0: associate with <MAC address> (try 3/3)
[ 6127.346105] wlan0: association with <MAC address> timed out
[ 6127.454217] wlan0: authenticate with <MAC address>
[ 6127.532210] wlan0: send auth to <MAC address> (try 1/3)
[ 6127.532804] wlan0: authenticated
[ 6127.534423] wlan0: associate with <MAC address> (try 1/3)
[ 6127.535344] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=30)
[ 6127.539290] wlan0: associated
[ 6127.539338] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6179.571998] wlan0: deauthenticated from <MAC address> (Reason: 6)
[ 6195.313696] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

---

### Post by Langney on 2014-08-13
Bump

---

### Post by Langney on 2014-08-14
Anybody? If nobody can help would It be better for me to go back to Windows as I cannot afford another wireless card :(

---

### Post by weatherman2 on 2014-08-14
Open a terminal and try the solution suggested here and see if it helps:

[http://ubuntuforums.org/showthread.php?t=2110150](http://ubuntuforums.org/showthread.php?t=2110150)

Here it is without the typo:

```
sudo modprobe -r  carll9170
sudo modprobe carl9170 noht=1

```

You may need to re-start network-manager as well this one time if you see no wireless networks after issuing those two commands:

```

sudo service network-manager restart

```

If the wireless is more stable after those two commands, you can add a modprobe.d file to make it persistent at each boot.

---

### Post by Langney on 2014-08-24
> **weatherman2 said:**
> Open a terminal and try the solution suggested here and see if it helps:

[http://ubuntuforums.org/showthread.php?t=2110150](http://ubuntuforums.org/showthread.php?t=2110150)

Here it is without the typo:

```
sudo modprobe -r  carll9170
sudo modprobe carl9170 noht=1

```

You may need to re-start network-manager as well this one time if you see no wireless networks after issuing those two commands:

```

sudo service network-manager restart

```

If the wireless is more stable after those two commands, you can add a modprobe.d file to make it persistent at each boot.


Hi when I open terminal and type that I get this message.

> craig@craig-All-Series:~$ sudo modprobe -r  carll9170modprobe: FATAL: Module carll9170 not found.

Any Idea's? Cheers :)

---

