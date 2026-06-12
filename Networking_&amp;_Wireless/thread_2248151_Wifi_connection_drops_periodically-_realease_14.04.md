---
title: "Wifi connection drops periodically- realease 14.04 (Intel centrino wireless N-1000)"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by apoorvmunshi on 2014-10-12
I have already installed the required firmware version for this wireless card but the wifi connection keeps dropping periodically. I think the firmware need debugging. Help please. You all know how annoying it is not to have a stable wifi connection.

---

### Post by Vladlenin5000 on 2014-10-12
Please read the stickies before posting: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
Please follow the instruction there for fully updating your system and if the symptom persists then follow the next instructions on to download, run and post the results of the wireless_script. Thank you.

---

### Post by apoorvmunshi on 2014-10-12
Hi. Sorry I didn't read the the stickies first. I have gone through many threads but could not find a solution. I am posting the result  of the script. Please help me.

```



########## wireless info START ##########


Report from: 12 Oct 2014 22:58 EDT -0400


Booted last: 12 Oct 2014 22:47 EDT -0400


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


12:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1325]
    Kernel driver in use: iwlwifi


13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 005: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 002 Device 004: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
mac80211              630653  1 iwldvm
dell_wmi               12761  0 
iwlwifi               169932  1 iwldvm
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wmi                    19177  1 dell_wmi
cfg80211              484040  3 iwlwifi,mac80211,iwldvm


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


vmnet1    Link encap:Ethernet  HWaddr <MAC 'vmnet1' [IF]>  
          inet addr:192.168.203.1  Bcast:192.168.203.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr <MAC 'vmnet8' [IF]>  
          inet addr:172.16.253.1  Bcast:172.16.253.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.14  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8ea9:82ff:fe21:e1fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2275471 (2.2 MB)  TX bytes:1255908 (1.2 MB)


##### iwconfig ##########################


vmnet8    no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


vmnet1    no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Apt_17B"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Apt_17B' [AC1]>   
          Bit Rate=6.5 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:349  Invalid misc:88   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
172.16.253.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.203.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1


##### resolv.conf #######################


nameserver 127.0.1.1


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


- Device: wlan0  [Apt_17B] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           14 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    HOME--5249-2.4:  Infra, <MAC 'HOME--5249-2.4' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    on the rocks:    Infra, <MAC 'on the rocks' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    15b:             Infra, <MAC '15b' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    Vicki:           Infra, <MAC 'Vicki' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    The Boss:        Infra, <MAC 'The Boss' [AN5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    RedSox14b:       Infra, <MAC 'RedSox14b' [AC19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Cool wifi:       Infra, <MAC 'Cool wifi' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    ROSA R:          Infra, <MAC 'ROSA R' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Cisco10299:      Infra, <MAC 'Cisco10299' [AC15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    NETRARR:         Infra, <MAC 'NETRARR' [AN10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 29 WPA
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    RAINMAN:         Infra, <MAC 'RAINMAN' [AN12]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    CLEARSpot4E4D8:  Infra, <MAC 'CLEARSpot4E4D8' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    desiboys15c:     Infra, <MAC 'desiboys15c' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    belkin.672:      Infra, <MAC 'belkin.672' [AC24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Blanquita:       Infra, <MAC 'Blanquita' [AC18]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    KT_WLAN_638D:    Infra, <MAC 'KT_WLAN_638D' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    HOMEOFAWESOMEPEOPLE: Infra, <MAC 'HOMEOFAWESOMEPEOPLE' [AC21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    HOME-29F2:       Infra, <MAC 'HOME-29F2' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    partyhouse:      Infra, <MAC 'partyhouse' [AN22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    monkey:          Infra, <MAC 'monkey' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    12 B Smith:      Infra, <MAC '12 B Smith' [AN24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    bakchod:         Infra, <MAC 'bakchod' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Aalishan 3BHK:   Infra, <MAC 'Aalishan 3BHK' [AN26]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 22 WPA2
    COMMAND CENTER:  Infra, <MAC 'COMMAND CENTER' [AC10]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    COMMAND CENTER-guest: Infra, <MAC 'COMMAND CENTER-guest' [AN28]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 30
    *Apt_17B:        Infra, <MAC 'Apt_17B' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    RobertReeves-2.4:Infra, <MAC 'RobertReeves-2.4' [AN31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Chloe&Emily:     Infra, <MAC 'Chloe<MAC 'Chloe<MAC address>Emily' [AN32]>Emily' [AC9]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    dudeism:         Infra, <MAC 'dudeism' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    VellailliaPatathari: Infra, <MAC 'VellailliaPatathari' [AC20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    SheelaKiJawani:  Infra, <MAC 'SheelaKiJawani' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    HOME-C5F2:       Infra, <MAC 'HOME-C5F2' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    MassArt:         Infra, <MAC 'MassArt' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25


  IPv4 Settings:
    Address:         192.168.1.14
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


[[/etc/NetworkManager/system-connections/NUwave]] (600 root)
[ipv6] method=auto
[connection] id=NUwave | type=802-11-wireless
[802-11-wireless] ssid=NUwave | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/usr/share/ca-certificates/mozilla/AddTrust_External_Root.crt
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Apt_17B]] (600 root)
[connection] id=Apt_17B | type=802-11-wireless
[802-11-wireless] ssid=Apt_17B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


vmnet8    no frequency information.


eth0      no frequency information.


lo        no frequency information.


vmnet1    no frequency information.


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      9   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      8   APs on   Frequency:2.462 GHz (Channel 11)


vmnet8    Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Apt_17B' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Apt_17B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001da490744
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '15b' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"15b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b9e7ff4b2
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'desiboys15c' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"desiboys15c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005a752cf9a
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'on the rocks' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"on the rocks"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000a4edfca
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'MassArt' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"MassArt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dd49588178
                    Extra: Last beacon: 21380ms ago
          Cell 06 - Address: <MAC 'HOME-C5F2' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HOME-C5F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ec22472184
                    Extra: Last beacon: 21372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ec22472a52
                    Extra: Last beacon: 21372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'KT_WLAN_638D' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"KT_WLAN_638D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000439419f
                    Extra: Last beacon: 21364ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Chloe<MAC 'Chloe<MAC address>Emily' [AN32]>Emily' [AC9]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Chloe&Emily"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000384e945f
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'COMMAND CENTER' [AC10]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"COMMAND CENTER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004534f18920
                    Extra: Last beacon: 21320ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HOME--5249-2.4' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"HOME--5249-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000112f4f24981
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'ROSA R' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ROSA R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003dc147653
                    Extra: Last beacon: 992ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'dudeism' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"dudeism"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000038806227
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC '' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000066f2c01dc02
                    Extra: Last beacon: 21068ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Cisco10299' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Cisco10299"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000044f9e5af55
                    Extra: Last beacon: 816ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Vicki' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Vicki"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f27ebb5bc
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'Cool wifi' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Cool wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001af4384f0d
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Blanquita' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Blanquita"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001adc861bc94
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'RedSox14b' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"RedSox14b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003436b9fa5c0
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'VellailliaPatathari' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"VellailliaPatathari"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f8a564a650
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'HOMEOFAWESOMEPEOPLE' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"HOMEOFAWESOMEPEOPLE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000066f2d341bc3
                    Extra: Last beacon: 996ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC '' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000162813a32b
                    Extra: Last beacon: 796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'xfinitywifi' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000162813b0e0
                    Extra: Last beacon: 0ms ago
          Cell 24 - Address: <MAC 'belkin.672' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"belkin.672"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c082aa4a
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'xfinitywifi' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bc8d052b0
                    Extra: Last beacon: 624ms ago
  vmnet1    Interface doesn't support scanning.


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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


[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        2C:B1:13:3B:35:F9:5A:9E:24:DE:AB:EE:B1:2B:A4:49:BC:BA:BB:C9
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
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0083 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  648.289612] iwlwifi 0000:12:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289675] iwlwifi 0000:12:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289748] iwlwifi 0000:12:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289807] iwlwifi 0000:12:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289865] iwlwifi 0000:12:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289924] iwlwifi 0000:12:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  648.289982] iwlwifi 0000:12:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.296747] iwlwifi 0000:12:00.0: fail to flush all tx fifo queues Q 2
[  650.296760] iwlwifi 0000:12:00.0: Current SW read_ptr 247 write_ptr 139
[  650.296794] iwl data: 00000000: 7f 00 00 00 00 00 00 00 00 00 80 ff 00 00 00 00  ................
[  650.296812] iwlwifi 0000:12:00.0: FH TRBs(0) = 0x00000000
[  650.296829] iwlwifi 0000:12:00.0: FH TRBs(1) = 0x80102006
[  650.296845] iwlwifi 0000:12:00.0: FH TRBs(2) = 0x00000000
[  650.296862] iwlwifi 0000:12:00.0: FH TRBs(3) = 0x80300094
[  650.296878] iwlwifi 0000:12:00.0: FH TRBs(4) = 0x00000000
[  650.296894] iwlwifi 0000:12:00.0: FH TRBs(5) = 0x00000000
[  650.296911] iwlwifi 0000:12:00.0: FH TRBs(6) = 0x00000000
[  650.296927] iwlwifi 0000:12:00.0: FH TRBs(7) = 0x0070409d
[  650.296989] iwlwifi 0000:12:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [149,149]
[  650.297099] iwlwifi 0000:12:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  650.297160] iwlwifi 0000:12:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [247,139]
[  650.297221] iwlwifi 0000:12:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297282] iwlwifi 0000:12:00.0: Q 4 is active and mapped to fifo 7 ra_tid 0x0000 [158,158]
[  650.297343] iwlwifi 0000:12:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297405] iwlwifi 0000:12:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297466] iwlwifi 0000:12:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297527] iwlwifi 0000:12:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297588] iwlwifi 0000:12:00.0: Q 9 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297649] iwlwifi 0000:12:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297710] iwlwifi 0000:12:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297771] iwlwifi 0000:12:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297833] iwlwifi 0000:12:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297894] iwlwifi 0000:12:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.297955] iwlwifi 0000:12:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.298016] iwlwifi 0000:12:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.298077] iwlwifi 0000:12:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.298139] iwlwifi 0000:12:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  650.298199] iwlwifi 0000:12:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265054] iwlwifi 0000:12:00.0: fail to flush all tx fifo queues Q 2
[  653.265064] iwlwifi 0000:12:00.0: Current SW read_ptr 250 write_ptr 156
[  653.265094] iwl data: 00000000: ff 03 00 00 00 00 00 00 00 00 00 fc 00 00 00 00  ................
[  653.265111] iwlwifi 0000:12:00.0: FH TRBs(0) = 0x00000000
[  653.265128] iwlwifi 0000:12:00.0: FH TRBs(1) = 0x80102009
[  653.265144] iwlwifi 0000:12:00.0: FH TRBs(2) = 0x00000000
[  653.265161] iwlwifi 0000:12:00.0: FH TRBs(3) = 0x80300095
[  653.265178] iwlwifi 0000:12:00.0: FH TRBs(4) = 0x00000000
[  653.265194] iwlwifi 0000:12:00.0: FH TRBs(5) = 0x00000000
[  653.265211] iwlwifi 0000:12:00.0: FH TRBs(6) = 0x00000000
[  653.265227] iwlwifi 0000:12:00.0: FH TRBs(7) = 0x007040a0
[  653.265289] iwlwifi 0000:12:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [150,150]
[  653.265350] iwlwifi 0000:12:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  653.265411] iwlwifi 0000:12:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [250,156]
[  653.265473] iwlwifi 0000:12:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265534] iwlwifi 0000:12:00.0: Q 4 is active and mapped to fifo 7 ra_tid 0x0000 [161,161]
[  653.265595] iwlwifi 0000:12:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265656] iwlwifi 0000:12:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265717] iwlwifi 0000:12:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265778] iwlwifi 0000:12:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265839] iwlwifi 0000:12:00.0: Q 9 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265900] iwlwifi 0000:12:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.265961] iwlwifi 0000:12:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266022] iwlwifi 0000:12:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266083] iwlwifi 0000:12:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266144] iwlwifi 0000:12:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266206] iwlwifi 0000:12:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266267] iwlwifi 0000:12:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266328] iwlwifi 0000:12:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266389] iwlwifi 0000:12:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  653.266450] iwlwifi 0000:12:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.269241] iwlwifi 0000:12:00.0: fail to flush all tx fifo queues Q 2
[  655.269251] iwlwifi 0000:12:00.0: Current SW read_ptr 252 write_ptr 158
[  655.269279] iwl data: 00000000: ff 0f 00 00 00 00 00 00 00 00 00 f0 00 00 00 00  ................
[  655.269296] iwlwifi 0000:12:00.0: FH TRBs(0) = 0x00000000
[  655.269312] iwlwifi 0000:12:00.0: FH TRBs(1) = 0x8010200b
[  655.269328] iwlwifi 0000:12:00.0: FH TRBs(2) = 0x00000000
[  655.269343] iwlwifi 0000:12:00.0: FH TRBs(3) = 0x80300096
[  655.269360] iwlwifi 0000:12:00.0: FH TRBs(4) = 0x00000000
[  655.269375] iwlwifi 0000:12:00.0: FH TRBs(5) = 0x00000000
[  655.269391] iwlwifi 0000:12:00.0: FH TRBs(6) = 0x00000000
[  655.269407] iwlwifi 0000:12:00.0: FH TRBs(7) = 0x007040a3
[  655.269468] iwlwifi 0000:12:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [151,151]
[  655.269529] iwlwifi 0000:12:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  655.269589] iwlwifi 0000:12:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [252,158]
[  655.269683] iwlwifi 0000:12:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.269745] iwlwifi 0000:12:00.0: Q 4 is active and mapped to fifo 7 ra_tid 0x0000 [164,164]
[  655.269806] iwlwifi 0000:12:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.269866] iwlwifi 0000:12:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.269926] iwlwifi 0000:12:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.269987] iwlwifi 0000:12:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270047] iwlwifi 0000:12:00.0: Q 9 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270107] iwlwifi 0000:12:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270168] iwlwifi 0000:12:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270228] iwlwifi 0000:12:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270289] iwlwifi 0000:12:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270349] iwlwifi 0000:12:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270409] iwlwifi 0000:12:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270469] iwlwifi 0000:12:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270530] iwlwifi 0000:12:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270590] iwlwifi 0000:12:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  655.270651] iwlwifi 0000:12:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]


########## wireless info END ############





```

