---
title: "Wifi connection fails - Ubuntu 14.04 with Intel 5100"
date: 2014-08-28
forum: Networking &amp; Wireless
---

### Post by simongsell on 2014-08-28
Hi Everybody,

I just installed Ubuntu 14.04 on my Dell E6410 bought secondhand from a profesional. The WiFi card is supposed to be OK as the laptob has been tested by the seller. Since the installation has been performed, I can see the wireless connections available but it does'nt connect. After hours of research I haven't tried so much things. The only manual modification that I have not canceled is the addition of the file "iwlwifi-5000-1.ucode" (which is supposed to be the driver for this card) in the "/lib/firmware/" repertory.
Here is the output of wireless_script :
```


########## wireless info START ##########

Report from: 28 Aug 2014 10:09 CEST +0200

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 dell_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5e26:aff:fe36:bcac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9679 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10822620 (10.8 MB)  TX bytes:1190175 (1.1 MB)
          Interrupt:20 Memory:f6900000-f6920000 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Livebox-464D:    Infra, <MAC addr Livebox-464D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    FreeWifi_secure: Infra, <MAC addr FreeWifi_secure>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA Enterprise
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    FreeWifi:        Infra, <MAC addr FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    Bbox-86B8E1:     Infra, <MAC addr Bbox-86B8E1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    dlcdlc:          Infra, <MAC addr dlcdlc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    Gsellou_box:     Infra, <MAC addr Gsellou_box>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA2 Enterprise
    PERIER:          Infra, <MAC addr PERIER>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Livebox-8dc6:    Infra, <MAC addr Livebox-8dc6>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27
    Livebox-16E4:    Infra, <MAC addr Livebox-16E4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC addr FreeWifi_secure>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    orange:          Infra, <MAC addr orange>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    Livebox-6b52:    Infra, <MAC addr Livebox-6b52>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SFR_A6E0:        Infra, <MAC addr SFR_A6E0>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA
    SFR_9648:        Infra, <MAC addr SFR_9648>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24
    FREEBOX_LOUISPHILIPPE_KJ: Infra, <MAC addr FREEBOX_LOUISPHILIPPE_KJ>, Freq 2442 MHz, Rate 54 Mb/s, Strength 24 WPA
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    az_fr_cn:        Infra, <MAC addr az_fr_cn>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC addr FreeWifi_secure>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC addr FreeWifi_secure>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA Enterprise
    NEUF_9ACC:       Infra, <MAC addr NEUF_9ACC>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    FreeWifi:        Infra, <MAC addr FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #####

Channel occupancy:

     5   WLAPs on   Frequency:2.412 GHz (Channel 1)
     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     9   WLAPs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr dlcdlc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"dlcdlc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e47ac7156
                    Extra: Last beacon: 2900ms ago
          Cell 02 - Address: <MAC addr FreeWifi_secure>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e47aafc0d
                    Extra: Last beacon: 2996ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e47ae0a15
                    Extra: Last beacon: 2796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr FreeWifi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e47ae134e
                    Extra: Last beacon: 2792ms ago
          Cell 05 - Address: <MAC addr az_fr_cn>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"az_fr_cn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000043bcf458e21
                    Extra: Last beacon: 3060ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC addr Bouygues Telecom Wi-Fi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aca2c368bd
                    Extra: Last beacon: 2920ms ago
          Cell 07 - Address: <MAC addr SFR_A6E0>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SFR_A6E0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000147a2f6a19d
                    Extra: Last beacon: 3144ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr SFR WiFi FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000147a2f6a94c
                    Extra: Last beacon: 3140ms ago
          Cell 09 - Address: <MAC addr SFR WiFi Mobile>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000147a2f6afa1
                    Extra: Last beacon: 3132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC addr SFR_9648>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"SFR_9648"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148a428dc52
                    Extra: Last beacon: 3128ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC addr SFR WiFi FON>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148a428e3e6
                    Extra: Last beacon: 3124ms ago
          Cell 12 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148a49f918b
                    Extra: Last beacon: 2980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NEUF_C36C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148a49f9702
                    Extra: Last beacon: 2980ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000148a49f9d08
                    Extra: Last beacon: 2980ms ago
          Cell 15 - Address: <MAC addr Bbox-86B8E1>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Bbox-86B8E1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000aca2c361e2
                    Extra: Last beacon: 2924ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos #####

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
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

##### module parameters #####

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    1.553001] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.811377] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.812115] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.812284] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[    2.892146] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    2.919205] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.919210] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.919212] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.919215] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    2.919366] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.974667] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    5.712466] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    5.716170] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[    5.813453] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    5.816476] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[    5.846642] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 1893.069832] wlan0: authenticate with <MAC addr Gsellou_box>
[ 1893.073332] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[ 1893.277462] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[ 1893.481479] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[ 1893.685479] wlan0: authentication with <MAC addr Gsellou_box> timed out
[ 1896.891537] wlan0: authenticate with <MAC addr Gsellou_box>
[ 1896.895664] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[ 1897.097849] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[ 1897.301868] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[ 1897.505887] wlan0: authentication with <MAC addr Gsellou_box> timed out

########## wireless info END ############

```

