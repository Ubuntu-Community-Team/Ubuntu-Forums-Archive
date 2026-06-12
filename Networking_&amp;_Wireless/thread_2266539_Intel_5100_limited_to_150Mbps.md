---
title: "Intel 5100 limited to 150Mbps"
date: 2015-02-23
forum: Networking &amp; Wireless
---

### Post by S4boteur on 2015-02-23
Hi Guys! 

I hope, you can help me. I have already read all the related threads in this forum, but couldn't find a solution. Here is my problem: 

Ubuntu can't connect to my router faster than 150Mbps, but my hardware (both computer and router) can do that with current configuration: I tested it on Windows 7, it says, the connection is 300Mbps. I tested with another speed test tool ([https://play.google.com/store/apps/details?id=com.pzolee.android.localwifispeedtester](https://play.google.com/store/apps/details?id=com.pzolee.android.localwifispeedtester)), which gave me the following results: 

Ubuntu: ~22Mbit/s
Windows 7: ~58Mbit/s

I already tried all the proposed solutions here in the forum, but nothing helped (iwlwifi.conf, grub edit to disable ipv6, etc.). I'm a bit desperate, I could use some valuable help from you. 

Configuration: 

Ubuntu 14.10 / Windows 7
Dell Studio XPS 1640 with Intel WIFI 5100
TP-LINK TL-WDR3600 N600 router, only on 5Ghz