---

### Post by apoorvmunshi on 2014-10-12
additional details : Dell Inspiron N5010

---

### Post by Vladlenin5000 on 2014-10-13
There are a few details that can be improved eventually.

Firstly, you live in a very crowed area, ie, with lots of networks in the neighborhood, with a high potential of interference. Channels 1 and 11 are the most crowded so changing to one in the middle like 6 might improve the transmission.
The recommend encryption is always WPA2-AES.

I suggest you try this changes at the router.

---

### Post by apoorvmunshi on 2014-10-13
Hi . I just changed the channel. The problem is wifi works fine on windows but not on ubuntu. the encryption mode is same as u suggested. I have many other firmwares installed apart from the one required for N-1000. Do you think that might be the problem ?

---

### Post by Vladlenin5000 on 2014-10-13
I'm not an expert but I don't think the other firmwares (?) are a problem. And I couldn't find anything else "wrong" in your report. I can be wrong though.

@varunendra and @chili555 are the recognized gurus in the networking field. Hopefully one of them will see this and give a better suggestion.

---

### Post by apoorvmunshi on 2014-10-13
And after googling a bit,  i found channel 6 is most common on 2.4 GHz networks. So i think m gonna change it back to 11 . :-P

---

### Post by weatherman2 on 2014-10-13
There are 6 other nearby access points broadcasting on channel 6.  But none apparently on channels 9 or 10.  I would choose channel 9 myself (and if you use a 40MHZ channel width - two channels - use the upper channel as control, so then it will use channels 9 and 10.)

