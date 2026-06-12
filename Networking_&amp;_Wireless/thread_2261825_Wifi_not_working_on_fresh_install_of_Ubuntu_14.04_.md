---
title: "Wifi not working on fresh install of Ubuntu 14.04 with Atheros AR9285 (ath9k)"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by flore2003 on 2015-01-21
Hi folks,

I have been reading this subforum, googleing for solutions and trying out things for the past three hours, but nothing seems to work.
I have a HP ProBook 4430s, which comes with an Atheros AR9285 chip. I have found out that the ath9k kernel module is responsible for this adapter.

The problem is, I can connect to my wireless network, but I can't even reach my router. Pinging anything beside localhost results in 100% package loss.
I have tried to set the nohwcrypt option to 1, but this changed nothing.

The wired LAN works flawlessly.

EDIT: I should add that the wireless adapter worked without a problem in the ubuntu 12.04 installation, that this fresh installation replaced, so it can't be a hardware problem.

This is the result of the wireless script:

```
 

########## wireless info START ##########


Report from: 21 Jan 2015 13:51 CET +0100


Booted last: 21 Jan 2015 13:50 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


24:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k


25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:167f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 003: ID 1bcf:2805 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 hp_wmi


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
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe4c:a049/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4877 (4.8 KB)  TX bytes:12316 (12.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"GreggyNetz"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'GreggyNetz' [AC8]>   
          Bit Rate=26 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search localdomain


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


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


- Device: wlan0  [GreggyNetz] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    EasyBox-AAFE66:  Infra, <MAC 'EasyBox-AAFE66' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    EasyBox-7B3912:  Infra, <MAC 'EasyBox-7B3912' [AC7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    WLAN-9B0906:     Infra, <MAC 'WLAN-9B0906' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    TutiFruti:       Infra, <MAC 'TutiFruti' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    carlawlan:       Infra, <MAC 'carlawlan' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Fabian1993:      Infra, <MAC 'Fabian1993' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    EasyBox-5BAC44:  Infra, <MAC 'EasyBox-5BAC44' [AC11]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    campus-guests:   Infra, <MAC 'campus-guests' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    campus-user:     Infra, <MAC 'campus-user' [AC6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    WLAN-C4D436:     Infra, <MAC 'WLAN-C4D436' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    *GreggyNetz:     Infra, <MAC 'GreggyNetz' [AC8]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 89 WPA2
    ALICE-WLAN22:    Infra, <MAC 'ALICE-WLAN22' [AC12]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA2


  IPv4 Settings:
    Address:         192.168.1.8
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


[[/etc/NetworkManager/system-connections/GreggyNetz]] (600 root)
[connection] id=GreggyNetz | type=802-11-wireless
[802-11-wireless] ssid=GreggyNetz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TutiFruti' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TutiFruti"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004c776f698ff
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'carlawlan' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"carlawlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f188206ed8
                    Extra: Last beacon: 27584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'EasyBox-AAFE66' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-AAFE66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001511112e8b5
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'WLAN-C4D436' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WLAN-C4D436"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000032865377188
                    Extra: Last beacon: 1640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'campus-guests' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"campus-guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058f7630dddc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'campus-user' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"campus-user"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058f7631be76
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'EasyBox-7B3912' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-7B3912"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a385c1cb5b
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'GreggyNetz' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"GreggyNetz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008f29639d0
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: <MAC '
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006937be19d
                    Extra: Last beacon: 400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLAN-9B0906' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-9B0906"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000073891f8013
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'EasyBox-5BAC44' [AC11]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-5BAC44"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001009216f1167
                    Extra: Last beacon: 29340ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 12 - Address: <MAC 'ALICE-WLAN22' [AC12]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd1f906b3
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC '' [AC13]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b56790919f
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     94B3813AF84C49B115229AD
depends:        ath
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.863572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   21.144202] wlan0: authenticate with <MAC 'GreggyNetz' [AC8]>
[   21.165269] wlan0: send auth to <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   21.167257] wlan0: authenticated
[   21.170425] wlan0: associate with <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   21.198891] wlan0: RX AssocResp from <MAC 'GreggyNetz' [AC8]> (capab=0x411 status=0 aid=2)
[   21.198998] wlan0: associated
[   21.199070] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.205109] ath: EEPROM regdomain: 0x8114
[   21.205117] ath: EEPROM indicates we should expect a country code
[   21.205121] ath: doing EEPROM country->regdmn map search
[   21.205124] ath: country maps to regdmn code: 0x37
[   21.205127] ath: Country alpha2 being used: DE
[   21.205130] ath: Regpair used: 0x37
[   21.205134] ath: regdomain 0x8114 dynamically updated by country IE
[   35.696493] wlan0: deauthenticated from <MAC 'GreggyNetz' [AC8]> (Reason: 3)
[   36.760805] wlan0: authenticate with <MAC 'GreggyNetz' [AC8]>
[   36.783130] wlan0: send auth to <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   36.785275] wlan0: authenticated
[   36.787148] wlan0: associate with <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   36.818406] wlan0: RX AssocResp from <MAC 'GreggyNetz' [AC8]> (capab=0x411 status=0 aid=2)
[   36.818496] wlan0: associated
[   36.823950] ath: EEPROM regdomain: 0x8114
[   36.823958] ath: EEPROM indicates we should expect a country code
[   36.823962] ath: doing EEPROM country->regdmn map search
[   36.823965] ath: country maps to regdmn code: 0x37
[   36.823969] ath: Country alpha2 being used: DE
[   36.823972] ath: Regpair used: 0x37
[   36.823976] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############

```

Do you guys have any idea?

Thank you so much!

---

### Post by dixdox12 on 2015-01-21
> **flore2003 said:**
> Hi folks,

