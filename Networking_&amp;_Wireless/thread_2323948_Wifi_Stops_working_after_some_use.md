---
title: "Wifi Stops working after some use"
date: 2016-05-09
forum: Networking &amp; Wireless
---

### Post by zonova on 2016-05-09
Hello everyone!

My wifi has been giving me issues. I've had linux on this laptop (Lenovo  Thinkpad X201) for over a year now and have never faced these issues.  However, for the past 3 weeks or so, the wifi on my laptop will randomly  stop working. It'll have worked for an hour or two and then it will just  disconnect, and it won't let me connect to any networks, saying that  "wifi is disabled on this device," even though when I right click on the  wifi icon, it clearly says that Wifi and Networking are enabled. I try  flipping the hardware wifi switch, however it doesn't fix it. I restart  it, and it goes back to normal. However, some random behavior I've  noticed with this is that, right when the wifi issue crops up(and at no  other time), when I move my cursor over the taskbar or right click on  the wifi symbol or open up the terminal, it freezes for over 5 seconds  and becomes very laggy momentarily. This never happens otherwise, the  computer always works super smoothly. This freezing issue doesn't happen all the time either, it's very random when it does, but it only occurs when the wifi is giving me trouble. When I hold the cursor over the wifi icon, is says that "Wifi Network Intel Centrino Advanced N 6200 2x2 AGN" is disconnected, and it doesn't show any wifi networks under it, despite the fact that it was connected only moments before that. I've attached the wireless info script to this post, I was hoping someone could help me figure out what's wrong. Currently I'm using a usb wifi card, just because I got tired of having to restart the laptop over and over again. Thanks!

