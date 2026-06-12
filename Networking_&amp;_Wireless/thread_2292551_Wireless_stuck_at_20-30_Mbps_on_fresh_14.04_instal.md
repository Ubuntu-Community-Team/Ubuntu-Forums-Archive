---
title: "Wireless stuck at 20-30 Mbps on fresh 14.04 install"
date: 2015-08-29
forum: Networking &amp; Wireless
---

### Post by adamr1337 on 2015-08-29
Hello,

I just built a new computer and installed 14.04 on it, but my wireless connection is stuck between 20-30 Mbps even though my roommate gets ~60Mbps on her Mac. I've combed through the forums and I've tried all of the following:
1) fixing Debian Avahi-daemon bug/problem by editing the line in /etc/nsswitch.conf
and
2) upgraded kernel

Here is some info about my wireless.

```


########## wireless info START ##########


Report from: 28 Aug 2015 22:29 PDT -0700


Booted last: 28 Aug 2015 21:47 PDT -0700


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:09:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-V [8086:153b] (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device [1043:859f]
    Kernel driver in use: e1000e


03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:850e]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0b05:17d0 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 174c:2074 ASMedia Technology Inc. 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 050d:1103 Belkin Components F9L1103 N750 DB 802.11abgn 2x3:3 [Ralink RT3573]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlwifi               188416  0 
rt2800usb              28672  0 
rt2x00usb              24576  1 rt2800usb
rt2800lib              90112  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              16384  1 rt2800lib
ath3k                  20480  0 
bluetooth             491520  23 bnep,ath3k,btusb,rfcomm
eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
mxm_wmi                16384  0 
sparse_keymap          16384  1 asus_wmi
ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              708608  4 ath9k,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              524288  6 ath,iwlwifi,ath9k_common,ath9k,mac80211,rt2x00lib
video                  20480  1 asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi


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
          Interrupt:20 Memory:ef300000-ef320000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.192  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:137260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:177757745 (177.7 MB)  TX bytes:24659139 (24.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11abgn  ESSID:"CobaltBlue"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'CobaltBlue' [AC1]>   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2499  Invalid misc:645   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1


##### resolv.conf #######################


nameserver 127.0.1.1
search socal.rr.com


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root      1056     1  0 21:47 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan1  [CobaltBlue] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>


  Capabilities:
    Speed:           39 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Yukihiromol:     Infra, <MAC 'Yukihiromol' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    TG1672G92:       Infra, <MAC 'TG1672G92' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    KrishaRoach:     Infra, <MAC 'KrishaRoach' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WEP
    DIGE:            Infra, <MAC 'DIGE' [AC11]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 42 WPA2
    *CobaltBlue:     Infra, <MAC 'CobaltBlue' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    DIGE:            Infra, <MAC 'CobaltBlue' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    TG1672GD2-5G:    Infra, <MAC 'DIGE' [AN7]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 19 WPA2
    Corinth:         Infra, <MAC 'TG1672GD2-5G' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    TG1672G92-5G:    Infra, <MAC 'TG1672G92-5G' [AC10]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 35 WPA2
    Yukihiromol:     Infra, <MAC 'Yukihiromol' [AC9]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 22 WPA2


  IPv4 Settings:
    Address:         192.168.0.192
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


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


[[/etc/NetworkManager/system-connections/CobaltBlue]] (600 root)
[connection] id=CobaltBlue | type=802-11-wireless
[802-11-wireless] ssid=CobaltBlue | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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
          Channel 14 : 2.484 GHz
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
wlan1     27 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 151 : 5.755 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 159 : 5.795 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.457 GHz (Channel 10)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.745 GHz (Channel 149)
      1   APs on   Frequency:5.785 GHz (Channel 157)


wlan0     No scan results


wlan1     Scan completed :
          Cell 01 - Address: <MAC 'CobaltBlue' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"CobaltBlue"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000060bcb70c
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'yoi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"yoi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f52a9f241
                    Extra: Last beacon: 8820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Public Access Terminal' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Public Access Terminal"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000414744e593
                    Extra: Last beacon: 72ms ago
          Cell 04 - Address: <MAC 'Yukihiromol' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Yukihiromol"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dcec5ca99a
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '202 Network' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"202 Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001413a614b
                    Extra: Last beacon: 8192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Otonokizaka' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Otonokizaka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000136c13fa923
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TG1672G92' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TG1672G92"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ca36115151
                    Extra: Last beacon: 3876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'KrishaRoach' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"KrishaRoach"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000134692ecd73b
                    Extra: Last beacon: 72ms ago
          Cell 09 - Address: <MAC 'Yukihiromol' [AC9]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Yukihiromol"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dcecd7905e
                    Extra: Last beacon: 4332ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'TG1672G92-5G' [AC10]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TG1672G92-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002ca36917055
                    Extra: Last beacon: 2224ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'DIGE' [AC11]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"DIGE"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000be9c38d048
                    Extra: Last beacon: 1192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlwifi]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[rt2800usb]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CDB4A56A88AAEC3126F6347
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     B51D09F4F13F9196B61EBE4
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     491D0D9622C1740D95E8041
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     7C3B03973B59C2A2A136B6C
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[ath3k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C77B8A018F5C738ABC4CA47
depends:        bluetooth
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DFC03DD607884E899C8398C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:83:39:FD:1A:2F:8D:C0:EF:DC:5D:F7:12:9D:FB:17:0A:6F:6D:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlwifi]
11n_disable: 1
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
uapsd_disable: Y
wd_disable: 1


[rt2800usb]
nohwcrypt: N


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[    8.018295] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3593, rev 0402 detected
[    8.028029] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 000d detected
[    9.361241] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    9.474524] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[    9.621273] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[    9.911866] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.414101] wlan1: authenticate with <MAC 'CobaltBlue' [AC1]>
[   15.450929] wlan1: send auth to <MAC 'CobaltBlue' [AC1]> (try 1/3)
[   15.452303] wlan1: authenticated
[   15.452815] wlan1: associate with <MAC 'CobaltBlue' [AC1]> (try 1/3)
[   15.455849] wlan1: RX AssocResp from <MAC 'CobaltBlue' [AC1]> (capab=0x431 status=0 aid=9)
[   15.460557] wlan1: associated
[   15.460571] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   15.472724] wlan1: deauthenticating from <MAC 'CobaltBlue' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   15.514441] wlan1: authenticate with <MAC 'CobaltBlue' [AC1]>
[   15.538851] wlan1: send auth to <MAC 'CobaltBlue' [AC1]> (try 1/3)
[   15.540275] wlan1: authenticated
[   15.540739] wlan1: associate with <MAC 'CobaltBlue' [AC1]> (try 1/3)
[   15.543753] wlan1: RX AssocResp from <MAC 'CobaltBlue' [AC1]> (capab=0x431 status=0 aid=9)
[   15.548397] wlan1: associated
[  923.305081] wlan1: authenticate with <MAC 'CobaltBlue' [AC1]>
[  923.333504] wlan1: direct probe to <MAC 'CobaltBlue' [AC1]> (try 1/3)
[  923.535184] wlan1: send auth to <MAC 'CobaltBlue' [AC1]> (try 2/3)
[  923.536596] wlan1: authenticated
[  923.539169] wlan1: associate with <MAC 'CobaltBlue' [AC1]> (try 1/3)
[  923.542138] wlan1: RX AssocResp from <MAC 'CobaltBlue' [AC1]> (capab=0x431 status=0 aid=7)
[  923.546949] wlan1: associated


########## wireless info END ############



```

