---
title: "Wifi connection periodically drops in 14.04 64-bit"
date: 2015-01-05
forum: Networking &amp; Wireless
---

### Post by Harvallen on 2015-01-05
Hello, I am new to Ubuntu and this forum. As the title says, every half hour or so my wifi connection drops. Hope to get an answer here, I have searched the net, then this forum but can't seem to find an answer. I have updated the drivers as instructed on this website and created a wireless log txt:

```


########## wireless info START ##########


Report from: 04 Jan 2015 22:25 CET +0100


Booted last: 04 Jan 2015 22:19 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0d8]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2232:1029  
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: samsung-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


ath3k                  13318  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
bluetooth             391136  12 bnep,ath3k,btusb,rfcomm
wmi                    19177  0 


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
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52b7:c3ff:fe56:b007/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2867 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3193 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1604751 (1.6 MB)  TX bytes:540078 (540.0 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"HG655D-68E0B5"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'HG655D-68E0B5' [AC1]>   
          Bit Rate=121.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [HG655D-68E0B5] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           81 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    van.heuningen:   Infra, <MAC 'van.heuningen' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Sitecom9F51D8:   Infra, <MAC 'Sitecom9F51D8' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    nasnien:         Infra, <MAC 'nasnien' [AC15]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Netwerk van Sterretje: Infra, <MAC 'Netwerk van Sterretje' [AC22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Ingrid:          Infra, <MAC 'Ingrid' [AC24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    UPC248304732:    Infra, <MAC 'UPC248304732' [AC23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    theanatolian:    Infra, <MAC 'theanatolian' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    home1:           Infra, <MAC 'home1' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    HG655D-CC6E85:   Infra, <MAC 'HG655D-CC6E85' [AC18]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA2
    H220N23C2D7:     Infra, <MAC 'H220N23C2D7' [AC9]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    UPC246568664:    Infra, <MAC 'UPC246568664' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Thomson185D6C:   Infra, <MAC 'Thomson185D6C' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    UPC WifiSpots:   Infra, <MAC 'UPC WifiSpots' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA2 Enterprise
    Zy_private_YJWPHJ: Infra, <MAC 'Zy_private_YJWPHJ' [AC16]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 15 WPA2
    UPC WifiSpots:   Infra, <MAC 'UPC WifiSpots' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 5 WPA2 Enterprise
    UPC246231588:    Infra, <MAC 'UPC246231588' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA2
    TELE2:           Infra, <MAC 'TELE2' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WEP
    KPN Fon:         Infra, <MAC 'KPN Fon' [AC26]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20
    KPN Fon:         Infra, <MAC 'KPN Fon' [AC7]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 17
    Zy_private_PHRUFC: Infra, <MAC 'Zy_private_PHRUFC' [AC19]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA2
    VGV7519B2BD9F:   Infra, <MAC 'VGV7519B2BD9F' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    VGV7519712DC0:   Infra, <MAC 'VGV7519712DC0' [AC17]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    UPC246085611:    Infra, <MAC 'UPC246085611' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    Sitecom2b689c:   Infra, <MAC 'Sitecom2b689c' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 12 WPA2
    Melissa:         Infra, <MAC 'Melissa' [AN25]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    Zy_private_7KEA34: Infra, <MAC 'Zy_private_7KEA34' [AN26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    VGV7519CD5C99:   Infra, <MAC 'VGV7519CD5C99' [AC6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA2
    UPC WifiSpots:   Infra, <MAC 'UPC WifiSpots' [AN28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    UPC0045625:      Infra, <MAC 'UPC0045625' [AN29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    UPC1394347:      Infra, <MAC 'UPC1394347' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    H220N10A3C3:     Infra, <MAC 'H220N10A3C3' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    SpeedTouchAA31FE:Infra, <MAC 'SpeedTouchAA31FE' [AN32]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    HEMA:            Infra, <MAC 'HEMA' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    KPN Fon:         Infra, <MAC 'KPN Fon' [AN34]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17
    *HG655D-68E0B5:  Infra, <MAC 'HG655D-68E0B5' [AC1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 63 WPA2
    Top secret:      Infra, <MAC 'Top secret' [AN36]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Zy_private_CJ7MJH: Infra, <MAC 'Zy_private_CJ7MJH' [AC5]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


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


[[/etc/NetworkManager/system-connections/HG655D-68E0B5]] (600 root)
[connection] id=HG655D-68E0B5 | type=802-11-wireless
[802-11-wireless] ssid=HG655D-68E0B5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HG655D-CC6E85]] (600 root)
[connection] id=HG655D-CC6E85 | type=802-11-wireless
[802-11-wireless] ssid=HG655D-CC6E85 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/H220N23C2D7]] (600 root)
[connection] id=H220N23C2D7 | type=802-11-wireless
[802-11-wireless] ssid=H220N23C2D7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.447 GHz (Channel 8)


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      7   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HG655D-68E0B5' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"HG655D-68E0B5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a244428b65
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'van.heuningen' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"van.heuningen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000107da4f2df9
                    Extra: Last beacon: 1664ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'VGV7519B2BD9F' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VGV7519B2BD9F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001faaf154029
                    Extra: Last beacon: 1712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'theanatolian' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"theanatolian"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8d129760d
                    Extra: Last beacon: 1720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Zy_private_CJ7MJH' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_CJ7MJH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000036d9b50a2
                    Extra: Last beacon: 10632ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VGV7519CD5C99' [AC6]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"VGV7519CD5C99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000058f1d184bbb
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'KPN Fon' [AC7]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000509fd35b4
                    Extra: Last beacon: 10208ms ago
          Cell 08 - Address: <MAC 'home1' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"home1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000033e823a12c9
                    Extra: Last beacon: 10208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'H220N23C2D7' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"H220N23C2D7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000509fd4e54
                    Extra: Last beacon: 10208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC246231588' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"UPC246231588"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b199913a
                    Extra: Last beacon: 11172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HEMA' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HEMA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000037d7a92a4
                    Extra: Last beacon: 10208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Sitecom2b689c' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Sitecom2b689c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000091df44b09
                    Extra: Last beacon: 1024ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'UPC246568664' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"UPC246568664"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c1aba13e
                    Extra: Last beacon: 1012ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'UPC WifiSpots' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001c110fb19
                    Extra: Last beacon: 11144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC 'nasnien' [AC15]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"nasnien"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019888c953d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Zy_private_YJWPHJ' [AC16]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_YJWPHJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000134e56187ec
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'VGV7519712DC0' [AC17]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"VGV7519712DC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d1a234dc8f
                    Extra: Last beacon: 56ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'HG655D-CC6E85' [AC18]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HG655D-CC6E85"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000025567d70d570
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Zy_private_PHRUFC' [AC19]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_PHRUFC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000053e805f725d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Sitecom9F51D8' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9F51D8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000ae0f0b9aba1
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'UPC246085611' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"UPC246085611"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011ba48140
                    Extra: Last beacon: 10268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'Netwerk van Sterretje' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Netwerk van Sterretje"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f671fe3260
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'UPC248304732' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC248304732"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000018fbb355
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'Ingrid' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Ingrid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f671fd776b
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'MAGDAANEL63' [AC25]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MAGDAANEL63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d03e3d7c37
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'KPN Fon' [AC26]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d1a234eac4
                    Extra: Last beacon: 56ms ago
          Cell 27 - Address: <MAC 'UPC243903052' [AC27]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"UPC243903052"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002aa853f6
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'UPC WifiSpots' [AC28]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"UPC WifiSpots"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002aa85da7
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     661F5D1CDD236CFF7BE3FA5
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     ADAEAFEC0FFEB04BC97E45D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    5.679106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    6.583661] wlan0: authenticate with <MAC 'HG655D-68E0B5' [AC1]>
[    6.600727] wlan0: send auth to <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[    6.602740] wlan0: authenticated
[    6.605218] wlan0: associate with <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[    6.609838] wlan0: RX AssocResp from <MAC 'HG655D-68E0B5' [AC1]> (capab=0x431 status=0 aid=4)
[    6.609885] wlan0: associated
[    6.609911] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.611582] ath: EEPROM regdomain: 0x807c
[    6.611585] ath: EEPROM indicates we should expect a country code
[    6.611586] ath: doing EEPROM country->regdmn map search
[    6.611587] ath: country maps to regdmn code: 0x3a
[    6.611587] ath: Country alpha2 being used: CA
[    6.611588] ath: Regpair used: 0x3a
[    6.611589] ath: regdomain 0x807c dynamically updated by country IE
[    7.710735] IPv6: wlan0: IPv6 duplicate address fe80::52b7:c3ff:fe56:b007 detected!
[  211.027065] wlan0: deauthenticating from <MAC 'HG655D-68E0B5' [AC1]> by local choice (reason=3)
[  211.942800] wlan0: authenticate with <MAC 'HG655D-68E0B5' [AC1]>
[  211.966651] wlan0: send auth to <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[  211.976877] wlan0: authenticated
[  211.977819] wlan0: associate with <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[  211.984233] wlan0: RX AssocResp from <MAC 'HG655D-68E0B5' [AC1]> (capab=0x431 status=0 aid=4)
[  211.984294] wlan0: associated
[  211.988116] ath: EEPROM regdomain: 0x807c
[  211.988120] ath: EEPROM indicates we should expect a country code
[  211.988123] ath: doing EEPROM country->regdmn map search
[  211.988125] ath: country maps to regdmn code: 0x3a
[  211.988127] ath: Country alpha2 being used: CA
[  211.988129] ath: Regpair used: 0x3a
[  211.988132] ath: regdomain 0x807c dynamically updated by country IE
[  212.971765] IPv6: wlan0: IPv6 duplicate address fe80::52b7:c3ff:fe56:b007 detected!


########## wireless info END ############

```