```



########## wireless info START ##########


Report from: 23 Feb 2015 22:28 CET +0100


Booted last: 23 Feb 2015 22:21 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


##### kernel ############################


Linux 3.16.0-30-generic #40-Ubuntu SMP Mon Jan 12 22:06:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, ipv6.disable=1, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1321]
    Kernel driver in use: iwlwifi


08:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Dell Device [1028:0272]
    Kernel driver in use: tg3


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0458:0158 KYE Systems Corp. (Mouse Systems) 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ca:18a3 Ricoh Co., Ltd 
Bus 001 Device 002: ID 18a5:0237 Verbatim, Ltd Portable Harddrive (500 GB)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18227  0 
iwldvm                236430  0 
dcdbas                 14928  1 dell_laptop
mac80211              660592  1 iwldvm
iwlwifi               183038  1 iwldvm
cfg80211              510218  3 iwlwifi,mac80211,iwldvm
wmi                    19193  1 dell_wmi


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
          Interrupt:17 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.19.90  Bcast:192.168.19.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10080673 (10.0 MB)  TX bytes:1870255 (1.8 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"8&8 network_5Ghz"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=13 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:324   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.19.1    0.0.0.0         UG    0      0        0 wlan0
192.168.19.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [8&8 network_5Ghz] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    UPC0891807:      Infra, <MAC 'UPC0891807' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    nelopj:          Infra, <MAC 'nelopj' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2 Enterprise
    UPC1384723:      Infra, <MAC 'UPC1384723' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Maschinka:       Infra, <MAC 'Maschinka' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2 Enterprise
    Fresno:          Infra, <MAC 'Fresno' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    UPC1907593:      Infra, <MAC 'UPC1907593' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2 Enterprise
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2 Enterprise
    *8&8 network_5Ghz: Infra, <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    UPC1897930:      Infra, <MAC 'UPC1897930' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    FloViv:          Infra, <MAC 'FloViv' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA2
    cake:            Infra, <MAC 'cake' [AN15]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UPC2127708:      Infra, <MAC 'UPC2127708' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2 Enterprise
    OEH:             Infra, <MAC 'OEH' [AN19]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA2 Enterprise
    imi-mikroTik:    Infra, <MAC 'imi-mikroTik' [AN21]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    imi-vendeg:      Infra, <MAC 'imi-vendeg' [AN23]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Kate:            Infra, <MAC 'Kate' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    UPC640799:       Infra, <MAC 'UPC640799' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    CP.TP LINK 2:    Infra, <MAC 'CP.TP LINK 2' [AN26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    TSiganet:        Infra, <MAC 'TSiganet' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 Enterprise
    TKMP WIFI:       Infra, <MAC 'TKMP WIFI' [AN30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    UPC5276555:      Infra, <MAC 'UPC5276555' [AN32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN33]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    UPC Wi-Free:     Infra, <MAC 'UPC Wi-Free' [AN34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    My Network:      Infra, <MAC 'My Network' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2


  IPv4 Settings:
    Address:         192.168.19.90
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.19.1


    DNS:             192.168.19.1


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


[[/etc/NetworkManager/system-connections/2Videkhalo-kkfh-attilautca-M2AP1]] (600 root)
[connection] id=2Videkhalo-kkfh-attilautca-M2AP1 | type=802-11-wireless
[802-11-wireless] ssid=2Videkhalo-kkfh-attilautca-M2AP1 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CostaAndrassy]] (600 root)
[connection] id=CostaAndrassy | type=802-11-wireless
[802-11-wireless] ssid=CostaAndrassy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network]] (600 root)
[connection] id=8&8 network | type=802-11-wireless
[802-11-wireless] ssid=8&8 network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dd-wrt_vap]] (600 root)
[connection] id=dd-wrt_vap | type=802-11-wireless
[802-11-wireless] ssid=dd-wrt_vap | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Moto X]] (600 root)
[connection] id=Moto X | type=802-11-wireless
[802-11-wireless] ssid=Moto X | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_46A495]] (600 root)
[connection] id=TP-LINK_2.4GHz_46A495 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_2.4GHz_46A495 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_2.4GHz_88DEBE]] (600 root)
[connection] id=TP-LINK_2.4GHz_88DEBE | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_2.4GHz_88DEBE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/McDonalds-Free-WiFi]] (600 root)
[connection] id=McDonalds-Free-WiFi | type=802-11-wireless
[802-11-wireless] ssid=McDonalds-Free-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_2D707F]] (600 root)
[connection] id=TP-LINK_2D707F | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_2D707F | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/dd-wrt]] (600 root)
[connection] id=dd-wrt | type=802-11-wireless
[802-11-wireless] ssid=dd-wrt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/1. Wi-Fi kapcsolat]] (600 root)
[connection] id=1. Wi-Fi kapcsolat | type=802-11-wireless
[802-11-wireless] ssid=8&8 network 5Ghz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network 2]] (600 root)
[connection] id=8&8 network 2 | type=802-11-wireless
[802-11-wireless] ssid=8&8 network | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/8&8 network_5Ghz 1]] (600 root)
[connection] id=8&8 network_5Ghz 1 | type=802-11-wireless
[802-11-wireless] ssid=8&8 network_5Ghz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network_nappali_5Ghz]] (600 root)
[connection] id=8&8 network_nappali_5Ghz | type=802-11-wireless
[802-11-wireless] ssid=8&8 network_nappali_5Ghz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WLAN-780267]] (600 root)
[connection] id=WLAN-780267 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-780267 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network_nappali]] (600 root)
[connection] id=8&8 network_nappali | type=802-11-wireless
[802-11-wireless] ssid=8&8 network_nappali | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_5GHz_46A494]] (600 root)
[connection] id=TP-LINK_5GHz_46A494 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_5GHz_46A494 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/infomediator]] (600 root)
[connection] id=infomediator | type=802-11-wireless
[802-11-wireless] ssid=infomediator | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Szentjanosbogar_Guest]] (600 root)
[connection] id=Szentjanosbogar_Guest | type=802-11-wireless
[802-11-wireless] ssid=Szentjanosbogar_Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Discus--FDE27C]] (600 root)
[connection] id=Discus--FDE27C | type=802-11-wireless
[802-11-wireless] ssid=Discus--FDE27C | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network_5Ghz]] (600 root)
[connection] id=8&8 network_5Ghz | type=802-11-wireless
[802-11-wireless] ssid=8&8 network_5Ghz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_5GHz_88DEBF]] (600 root)
[connection] id=TP-LINK_5GHz_88DEBF | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_5GHz_88DEBF | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/8&8 network 1]] (600 root)
[connection] id=8&8 network 1 | type=802-11-wireless
[802-11-wireless] ssid=8&8 network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC0891807]] (600 root)
[connection] id=UPC0891807 | type=802-11-wireless
[802-11-wireless] ssid=UPC0891807 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/iroda]] (600 root)
[connection] id=iroda | type=802-11-wireless
[802-11-wireless] ssid=iroda | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Budapest (based on set time zone)


country HU: DFS-UNSET
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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
          Current Frequency:5.18 GHz (Channel 36)


##### iwlist scan #######################


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"8&8 network_5Ghz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010214753b6
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TSiganet' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TSiganet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a04acbfc6
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'nelopj' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"nelopj"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e57bd3704
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'UPC Wi-Free' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e57bd3fe7
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'UPC0891807' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"UPC0891807"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013ef2bc7ed
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Maschinka' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Maschinka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a8ab8c74fe
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC Wi-Free' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=32000013ef2bd845
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'UPC1839524' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UPC1839524"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001a4d83651af
                    Extra: Last beacon: 4696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Adam' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Adam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d1b9dcb180
                    Extra: Last beacon: 4692ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC1907593' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC1907593"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ab05681ea
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'UPC1384723' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"UPC1384723"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000047ccab1b68
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'UPC Wi-Free' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000047ccab3f03
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE:lo        Interface doesn't support scanning.


 Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 13 - Address: <MAC 'UPC Wi-Free' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ab0568bda
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'UPC640799' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UPC640799"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006e5f91021e
                    Extra: Last beacon: 4096ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
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
sig_key:        FD:44:85:1C:C6:75:0F:85:E8:F0:C2:C6:9B:12:82:63:F4:04:D5:E3
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
sig_key:        FD:44:85:1C:C6:75:0F:85:E8:F0:C2:C6:9B:12:82:63:F4:04:D5:E3
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
sig_key:        FD:44:85:1C:C6:75:0F:85:E8:F0:C2:C6:9B:12:82:63:F4:04:D5:E3
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
sig_key:        FD:44:85:1C:C6:75:0F:85:E8:F0:C2:C6:9B:12:82:63:F4:04:D5:E3
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
bt_coex_active: N
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 1
uapsd_disable: N
wd_disable: 1


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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
# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   91.928731] iwlwifi 0000:04:00.0: RF_KILL bit toggled to enable radio.
[   91.944315] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   91.947315] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   92.047230] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   92.050247] iwlwifi 0000:04:00.0: Radio type=0x1-0x2-0x0
[   95.430829] wlan0: authenticate with <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]>
[   95.435502] wlan0: send auth to <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]> (try 1/3)
[   95.526906] wlan0: authenticated
[   95.528045] wlan0: associate with <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]> (try 1/3)
[   95.529460] wlan0: RX AssocResp from <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]> (capab=0x411 status=0 aid=2)
[   95.533082] wlan0: associated
[   95.628161] wlan0: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC '8<MAC '8<MAC address>8 network_5Ghz' [AN12]>8 network_5Ghz' [AC1]>


########## wireless info END ############



```

