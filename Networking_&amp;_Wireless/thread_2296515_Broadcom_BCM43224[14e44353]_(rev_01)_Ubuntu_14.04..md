---
title: "Broadcom BCM43224[14e4:4353] (rev 01) Ubuntu 14.04.3 drops wifi connection"
date: 2015-09-26
forum: Networking &amp; Wireless
---

### Post by madralino on 2015-09-26
Hi

Well I began to have problems with 14.04.01 with the wifi dropping connection when i changed my old router: 
I was using the broadcom proprietary driver  but when i upgrade to 14.04.03 this proprietary driver does not work any more. And I am using now the 
Special case #1: This device uses the driver combination bcma and brcmsmac, like it is indicated in the post [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110).
But i suffer the wifi connection continuosly dropping and dropping . Every minute i have to reconnect.


In Windows 7 in the same machine,(i have dual boot) the wifi works ok, without dropping the connection.

I post the wireless-info

```



########## wireless info START ##########


Report from: 26 Sep 2015 12:03 CEST +0200


Booted last: 26 Sep 2015 10:31 CEST +0200


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
    Subsystem: Dell Wireless 1520 Half-size Mini PCIe Card [1028:000e]
    Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
    Subsystem: Dell XPS 8300 [1028:04aa]
    Kernel driver in use: tg3


##### lsusb #############################


Bus 002 Device 006: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 005: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 004: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 18a5:0214 Verbatim, Ltd Portable Hard Drive
Bus 001 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone [Galaxy S III], GT-P7500 [Galaxy Tab 10.1]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


brcmsmac              569344  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              708608  1 brcmsmac
cfg80211              524288  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac


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
          Interrupt:19 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.132  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42336667 (42.3 MB)  TX bytes:5416137 (5.4 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"ManuWLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'ManuWLAN' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:84   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       983     1  0 10:31 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


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


- Device: wlan0  [ManuWLAN] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           130 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MOVISTAR_PLUS_AC3B: Infra, <MAC 'MOVISTAR_PLUS_AC3B' [AC13]>, Freq 5500 MHz, Rate 54 Mb/s, Strength 57 WPA2
    MOVISTAR_PLUS_AFF1: Infra, <MAC 'MOVISTAR_PLUS_AFF1' [AC14]>, Freq 5520 MHz, Rate 54 Mb/s, Strength 45 WPA2
    MOVISTAR_B75E:   Infra, <MAC 'MOVISTAR_B75E' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA
    MOVISTAR_AC3B:   Infra, <MAC 'MOVISTAR_AC3B' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2
    MOVISTAR_0C30_EXT: Infra, <MAC 'MOVISTAR_0C30_EXT' [AC8]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    MOVISTAR_9AA0:   Infra, <MAC 'MOVISTAR_9AA0' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Orange-326c:     Infra, <MAC 'Orange-326c' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WEP
    WLAN_9506:       Infra, <MAC 'WLAN_9506' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA
    WLAN_2E35:       Infra, <MAC 'WLAN_2E35' [AN9]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 37 WPA
    MOVISTAR_AFF1:   Infra, <MAC 'MOVISTAR_AFF1' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    ANTONIO:         Infra, <MAC 'ANTONIO' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    *ManuWLAN:       Infra, <MAC 'ManuWLAN' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA2
    vodafone76A7:    Infra, <MAC 'vodafone76A7' [AN13]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 35 WPA2
    JAZZTEL_gPAA:    Infra, <MAC 'JAZZTEL_gPAA' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Orange-326c:     Infra, <MAC 'Orange-326c' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP


  IPv4 Settings:
    Address:         192.168.1.132
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             8.8.8.8
    DNS:             208.67.222.222
    DNS:             208.67.220.220
    DNS:             87.216.1.65
    DNS:             87.216.1.66


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


[[/etc/NetworkManager/system-connections/WASC-001641fed7cc-PHILIPS]] (600 root)
[connection] id=WASC-001641fed7cc-PHILIPS | type=802-11-wireless
[802-11-wireless] ssid=WASC-001641fed7cc-PHILIPS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ManuWLAN]] (600 root)
[connection] id=ManuWLAN | type=802-11-wireless
[802-11-wireless] ssid=ManuWLAN | bssid=<MAC 'ManuWLAN' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Madrid (based on set time zone)


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.52 GHz (Channel 104)
      1   APs on   Frequency:5.5 GHz (Channel 100)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ManuWLAN' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"ManuWLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004a8638daa
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JAZZTEL_TEu4' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_TEu4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c5219b3717c
                    Extra: Last beacon: 10052ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MOVISTAR_9AA0' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_9AA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010ebef8c547
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Orange-326c' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Orange-326c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ccbf49a7f3
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: <MAC 'Orange-326c' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Orange-326c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000fe7bae418f
                    Extra: Last beacon: 200ms ago
          Cell 06 - Address: <MAC 'ANTONIO' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ANTONIO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009f04b6009
                    Extra: Last beacon: 2624ms ago
          Cell 07 - Address: <MAC 'JAZZTEL_gPAA' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_gPAA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002054e3b117c
                    Extra: Last beacon: 240ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'MOVISTAR_0C30_EXT' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_0C30_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c1dab5a09
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'MOVISTAR_AFF1' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_AFF1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d9bbfaf2ca
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'MOVISTAR_B75E' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_B75E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018b8665b7d3
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'WLAN_9506' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"WLAN_9506"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000031e08e245e1
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'MOVISTAR_AC3B' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_AC3B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d88472f4eb
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'MOVISTAR_PLUS_AC3B' [AC13]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_PLUS_AC3B"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000078353c34e0
                    Extra: Last beacon: 4968ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'MOVISTAR_PLUS_AFF1' [AC14]>
                    Channel:104
                    Frequency:5.52 GHz (Channel 104)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_PLUS_AFF1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000965f0fd982
                    Extra: Last beacon: 4716ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/3.19.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-28-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:4D:C0:12:70:6F:48:B7:CD:DF:63:74:E2:D7:9F:E1:B0:60:92:69
sig_hashalgo:   sha512


##### module parameters #################


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
blacklist b43
blacklist ssb


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
# PCI device 0x14e4:0x1691 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4353 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  766.548998] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[  766.558362] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  766.561305] wlan0: authenticated
[  766.564485] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  766.568164] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=6)
[  766.568785] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[  766.568789] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  766.568797] wlan0: associated
[  766.617541] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  952.834028] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[  952.834997] wlan0: deauthenticating from <MAC 'ManuWLAN' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  952.835952] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  952.835958] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  956.350432] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[  956.359835] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  956.361421] wlan0: authenticated
[  956.365511] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  956.368976] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=6)
[  956.369643] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[  956.369646] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  956.369653] wlan0: associated
[  956.414541] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 5319.723902] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 0 addresses (implement)
[ 5319.725134] wlan0: deauthenticating from <MAC 'ManuWLAN' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5319.726337] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 5319.726344] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 5323.530489] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[ 5323.538999] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 5323.541949] wlan0: authenticated
[ 5323.544952] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 5323.548711] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=3)
[ 5323.549310] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 5323.549314] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 5323.549325] wlan0: associated
[ 5323.592984] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 5462.692366] wlan0: deauthenticating from <MAC 'ManuWLAN' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5462.693397] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 5462.693405] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 5462.693408] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 5466.217569] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[ 5466.226917] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 5466.228989] wlan0: authenticated
[ 5466.232953] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 5466.238554] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=3)
[ 5466.239174] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 5466.239178] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 5466.239186] wlan0: associated
[ 5466.286265] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)


########## wireless info END ############
```



