---
title: "Realtek rtl8821ae not detected/disconnected (vivopc vm40b)"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by Brian_Deizt on 2015-01-09
Hi all,

I'm fairly new to Ubuntu so please be specific. I appreciate all your help. Problem is as in title. Thanks a lot for your time!

```

########## wireless info START ##########

Report from: 10 Jan 2015 00:57 ICT +0700

Booted last: 10 Jan 2015 00:54 ICT +0700

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85b4]
    Kernel driver in use: rtl8821ae

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0b05:17dc ASUSTek Computer, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:1126 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04f2:1125 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              76531  0 
ath9k_common           25638  1 ath9k_htc
ath9k_hw              459794  2 ath9k_common,ath9k_htc
ath                    29397  3 ath9k_common,ath9k_htc,ath9k_hw
eeepc_wmi              13151  0 
asus_wmi               24697  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
rtl8821ae             566837  0 
mac80211              687021  2 ath9k_htc,rtl8821ae
cfg80211              521225  5 ath,ath9k_common,mac80211,ath9k_htc,rtl8821ae
wmi                    19379  1 asus_wmi
video                  20521  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::eade:27ff:fe12:6818/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:540199 (540.1 KB)  TX bytes:253378 (253.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"Tenda_056620"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Tenda_056620' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:237   Missed beacon:0

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Tenda_056620] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Ha Nguyen:       Infra, <MAC 'Ha Nguyen' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA2
    DANGKHOA:        Infra, <MAC 'DANGKHOA' [AC4]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 39 WPA
    1Apartment475:   Infra, <MAC '1Apartment475' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA
    QuynhAnh:        Infra, <MAC 'QuynhAnh' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA
    anna:            Infra, <MAC 'anna' [AC12]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 15 WPA
    LE NGUYEN:       Infra, <MAC 'LE NGUYEN' [AN6]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 15 WPA2
    *Tenda_056620:   Infra, <MAC 'Tenda_056620' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA
    Supra:           Infra, <MAC 'Supra' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    ai dung toi do:  Infra, <MAC 'ai dung toi do' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    At2010:          Infra, <MAC 'At2010' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Taken:           Infra, <MAC 'Taken' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    gloops-mobile:   Infra, <MAC 'gloops-mobile' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    Other Network:   Infra, <MAC 'Other Network' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    SoNic21:         Infra, <MAC 'SoNic21' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

[[/etc/NetworkManager/system-connections/Tenda_056620]] (600 root)
[connection] id=Tenda_056620 | type=802-11-wireless
[802-11-wireless] ssid=Tenda_056620 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Ho_Chi_Minh (based on set time zone)

country 98:
    (2402 - 2482 @ 40), (N/A, 20)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     13 channels in total; available frequencies :
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

wlan0     24 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Tenda_056620' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Tenda_056620"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ef94cc6d
                    Extra: Last beacon: 184ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Ha Nguyen' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Ha Nguyen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006b1f97b5fb
                    Extra: Last beacon: 5572ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Supra' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Supra"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064760ac1cb
                    Extra: Last beacon: 200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DANGKHOA' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"DANGKHOA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ba23b014e
                    Extra: Last beacon: 264ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '1Apartment475' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"1Apartment475"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000003cf5b25
                    Extra: Last beacon: 188ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Taken' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"Taken"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006f527180
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 07 - Address: <MAC 'At2010' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"At2010"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000081d4860173
                    Extra: Last beacon: 1864ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'gloops-mobile' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"gloops-mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d3720aa186
                    Extra: Last beacon: 816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Other Network' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Other Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000173a2598abd
                    Extra: Last beacon: 1160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'QuynhAnh' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"QuynhAnh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000040452b0047
                    Extra: Last beacon: 1176ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'NguyenAn' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"NguyenAn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011b36bc256
                    Extra: Last beacon: 6352ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'anna' [AC12]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"anna"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f931c36ae5
                    Extra: Last beacon: 6120ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'HN' [AC13]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"HN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000173a2ef317f
                    Extra: Last beacon: 6128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'SAMIL F3' [AC14]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SAMIL F3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000482012e6
                    Extra: Last beacon: 5564ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
 eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

                       Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'hoanggiareal' [AC15]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"hoanggiareal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000079f93d6
                    Extra: Last beacon: 3344ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'SoNic21' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SoNic21"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008bef0c02e6
                    Extra: Last beacon: 1196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

wlan0     No scan results

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     6760E19A390B71B9B7D6299
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     50297023DA06CB0C907A2CA
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     765883F7BDCD751661973EB
depends:        ath
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtl8821ae]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/staging/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         Ping Yan<ping_yan@realsil.com.cn>
srcversion:     EA439BC895EA5691716AF12
depends:        mac80211,cfg80211
staging:        Y
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)

[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[rtl8821ae]
fwlps: N
ips: N
swenc: Y
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae swenc=1 ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   20.099669] rtl8821ae-0:rtl_pci_start():<0-0>  rtl_pci_start 
[   20.105146] rtl8821ae-0:rtl8821ae_download_fw():<0-0> normal Firmware SIZE 28984 
[   20.105150] rtl8821ae-0:rtl8821ae_download_fw():<0-0> Firmware Version(20), Signature(0x2101),Size(32)
[   20.120794] rtl8821ae-0:_rtl8821ae_fw_free_to_go():<0-0> Checksum report OK ! REG_MCUFWDL:0x00070604 .
[   20.152218] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 0] = 0x32343638
[   20.152224] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 1] = 0x36363838
[   20.152227] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 2] = 0x28303234
[   20.152229] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 3] = 0x34363838
[   20.152232] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 4] = 0x26283032
[   20.152235] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   20.152238] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   20.152240] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 0][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   20.152243] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 1] = 0x34343636
[   20.152246] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 2] = 0x26283032
[   20.152249] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 3] = 0x32343636
[   20.152251] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 4] = 0x24262830
[   20.152254] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 7] = 0x32343636
[   20.152257] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 8] = 0x24262830
[   20.152260] rtl8821ae-0:_rtl8821ae_store_tx_power_by_rate():<0-0> pHalData->TxPwrByRateOffset[Band 1][RfPath 0][TxNum 0][RateSection 9] = 0x2022
[   20.252983] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   20.253030] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> PairwiseEncAlgorithm = 0 GroupEncAlgorithm = 0
[   20.253033] rtl8821ae-0:rtl8821ae_enable_hw_security_config():<0-0> not open hw encryption
[   20.253291] rtl8821ae-0:rtl8821ae_set_hw_reg():<0-0> switch case not process 3e
[   20.253302] rtl8821ae-0:rtl_pci_start():<0-0> rtl_pci_start OK
[   20.258004] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.213282] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   22.077024] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   22.692829] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   23.556555] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   44.609879] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   45.473594] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[   77.599387] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[   78.463117] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  120.585709] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  121.449479] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  127.084088] usb 3-2: ath9k_htc: Firmware htc_9271.fw requested
[  127.084234] usbcore: registered new interface driver ath9k_htc
[  127.385025] usb 3-2: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[  127.622492] ath9k_htc 3-2:1.0: ath9k_htc: HTC initialized with 33 credits
[  127.890643] ath9k_htc 3-2:1.0: ath9k_htc: FW Version: 1.3
[  127.890659] ath: EEPROM regdomain: 0x809c
[  127.890661] ath: EEPROM indicates we should expect a country code
[  127.890663] ath: doing EEPROM country->regdmn map search
[  127.890664] ath: country maps to regdmn code: 0x52
[  127.890666] ath: Country alpha2 being used: CN
[  127.890668] ath: Regpair used: 0x52
[  128.208987] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  129.727664] wlan1: authenticate with <MAC 'Tenda_056620' [AC1]>
[  130.139484] wlan1: send auth to <MAC 'Tenda_056620' [AC1]> (try 1/3)
[  130.141369] wlan1: authenticated
[  130.142644] wlan1: associate with <MAC 'Tenda_056620' [AC1]> (try 1/3)
[  130.149017] wlan1: RX AssocResp from <MAC 'Tenda_056620' [AC1]> (capab=0x411 status=0 aid=2)
[  130.158823] wlan1: associated
[  130.158881] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  159.655672] ath: phy1: Could not kill baseband RX
[  173.584538] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  174.988769] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  236.599997] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  238.004273] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G
[  270.150132] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 5G
[  271.554412] rtl8821ae-0:rtl8821ae_phy_switch_wirelessband():<0-0> 2.4G

########## wireless info END ############


```[ATTACH]259124[/ATTACH]

---

### Post by Brian_Deizt on 2015-01-11
i've tried upgrading kernel, reloading driver but they doesn't work :( i'm really clueless now

---

