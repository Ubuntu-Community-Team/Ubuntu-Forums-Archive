---
title: "Atheros QCA9565/ AR9565 ubuntu 14.04 wireless not working"
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by Al-G on 2014-08-10
Hi, I'm a total Ubuntu Newbie so I appreciate your help and patience. I've tried for hours reading and searching posts and following instructions but still can't get the wireless working, The last thing I did was use the backport drivers backports-3.13-rc8-1 with no success, the wireless sees available networks but won't connect. After entering password for connection it just keeps saying authentication required (i've double checked and triple checked the password, other ubuntu laptops connect fine)  the laptop is a Lenovo ideapad flex 14. 

I would really appreciate any help, i'm off to bed now but will check the thread regularly in the morning.

Update: it did connect once which i was really happy about (i hadn't made any changes since the backports?), but unfortunately on restart it doesn't work again :(

---

### Post by wildmanne39 on 2014-08-10
Hi, click on the wireless script in my signature and follow the directions for running it.

---

### Post by Al-G on 2014-08-11
Hi thanks for the assistance, here's the output from the wireless script,

```

########## wireless info START ##########

Report from: 11 Aug 2014 17:46 BST +0100

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:3026]
    Kernel driver in use: ath9k

##### lsusb #####

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 003: ID 04f2:b421 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0eef:a107 D-WAV Scientific Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath9k                 105767  0 
ath9k_common           13550  1 ath9k
ath9k_hw              437171  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              530352  1 ath9k
cfg80211              483356  3 ath,ath9k,mac80211
compat                 13139  5 cfg80211,ath9k_common,ath9k,mac80211,ath9k_hw
ath3k                  13318  0 
bluetooth             391196  12 bnep,ath3k,btusb,rfcomm
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c654:44ff:fe11:a5d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:794836 (794.8 KB)  TX bytes:68296 (68.2 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7689 (7.6 KB)  TX bytes:10990 (10.9 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia4024094: Infra, <MAC addr virginmedia4024094>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2 Enterprise
    virginmedia4208758: Infra, <MAC addr virginmedia4208758>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    VM381976-2G:     Infra, <MAC addr VM381976-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTHub3-33QT:     Infra, <MAC addr BTHub3-33QT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15
    virginmedia8961008: Infra, <MAC addr virginmedia8961008>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr VM381976-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VM381976-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002cfdaf7bea
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr virginmedia4208758>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4208758"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002d9e4656b4
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr virginmedia4024094>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4024094"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000329f9fc4e23
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr BTHub3-33QT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-33QT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bc6ededfe
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bc6eee8a7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC addr BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bc6eec640
                    Extra: Last beacon: 12ms ago
          Cell 07 - Address: <MAC address>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e87e2a176
                    Extra: Last beacon: 508ms ago

##### module infos #####

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4FE8703F90CD409E1FDAC21
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     F1855C93DA7170B2E624BB2
depends:        compat,ath,ath9k_hw
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     842841BE7821B6483527C81
depends:        compat,ath
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0BE5FC7C1EAF38AFA84BEDB
depends:        cfg80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath3k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

##### module parameters #####

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.553526] type=1400 audit(1407774338.987:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   10.553545] type=1400 audit(1407774338.987:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=459 comm="apparmor_parser"
[   10.554000] type=1400 audit(1407774338.987:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=460 comm="apparmor_parser"
[   10.554021] type=1400 audit(1407774338.987:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=459 comm="apparmor_parser"
[   11.324031] ath: phy0: WB335 1-ANT card detected
[   11.324032] ath: phy0: Set BT/WLAN RX diversity capability
[   11.330707] ath: phy0: Enable LNA combining
[   11.331809] ath: EEPROM regdomain: 0x65
[   11.331809] ath: EEPROM indicates we should expect a direct regpair map
[   11.331810] ath: Country alpha2 being used: 00
[   11.331811] ath: Regpair used: 0x65
[   13.344697] Bluetooth: Error in firmware loading err = -110,len = 448, size = 1906
[   13.344832] ath3k: probe of 2-6:1.0 failed with error -110
[   14.269169] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.272223] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.094410] wlan0: authenticate with <MAC address>
[   16.114269] wlan0: send auth to <MAC address> (try 1/3)
[   16.117773] wlan0: authenticated
[   16.121747] wlan0: associate with <MAC address> (try 1/3)
[   16.225738] wlan0: associate with <MAC address> (try 2/3)
[   16.231397] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[   16.231442] wlan0: associated
[   16.231466] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  148.805148] wlan0: authenticate with <MAC address>
[  148.824916] wlan0: send auth to <MAC address> (try 1/3)
[  148.886021] wlan0: send auth to <MAC address> (try 2/3)
[  148.932066] wlan0: send auth to <MAC address> (try 3/3)
[  148.937735] wlan0: authenticated
[  148.940143] wlan0: associate with <MAC address> (try 1/3)
[  149.157168] wlan0: associate with <MAC address> (try 2/3)
[  149.303039] wlan0: associate with <MAC address> (try 3/3)
[  149.309495] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  149.309567] wlan0: associated
[  271.106383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

I have spent hours following the advice give here on the forums relating to this card, which i'm very grateful for, but still doesn't work.

Is it possible i've installed conflicting drivers now?? 

any assistance would be very helpful thanks :)

---

### Post by wildmanne39 on 2014-08-11
What is the name of the network you want to connect too?

---

### Post by Al-G on 2014-08-11
heya :) the network name is plokij, it's hidden at the moment, i did try letting the ssid broadcast but the issue remained? thanks for your help, i could see from the report that the ath9k drivers are in use, is it possible i've tried too many of the fixes advised and messed it up somehow? would i be better wiping and starting again? if i was to start again which backport package is the correct one? really sorry i'm totally out my depth here. i'm sure my stupidity shows.

Cheers,

Al

update: i tried to install ubuntu restricted extras, it froze for 3 hours i restarted and now the option to install is greyed out :( i'm trying very hard not to be dissillusioned here, but it's getting a bit hard lol :)

---

### Post by wildmanne39 on 2014-08-11
Hidden networks are not any more secure then non hidden networks and a lot harder for ubuntu to connect too, please unhide at least temporarily and post a new file so we can see if there are some settings that need to be changed in the router.

The ath9k driver comes with ubuntu when you install it and most of the time it works well with an added parameter which we will try, but I installed ubuntu 14.04 on my laptop using the same driver and for the first time with the parameter added it would not even connect.

Do:
```
sudo ifconfig wlan0 down
sudo modprobe -rv ath9k
sudo modprobe -v ath9k nohwcrypt=1
sudo ifconfig wlan0 up

``` 
if it helps we will need to make it permanent, it will be reset when you reboot.
How many different times did you install the driver?

---

### Post by Al-G on 2014-08-11
hiya , here the output with the ssid broadcast, i've also disabled the bluetoooth (don't know if that will make any difference just thout i'd try it)

```

########## wireless info START ##########

Report from: 12 Aug 2014 00:07 BST +0100

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:3026]
    Kernel driver in use: ath9k

##### lsusb #####

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 003: ID 04f2:b421 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0eef:a107 D-WAV Scientific Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath9k                 105767  0 
ath9k_common           13550  1 ath9k
ath9k_hw              437171  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              530352  1 ath9k
cfg80211              483356  3 ath,ath9k,mac80211
compat                 13139  5 cfg80211,ath9k_common,ath9k,mac80211,ath9k_hw
ath3k                  13318  0 
bluetooth             391196  23 bnep,ath3k,btusb,rfcomm
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c654:44ff:fe11:a5d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3396907 (3.3 MB)  TX bytes:509368 (509.3 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet6 addr: fe80::42f0:2fff:fe73:e9c7/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24680 (24.6 KB)  TX bytes:10845 (10.8 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia4024094: Infra, <MAC addr virginmedia4024094>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    virginmedia4208758: Infra, <MAC addr virginmedia4208758>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    VM381976-2G:     Infra, <MAC addr VM381976-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTHub3-33QT:     Infra, <MAC addr BTHub3-33QT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2 Enterprise
    plokij:          Infra, <MAC addr plokij>, Freq 2422 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    virginmedia8961008: Infra, <MAC addr virginmedia8961008>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    SKY99282:        Infra, <MAC addr SKY99282>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr plokij>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013c6b84176
                    Extra: Last beacon: 308764ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr virginmedia4024094>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4024094"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000032f4b2f3da7
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr BTHub3-33QT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-33QT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041181bf13f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041181cc983
                    Extra: Last beacon: 8ms ago
          Cell 05 - Address: <MAC addr virginmedia4208758>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4208758"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000032ef79a1b2
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000041181ce985
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC addr VM381976-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"VM381976-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000324ee0bef6
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr plokij>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"plokij"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000101429dc
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4FE8703F90CD409E1FDAC21
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,compat,cfg80211,ath
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     F1855C93DA7170B2E624BB2
depends:        compat,ath,ath9k_hw
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
version:        backported from Linux (v3.13-rc8-0-g7e22e91) using backports v3.13-rc8-1-0-gae71bd3
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     842841BE7821B6483527C81
depends:        compat,ath
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/3.13.0-32-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0BE5FC7C1EAF38AFA84BEDB
depends:        cfg80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 

[ath3k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

##### module parameters #####

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.288231] type=1400 audit(1407796571.681:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   10.289379] type=1400 audit(1407796571.685:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[   11.240075] ath: phy0: WB335 1-ANT card detected
[   11.240077] ath: phy0: Set BT/WLAN RX diversity capability
[   11.246784] ath: phy0: Enable LNA combining
[   11.247882] ath: EEPROM regdomain: 0x65
[   11.247883] ath: EEPROM indicates we should expect a direct regpair map
[   11.247885] ath: Country alpha2 being used: 00
[   11.247886] ath: Regpair used: 0x65
[   14.458453] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.461703] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.319821] wlan0: authenticate with <MAC addr plokij>
[   16.339761] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   16.386318] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   16.391330] wlan0: authenticated
[   16.395226] wlan0: associate with <MAC addr plokij> (try 1/3)
[   16.620531] wlan0: associate with <MAC addr plokij> (try 2/3)
[   16.650191] wlan0: associate with <MAC addr plokij> (try 3/3)
[   16.836823] wlan0: association with <MAC addr plokij> timed out
[   17.808553] wlan0: authenticate with <MAC addr plokij>
[   17.828430] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   17.897011] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   17.963420] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   18.051849] wlan0: authentication with <MAC addr plokij> timed out
[   19.417079] wlan0: authenticate with <MAC addr plokij>
[   19.437109] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   19.506335] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   19.569750] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   19.655033] wlan0: authentication with <MAC addr plokij> timed out
[   21.517904] wlan0: authenticate with <MAC addr plokij>
[   21.537932] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   21.539806] wlan0: authenticated
[   21.541374] wlan0: associate with <MAC addr plokij> (try 1/3)
[   21.545686] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   21.545730] wlan0: associated
[   21.545740] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.798875] wlan0: authenticate with <MAC addr plokij>
[   23.818937] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   23.871574] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   23.947686] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   24.138490] wlan0: authentication with <MAC addr plokij> timed out
[   25.495978] wlan0: authenticate with <MAC addr plokij>
[   25.516001] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   25.520177] wlan0: authenticated
[   25.523532] wlan0: associate with <MAC addr plokij> (try 1/3)
[   25.678925] wlan0: associate with <MAC addr plokij> (try 2/3)
[   25.772135] wlan0: associate with <MAC addr plokij> (try 3/3)
[   25.923895] wlan0: association with <MAC addr plokij> timed out
[   27.782101] wlan0: authenticate with <MAC addr plokij>
[   27.802146] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   28.013815] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   28.019268] wlan0: authenticated
[   28.021840] wlan0: associate with <MAC addr plokij> (try 1/3)
[   28.208200] wlan0: associate with <MAC addr plokij> (try 2/3)
[   28.222830] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   28.222876] wlan0: associated
[   31.812055] wlan0: authenticate with <MAC addr plokij>
[   31.826863] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   31.831036] wlan0: authenticated
[   31.833263] wlan0: associate with <MAC addr plokij> (try 1/3)
[   31.930633] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   31.930678] wlan0: associated
[   33.839767] wlan0: authenticate with <MAC addr plokij>
[   33.860561] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   33.862424] wlan0: authenticated
[   33.863118] wlan0: associate with <MAC addr plokij> (try 1/3)
[   33.867369] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   33.867412] wlan0: associated
[   37.823352] wlan0: authenticate with <MAC addr plokij>
[   37.843460] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   38.022953] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   38.113663] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   38.202934] wlan0: authentication with <MAC addr plokij> timed out
[   39.572977] wlan0: authenticate with <MAC addr plokij>
[   39.595834] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   39.700509] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   39.703542] wlan0: authenticated
[   39.704504] wlan0: associate with <MAC addr plokij> (try 1/3)
[   39.874428] wlan0: associate with <MAC addr plokij> (try 2/3)
[   40.021022] wlan0: associate with <MAC addr plokij> (try 3/3)
[   40.059585] wlan0: association with <MAC addr plokij> timed out
[   41.919404] wlan0: authenticate with <MAC addr plokij>
[   41.939580] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   41.942023] wlan0: authenticated
[   41.942531] wlan0: associate with <MAC addr plokij> (try 1/3)
[   41.975363] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   41.975417] wlan0: associated
[   77.852170] wlan0: authenticate with <MAC addr plokij>
[   77.872142] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   77.935135] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   78.003084] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   78.063037] wlan0: authentication with <MAC addr plokij> timed out
[   85.283079] wlan0: authenticate with <MAC addr plokij>
[   85.302937] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   85.482574] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   85.549989] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   85.654655] wlan0: authentication with <MAC addr plokij> timed out
[   87.517008] wlan0: authenticate with <MAC addr plokij>
[   87.537436] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   87.631069] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   87.635033] wlan0: authenticated
[   87.636498] wlan0: associate with <MAC addr plokij> (try 1/3)
[   87.714193] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   87.714238] wlan0: associated
[   90.843897] wlan0: authenticate with <MAC addr plokij>
[   90.863946] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   90.995625] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   91.037787] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   91.044489] wlan0: authenticated
[   91.047639] wlan0: associate with <MAC addr plokij> (try 1/3)
[   91.200575] wlan0: associate with <MAC addr plokij> (try 2/3)
[   91.319879] wlan0: associate with <MAC addr plokij> (try 3/3)
[   91.430729] wlan0: association with <MAC addr plokij> timed out
[   92.786009] wlan0: authenticate with <MAC addr plokij>
[   92.805874] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   92.876295] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   92.940269] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   92.998168] wlan0: authentication with <MAC addr plokij> timed out
[   94.855771] wlan0: authenticate with <MAC addr plokij>
[   94.878637] wlan0: send auth to <MAC addr plokij> (try 1/3)
[   94.931022] wlan0: send auth to <MAC addr plokij> (try 2/3)
[   95.009728] wlan0: send auth to <MAC addr plokij> (try 3/3)
[   95.012135] wlan0: authenticated
[   95.015258] wlan0: associate with <MAC addr plokij> (try 1/3)
[   95.064923] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[   95.064966] wlan0: associated
[  102.972202] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  888.807355] wlan0: authenticate with <MAC addr plokij>
[  888.826895] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  888.908943] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  888.979317] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  889.052079] wlan0: authentication with <MAC addr plokij> timed out
[  905.774418] wlan0: authenticate with <MAC addr plokij>
[  905.794165] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  905.857704] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  905.948294] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  906.003587] wlan0: authentication with <MAC addr plokij> timed out
[  943.462041] wlan0: authenticate with <MAC addr plokij>
[  943.481716] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  943.596848] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  943.738046] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  943.742289] wlan0: authenticated
[  943.745219] wlan0: associate with <MAC addr plokij> (try 1/3)
[  943.834505] wlan0: associate with <MAC addr plokij> (try 2/3)
[  943.846652] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[  943.846723] wlan0: associated
[  943.846783] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  946.231179] wlan0: authenticate with <MAC addr plokij>
[  946.251081] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  946.345741] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  946.431327] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  946.511550] wlan0: authentication with <MAC addr plokij> timed out
[  947.871870] wlan0: authenticate with <MAC addr plokij>
[  947.891563] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  947.975850] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  948.061424] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  948.165143] wlan0: authentication with <MAC addr plokij> timed out
[  950.025023] wlan0: authenticate with <MAC addr plokij>
[  950.044721] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  950.118339] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  950.175533] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  950.180774] wlan0: authenticated
[  950.183880] wlan0: associate with <MAC addr plokij> (try 1/3)
[  950.285014] wlan0: associate with <MAC addr plokij> (try 2/3)
[  950.410481] wlan0: associate with <MAC addr plokij> (try 3/3)
[  950.531231] wlan0: association with <MAC addr plokij> timed out
[  962.241761] wlan0: authenticate with <MAC addr plokij>
[  962.264776] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  962.341897] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  962.411221] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  962.450703] wlan0: authentication with <MAC addr plokij> timed out
[  985.027544] wlan0: authenticate with <MAC addr plokij>
[  985.047274] wlan0: send auth to <MAC addr plokij> (try 1/3)
[  985.127233] wlan0: send auth to <MAC addr plokij> (try 2/3)
[  985.184436] wlan0: send auth to <MAC addr plokij> (try 3/3)
[  985.236200] wlan0: authentication with <MAC addr plokij> timed out
[  989.668751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1290.474706] wlan0: authenticate with <MAC addr plokij>
[ 1290.494648] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1290.556163] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1290.626378] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1290.705620] wlan0: authentication with <MAC addr plokij> timed out
[ 1301.571783] wlan0: authenticate with <MAC addr plokij>
[ 1301.591471] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1301.681745] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1301.784108] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1301.884733] wlan0: authentication with <MAC addr plokij> timed out
[ 1324.333440] wlan0: authenticate with <MAC addr plokij>
[ 1324.352886] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1324.456306] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1324.551101] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1324.626873] wlan0: authentication with <MAC addr plokij> timed out
[ 1335.497943] wlan0: authenticate with <MAC addr plokij>
[ 1335.517597] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1335.571268] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1335.639674] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1335.706739] wlan0: authentication with <MAC addr plokij> timed out
[ 1346.498078] wlan0: authenticate with <MAC addr plokij>
[ 1346.518080] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1346.643537] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1346.782057] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1346.896343] wlan0: authentication with <MAC addr plokij> timed out
[ 1363.609518] wlan0: authenticate with <MAC addr plokij>
[ 1363.629315] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1363.713603] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1363.785927] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1363.834949] wlan0: authentication with <MAC addr plokij> timed out
[ 1374.508432] wlan0: authenticate with <MAC addr plokij>
[ 1374.528400] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1374.530264] wlan0: authenticated
[ 1374.531782] wlan0: associate with <MAC addr plokij> (try 1/3)
[ 1374.720915] wlan0: associate with <MAC addr plokij> (try 2/3)
[ 1374.834854] wlan0: associate with <MAC addr plokij> (try 3/3)
[ 1374.935586] wlan0: association with <MAC addr plokij> timed out
[ 1385.797625] wlan0: authenticate with <MAC addr plokij>
[ 1385.817281] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1385.886792] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1385.942634] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1386.010043] wlan0: authentication with <MAC addr plokij> timed out
[ 1398.689868] wlan0: authenticate with <MAC addr plokij>
[ 1398.704487] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1398.779165] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1398.830611] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1398.918161] wlan0: authentication with <MAC addr plokij> timed out
[ 1409.779662] wlan0: authenticate with <MAC addr plokij>
[ 1409.799332] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1409.804541] wlan0: authenticated
[ 1409.806686] wlan0: associate with <MAC addr plokij> (try 1/3)
[ 1409.986003] wlan0: associate with <MAC addr plokij> (try 2/3)
[ 1410.108216] wlan0: associate with <MAC addr plokij> (try 3/3)
[ 1410.142691] wlan0: association with <MAC addr plokij> timed out
[ 1423.687907] wlan0: authenticate with <MAC addr plokij>
[ 1423.702599] wlan0: send auth to <MAC addr plokij> (try 1/3)
[ 1423.776434] wlan0: send auth to <MAC addr plokij> (try 2/3)
[ 1423.834477] wlan0: send auth to <MAC addr plokij> (try 3/3)
[ 1423.840032] wlan0: authenticated
[ 1423.840489] wlan0: associate with <MAC addr plokij> (try 1/3)
[ 1423.937142] wlan0: associate with <MAC addr plokij> (try 2/3)
[ 1423.972431] wlan0: associate with <MAC addr plokij> (try 3/3)
[ 1423.990582] wlan0: RX AssocResp from <MAC addr plokij> (capab=0x411 status=0 aid=1)
[ 1423.990648] wlan0: associated
[ 1423.990696] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