I would be very grateful if someone can help me figuring out what it's happening ...
Thanks by advance,

---

### Post by chili555 on 2014-08-28
> The only manual modification that I have not canceled is the addition of the file "iwlwifi-5000-1.ucode" (which is supposed to be the driver for this card) in the "/lib/firmware/" repertory.The driver in use doesn't need or look for iwlwifi-5000-1.ucode at all:```
[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
<snip>
```I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=1"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Finally, Network Manager will default to ethernet if it's available. Please make your tests with the ethernet detached.

---

### Post by simongsell on 2014-08-28
Thank you very much for your answer.
I changed what I could in the setting of the router and I set WPA2/AES as security mode.
I followed the other instructions in your message but the connection still fails ...

---

### Post by chili555 on 2014-08-28
May we see another *wireless_script*?

---

### Post by simongsell on 2014-08-28
Sure :

```


########## wireless info START ##########

Report from: 28 Aug 2014 23:35 CEST +0200

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
    Subsystem: Dell Latitude E6410 [1028:040a]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd HD Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
wmi                    19177  1 dell_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17085278 (17.0 MB)  TX bytes:2240935 (2.2 MB)
          Interrupt:20 Memory:f6900000-f6920000 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
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
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FreeWifi_secure: Infra, <MAC addr FreeWifi_secure>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA Enterprise
    SFR_A6E0:        Infra, <MAC addr SFR_A6E0>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA
    FreeWifi:        Infra, <MAC addr FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    dlcdlc:          Infra, <MAC addr dlcdlc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WEP
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    PERIER:          Infra, <MAC addr PERIER>, Freq 2427 MHz, Rate 54 Mb/s, Strength 25 WPA2
    FREEBOX_LOUISPHILIPPE_KJ: Infra, <MAC addr FREEBOX_LOUISPHILIPPE_KJ>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA
    Gsellou_box:     Infra, <MAC addr Gsellou_box>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Livebox-464D:    Infra, <MAC addr Livebox-464D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    JMCB:            Infra, <MAC addr JMCB>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2 Enterprise
    FreeWifi:        Infra, <MAC addr FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15
    Bbox-DA3EB34B-5GHz: Infra, <MAC addr Bbox-DA3EB34B-5GHz>, Freq 5180 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Bouygues Telecom Wi-Fi: Infra, <MAC addr Bouygues Telecom Wi-Fi>, Freq 2467 MHz, Rate 54 Mb/s, Strength 30
    NEUF_C36C:       Infra, <MAC addr NEUF_C36C>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    Bbox-C3D418:     Infra, <MAC addr Bbox-C3D418>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    NEUF_9ACC:       Infra, <MAC addr NEUF_9ACC>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    SFR WiFi FON:    Infra, <MAC addr SFR WiFi FON>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    SFR_4E18:        Infra, <MAC addr SFR_4E18>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA
    SFR WiFi Mobile: Infra, <MAC addr SFR WiFi Mobile>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2 Enterprise
    SFR WiFi Public: Infra, <MAC addr SFR WiFi Public>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    Bbox-DA3EB34B:   Infra, <MAC addr Bbox-DA3EB34B>, Freq 2467 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NEUF_A584:       Infra, <MAC addr NEUF_A584>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA
    Livebox-7874:    Infra, <MAC addr Livebox-7874>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    charlyjackass:   Infra, <MAC addr charlyjackass>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA
    FreeWifi:        Infra, <MAC addr FreeWifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

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

country FR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
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
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #####

Channel occupancy:

     3   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     8   WLAPs on   Frequency:2.462 GHz (Channel 11)
     1   WLAPs on   Frequency:2.467 GHz (Channel 12)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Bouygues Telecom Wi-Fi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7e720487b
                    Extra: Last beacon: 2492ms ago
          Cell 02 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Bbox-86B8E1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b7e72041a0
                    Extra: Last beacon: 2496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr FreeWifi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001698c064343
                    Extra: Last beacon: 2364ms ago
          Cell 04 - Address: <MAC addr NEUF_A584>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NEUF_A584"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001547ba75354
                    Extra: Last beacon: 2492ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001698b6d1b4d
                    Extra: Last beacon: 12400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC addr FreeWifi_secure>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001698c07dc2a
                    Extra: Last beacon: 2260ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC addr Bbox-DA3EB34B>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Bbox-DA3EB34B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006b6430165
                    Extra: Last beacon: 12508ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC addr FREEBOX_LOUISPHILIPPE_KJ>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"FREEBOX_LOUISPHILIPPE_KJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004563930160
                    Extra: Last beacon: 2548ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC addr charlyjackass>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"charlyjackass"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000033af702524e
                    Extra: Last beacon: 12624ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC addr dlcdlc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"dlcdlc"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001698b69f207
                    Extra: Last beacon: 12608ms ago
          Cell 11 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Livebox-16E4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e6b7e0180
                    Extra: Last beacon: 2584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"az_fr_wpa2auth_test"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000044713a767c5
                    Extra: Last beacon: 2564ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC address>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004ff3c8160
                    Extra: Last beacon: 2564ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos #####

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
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

##### module parameters #####

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    1.545036] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.780128] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.071593] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.071784] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[    3.103293] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    3.130313] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.130318] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.130320] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.130323] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    3.130426] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    3.165389] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.065981] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    6.071523] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[    6.170269] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    6.174013] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[    6.204798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   24.936623] wlan0: authenticate with <MAC addr Gsellou_box>
[   24.940088] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[   25.144010] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[   25.348099] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[   25.552238] wlan0: authentication with <MAC addr Gsellou_box> timed out
[   28.831706] wlan0: authenticate with <MAC addr Gsellou_box>
[   28.832714] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[   29.034339] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[   29.238485] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[   29.442572] wlan0: authentication with <MAC addr Gsellou_box> timed out
[   33.026828] wlan0: authenticate with <MAC addr Gsellou_box>
[   33.027844] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[   33.228811] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[   33.432941] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[   33.637076] wlan0: authentication with <MAC addr Gsellou_box> timed out
[   37.737402] wlan0: authenticate with <MAC addr Gsellou_box>
[   37.738719] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[   37.939660] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[   38.143741] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[   38.347862] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  520.497186] wlan0: authenticate with <MAC addr Gsellou_box>
[  520.498283] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  520.698474] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  520.902508] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  521.106551] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  534.222698] wlan0: authenticate with <MAC addr Gsellou_box>
[  534.223851] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  534.427844] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  534.631863] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  534.835837] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  551.017390] wlan0: authenticate with <MAC addr Gsellou_box>
[  551.019085] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  551.221456] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  551.425540] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  551.629497] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  564.740033] wlan0: authenticate with <MAC addr Gsellou_box>
[  564.741592] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  564.942788] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  565.146789] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  565.350801] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  617.583624] wlan0: authenticate with <MAC addr Gsellou_box>
[  617.584976] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  617.787916] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  617.991929] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  618.195955] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  631.409007] wlan0: authenticate with <MAC addr Gsellou_box>
[  631.414144] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  631.617263] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  631.821277] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  632.025296] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  668.479263] wlan0: authenticate with <MAC addr Gsellou_box>
[  668.486121] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  668.688808] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  668.892794] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  669.096866] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  682.204817] wlan0: authenticate with <MAC addr Gsellou_box>
[  682.206013] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  682.410171] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  682.614201] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  682.818214] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  706.789664] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[  706.789804] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[  706.790598] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[  706.815120] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  706.815125] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  706.815127] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  706.815129] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[  706.815227] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  706.840657] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  706.849702] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  706.852751] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  706.951949] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  706.955017] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  706.986664] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  728.467349] wlan0: authenticate with <MAC addr Gsellou_box>
[  728.471787] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  728.674657] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  728.878659] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  729.082652] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  733.477444] wlan0: deauthenticating from <MAC addr Gsellou_box> by local choice (reason=3)
[  743.588818] wlan0: authenticate with <MAC addr Gsellou_box>
[  743.590047] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  743.792035] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  743.996051] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  744.200068] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  748.592227] wlan0: deauthenticating from <MAC addr Gsellou_box> by local choice (reason=3)
[  830.591906] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[  830.592047] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[  830.592804] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[  830.609067] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  830.609072] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  830.609074] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  830.609075] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[  830.609173] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  830.634344] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  830.642706] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  830.647434] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  830.748369] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[  830.751425] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[  830.784980] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  865.952698] wlan0: authenticate with <MAC addr Gsellou_box>
[  865.958597] wlan0: direct probe to <MAC addr Gsellou_box> (try 1/3)
[  866.159998] wlan0: direct probe to <MAC addr Gsellou_box> (try 2/3)
[  866.363989] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  866.567915] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  870.959360] wlan0: deauthenticating from <MAC addr Gsellou_box> by local choice (reason=3)
[ 1962.956291] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 1962.956483] iwlwifi 0000:02:00.0: irq 42 for MSI/MSI-X
[ 1962.957605] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[ 1962.982567] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[ 1962.982572] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[ 1962.982573] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[ 1962.982575] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[ 1962.982673] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1963.008031] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 1963.017406] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1963.020481] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[ 1963.121272] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[ 1963.124321] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[ 1963.155851] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by chili555 on 2014-08-28
> [  866.363989] wlan0: direct probe to <MAC addr Gsellou_box> (try 3/3)
[  866.567915] wlan0: authentication with <MAC addr Gsellou_box> timed out
[  870.959360] wlan0: deauthenticating from <MAC addr Gsellou_box> by local choice (reason=3)It looks like it's trying!