But you're right: this has nothing to do with Ubuntu if Windows works fine.  Changing to channel 9 should help overall WiFi however.

Have you tried adding this:

```

options iwlwifi 11n_disable=8

```

to the end of the file /etc/modprobe.d/iwlwifi.conf ?

[http://askubuntu.com/questions/497395/14-04-wireless-throughput-issues](http://askubuntu.com/questions/497395/14-04-wireless-throughput-issues)

Some people seem to need to set this parameter with Intel wireless cards in 14.04.  I have not needed to in my 14.04 tests so far (mostly I use Intel wireless cards in 12.04 with great success).  You can try it and see if it works - if not, remove it.

---

### Post by apoorvmunshi on 2014-10-13
Yes actually I have changed the channel to 10 and I have added the line. I have also added the line at the end of configuration  file. I will post performance results soon.:KS

---

### Post by apoorvmunshi on 2014-10-13
Hello all. The drops in wifi are still dere :( . I am willing to do anything to fix this coz i can't buy a new wifi card n I can't tolerate windows also . :-P

---

### Post by chili555 on 2014-10-24
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

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

Finally, I suggest you change the parameter in iwlwifi.conf:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the very last line to read:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close the text editor.

Reboot and let us hear your report.

---

### Post by jeremy31 on 2014-10-24
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809)

Looks like a patched kernel fixes this

---

### Post by apoorvmunshi on 2014-10-24
I have done all the changes except the width change in router because apparently my Netgear WNDR4300  router has no option t change the channel width.  I will post the findings soon. btw what does the [COLOR=#000000][FONT=Ubuntu Mono]11n_disable option do ? Does it disable n mode of my wireless card ?!! If yes, then i won't get speeds more than 11 mbps (due to b mode) right ? [/FONT][/COLOR]

---

### Post by chili555 on 2014-10-24
> **apoorvmunshi said:**
> I have done all the changes except the width change in router because apparently my Netgear WNDR4300  router has no option t change the channel width.  I will post the findings soon. btw what does the [COLOR=#000000][FONT=Ubuntu Mono]11n_disable option do ? Does it disable n mode of my wireless card ?!! If yes, then i won't get speeds more than 11 mbps (due to b mode) right ? [/FONT][/COLOR]It does disable N mode but not G mode. You will likely get speeds up to 54 Mb/s.

I would certainly try the patched kernel as mentioned in the bug report Jeremy linked:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1361809/comments/6)  

I suggest you download and install linux-image, linux-headers and linux-image-extra for amd64 which conforms to your architecture x86_64. If you have any doubts or questions, post back and Jeremy or I will assist you. 

After installation, reboot and tell us how it performs.

Great catch, Jeremy!

---

### Post by apoorvmunshi on 2014-10-24
I am not sure exactly how should I install [COLOR=#000000]linux-image, linux-headers and linux-image-extra for amd64 which conforms to my architecture x86_64. :( Please give me some hints or links. The wifi is now quite stable now . Though speed has decreased, the drops in connection are less frequent. I will still wait for 1-2 days to see how exactly is the performance.[/COLOR]

---

### Post by apoorvmunshi on 2014-10-24
I tried the patched kernel and it seems that the wifi is working perfectly fine now/ :) . Still I want to monitor the results for 1-2 days more and then post them here. Thanks a lot to all. You guys and the open source community deserves much more praise than Apple and Microsoft . Cheers to linux :D

---

### Post by apoorvmunshi on 2014-10-25
hello  all . The issue has been fixed . Thanks to the patch released and the changes suggested by @chili555 and others . Moderators may mark this thread as solved so that others can  get help :)

---

### Post by jeremy31 on 2014-10-25
You might be able to increase the speed with ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
``` then go to the line ```
options iwlwifi 11n_disable=1
``` change it to ```
options iwlwifi 11n_disable=8
``` save, exit, reboot

---