thanks again

Al.

i'm not sure how many times, i tried the backport first but got errors, so followed some other instructions that people had success with, then managed to get the backport to succeed. i did a lot of stuff to be honest so mifgt have messed it up?

---

### Post by Al-G on 2014-08-11
heya :) I applied the commands you suggested, sorry still doesn't work, whats you thoughts, i'm happy to wipe and reinstall if i have clear instructions of the procedure to install the backport, i was unsure of which one to use? plus all the other commands i ran to try and get it working may have messed things up?

i dunno lol

thanks again

---

### Post by wildmanne39 on 2014-08-11
Did you try to connect using the parameter from my last post and was your network unhidden at the time?

Yes if you installed the backport modules then installed from a different source it could be causing issues if you did not remove the other driver before trying a new one.
I do not have long and I have to leave and I will not be on much until at least the weekend, so if we do not get it solved hopefully someone else will jump in.

---

### Post by Al-G on 2014-08-11
yes i set the ssid to broadcast then ran the wireless script and posted it, then ran the commands suggested, i really appreciate it, I'm thinking a wipe might be the way to go? , but don't want to repeat my mistakes? so off a clean install with all ubuntu updates applied, should i go straight for the backport? and which one?

i appreciate your time, thanks for your help so far

Cheers,

Al.