I have read a few good reports from my colleagues about a different parameter for iwlwifi. Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the final line from:```
options iwlwifi 11n_disable=1
```To:```
options iwlwifi 11n_disable=8
```Proofread carefully, save and close the text editor. Reboot and then show us:```
cat /var/log/syslog | grep -e etwork -e iwl | tail -n20
```

---

### Post by simongsell on 2014-08-28
Here it is :

```

Aug 29 00:07:53 PC-Sim NetworkManager[738]: <info>   domain name 'home'
Aug 29 00:07:53 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 29 00:07:53 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> Policy set 'Connexion filaire 1' (eth0) as default for IPv4 routing and DNS.
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> DNS: starting dnsmasq...
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <warn> dnsmasq not available on the bus, can't update servers.
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <error> [1409263674.703024] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <warn> DNS: plugin dnsmasq update failed
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> Writing DNS information to /sbin/resolvconf
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> Activation (eth0) successful, device activated.
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <warn> dnsmasq appeared on DBus: :1.64
Aug 29 00:07:54 PC-Sim NetworkManager[738]: <info> Writing DNS information to /sbin/resolvconf
Aug 29 00:08:14 PC-Sim NetworkManager[738]: <info> (eth0): IP6 addrconf timed out or failed.
Aug 29 00:08:14 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 29 00:08:14 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 29 00:08:14 PC-Sim NetworkManager[738]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

---

### Post by chili555 on 2014-08-29
All we see here is a successful connection of the ethernet. Please detach the ethernet cable, try to connect with wireless and try again. I realize you need a working ethernet to post the result but you can save the log output to a text file and then connect the ethernet, connect and then copy and paste the text:```
cat /var/log/syslog | grep -e etwork -e iwl | tail -n20  >  wifi.txt
```

---

### Post by simongsell on 2014-08-29
Sorry. I was sure to do it without ethernet connection.
Here is the result of the command again :
```

Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Activation (wlan0/wireless): connection 'Gsellou_box' has security, and secrets exist.  No new secrets needed.
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Config: added 'ssid' value 'Gsellou_box'
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Config: added 'scan_ssid' value '1'
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Config: added 'psk' value '<omitted>'
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> Config: set interface ap_scan to 1
Aug 29 19:50:59 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: inactive -> authenticating
Aug 29 19:51:00 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 29 19:51:05 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Aug 29 19:51:23 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 29 19:51:23 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> NetworkManager state is now DISCONNECTED
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <warn> Activation (wlan0) failed for connection 'Gsellou_box'
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> (wlan0): deactivating device (reason 'none') [0]
Aug 29 19:51:27 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: disconnected -> inactive