```

########## wireless info START ##########

Report from: 09 May 2016 14:34 CDT -0500

Booted last: 09 May 2016 13:53 CDT -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
    Subsystem: Lenovo Device [17aa:2153]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)
    Subsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 17ef:4816 Lenovo Integrated Webcam
Bus 001 Device 005: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 004: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
iwldvm                236381  0 
mac80211              638915  4 rtl_usb,rtlwifi,iwldvm,rtl8192cu
iwlwifi               174028  1 iwldvm
cfg80211              496328  4 iwlwifi,mac80211,rtlwifi,iwldvm
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
          Interrupt:20 Memory:f2500000-f2520000 

ham0      Link encap:Ethernet  HWaddr <MAC 'ham0' [IF]>  
          inet addr:25.75.106.33  Bcast:25.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::<IP6 'ham0' [IF]>/64 Scope:Link
          inet6 addr: 2620:9b::194b:6a21/96 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:32721 (32.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:47568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59442561 (59.4 MB)  TX bytes:13483793 (13.4 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:10.0.0.165  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:484:c001:3171:f884:ad57:5a29:64a5/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          inet6 addr: 2601:484:c001:3171:<IP6 'wlan1' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39874 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51597622 (51.5 MB)  TX bytes:4863920 (4.8 MB)

##### iwconfig ##########################

ham0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"KHALID"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'KHALID' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:45   Missed beacon:0

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan1
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan1
25.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ham0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.tn.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1013     1  0 13:53 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1  [KHALID 1] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE512:        Infra, <MAC '2WIRE512' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA
    Home-2.4:        Infra, <MAC 'Home-2.4' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    2WIRE440:        Infra, <MAC '2WIRE440' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Stephenass:      Infra, <MAC 'Stephenass' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    ATTRRVKPqs:      Infra, <MAC 'ATTRRVKPqs' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    The Burnett's:   Infra, <MAC 'The Burnett's' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Warren Kerckhoff's Wi-Fi Network: Infra, <MAC 'Warren Kerckhoff's Wi-Fi Network' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
    2WIRE288:        Infra, <MAC '2WIRE288' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Tuckers:         Infra, <MAC 'Tuckers' [AN12]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 47 WPA2
    Childs:          Infra, <MAC 'Childs' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ATTZNUgxPi:      Infra, <MAC 'ATTZNUgxPi' [AN14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    ATTFrgz66a:      Infra, <MAC 'ATTFrgz66a' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *KHALID:         Infra, <MAC 'KHALID' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2

  IPv4 Settings:
    Address:         10.0.0.165
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
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
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Pilot Enhanced Outdoor]] (600 root)
[connection] id=Pilot Enhanced Outdoor | type=802-11-wireless
[802-11-wireless] ssid=Pilot Enhanced Outdoor | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KHALID]] (600 root)
[connection] id=KHALID | type=802-11-wireless
[802-11-wireless] ssid=KHALID | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BookSellers]] (600 root)
[connection] id=BookSellers | type=802-11-wireless
[802-11-wireless] ssid=BookSellers | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/khalid 1]] (600 root)
[connection] id=khalid 1 | type=802-11-wireless
[802-11-wireless] ssid=khalid | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GUEST]] (600 root)
[connection] id=GUEST | type=802-11-wireless
[802-11-wireless] ssid=GUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BusWifi_6742_921450]] (600 root)
[connection] id=BusWifi_6742_921450 | type=802-11-wireless
[802-11-wireless] ssid=BusWifi_6742_921450 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KHALID 1]] (600 root)
[connection] id=KHALID 1 | type=802-11-wireless
[802-11-wireless] ssid=KHALID | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CableWiFi]] (600 root)
[connection] id=CableWiFi | type=802-11-wireless
[802-11-wireless] ssid=CableWiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Pilot Free Inside WiFi]] (600 root)
[connection] id=Pilot Free Inside WiFi | type=802-11-wireless
[802-11-wireless] ssid=Pilot Free Inside WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Guest_Wireless]] (600 root)
[connection] id=Guest_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Guest_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BusWiFi_86031_204007128]] (600 root)
[connection] id=BusWiFi_86031_204007128 | type=802-11-wireless
[802-11-wireless] ssid=BusWiFi_86031_204007128 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Rhodes_Wireless]] (600 root)
[ipv6] method=auto
[connection] id=Rhodes_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Rhodes_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/aloft]] (600 root)
[connection] id=aloft | type=802-11-wireless
[802-11-wireless] ssid=aloft | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Rhodes_Security]] (600 root)
[connection] id=Rhodes_Security | type=802-11-wireless
[802-11-wireless] ssid=Rhodes_Security | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Khalid 2]] (600 root)
[connection] id=Khalid 2 | type=802-11-wireless
[802-11-wireless] ssid=Khalid | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Khalid 1]] (600 root)
[connection] id=Khalid 1 | type=802-11-wireless
[802-11-wireless] ssid=Khalid | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATL Free Wi-Fi]] (600 root)
[connection] id=ATL Free Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=ATL Free Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Student_Wireless]] (600 root)
[connection] id=Student_Wireless | type=802-11-wireless
[802-11-wireless] ssid=Student_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/linksys]] (600 root)
[connection] id=linksys | type=802-11-wireless
[802-11-wireless] ssid=linksys | bssid=<MAC address> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/khalid]] (600 root)
[connection] id=khalid | type=802-11-wireless
[802-11-wireless] ssid=khalid | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airserv123]] (600 root)
[connection] id=Airserv123 | type=802-11-wireless
[802-11-wireless] ssid=Airserv123 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BusWiFi_6372_920410]] (600 root)
[connection] id=BusWiFi_6372_920410 | type=802-11-wireless
[802-11-wireless] ssid=BusWiFi_6372_920410 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Khalid]] (600 root)
[connection] id=Khalid | type=802-11-wireless
[802-11-wireless] ssid=Khalid | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WCS-Guest]] (600 root)
[connection] id=WCS-Guest | type=802-11-wireless
[802-11-wireless] ssid=WCS-Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HomeNet]] (600 root)
[connection] id=HomeNet | type=802-11-wireless
[802-11-wireless] ssid=HomeNet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

ham0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

ham0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Input/output error

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      6   APs on   Frequency:2.462 GHz (Channel 11)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'KHALID' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"KHALID"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d0fa4684d9
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d0fa5d4180
                    Extra: Last beacon: 232ms ago
          Cell 03 - Address: <MAC 'The Burnett's' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"The Burnett's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004802ba86b7f
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d0fa5bb180
                    Extra: Last beacon: 284ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC '2WIRE512' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"2WIRE512"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002633812181
                    Extra: Last beacon: 1116ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ATTRRVKPqs' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ATTRRVKPqs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004802d3872ab
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Home-2.4' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Home-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f23fd6180
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f23fef17f
                    Extra: Last beacon: 1148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'wifi' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000048028fc1389
                    Extra: Last beacon: 1080ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Warren Kerckhoff's Wi-Fi Network' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Warren Kerckhoff's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c999878193
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'DIRECT-roku-761' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-761"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e2fb94469a
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC '' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f18aaf969
                    Extra: Last beacon: 144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC '' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006bd6991180
                    Extra: Last beacon: 136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'xfinitywifi' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f18aaf180
                    Extra: Last beacon: 120ms ago

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     503A009BEFC80A2CC32099E
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     25A04A53549C90C495EC03F
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

[iwldvm]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9036600D780304CB32B6EF2
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0EE2BE801594EE59EA3A85C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-85-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     F935FAF50D9A6B3215203C9
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
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
filename:       /lib/modules/3.13.0-85-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C6:33:E9:BF:A6:CA:49:D5:3D:2E:B5:25:6A:35:87:7D:04:F1:64:F8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

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
lp
rtc
lp
rtc
lp
rtc
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
blacklist rt2800pci

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

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
# PCI device 0x8086:0x10ea (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4239 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 1727.222419]  [<ffffffffa06a4779>] iwl_dump_nic_event_log+0x369/0x370 [iwldvm]
[ 1727.222434]  [<ffffffffa06a47c0>] iwl_nic_error+0x40/0x50 [iwldvm]
[ 1727.222450]  [<ffffffffa043adf0>] iwl_trans_pcie_send_hcmd+0x5b0/0x690 [iwlwifi]
[ 1727.222467]  [<ffffffffa06ad816>] iwl_dvm_send_cmd+0x46/0x110 [iwldvm]
[ 1727.222478]  [<ffffffffa06ada81>] iwl_dvm_send_cmd_pdu+0x41/0x50 [iwldvm]
[ 1727.222490]  [<ffffffffa06b64c4>] iwl_power_set_mode+0x1b4/0x300 [iwldvm]
[ 1727.222503]  [<ffffffffa06b66b7>] iwl_power_update_mode+0xa7/0x190 [iwldvm]
[ 1727.222515]  [<ffffffffa06ba4b1>] iwlagn_mac_config+0x2f1/0x390 [iwldvm]
[ 1727.222666] iwlwifi 0000:02:00.0: Log capacity -1515870811 is bogus, limit to 512 entries
[ 1727.222671] iwlwifi 0000:02:00.0: Log write index -1515870811 is bogus, limit to 512
[ 1727.222675] iwlwifi 0000:02:00.0: Start IWL Event Log Dump: display last 20 entries
[ 1727.241193] iwlwifi 0000:02:00.0: set power fail, ret = -110
[ 1729.152867] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[ 1731.085465] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[ 1733.055046] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[ 1734.985889] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[ 1736.866035] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 1e
[ 1736.866046] iwlwifi 0000:02:00.0: flush request fail
[ 1736.866076] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 18
[ 1736.866082] wlan0: HW problem - can not stop rx aggregation for <MAC address> tid 0
[ 1736.866087] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 18
[ 1736.866093] wlan0: HW problem - can not stop rx aggregation for <MAC address> tid 1
[ 1736.866100] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 18
[ 1736.866105] wlan0: HW problem - can not stop rx aggregation for <MAC address> tid 6
[ 1736.866293] iwlwifi 0000:02:00.0: Fw not loaded - dropping CMD: 1e
[ 1736.866300] iwlwifi 0000:02:00.0: flush request fail
[ 1736.866512] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[ 1736.940156] iwlwifi 0000:02:00.0: Radio type=0x1-0x3-0x1
[ 1742.658175] iwlwifi 0000:02:00.0: Failed to load firmware chunk!
[ 1742.658185] iwlwifi 0000:02:00.0: Could not load the [0] uCode section
[ 1744.567079] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 0 [0x5a5a5a5a]
[ 1746.474374] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 2 [0x5a5a5a5a]
[ 1748.413853] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 5 [0x5a5a5a5a]
[ 1750.316839] iwlwifi 0000:02:00.0: Failing on timeout while stopping DMA channel 7 [0x5a5a5a5a]
[ 1752.212637] iwlwifi 0000:02:00.0: Failed to run INIT ucode: -110
[ 1752.212685] iwlwifi 0000:02:00.0: Unable to initialize device.
[ 1752.215693] iwlwifi 0000:02:00.0: Request scan called when driver not ready.
[ 1764.926943] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1765.028082] iwlwifi 0000:02:00.0: Request scan called when driver not ready. (repeated 13 times)
[ 2144.630645] wlan1: authenticate with <MAC 'KHALID' [AC1]>
[ 2144.654189] wlan1: send auth to <MAC 'KHALID' [AC1]> (try 1/3)
[ 2144.704229] wlan1: authenticated
[ 2144.705987] wlan1: associate with <MAC 'KHALID' [AC1]> (try 1/3)
[ 2144.737772] wlan1: RX AssocResp from <MAC 'KHALID' [AC1]> (capab=0x431 status=0 aid=1)
[ 2144.737852] wlan1: associated
[ 2189.281673] iwlwifi 0000:02:00.0: Request scan called when driver not ready. (repeated 6 times)

########## wireless info END ############


```[ATTACH]268964[/ATTACH]

---

### Post by praseodym on 2016-05-09
Deactivate the queue of the driver:

```
echo "options iwlwifi wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot. If it is not enough change the encryption mode to WPA2-AES (CCMP), no mixed mode WPA/WPA2. Check the router manual. Also deactivate IPv6 in the settings

---

### Post by zonova on 2016-05-10
This unfortunately has not worked for me. I can that line in the terminal and rebooted however the behavior continued. Also, when I try to Edit Connections in my network manager, I don't have the option of WPA2-AES. I only have WPA/WPA2 Personal, WPA/WPA2 Enterprise, LEAP, and a few types of WEP.

---

### Post by jeremy31 on 2016-05-10
praseodym wants you to change the encryption on the wifi router, not in Network Manager.  It does show TKIP enabled on KHALID which does cause problems

---

### Post by zonova on 2016-05-11
Oh, I see. The problem is that this issue is happening both on Khalid as well as on Rhodes Wifi, one of which is my home network and the other is the university network. I can't really change the university networks settings. Is there anything else I could do?

---