---

### Post by wildmanne39 on 2014-08-11
Please:

Change the wpa/wpa2 encryption to just wpa2 (CCMP)(AES) not (TKIP) if you have that option it will work best.

Set your wireless channel in the router to 1 or 11 then save the router configuration and reboot it.

Go into network manager at top right corner of the screen and click on edit connections>wireless tab and set IPV6 to ignore.

Why do you think you need to install a driver when it comes with ubuntu?

---

### Post by wildmanne39 on 2014-08-11
If you do a reinstall and it does not connect post a new file so we can see what is going on before any changes are made.

---

### Post by Al-G on 2014-08-11
Heya when the wireless didn't work i read the forums and just tried to follow the instructions as best i could, as i said i really am clueless so i can understand how frustrating that is to you guys in the know, i'll try changin the router this very moment :)

Thanks.

---

### Post by Al-G on 2014-08-11
heya thanks again,
chenged the router settings as advised, did get a connection for around 2 mins then disconnected. i'm gonna start again, but would really like some pointers as to what to do. the wireless worked fine, i used it to download and install the ubuntu updates, then after restart it didn;t work. Should i not install the updates??? should i install the updates then use a backport, you've advised the driver is included in 14.04 so why the backport, i dunno i dunno lol i'm lost. plus the extras package stalled for some reason, grrrrrrrr, lts of hours researching and trying but think reinstall is the way to go. but then what do i do lol :)

