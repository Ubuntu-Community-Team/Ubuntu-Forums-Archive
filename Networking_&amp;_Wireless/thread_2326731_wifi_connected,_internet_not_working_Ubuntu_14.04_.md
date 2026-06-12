---
title: "wifi connected, internet not working Ubuntu 14.04 LTS"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by pushp2 on 2016-06-04
Here is the info . I read many forums. but didn't get through it.
```
########## wireless info START ##########

Report from: 04 Jun 2016 11:23 IST +0530


Booted last: 04 Jun 2016 00:00 IST +0530


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-59-generic #66~14.04.1-Ubuntu SMP Fri May 13 17:27:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2247]
    Kernel driver in use: r8169


09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b466 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 138a:003f Validity Sensors, Inc. VFS495 Fingerprint Reader
Bus 001 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 052: ID 22b8:2e24 Motorola PCS 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
29: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              720896  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              532480  2 mac80211,rtlwifi
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1831880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:632695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:432953796 (432.9 MB)  TX bytes:281340146 (281.3 MB)


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF2]>  
          inet addr:192.168.42.248  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'usb0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7063 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4750402 (4.7 MB)  TX bytes:1421939 (1.4 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF3]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF3]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28424 errors:0 dropped:1 overruns:0 frame:0
          TX packets:4142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5613587 (5.6 MB)  TX bytes:823531 (823.5 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       814     1  0 May28 ?        00:00:53 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF2]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.248
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF3]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    Mr basu:         Infra, <MAC 'Mr basu' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA
    Get Yours:       Infra, <MAC 'Get Yours' [AC6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 50 WPA
    Airtel_Zerotouch:Infra, <MAC 'Airtel_Zerotouch' [AC4]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 70 WPA
    Dagars:          Infra, <MAC 'Dagars' [AC14]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Glen:            Infra, <MAC 'Glen' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60 WPA
    TCC:             Infra, <MAC 'TCC' [AC16]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WEP
    MGMNT:           Infra, <MAC 'MGMNT' [AC5]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54 WEP
    TomCat:          Infra, <MAC 'TomCat' [AC9]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 40 WPA
    cz:              Infra, <MAC 'cz' [AC12]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 44
    Disconnected:    Infra, <MAC 'Disconnected' [AN10]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 40 WPA
    om@axe:          Infra, <MAC 'om@axe' [AC7]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 64 WEP
    OnidaAirCon-S183SMHW-796D: Infra, <MAC 'OnidaAirCon-S183SMHW-796D' [AC15]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WPA2
    RCTIWARI:        Infra, <MAC 'RCTIWARI' [AN13]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Abhishek:        Infra, <MAC 'Abhishek' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA
    srikanth:        Infra, <MAC 'srikanth' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA
    NETGEAR:         Infra, <MAC 'NETGEAR' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    fpmpl:           Infra, <MAC 'fpmpl' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    Aditya:          Infra, <MAC 'Aditya' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA
    utility:         Infra, <MAC 'utility' [AC2]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 54 WPA
    divam:           Infra, <MAC 'divam' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Sk dhiman:       Infra, <MAC 'Sk dhiman' [AC19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    usha mehta:      Infra, <MAC 'usha mehta' [AC10]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Abhijeet:        Infra, <MAC 'Abhijeet' [AC13]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA
    Dheer:           Infra, <MAC 'Dheer' [AN24]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 24 WPA
    MGMNT:           Infra, <MAC 'MGMNT' [AC20]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WEP
    XT1068 4214:     Infra, <MAC 'XT1068 4214' [AN26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Airtel_Zerotouch:Infra, <MAC 'Airtel_Zerotouch:Infra, <MAC address>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA' [AN27]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA
    WORLDWEB2:       Infra, <MAC 'WORLDWEB2' [AN28]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Abco:            Infra, <MAC 'Abco' [AN29]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA
    AKG:             Infra, <MAC 'AKG' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


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


[[/etc/NetworkManager/system-connections/CEO WiFi]] (600 root)
[connection] id=CEO WiFi | type=802-11-wireless
[802-11-wireless] ssid=CEO WiFi | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Apple]] (600 root)
[connection] id=Apple | type=802-11-wireless
[802-11-wireless] ssid=Apple | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FreeWiFi_Ozone@HaldiRam]] (600 root)
[connection] id=FreeWiFi_Ozone@HaldiRam | type=802-11-wireless
[802-11-wireless] ssid=FreeWiFi_Ozone@HaldiRam | mac-address=<MAC 'wlan0' [IF3]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Abhijeet]] (600 root)
[connection] id=Abhijeet | type=802-11-wireless
[802-11-wireless] ssid=Abhijeet | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WORK_HARD_DREAM_BIG]] (600 root)
[connection] id=WORK_HARD_DREAM_BIG | type=802-11-wireless
[802-11-wireless] ssid=WORK_HARD_DREAM_BIG | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/A9F1BDF1DAB1NVT4F4F59]] (600 root)
[connection] id=A9F1BDF1DAB1NVT4F4F59 | type=802-11-wireless
[802-11-wireless] ssid=A9F1BDF1DAB1NVT4F4F59 | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Reliance Wi-Pod MF802s B897]] (600 root)
[connection] id=Reliance Wi-Pod MF802s B897 | type=802-11-wireless
[802-11-wireless] ssid=Reliance Wi-Pod MF802s B897 | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF3]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


usb0      no frequency information.


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


eth0      Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.442 GHz (Channel 7)
      4   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Glen' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Glen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000385cdd530
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'utility' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"utility"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000035d0eabb4
                    Extra: Last beacon: 584ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Mr basu' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Mr basu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000383d6fcd8
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Airtel_Zerotouch' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Airtel_Zerotouch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003911bee7c
                    Extra: Last beacon: 244ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'MGMNT' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"MGMNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000071b3fbe4b9
                    Extra: Last beacon: 528ms ago
          Cell 06 - Address: <MAC 'Get Yours' [AC6]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Get Yours"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003854fc35e
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'om@axe' [AC7]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"om@axe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021d588a3182
                    Extra: Last beacon: 500ms ago
          Cell 08 - Address: <MAC 'Abhishek' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Abhishek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000387421d8d
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'TomCat' [AC9]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TomCat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000071b7304fe5
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'usha mehta' [AC10]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"usha mehta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000385bee173
                    Extra: Last beacon: 404ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'divam' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"divam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000397b5f5ba
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'cz' [AC12]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"cz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c7cde9182
                    Extra: Last beacon: 636ms ago
          Cell 13 - Address: <MAC 'Abhijeet' [AC13]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Abhijeet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003873cfae0
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Dagars' [AC14]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Dagars"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000039834e059
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'OnidaAirCon-S183SMHW-796D' [AC15]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"OnidaAirCon-S183SMHW-796D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000083534dd1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'TCC' [AC16]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000384b22187
                    Extra: Last beacon: 224ms ago
          Cell 17 - Address: <MAC 'joubles' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"joubles"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000384cb217c
                    Extra: Last beacon: 816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Lonewolf' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Lonewolf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000396182560
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'Sk dhiman' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Sk dhiman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003842c6af5
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'MGMNT' [AC20]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"MGMNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000385bbe4cd
                    Extra: Last beacon: 8ms ago
          Cell 21 - Address: <MAC 'DIRECT-tr-BRAVIA' [AC21]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-tr-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000012cc4f587
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'om namah shivay' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"om namah shivay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000396a2517c
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'vansh' [AC23]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"vansh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000038438ad5c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.19.0-59-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     FD5F7EDF9AE76221964BF9F
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl8723_common]
filename:       /lib/modules/3.19.0-59-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512


[rtl_pci]
filename:       /lib/modules/3.19.0-59-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     672803C0A81F3F01DD7EB68
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.19.0-59-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A1851295567B306D1C939BC
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46EBD6732E992614FD7F01B
depends:        
intree:         Y
vermagic:       3.19.0-59-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4B:9C:14:B4:D8:0B:60:0F:64:15:32:4B:C3:65:0C:9B:DF:E6:E5:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N


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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF3]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[221018.175987] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221031.161020] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221035.210497] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221048.197976] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221052.226573] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221098.321301] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221102.281322] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221115.269169] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221119.312570] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221160.190419] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221164.338387] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221237.045622] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221241.390705] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221254.383846] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221258.420375] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221308.795867] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221312.485390] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221325.582483] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221329.525772] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221347.554195] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221351.511541] rndis_host 1-1:1.0 eth1: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC address>
[221360.915799] rndis_host 1-1:1.0 eth1: unregister 'rndis_host' usb-0000:00:14.0-1, RNDIS device
[221382.391849] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:00:14.0-1, RNDIS device, <MAC 'usb0' [IF2]>


########## wireless info END ############
```