Sorry for my english.

---

### Post by madralino on 2015-10-03
Hi

I have tested the ubuntu live in USB and ¿the wifi connection doesn't drop?

```


########## wireless info START ##########


Report from: 27 Sep 2015 08:33 UTC +0000


Booted last: 27 Sep 2015 09:53 UTC +0000


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


noprompt, cdrom-detect/try-usb=true, persistent, file=/cdrom/preseed/ubuntu.seed, boot=casper, initrd=/casper/initrd.lz, quiet, splash, --, maybe-ubiquity


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
    Subsystem: Dell Wireless 1520 Half-size Mini PCIe Card [1028:000e]
    Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
    Subsystem: Dell XPS 8300 [1028:04aa]
    Kernel driver in use: tg3


##### lsusb #############################


Bus 002 Device 006: ID 18e3:9106 Fitipower Integrated Technology Inc 
Bus 002 Device 005: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 004: ID 046d:c063 Logitech, Inc. DELL Laser Mouse
Bus 002 Device 003: ID 413c:2107 Dell Computer Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 18a5:0214 Verbatim, Ltd Portable Hard Drive
Bus 001 Device 003: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 001 Device 006: ID 1949:0004 Lab126, Inc. Amazon Kindle 3/4/Paperwhite
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


brcmsmac              569344  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   421888  0 
mac80211              708608  2 b43,brcmsmac
cfg80211              524288  3 b43,brcmsmac,mac80211
ssb                    65536  1 b43
bcma                   53248  3 b43,brcmsmac


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
          Interrupt:19 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.136  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27002 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18476 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31521676 (31.5 MB)  TX bytes:2533009 (2.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"ManuWLAN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'ManuWLAN' [AC1]>   
          Bit Rate=117 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:40   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root      3961     1  0 07:53 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


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


- Device: wlan0  [ManuWLAN] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           117 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MOVISTAR_PLUS_AC3B: Infra, <MAC 'MOVISTAR_PLUS_AC3B' [AC12]>, Freq 5500 MHz, Rate 54 Mb/s, Strength 57 WPA2
    MOVISTAR_PLUS_AFF1: Infra, <MAC 'MOVISTAR_PLUS_AFF1' [AC13]>, Freq 5520 MHz, Rate 54 Mb/s, Strength 50 WPA2
    MOVISTAR_B75E:   Infra, <MAC 'MOVISTAR_B75E' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WPA
    MOVISTAR_9AA0:   Infra, <MAC 'MOVISTAR_9AA0' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA2
    MOVISTAR_AC3B:   Infra, <MAC 'MOVISTAR_AC3B' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    MOVISTAR_AFF1:   Infra, <MAC 'MOVISTAR_AFF1' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    WLAN_9506:       Infra, <MAC 'WLAN_9506' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    MOVISTAR_0C30_EXT: Infra, <MAC 'MOVISTAR_0C30_EXT' [AN8]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    JAZZTEL_FCAa:    Infra, <MAC 'JAZZTEL_FCAa' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    JAZZTEL_gPAA:    Infra, <MAC 'JAZZTEL_gPAA' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    JAZZTEL_TEu4:    Infra, <MAC 'JAZZTEL_TEu4' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    JAZZTEL_EzTC:    Infra, <MAC 'JAZZTEL_EzTC' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Orange-326c:     Infra, <MAC 'Orange-326c' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WEP
    WLAN_FC:         Infra, <MAC 'WLAN_FC' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    WLAN_16EF:       Infra, <MAC 'WLAN_16EF' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    *ManuWLAN:       Infra, <MAC 'ManuWLAN' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA2
    MOVISTAR_634F:   Infra, <MAC 'MOVISTAR_634F' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA
    Orange-326c:     Infra, <MAC 'Orange-326c' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    ANTONIO:         Infra, <MAC 'ANTONIO' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WEP
    TP-LINK_CE90F0:  Infra, <MAC 'TP-LINK_CE90F0' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Wifi CES:        Infra, <MAC 'Wifi CES' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    WLAN_2E35:       Infra, <MAC 'WLAN_2E35' [AC10]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA


  IPv4 Settings:
    Address:         192.168.1.136
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             87.216.1.65
    DNS:             87.216.1.66


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


[[/etc/NetworkManager/system-connections/ManuWLAN]] (600 root)
[connection] id=ManuWLAN | type=802-11-wireless
[802-11-wireless] ssid=ManuWLAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Etc/UTC (based on set time zone)


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.52 GHz (Channel 104)
      1   APs on   Frequency:5.5 GHz (Channel 100)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ManuWLAN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"ManuWLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000365809585
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MOVISTAR_9AA0' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_9AA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012199ddb650
                    Extra: Last beacon: 192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'JAZZTEL_TEu4' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_TEu4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c64f52ab17c
                    Extra: Last beacon: 152ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'JAZZTEL_EzTC' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_EzTC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000019b904a617c
                    Extra: Last beacon: 160ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'WLAN_FC' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"WLAN_FC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000078d24791e2
                    Extra: Last beacon: 304ms ago
          Cell 06 - Address: <MAC 'MOVISTAR_AC3B' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_AC3B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000eb5f5ab9c9
                    Extra: Last beacon: 8976ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'MOVISTAR_B75E' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_B75E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019e614d8bc6
                    Extra: Last beacon: 8120ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WLAN_9506' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"WLAN_9506"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000330e3bad01b
                    Extra: Last beacon: 8056ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'MOVISTAR_AFF1' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_AFF1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ec96f66eee
                    Extra: Last beacon: 8080ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WLAN_2E35' [AC10]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WLAN_2E35"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000071df234f1f8
                    Extra: Last beacon: 29684ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Wifi CES' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Wifi CES"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004418d180
                    Extra: Last beacon: 480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'MOVISTAR_PLUS_AC3B' [AC12]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_PLUS_AC3B"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000819cc9a04a
                    Extra: Last beacon: 4896ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'MOVISTAR_PLUS_AFF1' [AC13]>
                    Channel:104
                    Frequency:5.52 GHz (Channel 104)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_PLUS_AFF1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a24767b007
                    Extra: Last beacon: 4624ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     5F866C1008CB05E51B96C2E
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A2434DDD5B2051715F2E908
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[b43]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     25A88E97301A6821E663814
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)


[mac80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B23264F074A7D27F8B691A2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


[bcma]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


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
# PCI device 0x14e4:0x1691 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4353 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  810.111160] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[  810.120625] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  810.123318] wlan0: authenticated
[  810.126430] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[  810.130895] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=4)
[  810.131455] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[  810.131460] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  810.131471] wlan0: associated
[  818.237534] wlan0: deauthenticated from <MAC 'ManuWLAN' [AC1]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[  818.244675] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  818.244683] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1202.080915] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[ 1202.090324] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1202.091932] wlan0: authenticated
[ 1202.092338] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1202.101864] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=4)
[ 1202.102389] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1202.102393] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1202.102404] wlan0: associated
[ 1210.197578] wlan0: deauthenticated from <MAC 'ManuWLAN' [AC1]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)
[ 1210.202501] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1210.202509] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1227.660725] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[ 1227.670049] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1227.671803] wlan0: authenticated
[ 1227.672069] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1227.675629] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=4)
[ 1227.676237] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1227.676242] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1227.676251] wlan0: associated
[ 1229.875565] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1335.632069] wlan0: deauthenticated from <MAC 'ManuWLAN' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 1335.646149] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1335.646173] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1335.646176] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1335.662380] wlan0: authenticate with <MAC 'ManuWLAN' [AC1]>
[ 1335.662463] wlan0: send auth to <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1335.664022] wlan0: authenticated
[ 1335.665935] wlan0: associate with <MAC 'ManuWLAN' [AC1]> (try 1/3)
[ 1335.669321] wlan0: RX AssocResp from <MAC 'ManuWLAN' [AC1]> (capab=0x1411 status=0 aid=4)
[ 1335.669939] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1335.669944] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1335.669946] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1335.669961] wlan0: associated


########## wireless info END ############



```

---