As always I appreciate you's guys giving your time to help others. 

If knowledge is the new currency then help and advice is the new charity, did I hear that someplace else or did i just make that up lol :)

Cheers,

Al.

---

### Post by Al-G on 2014-08-11
fresh install nothing hdone apart from get update and get dist-upgrade as advised. output below ;

```

#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for ".txt" files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

SCRIPTDATE="2014-08-04 20:47 +0200"
FILEBASE="wireless-info"
OUTPUTDIR=$(pwd)
OUTPUTDIRFB="/tmp"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|ndis)[^[:punct:] ]*"
LSMODMATCHES="wmi"
DMESGMATCHES="(wlan0|eth1|firmware|[nN]etwork)[^[:punct:] ]*"
BLACKLISTEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"

export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"

if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
fi

exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt"
if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\", trying in \"%s\" instead.\n" "$OUTPUTDIR" "$OUTPUTDIRFB" >&2
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt"
    if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\" either, aborting.\n\n" "$OUTPUTDIR" >&2
    exit 1
    fi
fi
exec 2>&1

printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Script from: %s\n" "$SCRIPTDATE"

printf "\n##### release #####\n\n"
lsb_release -idrc

printf "\n##### kernel #####\n\n"
uname -srvmpio
echo
cat /proc/cmdline | sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/'

printf "\n##### desktop #####\n\n"
DESKTOP="$DESKTOP_SESSION"
if [ -z "$DESKTOP" ]; then
    DESKTOP=$(sed -n 's/^Session=\(.*\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
    DESKTOP=$(sed -n 's/^Name=\(.*\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    echo "Could not be determined."
fi

printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

printf "\n##### lsusb #####\n\n"
lsusb

printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info

printf "\n##### rfkill #####\n\n"
rfkill list all

printf "\n##### lsmod #####\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)([[:punct:] ]|$)")
echo "$LSMOD"

printf "\n##### interfaces #####\n\n"
sed '/^#/d;s/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### ifconfig #####\n\n"
ifconfig | sed '/^lo[ ]/,/^$/d'

printf "\n##### iwconfig #####\n\n"
iwconfig

printf "\n##### route #####\n\n"
route -n

printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### nm-tool #####\n\n"
nm-tool

printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### iw reg get #####\n\n"
iw reg get

printf "\n##### iwlist channels #####\n\n"
iwlist chan

printf "\n##### iwlist scan #####\n\n"
if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO iwlist scan || echo "Acquisition of admin privileges failed.")
    trap 2 3
    if [[ $IWLISTSCAN =~ ^[[:space:]]*Frequency: ]]; then
    echo "Channel occupancy:"
    grep '^[[:space:]]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]*\([0-9]\+\)[[:space:]]*/     \1   WLAPs on   /'
    echo
    fi
    grep -v '^[[:space:]]*IE:[ ]*Unknown:' <<< "$IWLISTSCAN"
else
    echo "No way to acquire admin privileges found."
fi

printf "\n##### module infos #####\n\n"
MODULES=$(egrep "^$MODMATCHES" <<< "$LSMOD" | awk '{print $1}')
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE)
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done

printf "\n##### module parameters #####\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
    MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
    printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done

printf "\n##### /etc/modules #####\n\n"
grep -v '^#' /etc/modules

printf "\n##### blacklists #####\n\n"
for CONFFILE in $(ls /etc/modprobe.d/*.conf | egrep -v "$BLACKLISTEXCL"); do
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
    printf "[%s]\n%s\n\n" "$CONFFILE" "$BLACKLIST"
    fi
done

printf "\n##### udev rules #####\n\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules

printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[[:punct:] ]"

printf "\n########## wireless info END ############\n\n"

exec 2>&4 4>&-
exec 1>&3 3>&-

##### MAC address masking #####

RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")

LOCDEVSRAW=$(sed -n '/^[- ]*Device:/,/^[ ]*HW Address:/p' <<< "$RESULTS")
NETDEVNAMES=($(sed -n 's/^[- ]*Device:[ ]*\([^ ]*\).*/\1/p' <<< "$LOCDEVSRAW"))
NETDEVMACS=($(sed -n 's/^[ ]*HW Address:[ ]*\([^ ]*\).*/\1/p' <<< "$LOCDEVSRAW"))

WLAPSRAW=$(sed -n '/^[ ]*Wireless Access Points/,/^$/p' <<< "$RESULTS")
NETDEVNAMES+=($(sed -n 's/^[ ]*\*\?\([^ ]*\):.*/\1/p' <<< "$WLAPSRAW"))
NETDEVMACS+=($(grep -o '\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]' <<< "$WLAPSRAW"))

for NETDEVNR in "${!NETDEVMACS[@]}"; do
    MACMASKSED+="s/${NETDEVMACS[$NETDEVNR]}/<MAC addr${NETDEVNAMES[$NETDEVNR]+ }${NETDEVNAMES[$NETDEVNR]-ess}>/I;"
done

sed "$MACMASKSED/\([[:alnum:]][[:alnum:]]:\)\{6,\}/! s/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"

##### The End #####

if [[ $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") -gt 19968 ]]; then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" --remove-files -C "$OUTPUTDIR" "$FILEBASE.txt"
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for \".txt\" files on the Ubuntu Forums.\n\n" "$OUTPUTDIR/$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$OUTPUTDIR/$FILEBASE"
fi

```

