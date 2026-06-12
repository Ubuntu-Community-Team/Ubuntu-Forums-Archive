---
title: "Wifi networks recognized, will not connect. Realtek 8188ce PCI"
date: 2015-03-19
forum: Networking &amp; Wireless
---

### Post by hdulcio on 2015-03-19
########## wireless info START ##########

Report from: 19 Mar 2015 22:25 CDT -0500

Booted last: 19 Mar 2015 22:21 CDT -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic

##### kernel ############################

Linux 3.16.0-31-generic #43-Ubuntu SMP Tue Mar 10 17:37:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8182]
    Kernel driver in use: rtl8192ce

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fc66]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              53509  0 
rtl_pci                26674  1 rtl8192ce
rtlwifi                64237  2 rtl_pci,rtl8192ce
rtl8192c_common        53170  1 rtl8192ce
mac80211              660592  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              510218  2 mac80211,rtlwifi
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: ::2187:bae4:e64c:566c/64 Scope:Global
          inet6 addr: ::3a60:77ff:fefc:35f/64 Scope:Global
          inet6 addr: fe80::3a60:77ff:fefc:35f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18473 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26539181 (26.5 MB)  TX bytes:906614 (906.6 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::e2ca:94ff:fe9e:79a4/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:227 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60653 (60.6 KB)  TX bytes:47373 (47.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.0.27
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             208.180.42.68
    DNS:             208.180.42.100

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    linksys:         Infra, <MAC 'linksys' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    ATT393:          Infra, <MAC 'ATT393' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    suddenlink.net-FEB0: Infra, <MAC 'suddenlink.net-FEB0' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    belkin.654:      Infra, <MAC 'belkin.654' [AC23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC28]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA2
    suddenlink.net-2D00: Infra, <MAC 'suddenlink.net-2D00' [AN6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA2
    ATT856:          Infra, <MAC 'ATT856' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Ostrander:       Infra, <MAC 'Ostrander' [AC34]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    suddenlink.net-FA42: Infra, <MAC 'suddenlink.net-FA42' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    DIRECT-LO-VIZIOTV: Infra, <MAC 'DIRECT-LO-VIZIOTV' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 99 WPA2
    NotYourWifi:     Infra, <MAC 'NotYourWifi' [AC4]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    suddenlink.net-F880: Infra, <MAC 'suddenlink.net-F880' [AC5]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC6]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA2
    KitanaMK:        Infra, <MAC 'KitanaMK' [AN15]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA2
    suddenlink.net-F1B2: Infra, <MAC 'suddenlink.net-F1B2' [AN16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    WiFiRSU_82606:   Infra, <MAC 'WiFiRSU_82606' [AC8]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 50 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    NSA Van 1:       Infra, <MAC 'NSA Van 1' [AC16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Warehouse 13:    Infra, <MAC 'Warehouse 13' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    suddenlink.net-8882: Infra, <MAC 'suddenlink.net-8882' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    suddenlink.net-E372: Infra, <MAC 'suddenlink.net-E372' [AN23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    suddenlink.net-5550: Infra, <MAC 'suddenlink.net-5550' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    ATT503:          Infra, <MAC 'ATT503' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    WM71cf5e:        Infra, <MAC 'WM71cf5e' [AC11]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 100
    suddenlink.net-9350: Infra, <MAC 'suddenlink.net-9350' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    NETGEAR02:       Infra, <MAC 'NETGEAR02' [AC18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    suddenlink.net-E270: Infra, <MAC 'suddenlink.net-E270' [AN29]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA2
    RSS-351540:      Infra, <MAC 'RSS-351540' [AC22]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA2
    suddenlink.net-6DA0: Infra, <MAC 'suddenlink.net-6DA0' [AC17]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 24 WPA2
    CARL-HP_Network_1_EXT: Infra, <MAC 'CARL-HP_Network_1_EXT' [AC21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    PlebNet:         Infra, <MAC 'PlebNet' [AN33]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    ATT696:          Infra, <MAC 'ATT696' [AN34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/suddenlink.net-8882]] (600 root)
[connection] id=suddenlink.net-8882 | type=802-11-wireless
[802-11-wireless] ssid=suddenlink.net-8882 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR

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

##### iwlist scan #######################

Channel occupancy:

      9   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      8   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'suddenlink.net-8882' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-8882"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040b38c6d45
                    Extra: Last beacon: 692ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'linksys' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b064075cc
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT393' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ATT393"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013eb7b7d998
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NotYourWifi' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NotYourWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c97335f807
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'suddenlink.net-F880' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-F880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000051e62f30f16
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'RSS-351540' [AC6]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000051e62f32fd0
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'suddenlink.net-FEB0' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-FEB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f994dd720f
                    Extra: Last beacon: 8056ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WiFiRSU_82606' [AC8]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"WiFiRSU_82606"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019cdb9908a9
                    Extra: Last beacon: 8056ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'RSS-351540' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f994dda30f
                    Extra: Last beacon: 248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Warehouse 13' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Warehouse 13"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000037cce47b624
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'WM71cf5e' [AC11]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"WM71cf5e"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cab71bdeb8
                    Extra: Last beacon: 8ms ago
          Cell 12 - Address: <MAC 'suddenlink.net-FA42' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-FA42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001443841d7bd
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'suddenlink.net-5550' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-5550"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f994afd13e
                    Extra: Last beacon: 8344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'RSS-351540' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f9952b4982
                    Extra: Last beacon: 256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'ATT503' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"ATT503"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000096c90eaa5f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'NSA Van 1' [AC16]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NSA Van 1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000042a3388fa8
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'suddenlink.net-6DA0' [AC17]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-6DA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e90ebb168
                    Extra: Last beacon: 8748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'NETGEAR02' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR02"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002673028c19a
                    Extra: Last beacon: 660ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'suddenlink.net-9350' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-9350"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d6b47ca4c6
                    Extra: Last beacon: 8840ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'RSS-351540' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d6b4f79be5
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'CARL-HP_Network_1_EXT' [AC21]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"CARL-HP_Network_1_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009d38139103d
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'RSS-351540' [AC22]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001084cc12990
                    Extra: Last beacon: 588ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'belkin.654' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"belkin.654"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000023c9ce41c
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'suddenlink.net-0112' [AC24]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-0112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000042a5c6b151
                    Extra: Last beacon: 8864ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'NETGEAR78' [AC25]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR78"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003fe9036f192
                    Extra: Last beacon: 8796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'ATT3284' [AC26]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"ATT3284"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000332fa98180
                    Extra: Last beacon: 852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'suddenlink.net-6166' [AC27]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-6166"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007435d73fbd2
                    Extra: Last beacon: 820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'RSS-351540' [AC28]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e91659972
                    Extra: Last beacon: 764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'RSS-351540' [AC29]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"RSS-351540"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000051f6221397b
                    Extra: Last beacon: 728ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'suddenlink.net-E3F0' [AC30]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-E3F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000beac8c813e
                    Extra: Last beacon: 724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'suddenlink.net-7A00' [AC31]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-7A00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024f2f2b9856
                    Extra: Last beacon: 656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'Rogue Net Remote' [AC32]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Rogue Net Remote"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017ee198b180
                    Extra: Last beacon: 524ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'suddenlink.net-6550' [AC33]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"suddenlink.net-6550"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000083ba44119
                    Extra: Last beacon: 516ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'Ostrander' [AC34]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Ostrander"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000238b5cd1a40
                    Extra: Last beacon: 8ms ago
          Cell 35 - Address: <MAC 'Infinite Empire' [AC35]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Infinite Empire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9lo        Interface doesn't support scanning.

 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029938e03b5
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BE372FB24A1F38A5218DAA0
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
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

[rtl_pci]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.16.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D0CBADABD6F74A53B0BE7CC
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     88153DA7841870E4F2012EE
depends:        
intree:         Y
vermagic:       3.16.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        8F:62:79:8D:54:61:C9:EE:0E:18:3A:ED:94:93:38:E3:EA:18:89:46
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

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

lp

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   71.187732] wlan0: deauthenticating from <MAC 'suddenlink.net-8882' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   74.003248] wlan0: authenticate with <MAC 'suddenlink.net-8882' [AC1]>
[   74.347599] wlan0: send auth to <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[   74.350559] wlan0: authenticated
[   74.352890] wlan0: associate with <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[   74.362760] wlan0: RX AssocResp from <MAC 'suddenlink.net-8882' [AC1]> (capab=0xc31 status=0 aid=3)
[   74.362907] wlan0: associated
[  122.188603] wlan0: deauthenticating from <MAC 'suddenlink.net-8882' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  125.029182] wlan0: authenticate with <MAC 'suddenlink.net-8882' [AC1]>
[  125.377222] wlan0: send auth to <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[  125.380149] wlan0: authenticated
[  125.384273] wlan0: associate with <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[  125.396632] wlan0: RX AssocResp from <MAC 'suddenlink.net-8882' [AC1]> (capab=0xc31 status=0 aid=3)
[  125.396799] wlan0: associated
[  174.190241] wlan0: deauthenticating from <MAC 'suddenlink.net-8882' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  177.005003] wlan0: authenticate with <MAC 'suddenlink.net-8882' [AC1]>
[  177.352492] wlan0: send auth to <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[  177.356061] wlan0: authenticated
[  177.363503] wlan0: associate with <MAC 'suddenlink.net-8882' [AC1]> (try 1/3)
[  177.375072] wlan0: RX AssocResp from <MAC 'suddenlink.net-8882' [AC1]> (capab=0xc31 status=0 aid=3)
[  177.375220] wlan0: associated
[  225.189038] wlan0: deauthenticating from <MAC 'suddenlink.net-8882' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


Any guidance would be much appreciated, I'm still an amatuer at this stuff.

---