---

### Post by Hadaka on 2015-08-29
hi, please do..
```
sudo modprobe -rf iwlwifi
sudo modprobe -rfv ath9k
echo "options ath9k nohwcrypt=1" | sudo tee-a /etc/modprobe.d/ath9k.conf
```
then do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```

```
then access your router settings and remove TKIP
it should just be wpa2 aes no TKIP
```
unplug your usb wireless, and test

---

### Post by Hadaka on 2015-08-29
oops.

---

### Post by adamr1337 on 2015-08-29
I inputted the first block of code and this is what I got:

```
~$ sudo modprobe -rf iwlwifirmmod: ERROR: missing module name.
modprobe: FATAL: Error running remove command for iwlwifi


~$ sudo modprobe -rfv ath9k
rmmod ath9k
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath


~$ echo "options ath9k nohwcrypt=1" | sudo tee-a /etc/modprobe.d/ath9k.conf
sudo: tee-a: command not found



```

I did the other block of code and thing changed my router settings to AES to no avail.

---

### Post by Hadaka on 2015-08-29
Hi, i made a typo, sorry ..it should be..
```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```

---

### Post by adamr1337 on 2015-08-29
Even after running the fixed line of code, I still appear to have the same problem.

---

### Post by Hadaka on 2015-08-29
Hi,please run and post a fresh wireless info txt file
thanks

---

