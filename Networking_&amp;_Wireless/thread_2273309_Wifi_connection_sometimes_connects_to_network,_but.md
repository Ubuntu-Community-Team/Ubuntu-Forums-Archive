---
title: "Wifi connection sometimes connects to network, but no internet access available"
date: 2015-04-12
forum: Networking &amp; Wireless
---

### Post by environmat on 2015-04-12
Hi there, 

I am trying to figure out my internet connection with Ubuntu 14.04. My wifi connection sometimes manages to connect to the network, but then the internet access does not work. I tried to change the IPv4 settings with DNS Server as 8.8.8.8, 8.8.4.4 (DHCP, adress only) and ignoring IPv6 but that did not help. I used Lubuntu before where the wifi worked correctly, but after some updates the wifi connection did not work anymore. I was able to connect to other wifi networks at work for example, but not to my home network. 

Here is the output of the wireless script. I am using a Intel® Centrino® Wireless-N 1000 Card and tried to update the firmware, but that did not solve or help. 
I am glad for any help. If you need further information please let me know! 

```


########## wireless info START ##########

Report from: 12 Apr 2015 12:10 CEST +0200

Booted last: 12 Apr 2015 11:48 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:029b]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232283  0 
mac80211              652718  1 iwldvm
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
iwlwifi               179412  1 iwldvm
cfg80211              494330  3 iwlwifi,mac80211,iwldvm
wmi                    19193  1 acer_wmi
video                  20128  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:9eff:feda:bc99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10359 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:9773359 (9.7 MB)  TX bytes:1293846 (1.2 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search localdomain

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [o2-WLAN64] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    AGCCOK-3:        Infra, <MAC 'AGCCOK-3' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    D-Link:          Infra, <MAC 'D-Link' [AC3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 29 WPA2
    EasyBox-639330:  Infra, <MAC 'EasyBox-639330' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    FRITZ!Box 6340 Cable: Infra, <MAC 'FRITZ!Box 6340 Cable' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    o2DSL:           Infra, <MAC 'o2DSL' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WEP
    FRITZ!Box WLAN 3270: Infra, <MAC 'FRITZ!Box WLAN 3270' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Eckhards WLAN-Netzwerk: Infra, <MAC 'Eckhards WLAN-Netzwerk' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    devolo-BCF2AFEF80BC: Infra, <MAC 'devolo-BCF2AFEF80BC' [AC8]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 22 WPA2
    o2-WLAN64:       Infra, <MAC 'o2-WLAN64' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

[[/etc/NetworkManager/system-connections/o2-WLAN64]] (600 root)
[connection] id=o2-WLAN64 | type=802-11-wireless
[802-11-wireless] ssid=o2-WLAN64 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'o2DSL' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"o2DSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002f4ef909882
                    Extra: Last beacon: 64ms ago
          Cell 02 - Address: <MAC 'AGCCOK-3' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"AGCCOK-3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000196e14253
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'D-Link' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"D-Link"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000052733c01a
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'EasyBox-639330' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-639330"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c8eeeed2ae
                    Extra: Last beacon: 908ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 05 - Address: <MAC 'FRITZ!Box WLAN 3270' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box WLAN 3270"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b65657c3
                    Extra: Last beacon: 564ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'WLApple' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLApple"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004603a20180
                    Extra: Last beacon: 1248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Im dichten Fichtendickicht' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Im dichten Fichtendickicht"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000022abff14180
                    Extra: Last beacon: 1128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'devolo-BCF2AFEF80BC' [AC8]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"devolo-BCF2AFEF80BC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018060fa140
                    Extra: Last beacon: 968ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'WLAppleR5' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WLAppleR5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a96c954180
                    Extra: Last beacon: 808ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Eckhards WLAN-Netzwerk' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Eckhards WLAN-Netzwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000071281e1d6ad
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'o2-WLAN64' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000088f8d9913a
                    Extra: Last beacon: 532ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 12 - Address: <MAC 'EasyBox-39D355' [AC12]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-39D355"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ce82d7cb93
                    Extra: Last beacon: 452ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                 lo        Interface doesn't support scanning.

       Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 13 - Address: <MAC 'o2-WLAN20' [AC13]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN20"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000013a2017561ef
                    Extra: Last beacon: 432ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     092C5F7885F1C7B9B99605B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D421794D4F30DF3A540FD24
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-30-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-30-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        7B:E2:A7:20:0F:17:F0:0C:A0:11:F7:0E:5A:87:4C:37:E3:E0:F6:BE
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
wd_disable: 1

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0083 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.728859] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.129850] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   19.137234] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   19.173070] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[   19.180447] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[   19.235723] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.478605] wlan0: authenticate with <MAC 'o2-WLAN64' [AC11]>
[   20.487726] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 1/3)
[   20.688029] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 2/3)
[   20.892029] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 3/3)
[   21.096027] wlan0: authentication with <MAC 'o2-WLAN64' [AC11]> timed out
[  619.905767] wlan0: authenticate with <MAC 'o2-WLAN64' [AC11]>
[  619.914461] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 1/3)
[  620.116126] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 2/3)
[  620.320124] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 3/3)
[  620.524123] wlan0: authentication with <MAC 'o2-WLAN64' [AC11]> timed out
[ 1226.383171] wlan0: authenticate with <MAC 'o2-WLAN64' [AC11]>
[ 1226.388350] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 1/3)
[ 1226.592128] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 2/3)
[ 1226.796129] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 3/3)
[ 1227.000132] wlan0: authentication with <MAC 'o2-WLAN64' [AC11]> timed out
[ 1312.774371] wlan0: authenticate with <MAC 'o2-WLAN64' [AC11]>
[ 1312.780053] wlan0: direct probe to <MAC 'o2-WLAN64' [AC11]> (try 1/3)

########## wireless info END ############


```