thats different!!!!!

---

### Post by wildmanne39 on 2014-08-11
You posted the script and not the file.:p

When you connected a few minutes ago before the new install was that with the driver parameter? or had you already rebooted the computer? 
I am leaving in about twenty minutes.

---

### Post by Al-G on 2014-08-11
```

#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for ".txt" files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

SCRIPTDATE="2014-08-04 20:47 +0200"
FILEBASE="wireless-info"
OUTPUTDIR=$(pwd)
OUTPUTDIRFB="/tmp"
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|ndis)[^[:punct:] ]*"
LSMODMATCHES="wmi"
DMESGMATCHES="(wlan0|eth1|firmware|[nN]etwork)[^[:punct:] ]*"
BLACKLISTEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"

export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"

if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
fi

exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt"
if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\", trying in \"%s\" instead.\n" "$OUTPUTDIR" "$OUTPUTDIRFB" >&2
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt"
    if [ "$?" != "0" ]; then
    printf "\nCannot write output file in \"%s\" either, aborting.\n\n" "$OUTPUTDIR" >&2
    exit 1
    fi
fi
exec 2>&1

printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Script from: %s\n" "$SCRIPTDATE"

printf "\n##### release #####\n\n"
lsb_release -idrc

printf "\n##### kernel #####\n\n"
uname -srvmpio
echo
cat /proc/cmdline | sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/'

printf "\n##### desktop #####\n\n"
DESKTOP="$DESKTOP_SESSION"
if [ -z "$DESKTOP" ]; then
    DESKTOP=$(sed -n 's/^Session=\(.*\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
    DESKTOP=$(sed -n 's/^Name=\(.*\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    echo "Could not be determined."
fi

printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 '^[^[:space:]].*net' | sed '/^--$/d; /^[^[:space:]]/ i\\'

printf "\n##### lsusb #####\n\n"
lsusb

printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info

printf "\n##### rfkill #####\n\n"
rfkill list all

printf "\n##### lsmod #####\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)([[:punct:] ]|$)")
echo "$LSMOD"

printf "\n##### interfaces #####\n\n"
sed '/^#/d;s/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### ifconfig #####\n\n"
ifconfig | sed '/^lo[ ]/,/^$/d'

printf "\n##### iwconfig #####\n\n"
iwconfig

printf "\n##### route #####\n\n"
route -n

printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### nm-tool #####\n\n"
nm-tool

printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### iw reg get #####\n\n"
iw reg get

printf "\n##### iwlist channels #####\n\n"
iwlist chan

printf "\n##### iwlist scan #####\n\n"
if [ -n "$SUDO" ]; then
    trap "" 2 3
    IWLISTSCAN=$($SUDO iwlist scan || echo "Acquisition of admin privileges failed.")
    trap 2 3
    if [[ $IWLISTSCAN =~ ^[[:space:]]*Frequency: ]]; then
    echo "Channel occupancy:"
    grep '^[[:space:]]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]*\([0-9]\+\)[[:space:]]*/     \1   WLAPs on   /'
    echo
    fi
    grep -v '^[[:space:]]*IE:[ ]*Unknown:' <<< "$IWLISTSCAN"
else
    echo "No way to acquire admin privileges found."
fi

printf "\n##### module infos #####\n\n"
MODULES=$(egrep "^$MODMATCHES" <<< "$LSMOD" | awk '{print $1}')
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE)
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done

printf "\n##### module parameters #####\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
    MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
    printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done

printf "\n##### /etc/modules #####\n\n"
grep -v '^#' /etc/modules

printf "\n##### blacklists #####\n\n"
for CONFFILE in $(ls /etc/modprobe.d/*.conf | egrep -v "$BLACKLISTEXCL"); do
    BLACKLIST=$(grep '^blacklist' $CONFFILE)
    if [ -n "$BLACKLIST" ]; then
    printf "[%s]\n%s\n\n" "$CONFFILE" "$BLACKLIST"
    fi
done

printf "\n##### udev rules #####\n\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules

printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[[:punct:] ]"

printf "\n########## wireless info END ############\n\n"

exec 2>&4 4>&-
exec 1>&3 3>&-

##### MAC address masking #####

RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")

LOCDEVSRAW=$(sed -n '/^[- ]*Device:/,/^[ ]*HW Address:/p' <<< "$RESULTS")
NETDEVNAMES=($(sed -n 's/^[- ]*Device:[ ]*\([^ ]*\).*/\1/p' <<< "$LOCDEVSRAW"))
NETDEVMACS=($(sed -n 's/^[ ]*HW Address:[ ]*\([^ ]*\).*/\1/p' <<< "$LOCDEVSRAW"))

WLAPSRAW=$(sed -n '/^[ ]*Wireless Access Points/,/^$/p' <<< "$RESULTS")
NETDEVNAMES+=($(sed -n 's/^[ ]*\*\?\([^ ]*\):.*/\1/p' <<< "$WLAPSRAW"))
NETDEVMACS+=($(grep -o '\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]' <<< "$WLAPSRAW"))

for NETDEVNR in "${!NETDEVMACS[@]}"; do
    MACMASKSED+="s/${NETDEVMACS[$NETDEVNR]}/<MAC addr${NETDEVNAMES[$NETDEVNR]+ }${NETDEVNAMES[$NETDEVNR]-ess}>/I;"
done

sed "$MACMASKSED/\([[:alnum:]][[:alnum:]]:\)\{6,\}/! s/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"

##### The End #####

if [[ $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") -gt 19968 ]]; then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" --remove-files -C "$OUTPUTDIR" "$FILEBASE.txt"
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for \".txt\" files on the Ubuntu Forums.\n\n" "$OUTPUTDIR/$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$OUTPUTDIR/$FILEBASE"
fi

```

