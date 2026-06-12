---
title: "A problem with my Wifi connection"
date: 2015-12-19
forum: Networking &amp; Wireless
---

### Post by amir20 on 2015-12-19
Hello there,

I have recently installed Ubuntu 14.04 on my Lenovo G50 laptop but unfortunately, I have faced an issue with the wifi connection. Usually after few minutes, it's disconnected or sometimes, although it's connected it doesn't respond; Moreover, the signal strength is not good enough while on Windows 8 I had faced neither of these issues....
I have read many threads here but I couldn't figure it out....
Here is the result of wifi script:
I wonder if you could take a look and help me out:
```



########## wireless info START ##########


Report from: 19 Dec 2015 12:37 EST -0500


Booted last: 19 Dec 2015 11:21 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-41-generic #46~14.04.2-Ubuntu SMP Tue Dec 8 17:46:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3821]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 13d3:5727 IMC Networks 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


iwlmvm                278528  0 
mac80211              708608  1 iwlmvm
iwlwifi               188416  1 iwlmvm
cfg80211              524288  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  0 
ideapad_laptop         24576  0 
sparse_keymap          16384  1 ideapad_laptop


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
          inet addr:192.168.2.45  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132637177 (132.6 MB)  TX bytes:7554483 (7.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"BELL406"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'BELL406' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:66   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       895     1  0 11:21 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [BELL406] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           48 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    BELL742:         Infra, <MAC 'BELL742' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    MARTIA:          Infra, <MAC 'MARTIA' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    BELL881:         Infra, <MAC 'BELL881' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA2
    TNCAP55707D:     Infra, <MAC 'TNCAP55707D' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA2
    BELL759:         Infra, <MAC 'BELL759' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2
    Altima-21519:    Infra, <MAC 'Altima-21519' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    VIDEOTRON2565:   Infra, <MAC 'VIDEOTRON2565' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    BELL742-5ghz:    Infra, <MAC 'BELL742-5ghz' [AC15]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 50 WPA2
    _____TPLink______: Infra, <MAC '_____TPLink______' [AC5]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA2
    BELL759:         Infra, <MAC 'BELL759' [AC16]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 47 WPA2
    BELL571:         Infra, <MAC 'BELL571' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    BELL293:         Infra, <MAC 'BELL293' [AC17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    VIDEOTRON7729:   Infra, <MAC 'VIDEOTRON7729' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    VIDEOTRON2565_media: Infra, <MAC 'VIDEOTRON2565_media' [AC14]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    NiNi:            Infra, <MAC 'NiNi' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    BELL317:         Infra, <MAC 'BELL317' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    BELL123:         Infra, <MAC 'BELL123' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    BELL687:         Infra, <MAC 'BELL687' [AN18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    VIDEOTRON0696:   Infra, <MAC 'VIDEOTRON0696' [AC6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    123:             Infra, <MAC '123' [AN20]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    VIDEOTRON0218:   Infra, <MAC 'VIDEOTRON0218' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BELL792:         Infra, <MAC 'BELL792' [AN22]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BELL437:         Infra, <MAC 'BELL437' [AN23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    BELL813:         Infra, <MAC 'BELL813' [AN24]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    abeta:           Infra, <MAC 'abeta' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 39 WPA
    VIDEOTRON2462:   Infra, <MAC 'VIDEOTRON2462' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BELL831:         Infra, <MAC 'BELL831' [AN27]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    BELL984:         Infra, <MAC 'BELL984' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    BELL844:         Infra, <MAC 'BELL844' [AN29]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    VIDEOTRON4458:   Infra, <MAC 'VIDEOTRON4458' [AN30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    VM Guests:       Infra, <MAC 'VM Guests' [AN31]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    VM Admin:        Infra, <MAC 'VM Admin' [AN32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    BELL277:         Infra, <MAC 'BELL277' [AN33]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Garen&Meghrig:   Infra, <MAC 'Garen<MAC address>Meghrig' [AN34]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    jolly:           Infra, <MAC 'jolly' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    VIDEOTRON5956:   Infra, <MAC 'VIDEOTRON5956' [AN36]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Can't see me:    Infra, <MAC 'Can't see me' [AN37]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA2
    BELL550:         Infra, <MAC 'BELL550' [AN38]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    BELL309:         Infra, <MAC 'BELL309' [AN39]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA2
    BELL248:         Infra, <MAC 'BELL248' [AN40]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    CharlesAirbnb:   Infra, <MAC 'CharlesAirbnb' [AN41]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Ali's Wi-Fi Network: Infra, <MAC 'Ali's Wi-Fi Network' [AN42]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BELL040:         Infra, <MAC 'BELL040' [AN43]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA2
    VIDEOTRON9124:   Infra, <MAC 'VIDEOTRON9124' [AN44]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    dlink-9796:      Infra, <MAC 'dlink-9796' [AN45]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    VM Guests:       Infra, <MAC 'VM Guests' [AN46]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    AltimaTelecom-102402: Infra, <MAC 'AltimaTelecom-102402' [AN47]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    toidus_net:      Infra, <MAC 'toidus_net' [AN48]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WEP
    *BELL406:        Infra, <MAC 'BELL406' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA2
    BELL310:         Infra, <MAC 'BELL310' [AN50]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA2
    BELL844-V:       Infra, <MAC 'BELL844-V' [AN51]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Bob-Bob-Guest:   Infra, <MAC 'Bob-Bob-Guest' [AN52]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 20 WPA2
    BELL277:         Infra, <MAC 'BELL277' [AN53]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 20 WPA2


  IPv4 Settings:
    Address:         192.168.2.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


[[/etc/NetworkManager/system-connections/BELL406]] (600 root)
[connection] id=BELL406 | type=802-11-wireless
[802-11-wireless] ssid=BELL406 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Montreal (based on set time zone)


country CA:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)


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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.805 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BELL406' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"BELL406"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b8fdca87
                    Extra: Last beacon: 104088ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TNCAP55707D' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TNCAP55707D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BELL881' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"BELL881"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000033383bec40
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Altima-21519' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Altima-21519"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003418a3d4d37
                    Extra: Last beacon: 21452ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '_____TPLink______' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"_____TPLink______"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000da33eb9f9
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VIDEOTRON0696' [AC6]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON0696"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000ea182180
                    Extra: Last beacon: 24708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VIDEOTRON2462' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON2462"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000383817d85
                    Extra: Last beacon: 24696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'abeta' [AC8]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"abeta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000011aa7f7d80
                    Extra: Last beacon: 24692ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'NiNi' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NiNi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009d33c9cee
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'BELL759' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"BELL759"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000020f25ce
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'BELL742' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"BELL742"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017f472a5b7
                    Extra: Last beacon: 3240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'VIDEOTRON2565' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON2565"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000948809c
                    Extra: Last beacon: 21452ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'MARTIA' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"MARTIA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009f73edd9f
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'VIDEOTRON2565_media' [AC14]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON2565_media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000041c2c09b62f
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'BELL742-5ghz' [AC15]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BELL742-5ghz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000079318cd848
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'BELL759' [AC16]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BELL759"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000007b69bf4adca
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'BELL293' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BELL293"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001d6808042
                    Extra: Last beacon: 3400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'VIDEOTRON7729' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON7729"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002fa1873cf
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'APT.160008' [AC19]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"APT.160008"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b9923d1ae
                    Extra: Last beacon: 3200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.19.0-41-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4375FD8600770B0C2A7E11D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9F:CD:AF:5C:8B:8B:CC:67:97:46:89:5C:4A:DA:36:25:A8:42:23:FD
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.19.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9F:CD:AF:5C:8B:8B:CC:67:97:46:89:5C:4A:DA:36:25:A8:42:23:FD
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-41-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B470AF663F8CCFC606AA966
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9F:CD:AF:5C:8B:8B:CC:67:97:46:89:5C:4A:DA:36:25:A8:42:23:FD
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


[cfg80211]
filename:       /lib/modules/3.19.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9F:CD:AF:5C:8B:8B:CC:67:97:46:89:5C:4A:DA:36:25:A8:42:23:FD
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
uapsd_disable: Y
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 3905.059164] wlan0: deauthenticating from <MAC 'BELL406' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3910.263565] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 3910.268093] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 3910.272796] wlan0: authenticated
[ 3910.273552] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 3910.277985] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=2)
[ 3910.279167] wlan0: associated
[ 4362.903735] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 4362.932603] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4369.272107] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 4369.278622] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 4369.282531] wlan0: authenticated
[ 4369.286308] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 4369.291730] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=2)
[ 4369.293204] wlan0: associated
[ 4369.293234] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4369.335020] wlan0: deauthenticating from <MAC 'BELL406' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 4369.351463] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 4369.356143] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 4369.376101] wlan0: authenticated
[ 4369.378440] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 4369.384758] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=2)
[ 4369.386697] wlan0: associated


########## wireless info END ############



```