---

### Post by environmat on 2015-04-13
Since I am logged in at the university wifi with the same laptop and no problems I guess that it has to do something with the settings of my home wifi... Any suggestions?

---

### Post by markohrastovec on 2015-04-13
I find two things in the script output you have provided. You are connected via the cable too (eth0). When you have wireless and cable connection the cable connection will be used to access internet. When wireless connects the cable is already connected and the default gateway for the cable will have higher priority. If cable does not provide you the internet connectivity, you will not be able to use it. Unplug the cable and see if the wireless works when it manages to connect.

The other thing is it says the wireless is connecting. It is not connected. That is probably linked to the issue you are mentioning that wireless is connecting only sometimes. I don't have a clue why is this happening.

---

### Post by Bucky Ball on 2015-04-13
Have a look at what it has in the IPv4 settings when you are at Uni. That is probably serving you an IP address via DHCP and there are probably no DNS IPs. What are you connecting with at home? If it is a wireless router and that is serving the IP address (you haven't set up a static one) then the router will be taking care of the DNS IPs also so get rid of them locally. Continue to ignore IPv6. 

You know the card is working fine so you can look elsewhere to the router or your local set up. You normally only need to add the DNS IPs if you are setting up a static IP address on the local machine.

So, get rid of the DNS IPs you've added, reboot or restart networking and see if it connects. Left click the network icon and see if it shows any available networks. If yours is there, attempt to connect. If you can, open a terminal and ping the router:

```
ping ***.***.***.***
```

Where '***.***.***.***' is the IP of your router. Let us know how far you get and what happens.

---

### Post by environmat on 2015-04-14
Ok, so I am still trying to connect to the wireless router without any  static IP adress. I set the settings to the default connection settings,  but still ignoring IPv6. 
At the beginning it did not work, laptop  finds the network but can't connect, so I plugged in the cabel and after  a second it tells me that I am connected to the wifi network (internet  works perfectly fine and I can access the router). But after the restart  the connection does not work anymore. So I am very confused.... 
Any suggestions...

---