---

### Post by tgalati4 on 2015-02-24
Make a hard mount in /etc/fstab and try your speed tests again.  Making a temporary mount in Nautilus is known to be slower than hard mounts.

---

### Post by S4boteur on 2015-02-25
Why would I mount a wireless card in fstab? This problem is not related to a hard drive or something other media.

---

### Post by jeremy31 on 2015-03-11
The usuall fix is ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
``` 
Reboot

---

### Post by S4boteur on 2015-03-13
This is going to disable N channels, isn't it? If yes, then this fix is not a fix: it will limit my speed to 54Mbps only, but now I have 150Mbps. I would like to achieve 300 Mbps.

---

### Post by jeremy31 on 2015-03-13
> **S4boteur said:**
> This is going to disable N channels, isn't it? If yes, then this fix is not a fix: it will limit my speed to 54Mbps only, but now I have 150Mbps. I would like to achieve 300 Mbps.

11n_disable=1 will disable N, 8 actually enables aggressive tx which should make it much faster than the default of 0
```
modinfo -p iwlwifi | grep 11n
```

---

### Post by S4boteur on 2015-03-24
What will happen with this? 5Ghz will be disabled, N too, and G will be faster than 54Mbps? Or this will change N mode to agressive TX?

---

### Post by jeremy31 on 2015-03-24
> **S4boteur said:**
> What will happen with this? 5Ghz will be disabled, N too, and G will be faster than 54Mbps? Or this will change N mode to agressive TX?

It should just change N mode to agg TX.   It should not disable 5 GHz or N mode

If you want to read a bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)

---

### Post by S4boteur on 2015-04-02
Thank you for your reply. I tried what you suggested, but sadly it did not solved the problem. It made the performance a little better, but could not compete Windows: 

Windows: 33-44 Mbit/s
Ubuntu: 28-31 Mbit/s. 

That is the top speed, and it is a shame that Ubuntu could not reach even the worst performance of Windows. Other things you could advise me? I want to use all the possibilities hardwares have, and I don't like compromises in basic functions like wireless performance.

---

### Post by tgalati4 on 2015-04-02
Use *iperf* to characterize your network throughput.  It's possible that you have a lot of wireless interference.  Use a wired ethernet cable and test those speeds first.

---

### Post by S4boteur on 2015-04-03
Wired connection has nothing to do here. I did the tests right after each other, nothing changed, excluding a reboot to another OS. I measured between the same 2 devices, using the same settings. I used the free wifi speed test application from the Google play store. Ubuntu is much slower.

---