---

### Post by Hadaka on 2015-12-19
Hi,please open a terminal then COPY and paste one line at a time.
```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
echo "blacklist ideapad-laptop" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
then do..
```
sudo ifconfig wlan0 down
sudo modprobe -r iwldvm
sudo modprobe -r iwlwifi
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
echo "options mac80211 probe_wait_ms=1000" | sudo tee -a /etc/modprobe.d/mac80211.conf
sudo modprobe -v iwlwifi
```
thanks.

---

### Post by amir20 on 2015-12-19
Dear Hadaka,

Thank you so much for your help.... It works like a charm!

---

### Post by Hadaka on 2015-12-19
Great! Please take the time to log back in to your thread,
first post,in the upper right area click TOOLS and then choose SOLVED
thanks.

---

### Post by amir20 on 2015-12-19
Well, unfortunately it happened again! Seemingly it's still unstable, but the duration between being disconnected increased....
Any idea?!

Thanks

---

### Post by Hadaka on 2015-12-19
Hi, please run the wireless script file again.
thanks.

---

### Post by amir20 on 2015-12-19
Here you are:
```



########## wireless info START ##########


Report from: 19 Dec 2015 16:57 EST -0500


Booted last: 19 Dec 2015 14:39 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.19.0-42-generic #48~14.04.1-Ubuntu SMP Fri Dec 18 10:24:49 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: Lenovo Device [17aa:3821]
	Kernel driver in use: r8169


03:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 13d3:5727 IMC Networks 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no


##### lsmod #############################


iwlmvm                278528  0 
mac80211              708608  1 iwlmvm
iwlwifi               188416  1 iwlmvm
cfg80211              524288  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  0 


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
          inet addr:192.168.2.45  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:106583039 (106.5 MB)  TX bytes:7197281 (7.1 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"BELL406"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'BELL406' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:635   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root       838     1  0 14:39 ?        00:00:03 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [BELL406] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           12 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MARTIA:          Infra, <MAC 'MARTIA' [AN1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WPA2
    BELL881:         Infra, <MAC 'BELL881' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA2
    TNCAP55707D:     Infra, <MAC 'TNCAP55707D' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    BELL310:         Infra, <MAC 'BELL310' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2
    Altima-21519:    Infra, <MAC 'Altima-21519' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    VIDEOTRON2565:   Infra, <MAC 'VIDEOTRON2565' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    _____TPLink______: Infra, <MAC '_____TPLink______' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA2
    BELL742-5ghz:    Infra, <MAC 'BELL742-5ghz' [AC13]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 50 WPA2
    VIDEOTRON2565_media: Infra, <MAC 'VIDEOTRON2565_media' [AC11]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BELL759:         Infra, <MAC 'BELL759' [AC14]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 40 WPA2
    *BELL406:        Infra, <MAC 'BELL406' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    NiNi:            Infra, <MAC 'NiNi' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA
    BELL687:         Infra, <MAC 'BELL687' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    BELL571:         Infra, <MAC 'BELL571' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA2
    BELL742:         Infra, <MAC 'BELL742' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2
    123:             Infra, <MAC '123' [AN16]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    BELL984:         Infra, <MAC 'BELL984' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    APT.160008:      Infra, <MAC 'APT.160008' [AN18]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    dlink-E8C8:      Infra, <MAC 'dlink-E8C8' [AC10]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    BELL293:         Infra, <MAC 'BELL293' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    BELL518:         Infra, <MAC 'BELL518' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2


  IPv4 Settings:
    Address:         192.168.2.45
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1


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


[[/etc/NetworkManager/system-connections/BELL406]] (600 root)
[connection] id=BELL406 | type=802-11-wireless
[802-11-wireless] ssid=BELL406 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Montreal (based on set time zone)


country CA:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)


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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.805 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'BELL406' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"BELL406"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000055b6b27c1
                    Extra: Last beacon: 71448ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Altima-21519' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Altima-21519"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003452bf9011f
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '_____TPLink______' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"_____TPLink______"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001143b3bf2e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BELL742' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"BELL742"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002a7034c
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'VIDEOTRON7729' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON7729"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000046cec55b
                    Extra: Last beacon: 3624ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'BELL759' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"BELL759"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000b2a4b3
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VIDEOTRON4458' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON4458"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000212755fa0d
                    Extra: Last beacon: 3616ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NiNi' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"NiNi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002a4649dc
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Can't see me' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Can't see me"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000053a0647180
                    Extra: Last beacon: 3508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'dlink-E8C8' [AC10]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"dlink-E8C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000060881753b1
                    Extra: Last beacon: 3500ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: <MAC 'VIDEOTRON2565_media' [AC11]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON2565_media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000041fcc7dc13e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'VIDEOTRON2565' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON2565"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000052ad9dbe
                    Extra: Last beacon: 3436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'BELL742-5ghz' [AC13]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"BELL742-5ghz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007cd20037a1
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'BELL759' [AC14]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"BELL759"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4375FD8600770B0C2A7E11D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     47672A7084D52DFBE51E2D2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-42-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     B470AF663F8CCFC606AA966
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
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


[cfg80211]
filename:       /lib/modules/3.19.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-42-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        75:9B:CD:64:55:A9:DF:AB:A6:11:14:85:D0:4E:DE:D5:3A:B8:31:50
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 1000


[iwlwifi]
11n_disable: 8
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
blacklist ideapad-laptop


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
options iwlwifi 11n_disable=8


[/etc/modprobe.d/mac80211.conf]
options mac80211 probe_wait_ms=1000


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 6303.955951] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 6303.961662] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 6304.135732] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 2/3)
[ 6304.212048] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 3/3)
[ 6304.300171] wlan0: authentication with <MAC 'BELL406' [AC1]> timed out
[ 6307.859799] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 6307.865213] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 6307.868621] wlan0: authenticated
[ 6307.871219] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 6307.885331] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=3)
[ 6307.885833] wlan0: associated
[ 6910.335229] wlan0: AP <MAC 'BELL406' [AC1]> changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[ 6995.414136] r8169 0000:02:00.0 eth0: link down
[ 6995.414189] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 6995.415297] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[ 6995.441669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7001.976823] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 7001.983681] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 7001.991689] wlan0: authenticated
[ 7001.994498] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 7002.002434] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=3)
[ 7002.006092] wlan0: associated
[ 7002.006120] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7002.030437] wlan0: deauthenticating from <MAC 'BELL406' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 7002.043542] wlan0: authenticate with <MAC 'BELL406' [AC1]>
[ 7002.049085] wlan0: send auth to <MAC 'BELL406' [AC1]> (try 1/3)
[ 7002.053855] wlan0: authenticated
[ 7002.054748] wlan0: associate with <MAC 'BELL406' [AC1]> (try 1/3)
[ 7002.059229] wlan0: RX AssocResp from <MAC 'BELL406' [AC1]> (capab=0x431 status=0 aid=3)
[ 7002.060232] wlan0: associated


########## wireless info END ############



```

---

### Post by Hadaka on 2015-12-19
Hi,looks like power management somehow got turned on..
```
wlan0     IEEE 802.11abgn  ESSID:"[COLOR=#ff0000]BELL406[/COLOR]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'BELL406' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR=#ff0000]on[/COLOR]
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:635   Missed beacon:0
```
*It was off in your first wireless-info.txt printout.
Try this to turn it off,unless you are already running some file.
```
http://ubuntuforums.org/showthread.php?t=1686641
post #2
```

There are several ssid's in your report that are "BELLXXX" so you are most likely roaming from AP to AP
BELL406 seems to be the strongest signal for you,. Take note of "BELL406's" MAC ADDRESS *
you can put the mac adress of BELL406 in the BSSID feild to help with the roaming and cutoffs *See attached..
[ATTACH=CONFIG]266269[/ATTACH][ATTACH=CONFIG]266270[/ATTACH][ATTACH=CONFIG]266271[/ATTACH]
[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]
insert your data of course..

---

### Post by amir20 on 2015-12-19
Thank you so much for your help.... :)

---

### Post by Hadaka on 2015-12-19
Glad you are up and running !!

---

