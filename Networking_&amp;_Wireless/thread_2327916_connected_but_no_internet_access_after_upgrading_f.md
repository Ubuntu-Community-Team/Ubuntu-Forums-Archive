---
title: "connected but no internet access after upgrading from 12.04 to 14.04"
date: 2016-06-15
forum: Networking &amp; Wireless
---

### Post by dan229 on 2016-06-15
Hi guys,

I have been struggling with this network problem for two days. For both wired and wireless connection, it shows connected but there's no internet access. I read many threads but still can't solve my problem.

Here's the info. Thanks in advance.

```



########## wireless info START ##########


Report from: 15 Jun 2016 14:38 EDT -0400


Booted last: 15 Jun 2016 10:30 EDT -0400


Script from: 26 May 2016 21:56 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-88-generic #135-Ubuntu SMP Wed Jun 8 21:10:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, acpi_backlight=vendor, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e058]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 001 Device 005: ID 04f2:b33c Chicony Electronics Co., Ltd 
Bus 001 Device 009: ID 0489:e056 Foxconn / Hon Hai 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04f3:0011 Elan Microelectronics Corp. 
Bus 002 Device 004: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102/2.0 / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath3k                  17414  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              638901  1 ath9k
cfg80211              496328  3 ath,ath9k,mac80211
wmi                    19177  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF1]>  
          inet addr:10.1.215.59  Bcast:10.1.215.255  Mask:255.255.248.0
          inet6 addr: fe80::<IP6 'wlan0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15662 (15.6 KB)  TX bytes:30295 (30.2 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"WolfieNet-Secure"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: <MAC 'WolfieNet-Secure' [AC1]>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.208.1      0.0.0.0         UG    0      0        0 wlan0
10.1.208.0      0.0.0.0         255.255.248.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.0.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1080     1  0 10:30 ?        00:00:05 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [WolfieNet-Secure] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF1]>


  Capabilities:
    Speed:           6 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    eduroam:         Infra, <MAC 'eduroam' [AC33]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC15]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN5]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise
    IMSWAP:          Infra, <MAC 'IMSWAP' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA2
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC26]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    radio11N:        Infra, <MAC 'radio11N' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC23]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC32]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 100
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC14]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 72
    WolfieNet-Get-Connected: Infra, <MAC 'WolfieNet-Get-Connected' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AN16]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 52
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    WolfieNet-Get-Connected: Infra, <MAC 'WolfieNet-Get-Connected' [AC20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC27]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 47
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC24]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 52
    eduroam:         Infra, <MAC 'eduroam' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC34]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC36]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2 Enterprise
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75
    WolfieNet-Get-Connected: Infra, <MAC 'WolfieNet-Get-Connected' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AC35]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 52
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC31]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure:Infra, <MAC address>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise' [AN30]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC25]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure' [AC29]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AN34]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 25
    eduroam:         Infra, <MAC 'eduroam' [AC30]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure:Infra, <MAC address>, Freq 5240 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise' [AN36]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AN37]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 27
    eduroam:         Infra, <MAC 'eduroam' [AN38]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN39]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN40]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    *WolfieNet-Secure: Infra, <MAC 'WolfieNet-Secure' [AC1]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure:Infra, <MAC address>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2 Enterprise' [AN42]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2 Enterprise
    DIRECT-8A-HP ENVY 7640 series: Infra, <MAC 'DIRECT-8A-HP ENVY 7640 series' [AN43]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA2
    WolfieNet-Guest: Infra, <MAC 'WolfieNet-Guest' [AN44]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84
    WolfieNet-Get-Connected: Infra, <MAC 'WolfieNet-Get-Connected' [AN45]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80
    eduroam:         Infra, <MAC 'eduroam' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure:Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2 Enterprise' [AN47]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2 Enterprise
    WolfieNet-Secure:Infra, <MAC 'WolfieNet-Secure:Infra, <MAC address>, Freq 5200 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise' [AN48]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    WolfieNet-Get-Connected: Infra, <MAC 'WolfieNet-Get-Connected' [AN49]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44


  IPv4 Settings:
    Address:         10.1.215.59
    Prefix:          21 (255.255.248.0)
    Gateway:         10.1.208.1


    DNS:             10.1.16.16


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


[[/etc/NetworkManager/system-connections/Hanting]] (600 root)
[connection] id=Hanting | type=802-11-wireless
[802-11-wireless] ssid=Hanting | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/protossimba]] (600 root)
[connection] id=protossimba | type=802-11-wireless
[802-11-wireless] ssid=protossimba | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TreasureIsland-Rooms-Cox]] (600 root)
[connection] id=TreasureIsland-Rooms-Cox | type=802-11-wireless
[802-11-wireless] ssid=TreasureIsland-Rooms-Cox | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WyndhamBeaconHill]] (600 root)
[connection] id=WyndhamBeaconHill | type=802-11-wireless
[802-11-wireless] ssid=WyndhamBeaconHill | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WolfieNet-Secure]] (600 root)
[ipv6] method=auto
[connection] id=WolfieNet-Secure | type=802-11-wireless
[802-11-wireless] ssid=WolfieNet-Secure | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/LAX Free WiFi]] (600 root)
[connection] id=LAX Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=LAX Free WiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Days Inn Guest]] (600 root)
[connection] id=Days Inn Guest | type=802-11-wireless
[802-11-wireless] ssid=Days Inn Guest | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/FreeMSGWiFi]] (600 root)
[connection] id=FreeMSGWiFi | type=802-11-wireless
[802-11-wireless] ssid=FreeMSGWiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Hynes Wireless Network]] (600 root)
[connection] id=Hynes Wireless Network | type=802-11-wireless
[802-11-wireless] ssid=Hynes Wireless Network | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/sgs]] (600 root)
[connection] id=sgs | type=802-11-wireless
[802-11-wireless] ssid=sgs | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_Luke]] (600 root)
[connection] id=TP-LINK_Luke | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_Luke | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/greentea]] (600 root)
[connection] id=greentea | type=802-11-wireless
[802-11-wireless] ssid=greentea | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FREE-AIRPORT-WiFi]] (600 root)
[connection] id=FREE-AIRPORT-WiFi | type=802-11-wireless
[802-11-wireless] ssid=FREE-AIRPORT-WiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Fly-Fi]] (600 root)
[connection] id=Fly-Fi | type=802-11-wireless
[802-11-wireless] ssid=Fly-Fi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Sheraton Meeting]] (600 root)
[connection] id=Sheraton Meeting | type=802-11-wireless
[802-11-wireless] ssid=Sheraton Meeting | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/24 Malvern]] (600 root)
[connection] id=24 Malvern | type=802-11-wireless
[802-11-wireless] ssid=24 Malvern | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Comfort Suites]] (600 root)
[connection] id=Comfort Suites | type=802-11-wireless
[802-11-wireless] ssid=Comfort Suites | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Guest-RFL]] (600 root)
[connection] id=Guest-RFL | type=802-11-wireless
[802-11-wireless] ssid=Guest-RFL | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TC8715D3B]] (600 root)
[connection] id=TC8715D3B | type=802-11-wireless
[802-11-wireless] ssid=TC8715D3B | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tuscany-Rooms-Cox]] (600 root)
[connection] id=Tuscany-Rooms-Cox | type=802-11-wireless
[802-11-wireless] ssid=Tuscany-Rooms-Cox | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ATT-HOMEBASE-6032]] (600 root)
[connection] id=ATT-HOMEBASE-6032 | type=802-11-wireless
[802-11-wireless] ssid=ATT-HOMEBASE-6032 | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:5.785 GHz (Channel 157)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      12   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:5.22 GHz (Channel 44)
      3   APs on   Frequency:5.745 GHz (Channel 149)
      5   APs on   Frequency:5.765 GHz (Channel 153)
      3   APs on   Frequency:5.785 GHz (Channel 157)
      3   APs on   Frequency:5.805 GHz (Channel 161)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'WolfieNet-Secure' [AC1]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ea80274ca
                    Extra: Last beacon: 248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'WolfieNet-Secure' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a08a06139f
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC 'WolfieNet-Get-Connected' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Get-Connected"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a08a0616a9
                    Extra: Last beacon: 64ms ago
          Cell 04 - Address: <MAC 'WolfieNet-Guest' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a08a061976
                    Extra: Last beacon: 64ms ago
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a08a05c697
                    Extra: Last beacon: 8352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'eduroam' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a08a062b08
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'eduroam' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000074c477e838
                    Extra: Last beacon: 8340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'WolfieNet-Secure' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000183ce381b7
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'WolfieNet-Get-Connected' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Get-Connected"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000183ce384be
                    Extra: Last beacon: 64ms ago
          Cell 10 - Address: <MAC 'WolfieNet-Guest' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000183ce38787
                    Extra: Last beacon: 64ms ago
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000183ce39a65
                    Extra: Last beacon: 8324ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'eduroam' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000183ce45818
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'eduroam' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014261ae7839
                    Extra: Last beacon: 8300ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'WolfieNet-Guest' [AC14]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ec48831b7
                    Extra: Last beacon: 248ms ago
          Cell 15 - Address: <MAC 'eduroam' [AC15]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ec48832ec
                    Extra: Last beacon: 248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 16 - Address: <MAC 'WolfieNet-Secure' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a5ffcce3
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC '' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a5ffb717
                    Extra: Last beacon: 7640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'eduroam' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a603e3cd
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'WolfieNet-Guest' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a5ffcfea
                    Extra: Last beacon: 64ms ago
          Cell 20 - Address: <MAC 'WolfieNet-Get-Connected' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Get-Connected"
                    Bit Rates:5.5 Mb/s; 6 Mb/s; 9 Mb/s; 11 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a5ffd2a0
                    Extra: Last beacon: 64ms ago
          Cell 21 - Address: <MAC 'radio11N' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"radio11N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000159ffa6075a
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'eduroam' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000061c27273e6
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 23 - Address: <MAC 'WolfieNet-Secure' [AC23]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000efc49103b
                    Extra: Last beacon: 5832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC 'WolfieNet-Guest' [AC24]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000efc4911bc
                    Extra: Last beacon: 5832ms ago
          Cell 25 - Address: <MAC 'eduroam' [AC25]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000efc4912f2
                    Extra: Last beacon: 5832ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 26 - Address: <MAC 'WolfieNet-Secure' [AC26]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024c4cfb036
                    Extra: Last beacon: 1400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 27 - Address: <MAC 'WolfieNet-Guest' [AC27]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024c4cfb1b9
                    Extra: Last beacon: 1400ms ago
          Cell 28 - Address: <MAC 'eduroam' [AC28]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024c4cfb2ee
                    Extra: Last beacon: 1400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 29 - Address: <MAC 'WolfieNet-Secure' [AC29]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000169e83e03b
                    Extra: Last beacon: 1120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 30 - Address: <MAC 'eduroam' [AC30]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000169e83e2f2
                    Extra: Last beacon: 1120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 31 - Address: <MAC 'WolfieNet-Secure' [AC31]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001c85903b
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 32 - Address: <MAC 'WolfieNet-Guest' [AC32]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001c8591bc
                    Extra: Last beacon: 1048ms ago
          Cell 33 - Address: <MAC 'eduroam' [AC33]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001c8592f2
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 34 - Address: <MAC 'WolfieNet-Secure' [AC34]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"WolfieNet-Secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000167ebf1036
                    Extra: Last beacon: 472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 35 - Address: <MAC 'WolfieNet-Guest' [AC35]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"WolfieNet-Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000167ebf11b8
                    Extra: Last beacon: 472ms ago
          Cell 36 - Address: <MAC 'eduroam' [AC36]>
                    Channel:161
                    Frequency:5.805 GHz (Channel 161)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000167ebf12ed
                    Extra: Last beacon: 472ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[ath3k]
filename:       /lib/modules/3.13.0-88-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     A49A3D87CA20DB742E336F9
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/3.13.0-88-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1F2BE74683868C04A429DFF
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-88-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-88-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4D7E3FBEBDFF649364222B3
depends:        ath
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-88-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-88-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C31A92A72ADA65F2F8247FB
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-88-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0055529745EF9A8A3E57FC3
depends:        
intree:         Y
vermagic:       3.13.0-88-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6C:03:59:FA:8E:B9:85:6F:D7:35:58:CE:47:3E:79:BB:B7:F3:F8:15
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
blacklist acer-wmi


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


echo 500 > /sys/class/backlight/acpi_video0/brightness


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
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0b95:0x772b (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[ 4638.141370] wlan0: associated
[ 4638.147126] ath: EEPROM regdomain: 0x8348
[ 4638.147131] ath: EEPROM indicates we should expect a country code
[ 4638.147133] ath: doing EEPROM country->regdmn map search
[ 4638.147135] ath: country maps to regdmn code: 0x3a
[ 4638.147137] ath: Country alpha2 being used: US
[ 4638.147139] ath: Regpair used: 0x3a
[ 4638.147141] ath: regdomain 0x8348 dynamically updated by country IE
[ 4638.180332] wlan0: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'WolfieNet-Secure' [AC31]>
[ 7693.619316] wlan0: deauthenticated from <MAC 'WolfieNet-Secure' [AC31]> (Reason: 1)
[ 7694.444384] wlan0: authenticate with <MAC 'WolfieNet-Secure' [AC1]>
[ 7694.458997] wlan0: direct probe to <MAC 'WolfieNet-Secure' [AC1]> (try 1/3)
[ 7694.659677] wlan0: send auth to <MAC 'WolfieNet-Secure' [AC1]> (try 2/3)
[ 7694.661698] wlan0: authenticated
[ 7694.663687] wlan0: associate with <MAC 'WolfieNet-Secure' [AC1]> (try 1/3)
[ 7694.667403] wlan0: RX AssocResp from <MAC 'WolfieNet-Secure' [AC1]> (capab=0x511 status=0 aid=3)
[ 7694.667584] wlan0: associated
[ 7694.675004] ath: EEPROM regdomain: 0x8348
[ 7694.675012] ath: EEPROM indicates we should expect a country code
[ 7694.675017] ath: doing EEPROM country->regdmn map search
[ 7694.675021] ath: country maps to regdmn code: 0x3a
[ 7694.675024] ath: Country alpha2 being used: US
[ 7694.675027] ath: Regpair used: 0x3a
[ 7694.675031] ath: regdomain 0x8348 dynamically updated by country IE
[ 7694.675858] wlan0: Limiting TX power to 36 (36 - 0) dBm as advertised by <MAC 'WolfieNet-Secure' [AC1]>


########## wireless info END ############



```

---

### Post by dan229 on 2016-06-16
I fix the problem finally. In /etc/resolv.conf, the nameserver was set as 127.0.0.1. The internet works after I set it as 8.8.8.8.

---