---

### Post by howefield on 2016-06-04
Thread moved to the "*Networking & Wireless*" forum.

---

### Post by Hadaka on 2016-06-04
Hi, first remove the usb wifi module, then from a working wired connection.
Please COPY and paste one line at a time..
```
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
```
then do..
```
sudo apt-get install linux-headers-generic git dkms build-essential
rm -rf rtlwifi_new
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms build -m rtlwifi-new -v 0.6
sudo dkms install -m rtlwifi-new -v 0.6
```
remove wired connection,boot and test wireless.
thanks.

---

### Post by pushp2 on 2016-06-04
Thanks Hadaka. Problem solved. Its working like charm. I was struggling with this problem since last three months.
BTW, can you please breif, what was the problem? If you want.

---

### Post by Hadaka on 2016-06-04
Great ! glad it is working. Your wifi card rtl8723be has the ability to select  2
different antenna connections in software. Thanks to ubuntu member jeremy31
for providing the forum with the latest larry finger version of the rtl8723be driver
that i simply passed on to you. So what we did was set your country code to the
correct country then we deleted your old driver and inserted the latest rtl8723be
driver that selects the correct antenna. Thank you for marking your thread solved.

---

### Post by pushp2 on 2016-06-05
Once again Thank you Hadaka for explaining the thing.

---