sorry it's really late for me lol

---

### Post by wildmanne39 on 2014-08-11
Why don't you call it a night I am sure someone else will help you tomorrow and I will check in when I can but I am going where there is no wifi.

---

### Post by Al-G on 2014-08-11
ssorrry it late here lol

```

########## wireless info START ##########

Report from: 12 Aug 2014 02:39 BST +0100

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 08)
    Subsystem: Lenovo Device [17aa:3805]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lenovo Device [17aa:3026]
    Kernel driver in use: ath9k

##### lsusb #####

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 002 Device 003: ID 04f2:b421 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 0eef:a107 D-WAV Scientific Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              626489  1 ath9k
ath3k                  13318  0 
bluetooth             395423  12 bnep,ath3k,btusb,rfcomm
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::c654:44ff:fe11:a5d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:226270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117866 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:339311638 (339.3 MB)  TX bytes:8280652 (8.2 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:628 errors:0 dropped:0 overruns:0 frame:0
          TX packets:546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:512668 (512.6 KB)  TX bytes:71942 (71.9 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia4024094: Infra, <MAC addr virginmedia4024094>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    VM381976-2G:     Infra, <MAC addr VM381976-2G>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    BTWifi-X:        Infra, <MAC addr BTWifi-X>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2 Enterprise
    BTHub3-33QT:     Infra, <MAC addr BTHub3-33QT>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    BTWifi-with-FON: Infra, <MAC addr BTWifi-with-FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.55
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

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

##### iwlist scan #####

Sorry, try again.
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr virginmedia4024094>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4024094"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003316d56164d
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr BTWifi-with-FON>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000433a419b02
                    Extra: Last beacon: 12ms ago
          Cell 03 - Address: <MAC address>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"plokij"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001604f6745
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr VM381976-2G>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VM381976-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000346e072b04
                    Extra: Last beacon: 756ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr BTHub3-33QT>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-33QT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000433a40c2c5
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr BTWifi-X>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000433a41a45a
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos #####

[ath9k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BAF225EEB618908380B28DA
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512

[ath3k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
alias:          usb:v0489pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE02Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3121d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04C5p1330d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE056d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE04Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3393d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0219d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3362d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3005d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04CAp3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3375d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p817Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3004d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p0036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p311Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0489pE03Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0215d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3pE019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p3000d*dc*dsc*dp*ic*isc*ip*in*
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        69:B0:D0:A7:9B:85:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512

##### module parameters #####

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   10.155791] ath: phy0: WB335 1-ANT card detected
[   10.155795] ath: phy0: Set BT/WLAN RX diversity capability
[   10.162489] ath: phy0: Enable LNA combining
[   10.163622] ath: EEPROM regdomain: 0x65
[   10.163625] ath: EEPROM indicates we should expect a direct regpair map
[   10.163629] ath: Country alpha2 being used: 00
[   10.163631] ath: Regpair used: 0x65
[   11.371238] type=1400 audit(1407804561.776:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
[   11.371440] type=1400 audit(1407804561.776:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=441 comm="apparmor_parser"
[   11.371715] type=1400 audit(1407804561.776:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=440 comm="apparmor_parser"
[   11.372167] type=1400 audit(1407804561.776:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=441 comm="apparmor_parser"
[   12.993960] Bluetooth: Error in firmware loading err = -110,len = 448, size = 4096
[   12.994038] ath3k: probe of 2-6:1.0 failed with error -110
[   22.217922] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.221311] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.346710] type=1400 audit(1407804573.748:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=892 comm="apparmor_parser"
[   23.347440] type=1400 audit(1407804573.748:20): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=892 comm="apparmor_parser"
[   23.388406] wlan0: authenticate with <MAC address>
[   23.403014] wlan0: send auth to <MAC address> (try 1/3)
[   23.404876] wlan0: authenticated
[   23.406270] wlan0: associate with <MAC address> (try 1/3)
[   23.410552] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[   23.410591] wlan0: associated
[   23.410617] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  156.933206] wlan0: authenticate with <MAC address>
[  156.952636] wlan0: send auth to <MAC address> (try 1/3)
[  156.992864] wlan0: send auth to <MAC address> (try 2/3)
[  157.106927] wlan0: send auth to <MAC address> (try 3/3)
[  157.247200] wlan0: authentication with <MAC address> timed out
[  158.606701] wlan0: authenticate with <MAC address>
[  158.626240] wlan0: send auth to <MAC address> (try 1/3)
[  158.790218] wlan0: send auth to <MAC address> (try 2/3)
[  158.864136] wlan0: send auth to <MAC address> (try 3/3)
[  158.926493] wlan0: authentication with <MAC address> timed out
[  160.785292] wlan0: authenticate with <MAC address>
[  160.804198] wlan0: send auth to <MAC address> (try 1/3)
[  160.806708] wlan0: authenticated
[  160.807287] wlan0: associate with <MAC address> (try 1/3)
[  161.126506] wlan0: associate with <MAC address> (try 2/3)
[  161.280374] wlan0: associate with <MAC address> (try 3/3)
[  161.329126] wlan0: association with <MAC address> timed out
[  171.422138] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  174.184604] wlan0: authenticate with <MAC address>
[  174.199255] wlan0: send auth to <MAC address> (try 1/3)
[  174.325081] wlan0: send auth to <MAC address> (try 2/3)
[  174.468457] wlan0: send auth to <MAC address> (try 3/3)
[  174.587961] wlan0: authentication with <MAC address> timed out
[  185.454994] wlan0: authenticate with <MAC address>
[  185.474772] wlan0: send auth to <MAC address> (try 1/3)
[  185.621683] wlan0: send auth to <MAC address> (try 2/3)
[  185.745328] wlan0: send auth to <MAC address> (try 3/3)
[  185.879563] wlan0: authentication with <MAC address> timed out
[  202.210646] wlan0: authenticate with <MAC address>
[  202.225287] wlan0: send auth to <MAC address> (try 1/3)
[  202.323623] wlan0: send auth to <MAC address> (try 2/3)
[  202.443255] wlan0: send auth to <MAC address> (try 3/3)
[  202.580603] wlan0: authentication with <MAC address> timed out
[  213.456721] wlan0: authenticate with <MAC address>
[  213.476582] wlan0: send auth to <MAC address> (try 1/3)
[  213.616443] wlan0: send auth to <MAC address> (try 2/3)
[  213.755332] wlan0: send auth to <MAC address> (try 3/3)
[  213.853749] wlan0: authentication with <MAC address> timed out
[  230.231112] wlan0: authenticate with <MAC address>
[  230.245760] wlan0: send auth to <MAC address> (try 1/3)
[  230.250963] wlan0: authenticated
[  230.255348] wlan0: associate with <MAC address> (try 1/3)
[  230.557956] wlan0: associate with <MAC address> (try 2/3)
[  230.757972] wlan0: associate with <MAC address> (try 3/3)
[  230.807410] wlan0: association with <MAC address> timed out
[  241.682703] wlan0: authenticate with <MAC address>
[  241.702306] wlan0: send auth to <MAC address> (try 1/3)
[  241.840809] wlan0: send auth to <MAC address> (try 2/3)
[  241.944211] wlan0: send auth to <MAC address> (try 3/3)
[  242.083743] wlan0: authentication with <MAC address> timed out
[  255.258415] wlan0: authenticate with <MAC address>
[  255.273039] wlan0: send auth to <MAC address> (try 1/3)
[  255.347231] wlan0: send auth to <MAC address> (try 2/3)
[  255.460775] wlan0: send auth to <MAC address> (try 3/3)
[  255.574948] wlan0: authentication with <MAC address> timed out
[  266.446201] wlan0: authenticate with <MAC address>
[  266.465188] wlan0: send auth to <MAC address> (try 1/3)
[  266.535242] wlan0: send auth to <MAC address> (try 2/3)
[  266.666068] wlan0: send auth to <MAC address> (try 3/3)
[  266.810759] wlan0: authentication with <MAC address> timed out
[  526.135600] wlan0: authenticate with <MAC address>
[  526.155509] wlan0: send auth to <MAC address> (try 1/3)
[  526.270332] wlan0: send auth to <MAC address> (try 2/3)
[  526.397320] wlan0: send auth to <MAC address> (try 3/3)
[  526.453621] wlan0: authentication with <MAC address> timed out
[  537.325514] wlan0: authenticate with <MAC address>
[  537.345508] wlan0: send auth to <MAC address> (try 1/3)
[  537.467719] wlan0: send auth to <MAC address> (try 2/3)
[  537.621068] wlan0: send auth to <MAC address> (try 3/3)
[  537.744490] wlan0: authentication with <MAC address> timed out
[ 1897.375363] wlan0: authenticate with <MAC address>
[ 1897.395270] wlan0: send auth to <MAC address> (try 1/3)
[ 1897.397122] wlan0: authenticated
[ 1897.398319] wlan0: associate with <MAC address> (try 1/3)
[ 1897.404632] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[ 1897.404677] wlan0: associated
[ 1897.404687] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1964.861360] wlan0: authenticate with <MAC address>
[ 1964.881088] wlan0: send auth to <MAC address> (try 1/3)
[ 1964.997547] wlan0: send auth to <MAC address> (try 2/3)
[ 1965.105600] wlan0: send auth to <MAC address> (try 3/3)
[ 1965.228706] wlan0: authentication with <MAC address> timed out
[ 1966.586318] wlan0: authenticate with <MAC address>
[ 1966.605912] wlan0: send auth to <MAC address> (try 1/3)
[ 1966.709003] wlan0: send auth to <MAC address> (try 2/3)
[ 1966.819979] wlan0: send auth to <MAC address> (try 3/3)
[ 1966.977431] wlan0: authentication with <MAC address> timed out
[ 1968.846889] wlan0: authenticate with <MAC address>
[ 1968.866768] wlan0: send auth to <MAC address> (try 1/3)
[ 1969.008815] wlan0: send auth to <MAC address> (try 2/3)
[ 1969.137122] wlan0: send auth to <MAC address> (try 3/3)
[ 1969.281202] wlan0: authentication with <MAC address> timed out
[ 1979.384867] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

```