Please let me know if you need more info, I'll be happy to provide.

---

### Post by praseodym on 2015-01-05
Deactivate the hardware encryption of the driver

```
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by Harvallen on 2015-01-10
Haven't had any issues for 4 days straight so I can safely assume that did the trick. Thank you!

---

### Post by Harvallen on 2015-01-31
And after a good four weeks the wifi drops again every 30 minutes or so. I ran the de-encrypt code again in terminal but that didnt help. So here is the wireless script again. Mind you I followed the steps carefully and updated first before running the wireless script. Can someone please have a look? Many thanks in advance!

```
########## wireless info START ##########

Report from: 31 Jan 2015 20:15 CET +0100


Booted last: 31 Jan 2015 18:07 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0d8]
    Kernel driver in use: r8169


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Samsung Electronics Co Ltd Device [144d:4105]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2232:1029  
Bus 001 Device 008: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  0 


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
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::52b7:c3ff:fe56:b007/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:127048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140863683 (140.8 MB)  TX bytes:13862494 (13.8 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"HG655D-68E0B5"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'HG655D-68E0B5' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:8   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [HG655D-68E0B5] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    van.heuningen:   Infra, <MAC 'van.heuningen' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Sitecom9F51D8:   Infra, <MAC 'Sitecom9F51D8' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA2
    nasnien:         Infra, <MAC 'nasnien' [AC6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 45 WPA2
    H220N23C2D7:     Infra, <MAC 'H220N23C2D7' [AC10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Zy_private_PHRUFC: Infra, <MAC 'Zy_private_PHRUFC' [AN5]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 34 WPA2
    netwerk:         Infra, <MAC 'netwerk' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HG655D-CC6E85:   Infra, <MAC 'HG655D-CC6E85' [AC13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA2
    VGV7519B2BD9F:   Infra, <MAC 'VGV7519B2BD9F' [AC19]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 27 WPA2
    VGV7519712DC0:   Infra, <MAC 'VGV7519712DC0' [AC12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    KPN Fon:         Infra, <MAC 'KPN Fon' [AC9]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 22
    KPN Fon:         Infra, <MAC 'KPN Fon' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 19
    KPN Fon:         Infra, <MAC 'KPN Fon' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    theanatolian:    Infra, <MAC 'theanatolian' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2
    Thomson185D6C:   Infra, <MAC 'Thomson185D6C' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    VGV7519CD5C99:   Infra, <MAC 'VGV7519CD5C99' [AC8]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 29 WPA2
    UPC246945025:    Infra, <MAC 'UPC246945025' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA2
    abe:             Infra, <MAC 'abe' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    UPC WifiSpots:   Infra, <MAC 'UPC WifiSpots' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    UPC248304732:    Infra, <MAC 'UPC248304732' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Ingrid:          Infra, <MAC 'Ingrid' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Zy_private_YJWPHJ: Infra, <MAC 'Zy_private_YJWPHJ' [AN21]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 14 WPA2
    TELE2:           Infra, <MAC 'TELE2' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WEP
    KPN Fon:         Infra, <MAC 'KPN Fon' [AN23]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 7
    home1:           Infra, <MAC 'home1' [AC11]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Zy_private_7KEA34: Infra, <MAC 'Zy_private_7KEA34' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 15 WPA2
    DIRECT-HQ-BRAVIA:Infra, <MAC 'DIRECT-HQ-BRAVIA' [AN26]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2
    MAGDAANEL63:     Infra, <MAC 'MAGDAANEL63' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Sitecom2b689c:   Infra, <MAC 'Sitecom2b689c' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Adco:            Infra, <MAC 'Adco' [AN29]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 14 WPA
    Bzrk:            Infra, <MAC 'Bzrk' [AN30]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2
    Netwerk van Sterretje: Infra, <MAC 'Netwerk van Sterretje' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Top secret:      Infra, <MAC 'Top secret' [AN32]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    H220N23DCEA:     Infra, <MAC 'H220N23DCEA' [AN33]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    UPC244875841:    Infra, <MAC 'UPC244875841' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    UPC246085611:    Infra, <MAC 'UPC246085611' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2
    *HG655D-68E0B5:  Infra, <MAC 'HG655D-68E0B5' [AC1]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 71 WPA2
    UPC WifiSpots:   Infra, <MAC 'UPC WifiSpots' [AN37]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2 Enterprise
    UPC246568664:    Infra, <MAC 'UPC246568664' [AN38]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    H220N10A3C3:     Infra, <MAC 'H220N10A3C3' [AN39]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 9 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.66
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


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


[[/etc/NetworkManager/system-connections/HG655D-68E0B5]] (600 root)
[connection] id=HG655D-68E0B5 | type=802-11-wireless
[802-11-wireless] ssid=HG655D-68E0B5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HG655D-CC6E85]] (600 root)
[connection] id=HG655D-CC6E85 | type=802-11-wireless
[802-11-wireless] ssid=HG655D-CC6E85 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/H220N23C2D7]] (600 root)
[connection] id=H220N23C2D7 | type=802-11-wireless
[802-11-wireless] ssid=H220N23C2D7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Amsterdam (based on set time zone)


country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.447 GHz (Channel 8)


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      3   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HG655D-68E0B5' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"HG655D-68E0B5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015d2bde203
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Melissa' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:on
                    ESSID:"Melissa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000122ee106170
                    Extra: Last beacon: 1724ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'van.heuningen' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"van.heuningen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003252d5d6063
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'Thomson185D6C' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"Thomson185D6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012f9cc64865
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'theanatolian' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"theanatolian"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d6250ff2df
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'nasnien' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"nasnien"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000224abc9da7
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'KPN Fon' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003eef4da7b6a
                    Extra: Last beacon: 400ms ago
          Cell 08 - Address: <MAC 'VGV7519CD5C99' [AC8]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VGV7519CD5C99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007ac708c80e2
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'KPN Fon' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bc6694fd7
                    Extra: Last beacon: 60ms ago
          Cell 10 - Address: <MAC 'H220N23C2D7' [AC10]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"H220N23C2D7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bc66968a0
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'home1' [AC11]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"home1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000065ebeff00a
                    Extra: Last beacon: 1344ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'VGV7519712DC0' [AC12]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VGV7519712DC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003eef4da518e
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'HG655D-CC6E85' [AC13]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"HG655D-CC6E85"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00002773d146a46c
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'netwerk' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"netwerk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009bcae96f7e6
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'KPN Fon' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"KPN Fon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000009bcae9706c8
                    Extra: Last beacon: 60ms ago
          Cell 16 - Address: <MAC 'TELE2' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TELE2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ffe5d2b1a
                    Extra: Last beacon: 60ms ago
          Cell 17 - Address: <MAC 'UPC244875841' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"UPC244875841"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000009c5922e
                    Extra: Last beacon: 788ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Zy_private_7KEA34' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Zy_private_7KEA34"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006ba82c33e0a
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'VGV7519B2BD9F' [AC19]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"VGV7519B2BD9F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001480693073f
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Netwerk van Sterretje' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Netwerk van Sterretje"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a6a76d825
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'Ingrid' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Ingrid"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a6a76310c
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     661F5D1CDD236CFF7BE3FA5
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     94B3813AF84C49B115229AD
depends:        ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
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
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 6236.767369] IPv6: wlan0: IPv6 duplicate address fe80::52b7:c3ff:fe56:b007 detected!
[ 6843.191846] wlan0: deauthenticating from <MAC 'HG655D-68E0B5' [AC1]> by local choice (reason=3)
[ 6844.093985] wlan0: authenticate with <MAC 'HG655D-68E0B5' [AC1]>
[ 6844.119510] wlan0: send auth to <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6844.121501] wlan0: authenticated
[ 6844.124397] wlan0: associate with <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6844.128848] wlan0: RX AssocResp from <MAC 'HG655D-68E0B5' [AC1]> (capab=0x31 status=0 aid=3)
[ 6844.128895] wlan0: associated
[ 6844.132184] ath: EEPROM regdomain: 0x807c
[ 6844.132190] ath: EEPROM indicates we should expect a country code
[ 6844.132192] ath: doing EEPROM country->regdmn map search
[ 6844.132194] ath: country maps to regdmn code: 0x3a
[ 6844.132196] ath: Country alpha2 being used: CA
[ 6844.132198] ath: Regpair used: 0x3a
[ 6844.132201] ath: regdomain 0x807c dynamically updated by country IE
[ 6844.902784] wlan0: deauthenticating from <MAC 'HG655D-68E0B5' [AC1]> by local choice (reason=2)
[ 6844.912360] wlan0: authenticate with <MAC 'HG655D-68E0B5' [AC1]>
[ 6844.929584] wlan0: send auth to <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6844.931807] wlan0: authenticated
[ 6844.932254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 6844.932964] wlan0: associate with <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6844.937342] wlan0: RX AssocResp from <MAC 'HG655D-68E0B5' [AC1]> (capab=0x31 status=0 aid=3)
[ 6844.937373] wlan0: associated
[ 6844.937398] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6844.939847] ath: EEPROM regdomain: 0x807c
[ 6844.939853] ath: EEPROM indicates we should expect a country code
[ 6844.939855] ath: doing EEPROM country->regdmn map search
[ 6844.939856] ath: country maps to regdmn code: 0x3a
[ 6844.939857] ath: Country alpha2 being used: CA
[ 6844.939858] ath: Regpair used: 0x3a
[ 6844.939859] ath: regdomain 0x807c dynamically updated by country IE
[ 6845.542209] IPv6: wlan0: IPv6 duplicate address fe80::52b7:c3ff:fe56:b007 detected!
[ 6852.605113] wlan0: deauthenticating from <MAC 'HG655D-68E0B5' [AC1]> by local choice (reason=3)
[ 6853.509759] wlan0: authenticate with <MAC 'HG655D-68E0B5' [AC1]>
[ 6853.532683] wlan0: send auth to <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6853.534706] wlan0: authenticated
[ 6853.536291] wlan0: associate with <MAC 'HG655D-68E0B5' [AC1]> (try 1/3)
[ 6853.540714] wlan0: RX AssocResp from <MAC 'HG655D-68E0B5' [AC1]> (capab=0x31 status=0 aid=3)
[ 6853.540743] wlan0: associated
[ 6853.544470] ath: EEPROM regdomain: 0x807c
[ 6853.544473] ath: EEPROM indicates we should expect a country code
[ 6853.544475] ath: doing EEPROM country->regdmn map search
[ 6853.544476] ath: country maps to regdmn code: 0x3a
[ 6853.544477] ath: Country alpha2 being used: CA
[ 6853.544478] ath: Regpair used: 0x3a
[ 6853.544480] ath: regdomain 0x807c dynamically updated by country IE
[ 6854.369739] IPv6: wlan0: IPv6 duplicate address fe80::52b7:c3ff:fe56:b007 detected!


########## wireless info END ############

```

---