I have been reading this subforum, googleing for solutions and trying out things for the past three hours, but nothing seems to work.
I have a HP ProBook 4430s, which comes with an Atheros AR9285 chip. I have found out that the ath9k kernel module is responsible for this adapter.

The problem is, I can connect to my wireless network, but I can't even reach my router. Pinging anything beside localhost results in 100% package loss.
I have tried to set the nohwcrypt option to 1, but this changed nothing.

The wired LAN works flawlessly.

EDIT: I should add that the wireless adapter worked without a problem in the ubuntu 12.04 installation, that this fresh installation replaced, so it can't be a hardware problem.

This is the result of the wireless script:

```
 

########## wireless info START ##########


Report from: 21 Jan 2015 13:51 CET +0100


Booted last: 21 Jan 2015 13:50 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


24:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k


25:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:167f]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 003: ID 1bcf:2805 Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 hp_wmi


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
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe4c:a049/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4877 (4.8 KB)  TX bytes:12316 (12.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"GreggyNetz"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'GreggyNetz' [AC8]>   
          Bit Rate=26 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search localdomain


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


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


- Device: wlan0  [GreggyNetz] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    EasyBox-AAFE66:  Infra, <MAC 'EasyBox-AAFE66' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    EasyBox-7B3912:  Infra, <MAC 'EasyBox-7B3912' [AC7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    WLAN-9B0906:     Infra, <MAC 'WLAN-9B0906' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    TutiFruti:       Infra, <MAC 'TutiFruti' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    carlawlan:       Infra, <MAC 'carlawlan' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    Fabian1993:      Infra, <MAC 'Fabian1993' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    EasyBox-5BAC44:  Infra, <MAC 'EasyBox-5BAC44' [AC11]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    campus-guests:   Infra, <MAC 'campus-guests' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    campus-user:     Infra, <MAC 'campus-user' [AC6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 15 WPA2 Enterprise
    WLAN-C4D436:     Infra, <MAC 'WLAN-C4D436' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    *GreggyNetz:     Infra, <MAC 'GreggyNetz' [AC8]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 89 WPA2
    ALICE-WLAN22:    Infra, <MAC 'ALICE-WLAN22' [AC12]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA2


  IPv4 Settings:
    Address:         192.168.1.8
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


[[/etc/NetworkManager/system-connections/GreggyNetz]] (600 root)
[connection] id=GreggyNetz | type=802-11-wireless
[802-11-wireless] ssid=GreggyNetz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TutiFruti' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TutiFruti"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004c776f698ff
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'carlawlan' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"carlawlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001f188206ed8
                    Extra: Last beacon: 27584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'EasyBox-AAFE66' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-AAFE66"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001511112e8b5
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'WLAN-C4D436' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WLAN-C4D436"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000032865377188
                    Extra: Last beacon: 1640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'campus-guests' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"campus-guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058f7630dddc
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'campus-user' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"campus-user"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000058f7631be76
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'EasyBox-7B3912' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-7B3912"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a385c1cb5b
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'GreggyNetz' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"GreggyNetz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008f29639d0
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 09 - Address: <MAC '
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006937be19d
                    Extra: Last beacon: 400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLAN-9B0906' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"WLAN-9B0906"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000073891f8013
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'EasyBox-5BAC44' [AC11]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-5BAC44"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001009216f1167
                    Extra: Last beacon: 29340ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 12 - Address: <MAC 'ALICE-WLAN22' [AC12]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bd1f906b3
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC '' [AC13]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b56790919f
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     94B3813AF84C49B115229AD
depends:        ath
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.863572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   21.144202] wlan0: authenticate with <MAC 'GreggyNetz' [AC8]>
[   21.165269] wlan0: send auth to <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   21.167257] wlan0: authenticated
[   21.170425] wlan0: associate with <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   21.198891] wlan0: RX AssocResp from <MAC 'GreggyNetz' [AC8]> (capab=0x411 status=0 aid=2)
[   21.198998] wlan0: associated
[   21.199070] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   21.205109] ath: EEPROM regdomain: 0x8114
[   21.205117] ath: EEPROM indicates we should expect a country code
[   21.205121] ath: doing EEPROM country->regdmn map search
[   21.205124] ath: country maps to regdmn code: 0x37
[   21.205127] ath: Country alpha2 being used: DE
[   21.205130] ath: Regpair used: 0x37
[   21.205134] ath: regdomain 0x8114 dynamically updated by country IE
[   35.696493] wlan0: deauthenticated from <MAC 'GreggyNetz' [AC8]> (Reason: 3)
[   36.760805] wlan0: authenticate with <MAC 'GreggyNetz' [AC8]>
[   36.783130] wlan0: send auth to <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   36.785275] wlan0: authenticated
[   36.787148] wlan0: associate with <MAC 'GreggyNetz' [AC8]> (try 1/3)
[   36.818406] wlan0: RX AssocResp from <MAC 'GreggyNetz' [AC8]> (capab=0x411 status=0 aid=2)
[   36.818496] wlan0: associated
[   36.823950] ath: EEPROM regdomain: 0x8114
[   36.823958] ath: EEPROM indicates we should expect a country code
[   36.823962] ath: doing EEPROM country->regdmn map search
[   36.823965] ath: country maps to regdmn code: 0x37
[   36.823969] ath: Country alpha2 being used: DE
[   36.823972] ath: Regpair used: 0x37
[   36.823976] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############

```

Do you guys have any idea?

Thank you so much!

Have you tried opening the Additional Drivers application?
Sometimes Ubuntu recognises the wlan card but the driver for it is proprietary and closed-source, and you have to manually enable it.

---

### Post by flore2003 on 2015-01-21
Yes, sadly there are no additional drivers available.

---

