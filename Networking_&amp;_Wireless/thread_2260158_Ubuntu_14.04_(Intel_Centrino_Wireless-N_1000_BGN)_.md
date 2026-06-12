---
title: "Ubuntu 14.04 (Intel Centrino Wireless-N 1000 BGN) not connecting on Asus RT-N56U"
date: 2015-01-09
forum: Networking &amp; Wireless
---

### Post by aimee-thomson on 2015-01-09
Hi all,

Toshiba Portege R835-ST6N02 with a Intel Corporation Centrino Wireless-N 1000 card. I dual boot my computer with Ubuntu 14.04 and Windows 7. I just installed a new dual band router in the apartment (Asus RT-N56U), and now the internet isn't working on the Linux side only of my computer. Ubuntu recognizes the network and connects, but there's no internet (pages won't load, etc.). After poking around, I think the problem has to do with my wireless card not supporting 5Ghz (though this doesn't explain why it works on the Windows side). I'd like to keep the 5G band enabled on the router itself for the other people in my apartment. Is there a way to make my wireless connection only connect on the 2.4 Ghz band and/or upgrade my driver so that I can connect to a dual band router? Or is there something else causing the problem? 

Wireless info below.

Thanks! 

```


########## wireless info START ##########


Report from: 09 Jan 2015 14:44 EST -0500


Booted last: 09 Jan 2015 14:20 EST -0500


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


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:0001]
    Kernel driver in use: e1000e


04:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1305]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1bcf:288e Sunplus Innovation Technology Inc. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  1 toshiba_acpi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::eae0:b7ff:fe9d:1054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52372 errors:0 dropped:1 overruns:0 frame:0
          TX packets:26425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60513722 (60.5 MB)  TX bytes:4095466 (4.0 MB)
          Interrupt:20 Memory:c4800000-c4820000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.127  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:bff:fea2:af72/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70262 (70.2 KB)  TX bytes:82320 (82.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"GoldfishRodeo"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'GoldfishRodeo' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:94   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [GoldfishRodeo] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Axalon:          Infra, <MAC 'Axalon' [AC16]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 85 WPA2
    Linksys30371:    Infra, <MAC 'Linksys30371' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    HOME-494A-2.4:   Infra, <MAC 'HOME-494A-2.4' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA WPA2
    DIRECT-roku-5888A9: Infra, <MAC 'DIRECT-roku-5888A9' [AC13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Azante-Guest:    Infra, <MAC 'Azante-Guest' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    Haines_MD:       Infra, <MAC 'Haines_MD' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Linksys18973:    Infra, <MAC 'Linksys18973' [AC22]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    2GPWK:           Infra, <MAC '2GPWK' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2
    Meftish:         Infra, <MAC 'Meftish' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA
    NUTerplink:      Infra, <MAC 'NUTerplink' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Cisco05358:      Infra, <MAC 'Cisco05358' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    NDW4G:           Infra, <MAC 'NDW4G' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    25BZD:           Infra, <MAC '25BZD' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    5T425:           Infra, <MAC '5T425' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN15]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    HP-Print-B4-ENVY 4500 series: Infra, <MAC 'HP-Print-B4-ENVY 4500 series' [AC23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2
    SilverTiger:     Infra, <MAC 'SilverTiger' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Cisco05508:      Infra, <MAC 'Cisco05508' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    L3P72:           Infra, <MAC 'L3P72' [AN19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WEP
    M3CR3:           Infra, <MAC 'M3CR3' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Yogi1:           Infra, <MAC 'Yogi1' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    HOME-CF92:       Infra, <MAC 'HOME-CF92' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    RBDZ5:           Infra, <MAC 'RBDZ5' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN24]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35
    Lindberg:        Infra, <MAC 'Lindberg' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    hippopotamus amphibius: Infra, <MAC 'hippopotamus amphibius' [AN26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    SchmoopyNet:     Infra, <MAC 'SchmoopyNet' [AN27]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 44 WPA2
    ALJOHARH:        Infra, <MAC 'ALJOHARH' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    NETGEAR70:       Infra, <MAC 'NETGEAR70' [AN29]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    sn:              Infra, <MAC 'sn' [AN30]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34
    HOME-9929-2.4:   Infra, <MAC 'HOME-9929-2.4' [AN32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HOME-8E32:       Infra, <MAC 'HOME-8E32' [AN33]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Newsgal :        Infra, <MAC 'Newsgal ' [AN34]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 35 WPA
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50
    AN221:           Infra, <MAC 'AN221' [AN36]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    HOME-A0C0-2.4:   Infra, <MAC 'HOME-A0C0-2.4' [AN37]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    ZackSharon:      Infra, <MAC 'ZackSharon' [AN38]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    SVTJL:           Infra, <MAC 'SVTJL' [AN39]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    VerticalOptimization4: Infra, <MAC 'VerticalOptimization4' [AN40]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN41]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN42]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27
    wendy:           Infra, <MAC 'wendy' [AN43]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    *GoldfishRodeo:  Infra, <MAC 'GoldfishRodeo' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 84 WPA2
    NETGEAR76:       Infra, <MAC 'NETGEAR76' [AN45]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 39 WPA2
    9D8YJ:           Infra, <MAC '9D8YJ' [AN46]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN47]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    mpbebe:          Infra, <MAC 'mpbebe' [AN48]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    Cisco05865:      Infra, <MAC 'Cisco05865' [AN49]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETGEAR1:        Infra, <MAC 'NETGEAR1' [AN50]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN51]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24


  IPv4 Settings:
    Address:         192.168.1.127
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.198
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


[[/etc/NetworkManager/system-connections/WiFius]] (600 root)
[connection] id=WiFius | type=802-11-wireless
[802-11-wireless] ssid=WiFius | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VGS46]] (600 root)
[connection] id=VGS46 | type=802-11-wireless
[802-11-wireless] ssid=VGS46 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MOTOROLA-608B8]] (600 root)
[connection] id=MOTOROLA-608B8 | type=802-11-wireless
[802-11-wireless] ssid=MOTOROLA-608B8 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-8C86]] (600 root)
[connection] id=HOME-8C86 | type=802-11-wireless
[802-11-wireless] ssid=HOME-8C86 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hileywmet 1]] (600 root)
[connection] id=hileywmet 1 | type=802-11-wireless
[802-11-wireless] ssid=hileywmet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/gulaw events]] (600 root)
[connection] id=gulaw events | type=802-11-wireless
[802-11-wireless] ssid=gulaw events | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CCR-WiFi-2]] (600 root)
[connection] id=CCR-WiFi-2 | type=802-11-wireless
[802-11-wireless] ssid=CCR-WiFi-2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TG852G62 1]] (600 root)
[connection] id=TG852G62 1 | type=802-11-wireless
[802-11-wireless] ssid=TG852G62 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SGS WiFi]] (600 root)
[connection] id=SGS WiFi | type=802-11-wireless
[802-11-wireless] ssid=SGS WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SUPER 8]] (600 root)
[connection] id=SUPER 8 | type=802-11-wireless
[802-11-wireless] ssid=SUPER 8 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hileywmet]] (600 root)
[connection] id=hileywmet | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=hileywmet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Crazy Mocha]] (600 root)
[connection] id=Crazy Mocha | type=802-11-wireless
[802-11-wireless] ssid=Crazy Mocha | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/FirehookGuest]] (600 root)
[connection] id=FirehookGuest | type=802-11-wireless
[802-11-wireless] ssid=FirehookGuest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CCR-WiFi-1]] (600 root)
[connection] id=CCR-WiFi-1 | type=802-11-wireless
[802-11-wireless] ssid=CCR-WiFi-1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GSP-Public-WiFi]] (600 root)
[connection] id=GSP-Public-WiFi | type=802-11-wireless
[802-11-wireless] ssid=GSP-Public-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WL_Guest]] (600 root)
[connection] id=WL_Guest | type=802-11-wireless
[802-11-wireless] ssid=WL_Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/nyu]] (600 root)
[ipv6] method=auto
[connection] id=nyu | type=802-11-wireless
[802-11-wireless] ssid=nyu | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hileywmet 2]] (600 root)
[connection] id=hileywmet 2 | type=802-11-wireless
[802-11-wireless] ssid=hileywmet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SS Library Zone1]] (600 root)
[connection] id=SS Library Zone1 | type=802-11-wireless
[802-11-wireless] ssid=SS Library Zone1 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/5T425]] (600 root)
[connection] id=5T425 | type=802-11-wireless
[802-11-wireless] ssid=5T425 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/11FX01259794]] (600 root)
[connection] id=11FX01259794 | type=802-11-wireless
[802-11-wireless] ssid=11FX01259794 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/A_GUEST]] (600 root)
[connection] id=A_GUEST | type=802-11-wireless
[802-11-wireless] ssid=A_GUEST | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/belkin.f7e]] (600 root)
[connection] id=belkin.f7e | type=802-11-wireless
[802-11-wireless] ssid=belkin.f7e | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-3CC8]] (600 root)
[connection] id=HOME-3CC8 | type=802-11-wireless
[802-11-wireless] ssid=HOME-3CC8 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HolidayInnExpress2]] (600 root)
[connection] id=HolidayInnExpress2 | type=802-11-wireless
[802-11-wireless] ssid=HolidayInnExpress2 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/LaQuinta_Macrotech]] (600 root)
[connection] id=LaQuinta_Macrotech | type=802-11-wireless
[802-11-wireless] ssid=LaQuinta_Macrotech | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Gunther - Portable WIFI 5]] (600 root)
[connection] id=Gunther - Portable WIFI 5 | type=802-11-wireless
[802-11-wireless] ssid=Gunther - Portable WIFI 5 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Au Bon Pain]] (600 root)
[connection] id=Au Bon Pain | type=802-11-wireless
[802-11-wireless] ssid=Au Bon Pain | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TG852G62]] (600 root)
[connection] id=TG852G62 | type=802-11-wireless
[802-11-wireless] ssid=TG852G62 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hileywmet 3]] (600 root)
[connection] id=hileywmet 3 | type=802-11-wireless
[802-11-wireless] ssid=hileywmet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CLUBQUARTERS]] (600 root)
[connection] id=CLUBQUARTERS | type=802-11-wireless
[802-11-wireless] ssid=CLUBQUARTERS | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DW]] (600 root)
[connection] id=DW | type=802-11-wireless
[802-11-wireless] ssid=DW | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DCPL_MLK_Public]] (600 root)
[connection] id=DCPL_MLK_Public | type=802-11-wireless
[802-11-wireless] ssid=DCPL_MLK_Public | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/GoldfishRodeo]] (600 root)
[connection] id=GoldfishRodeo | type=802-11-wireless
[802-11-wireless] ssid=GoldfishRodeo | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EPIC2]] (600 root)
[connection] id=EPIC2 | type=802-11-wireless
[802-11-wireless] ssid=EPIC2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hileywment]] (600 root)
[connection] id=hileywment | type=802-11-wireless
[802-11-wireless] ssid=hileywment | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/LV5D2]] (600 root)
[connection] id=LV5D2 | type=802-11-wireless
[802-11-wireless] ssid=LV5D2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/pcfi]] (600 root)
[connection] id=pcfi | type=802-11-wireless
[802-11-wireless] ssid=pcfi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/POGO Guest]] (600 root)
[connection] id=POGO Guest | type=802-11-wireless
[802-11-wireless] ssid=POGO Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TG1672G12]] (600 root)
[connection] id=TG1672G12 | type=802-11-wireless
[802-11-wireless] ssid=TG1672G12 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Axalon]] (600 root)
[connection] id=Axalon | type=802-11-wireless
[802-11-wireless] ssid=Axalon | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Leora's Network]] (600 root)
[connection] id=Leora's Network | type=802-11-wireless
[802-11-wireless] ssid=Leora's Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/cpk_public]] (600 root)
[connection] id=cpk_public | type=802-11-wireless
[802-11-wireless] ssid=cpk_public | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TG852G62 1-db1e0ec3-a7a0-4e0c-87b8-8cc2c4f5253e]] (600 root)
[connection] id=TG852G62 1 | type=802-11-wireless
[802-11-wireless] ssid=TG852G62 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Brandeis]] (600 root)
[connection] id=Brandeis | type=802-11-wireless
[802-11-wireless] ssid=Brandeis | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CPK_Public_WiFi]] (600 root)
[connection] id=CPK_Public_WiFi | type=802-11-wireless
[802-11-wireless] ssid=CPK_Public_WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


Channel occupancy:


      8   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      4   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'GoldfishRodeo' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"GoldfishRodeo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004371dcb4
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027ceffffa67
                    Extra: Last beacon: 932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'xfinitywifi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000027cf0000164
                    Extra: Last beacon: 932ms ago
          Cell 04 - Address: <MAC 'Meftish' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Meftish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000df4fed05c9
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Linksys30371' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Linksys30371"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006613000609
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '2GPWK' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"2GPWK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000581c826011
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Haines_MD' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Haines_MD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004873327ba38
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'R9V7L' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"R9V7L"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b9188b30ad
                    Extra: Last beacon: 36ms ago
          Cell 09 - Address: <MAC 'HOME-F928' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HOME-F928"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030ec4d225a2
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'HOME-494A-2.4' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"HOME-494A-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b6ce106c99
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003b6ce112c0d
                    Extra: Last beacon: 512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'NUTerplink' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"NUTerplink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a6b4e1c7d3
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'DIRECT-roku-5888A9' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-5888A9"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a5ecdfb9a83
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Yogi1' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Yogi1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000581b218c50
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'NDW4G' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NDW4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000585b147916
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Axalon' [AC16]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Axalon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007508160304
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC '' [AC17]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008acc2112a7
                    Extra: Last beacon: 292ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC '' [AC18]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008acc211b09
                    Extra: Last beacon: 292ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC '' [AC19]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026d25c06ac5
                    Extra: Last beacon: 112ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Azante-Guest' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Azante-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006733e3a61e
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'Cisco05508' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Cisco05508"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000031e466608ce
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'Linksys18973' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Linksys18973"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000221776c8cd2
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'HP-Print-B4-ENVY 4500 series' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-B4-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005facf26f142
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
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


[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   24.836503] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   24.844175] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.879889] iwlwifi 0000:04:00.0: L1 Enabled - LTR Disabled
[   24.887141] iwlwifi 0000:04:00.0: Radio type=0x0-0x0-0x3
[   24.939029] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   25.593472] wlan0: authenticate with <MAC 'GoldfishRodeo' [AC1]>
[   25.606591] wlan0: send auth to <MAC 'GoldfishRodeo' [AC1]> (try 1/3)
[   25.609074] wlan0: authenticated
[   25.609200] wlan0: waiting for beacon from <MAC 'GoldfishRodeo' [AC1]>
[   25.625494] wlan0: associate with <MAC 'GoldfishRodeo' [AC1]> (try 1/3)
[   25.634108] wlan0: RX AssocResp from <MAC 'GoldfishRodeo' [AC1]> (capab=0xc11 status=0 aid=3)
[   25.646818] wlan0: associated
[   25.646848] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  215.568584] wlan0: deauthenticating from <MAC 'GoldfishRodeo' [AC1]> by local choice (reason=3)
[ 1351.318699] wlan0: authenticate with <MAC 'GoldfishRodeo' [AC1]>
[ 1351.329998] wlan0: send auth to <MAC 'GoldfishRodeo' [AC1]> (try 1/3)
[ 1351.334685] wlan0: authenticated
[ 1351.336009] wlan0: associate with <MAC 'GoldfishRodeo' [AC1]> (try 1/3)
[ 1351.340111] wlan0: RX AssocResp from <MAC 'GoldfishRodeo' [AC1]> (capab=0xc11 status=0 aid=1)
[ 1351.343614] wlan0: associated


########## wireless info END ############



```

---

### Post by aimee-thomson on 2015-01-12
Anyone?

---