```

---

### Post by chili555 on 2014-08-29
I'm really mystified. This suggests that the card and driver combination can't see and therefor can't connect to the access point.> Aug 29 19:51:23 PC-Sim NetworkManager[748]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> (wlan0): device state change: config -> failed (reason '[COLOR="#FF0000"]SSID not found[/COLOR]') [50 120 53]
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> NetworkManager state is now DISCONNECTED
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <warn> Activation (wlan0) failed for connection 'Gsellou_box'
Aug 29 19:51:25 PC-Sim NetworkManager[748]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]In fact, your last wireless_script does not include Gsellou_box in the iwlist scan results. It does show up in the nm-tool results:> [COLOR="#FF0000"]Gsellou_box[/COLOR]:     Infra, <MAC addr Gsellou_box>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2I don't understand why it appears some times and not others. Does it help if you reboot the router by unplugging and replugging it? Have you tried channel 13? There is no one on it now. Do other devices connect to the access point Gsellou_box with no trouble?

---

### Post by simongsell on 2014-08-29
I have an other Dell laptop with windows XP and the wireless connection works fine.
The router has been rebooted several times yet... I can try with the channel 13 but as I said, the current configuration of the router works well with windows XP ...

---

### Post by simongsell on 2014-08-31
No more results using the channel 13 ... 
Do you think this could be due to a hardware problem ?

---

### Post by jeremy31 on 2014-08-31
> **simongsell said:**
> No more results using the channel 13 ... 
Do you think this could be due to a hardware problem ?

If your laptops are easy to swap wifi cards, and the laptops aren't whitelisted, swap the cards

---

### Post by simongsell on 2014-08-31
My other laptop belongs to my laboratory and I use it for professsional stuff. I am not supposed (neither allowed) to touch its components. 
So, are you suggesting that a hardware problem isn't excluded ?

---

### Post by jeremy31 on 2014-08-31
> **simongsell said:**
> My other laptop belongs to my laboratory and I use it for professsional stuff. I am not supposed (neither allowed) to touch its components. 
So, are you suggesting that a hardware problem isn't excluded ?

So that rules out a card swap, it might be hardware related.  Let's try a simple grub edit```
sudo gedit /etc/default/grub
```
Now find the line that begins with GRUB_CMDLINE and contains "quiet splash" and make it be ```
"acpi_osi=Linux quiet splash"
``` save, exit gedit and ```
sudo update-grub
```
Reboot


my grub line looks like this ```
GRUB_CMDLINE_LINUX_DEFAULT="acpi_osi=Linux quiet splash"
```
This might change some info the BIOS is giving Ubuntu on how to control everything
I would also check to see if there are any BIOS updates for your PC

---

### Post by simongsell on 2014-08-31
Thank you jeremy31. I tried to edit the file /etc/default/grub but it didn't fix the problem.
I am surprised to hear about the grub configuration. I did have some troubles with the grub just after I installed the OS. I fixed it following this article : [http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux](http://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux)
I also cheked my BIOS version and it seems to be quiet old. I can update it if it is not dangerous and if you think it can help. If I update it, maybe it would be better to make a fresh install of Ubuntu 14.04. What do you think ?

---

### Post by weatherman2 on 2014-08-31
It IS slightly dangerous to update your BIOS, especially if you can't boot Windows anymore.  Any sort of glitch could cause an error flashing the BIOS and turn the laptop into a useless "brick."  And personally, I doubt a newer BIOS will have any effect on your wireless card.

I've used the Intel 5100 and other similar Intel wireless cards in Ubuntu laptops numerous times, and I've had great luck with them.  I recently installed 14.04 on a laptop with a 5100 and it connects fine to my access point using WPA2 + AES.  I wish I had suggestions to help.

FYI, I'm in the US, and in the US only channels 1 through 11 are supported for 802.11n 2.4GHZ WiFi.  If you are using channel 12 or 13, you must either be in another country where these are legal or you are using illegal channels.  In either case, if by chance the Ubuntu WiFi is somehow configured to work in a North American country, it may not see channels 12 or 13....

---

### Post by simongsell on 2014-09-02
No more help ? :/

---

### Post by chili555 on 2014-09-02
Please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Use nano or kate or leafpad if you don't have the text editor gedit.

Change the final line from:```
options iwlwifi 11n_disable=8
```
To:

```
options iwlwifi 11n_disable=2
```
Proofread carefully, save and close the text editor. Reboot and then show us:```
cat /var/log/syslog | grep -e etwork -e iwl | tail -n20
```

---

### Post by simongsell on 2014-09-03
Here it is :
```

Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Activation (wlan0/wireless): connection 'Gsellou_box' has security, and secrets exist.  No new secrets needed.
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Config: added 'ssid' value 'Gsellou_box'
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Config: added 'scan_ssid' value '1'
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Config: added 'psk' value '<omitted>'
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> Config: set interface ap_scan to 1
Sep  3 20:40:04 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: inactive -> scanning
Sep  3 20:40:06 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  3 20:40:07 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep  3 20:40:17 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Sep  3 20:40:19 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Sep  3 20:40:20 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <info> NetworkManager state is now DISCONNECTED
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <warn> Activation (wlan0) failed for connection 'Gsellou_box'
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Sep  3 20:40:30 PC-Sim NetworkManager[750]: <info> (wlan0): deactivating device (reason 'none') [0]
Sep  3 20:40:32 PC-Sim NetworkManager[750]: <info> (wlan0): supplicant interface state: disconnected -> inactive

```

---

### Post by chili555 on 2014-09-03
I regret I have no further suggestions. My colleagues and I have tried every probable and a few improbable tricks, magic, etc., and nothing whatever seems to have changed this:> <info> (wlan0): device state change: config -> failed (reason 'SSID not found')The ability of your card to see the router seems to come and go. When it goes, the connection drops. In some cases, the drop is just a few seconds after connection. 

I seldom admit to defeat, but I have nothing.

---

### Post by jeremy31 on 2014-09-03
> **chili555 said:**
> I regret I have no further suggestions. My colleagues and I have tried every probable and a few improbable tricks, magic, etc., and nothing whatever seems to have changed this:The ability of your card to see the router seems to come and go. When it goes, the connection drops. In some cases, the drop is just a few seconds after connection. 

I seldom admit to defeat, but I have nothing.

I noticed that too, I wonder if there is an issue with the antenna connector on the card?  I do have an Intel 5100 and don't have this issue, but I am waiting on a hard drive for that laptop now

---

### Post by chili555 on 2014-09-03
>  I wonder if there is an issue with the antenna connector on the cardCertainly worth checking.

---

