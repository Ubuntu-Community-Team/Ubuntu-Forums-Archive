---
title: "Upgrading 12.04 to 14.04, then frequently disconnecting wifi"
date: 2015-08-20
forum: Networking &amp; Wireless
---

### Post by JinwooGo on 2015-08-20
Hi

After upgrading from 12.04 to 14.04 I have the problem with Wifi

and the Wifi script is below. 

What is the problem?

---

### Post by Bucky Ball on 2015-08-21
Welcome. Please post the script between code tags in a post (see the link in my thread for how). Thanks. Some users are unwilling to download and open files from unknown sources, saves time, and improves your chances of support.

---

### Post by JinwooGo on 2015-08-23
Thank you for your suggestion.

And the below is the attachment file.

```

########## wireless info START ##########


Report from: 21 Aug 2015 11:37 KST +0900


Booted last: 21 Aug 2015 11:27 KST +0900


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-62-generic #102-Ubuntu SMP Tue Aug 11 14:29:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 93)
    Subsystem: Intel Corporation Device [8086:5070]
    Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c109]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 004: ID 2232:1059  
Bus 002 Device 002: ID 3938:1032  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                189852  0 
mac80211              630728  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
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
          inet addr:172.30.7.85  Bcast:172.30.255.255  Mask:255.255.0.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:476 errors:0 dropped:0 overruns:0 frame:0
          TX packets:670 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187813 (187.8 KB)  TX bytes:109789 (109.7 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"ollehWiFi_SNU"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'ollehWiFi_SNU' [AC1]>   
          Bit Rate=86.7 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.30.1.254    0.0.0.0         UG    0      0        0 wlan0
172.30.0.0      0.0.0.0         255.255.0.0     U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       812     1  0 11:27 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


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


- Device: wlan0  [ollehWiFi_SNU] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           78 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AC15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    DIRECT-UlCLX-4190 Series: Infra, <MAC 'DIRECT-UlCLX-4190 Series' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 65 WPA2
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN3]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2 Enterprise
    EASTBLUE:        Infra, <MAC 'EASTBLUE' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2
    iptime 308:      Infra, <MAC 'iptime 308' [AC2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 40 WPA2
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AC34]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    SCM_Lab5G:       Infra, <MAC 'SCM_Lab5G' [AC23]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AN8]>, Freq 5580 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2 Enterprise
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AC16]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 72
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN10]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 70
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 72
    iptime:          Infra, <MAC 'iptime' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    T wifi zone:     Infra, <MAC 'T wifi zone' [AN14]>, Freq 5580 MHz, Rate 54 Mb/s, Strength 7
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AC6]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2 Enterprise
    LET:             Infra, <MAC 'LET' [AN16]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    SNU_SPRC:        Infra, <MAC 'SNU_SPRC' [AN17]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 60 WPA
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AN18]>, Freq 5500 MHz, Rate 54 Mb/s, Strength 5 WPA WPA2 Enterprise
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AC26]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN20]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 75
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AC29]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 34
    T wifi zone:     Infra, <MAC 'T wifi zone' [AC20]>, Freq 5580 MHz, Rate 54 Mb/s, Strength 2
    T wifi zone:     Infra, <MAC 'T wifi zone' [AC27]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 60
    T wifi zone:     Infra, <MAC 'T wifi zone' [AC22]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 37
    39-309:          Infra, <MAC '39-309' [AN25]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AC30]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 70
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN27]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2 Enterprise
    DIRECT-sSC460 Series: Infra, <MAC 'DIRECT-sSC460 Series' [AN28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA2
    sisulteam5:      Infra, <MAC 'sisulteam5' [AC24]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN30]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39
    T wifi zone:     Infra, <MAC 'T wifi zone' [AC12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 48
    new-weblab:      Infra, <MAC 'new-weblab' [AN32]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA2
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN33]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 Enterprise
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AC32]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 64
    T wifi zone:     Infra, <MAC 'T wifi zone' [AN35]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN36]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2 Enterprise
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AC5]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2 Enterprise
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN38]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2 Enterprise
    WebLab:          Infra, <MAC 'WebLab' [AN39]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WEP
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN40]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 62
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN41]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN42]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    portthru:        Ad-Hoc, <MAC 'portthru' [AN43]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN44]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 64
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AN45]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AN46]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AC19]>, Freq 5580 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2 Enterprise
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN48]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 42
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN49]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AC14]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32
    SNU-1st-time:    Infra, <MAC 'SNU-1st-time' [AN51]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN52]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 40
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AN53]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 34
    *ollehWiFi_SNU:  Infra, <MAC 'ollehWiFi_SNU' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 61
    38-327(2.4GHz):  Infra, <MAC '38-327(2.4GHz)' [AN55]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA2
    LAUS:            Infra, <MAC 'LAUS' [AN56]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA2
    engineering:     Infra, <MAC 'engineering' [AN57]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    iptime5G:        Infra, <MAC 'iptime5G' [AC21]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 29
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN59]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AN60]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25
    SCM_Lab:         Infra, <MAC 'SCM_Lab' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2 Enterprise
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AC11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2 Enterprise
    ollehWiFi:       Infra, <MAC 'ollehWiFi' [AC9]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2 Enterprise
    T wifi zone_secure: Infra, <MAC 'T wifi zone_secure' [AC13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2 Enterprise
    ollehWiFi :      Infra, <MAC 'ollehWiFi ' [AC10]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 37
    ollehWiFi_SNU:   Infra, <MAC 'ollehWiFi_SNU' [AC8]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 35


  IPv4 Settings:
    Address:         172.30.7.85
    Prefix:          16 (255.255.0.0)
    Gateway:         172.30.1.254


    DNS:             168.126.63.1
    DNS:             168.126.63.2


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


[[/etc/NetworkManager/system-connections/38-323]] (600 root)
[connection] id=38-323 | type=802-11-wireless
[802-11-wireless] ssid=38-323 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/cafebene]] (600 root)
[connection] id=cafebene | type=802-11-wireless
[802-11-wireless] ssid=cafebene | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SNU-Member]] (600 root)
[ipv6] method=auto
[connection] id=SNU-Member | type=802-11-wireless
[802-11-wireless] ssid=SNU-Member | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AndroidHotspot1381]] (600 root)
[connection] id=AndroidHotspot1381 | type=802-11-wireless
[802-11-wireless] ssid=AndroidHotspot1381 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/316_1]] (600 root)
[connection] id=316_1 | type=802-11-wireless
[802-11-wireless] ssid=316_1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/petro]] (600 root)
[connection] id=petro | type=802-11-wireless
[802-11-wireless] ssid=petro | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/301-306]] (600 root)
[connection] id=301-306 | type=802-11-wireless
[802-11-wireless] ssid=301-306 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/AndroidHotspot8806]] (600 root)
[connection] id=AndroidHotspot8806 | type=802-11-wireless
[802-11-wireless] ssid=AndroidHotspot8806 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ollehWiFi_SNU]] (600 root)
[connection] id=ollehWiFi_SNU | type=802-11-wireless
[802-11-wireless] ssid=ollehWiFi_SNU | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SNU-1st-time]] (600 root)
[connection] id=SNU-1st-time | type=802-11-wireless
[802-11-wireless] ssid=SNU-1st-time | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ENI-2]] (600 root)
[connection] id=ENI-2 | type=802-11-wireless
[802-11-wireless] ssid=ENI-2 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/iptime]] (600 root)
[connection] id=iptime | type=802-11-wireless
[802-11-wireless] ssid=iptime | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Math_AP_27_2F_1]] (600 root)
[connection] id=Math_AP_27_2F_1 | type=802-11-wireless
[802-11-wireless] ssid=Math_AP_27_2F_1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/microstrategy]] (600 root)
[connection] id=microstrategy | type=802-11-wireless
[802-11-wireless] ssid=microstrategy | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/301-305]] (600 root)
[connection] id=301-305 | type=802-11-wireless
[802-11-wireless] ssid=301-305 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SCSC]] (600 root)
[connection] id=SCSC | type=802-11-wireless
[802-11-wireless] ssid=SCSC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/iptime 1]] (600 root)
[connection] id=iptime 1 | type=802-11-wireless
[802-11-wireless] ssid=iptime | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SCSC_GUEST]] (600 root)
[connection] id=SCSC_GUEST | type=802-11-wireless
[802-11-wireless] ssid=SCSC_GUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/NetweeN]] (600 root)
[connection] id=NetweeN | type=802-11-wireless
[802-11-wireless] ssid=NetweeN | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/subway]] (600 root)
[connection] id=subway | type=802-11-wireless
[802-11-wireless] ssid=subway | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/T wifi zone]] (600 root)
[connection] id=T wifi zone | type=802-11-wireless
[802-11-wireless] ssid=T wifi zone | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/U+NetEC73]] (600 root)
[connection] id=U+NetEC73 | type=802-11-wireless
[802-11-wireless] ssid=U+NetEC73 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Seoul (based on set time zone)


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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      21   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)
      2   APs on   Frequency:5.58 GHz (Channel 116)
      1   APs on   Frequency:5.745 GHz
      2   APs on   Frequency:5.785 GHz
      1   APs on   Frequency:5.805 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'ollehWiFi_SNU' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi_SNU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007e9988ed
                    Extra: Last beacon: 0ms ago
          Cell 02 - Address: <MAC 'iptime 308' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"iptime 308"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000d302fab1199
                    Extra: Last beacon: 26920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SCM_Lab' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"SCM_Lab"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006c1359d64a4
                    Extra: Last beacon: 22596ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'DIRECT-UlCLX-4190 Series' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-UlCLX-4190 Series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064769e793c
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'T wifi zone_secure' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"T wifi zone_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000528db2a82
                    Extra: Last beacon: 26680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'ollehWiFi' [AC6]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"ollehWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000735b40b1
                    Extra: Last beacon: 26672ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'T wifi zone_secure' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"T wifi zone_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e32d9df3
                    Extra: Last beacon: 3720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'ollehWiFi_SNU' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi_SNU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000761da520
                    Extra: Last beacon: 26664ms ago
          Cell 09 - Address: <MAC 'ollehWiFi' [AC9]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ollehWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000053fc0356
                    Extra: Last beacon: 26660ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC 'ollehWiFi ' [AC10]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b182304d
                    Extra: Last beacon: 26660ms ago
          Cell 11 - Address: <MAC 'ollehWiFi' [AC11]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ollehWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002d1e2d0
                    Extra: Last beacon: 26660ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC 'T wifi zone' [AC12]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"T wifi zone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005015773fc
                    Extra: Last beacon: 26656ms ago
          Cell 13 - Address: <MAC 'T wifi zone_secure' [AC13]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"T wifi zone_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004b9c2bc96
                    Extra: Last beacon: 26648ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'ollehWiFi ' [AC14]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000051f2220b
                    Extra: Last beacon: 26644ms ago
          Cell 15 - Address: <MAC 'ollehWiFi' [AC15]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"ollehWiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007e998463
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 16 - Address: <MAC 'ollehWiFi ' [AC16]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000074b7c609
                    Extra: Last beacon: 0ms ago
          Cell 17 - Address: <MAC 'iptime' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000022e4652228
                    Extra: Last beacon: 0ms ago
          Cell 18 - Address: <MAC 'EASTBLUE' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"EASTBLUE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026a9b34ad77
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'T wifi zone_secure' [AC19]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"T wifi zone_secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004fe85903b
                    Extra: Last beacon: 1556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 20 - Address: <MAC 'T wifi zone' [AC20]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:off
                    ESSID:"T wifi zone"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004b59a603b
                    Extra: Last beacon: 24284ms ago
          Cell 21 - Address: <MAC 'iptime5G' [AC21]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"iptime5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003ee269b28d4
                    Extra: Last beacon: 22596ms ago
          Cell 22 - Address: <MAC 'T wifi zone' [AC22]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"T wifi zone"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e344dc0f
                    Extra: Last beacon: 22596ms ago
          Cell 23 - Address: <MAC 'SCM_Lab5G' [AC23]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"SCM_Lab5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000006c135ce48b3
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'sisulteam5' [AC24]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"sisulteam5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013eb30ad34b
                    Extra: Last beacon: 3988ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'T wifi zone' [AC25]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"T wifi zone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000052a378180
                    Extra: Last beacon: 3796ms ago
          Cell 26 - Address: <MAC 'ollehWiFi ' [AC26]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007e99875a
                    Extra: Last beacon: 4ms ago
          Cell 27 - Address: <MAC 'T wifi zone' [AC27]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"T wifi zone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e489db5e
                    Extra: Last beacon: 4ms ago
          Cell 28 - Address: <MAC 'ollehWiFi ' [AC28]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055587f7a
                    Extra: Last beacon: 3780ms ago
          Cell 29 - Address: <MAC 'ollehWiFi ' [AC29]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008bbbe717
                    Extra: Last beacon: 3772ms ago
          Cell 30 - Address: <MAC 'ollehWiFi_SNU' [AC30]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi_SNU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000007b3c7086
                    Extra: Last beacon: 3772ms ago
          Cell 31 - Address: <MAC 'ollehWiFi ' [AC31]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi "
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013454d076
                    Extra: Last beacon: 3772ms ago
          Cell 32 - Address: <MAC 'ollehWiFi_SNU' [AC32]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"ollehWiFi_SNU"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003df36152
                    Extra: Last beacon: 3772ms ago
          Cell 33 - Address: <MAC 'engineering' [AC33]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"engineering"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000010f74e221d8
                    Extra: Last beacon: 3500ms ago
          Cell 34 - Address: <MAC 'T wifi zone_secure' [AC34]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"T wifi zone_secure"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004e49e503b
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     2ED88DF9FE06B5CF295C51A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.13.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8D081A0C2EE28771C5194E1
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.13.0-62-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     A45BAACCAD263355629DB7A
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
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
filename:       /lib/modules/3.13.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-62-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E0:7C:FC:BE:E8:34:59:BA:45:54:3D:39:B2:C2:A5:78:75:74:50:01
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.814306] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    4.829353] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    8.373903] wlan0: authenticate with <MAC 'T wifi zone' [AC22]>
[    8.376764] wlan0: send auth to <MAC 'T wifi zone' [AC22]> (try 1/3)
[    8.378257] wlan0: authenticated
[    8.381389] wlan0: associate with <MAC 'T wifi zone' [AC22]> (try 1/3)
[    8.383285] wlan0: RX AssocResp from <MAC 'T wifi zone' [AC22]> (capab=0x401 status=0 aid=1)
[    8.384137] wlan0: associated
[    8.384157] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.075181] wlan0: authenticate with <MAC 'T wifi zone' [AC25]>
[   32.075949] wlan0: direct probe to <MAC 'T wifi zone' [AC25]> (try 1/3)
[   32.278839] wlan0: direct probe to <MAC 'T wifi zone' [AC25]> (try 2/3)
[   32.481636] wlan0: direct probe to <MAC 'T wifi zone' [AC25]> (try 3/3)
[   32.685058] wlan0: authentication with <MAC 'T wifi zone' [AC25]> timed out
[   33.004886] wlan0: authenticate with <MAC 'T wifi zone' [AC22]>
[   33.008086] wlan0: send auth to <MAC 'T wifi zone' [AC22]> (try 1/3)
[   33.009366] wlan0: authenticated
[   33.013300] wlan0: associate with <MAC 'T wifi zone' [AC22]> (try 1/3)
[   33.015129] wlan0: RX AssocResp from <MAC 'T wifi zone' [AC22]> (capab=0x401 status=0 aid=1)
[   33.016052] wlan0: associated
[   75.281078] wlan0: authenticate with <MAC 'T wifi zone' [AC27]>
[   75.282013] wlan0: direct probe to <MAC 'T wifi zone' [AC27]> (try 1/3)
[   75.484504] wlan0: direct probe to <MAC 'T wifi zone' [AC27]> (try 2/3)
[   75.690514] wlan0: direct probe to <MAC 'T wifi zone' [AC27]> (try 3/3)
[   75.892007] wlan0: authentication with <MAC 'T wifi zone' [AC27]> timed out
[   76.268536] wlan0: authenticate with <MAC 'T wifi zone' [AC22]>
[   76.271313] wlan0: send auth to <MAC 'T wifi zone' [AC22]> (try 1/3)
[   76.272608] wlan0: authenticated
[   76.276232] wlan0: associate with <MAC 'T wifi zone' [AC22]> (try 1/3)
[   76.278065] wlan0: RX AssocResp from <MAC 'T wifi zone' [AC22]> (capab=0x401 status=0 aid=1)
[   76.279278] wlan0: associated
[  221.224046] wlan0: authenticate with <MAC 'T wifi zone' [AC12]>
[  221.224989] wlan0: direct probe to <MAC 'T wifi zone' [AC12]> (try 1/3)
[  221.426876] wlan0: direct probe to <MAC 'T wifi zone' [AC12]> (try 2/3)
[  221.630910] wlan0: send auth to <MAC 'T wifi zone' [AC12]> (try 3/3)
[  221.636276] wlan0: authenticated
[  221.637651] wlan0: associate with <MAC 'T wifi zone' [AC12]> (try 1/3)
[  221.741253] wlan0: RX AssocResp from <MAC 'T wifi zone' [AC12]> (capab=0x421 status=0 aid=1)
[  221.746605] wlan0: associated
[  533.585206] wlan0: deauthenticating from <MAC 'T wifi zone' [AC12]> by local choice (reason=3)
[  536.942415] wlan0: authenticate with <MAC 'ollehWiFi_SNU' [AN48]>
[  536.945091] wlan0: direct probe to <MAC 'ollehWiFi_SNU' [AN48]> (try 1/3)
[  537.149700] wlan0: direct probe to <MAC 'ollehWiFi_SNU' [AN48]> (try 2/3)
[  537.353698] wlan0: direct probe to <MAC 'ollehWiFi_SNU' [AN48]> (try 3/3)
[  537.556773] wlan0: authentication with <MAC 'ollehWiFi_SNU' [AN48]> timed out
[  537.731847] wlan0: authenticate with <MAC 'ollehWiFi_SNU' [AC1]>
[  537.734123] wlan0: send auth to <MAC 'ollehWiFi_SNU' [AC1]> (try 1/3)
[  537.837897] wlan0: send auth to <MAC 'ollehWiFi_SNU' [AC1]> (try 2/3)
[  537.848391] wlan0: authenticated
[  537.849000] wlan0: associate with <MAC 'ollehWiFi_SNU' [AC1]> (try 1/3)
[  537.852343] wlan0: RX AssocResp from <MAC 'ollehWiFi_SNU' [AC1]> (capab=0x401 status=0 aid=3)
[  537.853457] wlan0: associated


########## wireless info END ############

```

---