---

### Post by Al-G on 2014-08-11
oh and p.s. i didn't apply any changes at all, yeh i'm off ot bed lol, enjoy your time away mad dog :) thanks for all your help :)

Cheers,

Al.

---

### Post by wildmanne39 on 2014-08-11
Change your channel to 1 or 11 then remove all connections from network manager and reboot your computer letting network manager find your network, make sure it is not hidden. You can also run the commands I posted in my other post after you reboot and see if that helps if it does not connect without the parameter.

---

### Post by varunendra on 2014-08-12
I'm not really the kind of person Wild Man wants on this thread, since my availability is more unpredictable these days than ever (posting sometimes, then disappearing for 2-3 days!), but couldn't help noticing this and pointing it out -

> **Al-G said:**
> ```
          Cell 03 - Address: <MAC address>
                    **Channel:3**
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"plokij"
                    *...<snip>...*
                    IE: **[COLOR="#FF0000"]WPA[/COLOR]** Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/[COLOR="#FF0000"]**WPA2**[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

```

So evidently, you are still using WPA/WPA2 mixed mode in the router, and the channel isn't changed to 1 or 11 as suggested either. The module parameter 'nohwcrypt' is also at default '0'. So it seems none of the suggested changes have been applied.

Oh yeah, you admitted that two posts ago. But what is the point of posting the report multiple times without changing anything? Please try what has been suggested - all three changes above (and more, regarding IPv6 or whatever), then post back a fresh report showing the changed state.

---

### Post by Al-G on 2014-08-13
Hi there thanks for all the advice, I removed the security completely and changed the channel and applied all other changes to no avail. After hours and hours of changes and research, and the much appreciated help of the forum, I tried a different router and it works fine, with WPA2. So looks like it was something to do with my router, which was a Zyxel for info. I wish I'd thought of that and changed the router earlier lol.

Thanks again for all your help

---

### Post by varunendra on 2014-08-13
Not the kind of solution we like to see, but any solution is good as long as you are satisfied. :)


Please mark the thread as [SOLVED] using "Thread Tools" link above the top post. Thanks!

---

