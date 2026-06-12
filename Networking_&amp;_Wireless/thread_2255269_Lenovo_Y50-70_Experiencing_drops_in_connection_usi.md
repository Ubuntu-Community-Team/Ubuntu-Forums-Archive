---
title: "Lenovo Y50-70 Experiencing drops in connection using intel 7260 and alfa awus03h"
date: 2014-12-03
forum: Networking &amp; Wireless
---

### Post by machinanoctua on 2014-12-03
Hello its been a long time since i have been on here but i am having connectivity issues every 10 minutes or so i have rummaged through the threads on here that ae related but nothing seems to help i am having the issues whether i use my alfa usb device or just my onboard wireless here is my wifi info file .
```

########## wireless info START ##########

Report from: 03 Dec 2014 14:34 EST -0500

Booted last: 02 Dec 2014 23:31 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
    Kernel driver in use: iwlwifi

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 1532:0039 Razer USA, Ltd 
Bus 003 Device 004: ID 8087:07dc Intel Corp. 
Bus 003 Device 003: ID 174f:14b8 Syntek 
Bus 003 Device 011: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
10: phy7: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                189813  0 
rtl8187                64909  0 
mac80211              626557  2 rtl8187,iwlmvm
eeprom_93cx6           13344  1 rtl8187
mxm_wmi                13021  1 nouveau
iwlwifi               169932  1 iwlmvm
cfg80211              484040  4 iwlwifi,mac80211,rtl8187,iwlmvm
wmi                    19177  2 mxm_wmi,nouveau
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

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
          inet addr:192.168.0.24  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::7e7a:91ff:fef2:698f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:212160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123529418 (123.5 MB)  TX bytes:22666946 (22.6 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.22  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:caff:fe47:9986/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:205 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48652 (48.6 KB)  TX bytes:12757 (12.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"Apple Wi-Fi Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Apple Wi-Fi Network' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:50   Missed beacon:0

wlan0     IEEE 802.11abg  ESSID:"Apple Wi-Fi Network"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'Apple Wi-Fi Network' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:59   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan1  [Apple Wi-Fi Network] -----------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    2WIRE445:        Infra, <MAC '2WIRE445' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
     Trojan Virus :  Infra, <MAC ' Trojan Virus ' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    2WIRE738:        Infra, <MAC '2WIRE738' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Baker:           Infra, <MAC 'Baker' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    HOME-655A-2.4:   Infra, <MAC 'HOME-655A-2.4' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    DIRECT-roku-461: Infra, <MAC 'DIRECT-roku-461' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 95 WPA2
    Hart Home:       Infra, <MAC 'Hart Home' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    HOME-D531-2.4:   Infra, <MAC 'HOME-D531-2.4' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    FCC Van 5:       Infra, <MAC 'FCC Van 5' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    GPS_Cribs:       Infra, <MAC 'GPS_Cribs' [AC7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    HOME-2EFF:       Infra, <MAC 'HOME-2EFF' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    ATT1055:         Infra, <MAC 'ATT1055' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 99
    HP-nomodel.8901F0: Ad-Hoc, <MAC 'HP-nomodel.8901F0' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77
    *Apple Wi-Fi Network: Infra, <MAC 'Apple Wi-Fi Network' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA2
    2WIRE880:        Infra, <MAC '2WIRE880' [AC12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    HOME-ACC8:       Infra, <MAC 'HOME-ACC8' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
    belkin.9b0:      Infra, <MAC 'belkin.9b0' [AC5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    Tennvolss:       Infra, <MAC 'Tennvolss' [AC15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 97 WPA WPA2
    HOME-9EF2:       Infra, <MAC 'HOME-9EF2' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    HOME-7CCE:       Infra, <MAC 'HOME-7CCE' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.22
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

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

- Device: wlan0  [Apple Wi-Fi Network 1] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
     Trojan Virus -5G: Infra, <MAC ' Trojan Virus -5G' [AC24]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 64 WPA2
     Trojan Virus :  Infra, <MAC ' Trojan Virus ' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    HOME-655A-5:     Infra, <MAC 'HOME-655A-5' [AC13]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    HOME-D531-5:     Infra, <MAC 'HOME-D531-5' [AC14]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    Cisco_960E1B1B:  Infra, <MAC 'Cisco_960E1B1B' [AC15]>, Freq 5560 MHz, Rate 54 Mb/s, Strength 20 WPA2
    2WIRE738:        Infra, <MAC '2WIRE738' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    2WIRE445:        Infra, <MAC '2WIRE445' [AC8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    Baker:           Infra, <MAC 'Baker' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 70 WPA
    Hart Home:       Infra, <MAC 'Hart Home' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    Tennvolss:       Infra, <MAC 'Tennvolss' [AC15]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    HOME-2EFF:       Infra, <MAC 'HOME-2EFF' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    belkin.9b0:      Infra, <MAC 'belkin.9b0' [AC5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    2WIRE880:        Infra, <MAC '2WIRE880' [AC12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75
    HOME-655A-2.4:   Infra, <MAC 'HOME-655A-2.4' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    DIRECT-roku-461: Infra, <MAC 'DIRECT-roku-461' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 69 WPA2
    FCC Van 5:       Infra, <MAC 'FCC Van 5' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    xfinitywifi:     Infra, <MAC 'FCC Van 5' [AN39]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    HOME-9EF2:       Infra, <MAC 'HOME-9EF2' [AN20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HOME-D531-2.4:   Infra, <MAC 'HOME-D531-2.4' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    xfinitywifi:     Infra, <MAC 'HOME-D531-2.4' [AN42]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39
    GPS_Cribs:       Infra, <MAC 'GPS_Cribs' [AC7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    HOME-E9DA:       Infra, <MAC 'GPS_Cribs' [AN44]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    ATT7I5A5S7:      Infra, <MAC 'HOME-E9DA' [AN45]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    HOME-8C59:       Infra, <MAC 'HOME-8C59' [AC14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    xfinitywifi:     Infra, <MAC 'HOME-8C59' [AN47]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    Apple Wi-Fi Network: Infra, <MAC 'Apple Wi-Fi Network' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2
    ATT456:          Infra, <MAC 'Apple Wi-Fi Network' [AN49]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    HOME-ACC8:       Infra, <MAC 'HOME-ACC8' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    FCC Van 5:       Infra, <MAC 'FCC Van 5' [AC25]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    UFD:             Infra, <MAC 'UFD' [AC26]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    ATTuiRanFi:      Infra, <MAC 'UFD' [AN53]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    xfinitywifi:     Infra, <MAC 'ATTuiRanFi' [AN54]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    HOME-1BC2:       Infra, <MAC 'xfinitywifi' [AN55]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.24
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

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

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HOME-1A9B-2.4]] (600 root)
[connection] id=HOME-1A9B-2.4 | type=802-11-wireless
[802-11-wireless] ssid=HOME-1A9B-2.4 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATT711]] (600 root)
[connection] id=ATT711 | type=802-11-wireless
[802-11-wireless] ssid=ATT711 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AMnetwork 1]] (600 root)
[connection] id=AMnetwork 1 | type=802-11-wireless
[802-11-wireless] ssid=AMnetwork | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-8E52]] (600 root)
[connection] id=HOME-8E52 | type=802-11-wireless
[802-11-wireless] ssid=HOME-8E52 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HP-nomodel.8901F0-db860ed9-06e0-45e7-ab46-de86fad9bb01]] (600 root)
[connection] id=HP-nomodel.8901F0 | type=802-11-wireless
[802-11-wireless] ssid=HP-nomodel.8901F0 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HP-nomodel.8901F0]] (600 root)
[connection] id=HP-nomodel.8901F0 | type=802-11-wireless
[802-11-wireless] ssid=HP-nomodel.8901F0 | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/GreensTavern-2.4]] (600 root)
[connection] id=GreensTavern-2.4 | type=802-11-wireless
[802-11-wireless] ssid=GreensTavern-2.4 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/epson-setup-00000125]] (600 root)
[connection] id=epson-setup-00000125 | type=802-11-wireless
[802-11-wireless] ssid=epson-setup-00000125 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT7917]] (600 root)
[connection] id=ATT7917 | type=802-11-wireless
[802-11-wireless] ssid=ATT7917 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Baker]] (600 root)
[connection] id=Baker | type=802-11-wireless
[802-11-wireless] ssid=Baker | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi 1]] (600 root)
[connection] id=xfinitywifi 1 | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/2WIRE445]] (600 root)
[connection] id=2WIRE445 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE445 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR07 1]] (600 root)
[connection] id=NETGEAR07 1 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR07 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/belkin.0e6.guests]] (600 root)
[connection] id=belkin.0e6.guests | type=802-11-wireless
[802-11-wireless] ssid=belkin.0e6.guests | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ Trojan Virus ]] (600 root)
[connection] id=\sTrojan Virus  | type=802-11-wireless
[802-11-wireless] ssid=\sTrojan Virus  | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Apple Wi-Fi Network]] (600 root)
[connection] id=Apple Wi-Fi Network | type=802-11-wireless
[802-11-wireless] ssid=Apple Wi-Fi Network | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HP-Print-A7-Officejet 6600]] (600 root)
[connection] id=HP-Print-A7-Officejet 6600 | type=802-11-wireless
[802-11-wireless] ssid=HP-Print-A7-Officejet 6600 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR07-5G]] (600 root)
[connection] id=NETGEAR07-5G | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR07-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR07]] (600 root)
[connection] id=NETGEAR07 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR07 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR44]] (600 root)
[connection] id=NETGEAR44 | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR44 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-D531-2.4]] (600 root)
[connection] id=HOME-D531-2.4 | type=802-11-wireless
[802-11-wireless] ssid=HOME-D531-2.4 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AMnetwork]] (600 root)
[connection] id=AMnetwork | type=802-11-wireless
[802-11-wireless] ssid=AMnetwork | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR71-5G]] (600 root)
[connection] id=NETGEAR71-5G | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR71-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Verizon-SCH-I605-360B]] (600 root)
[connection] id=Verizon-SCH-I605-360B | type=802-11-wireless
[802-11-wireless] ssid=Verizon-SCH-I605-360B | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Apple Wi-Fi Network 1]] (600 root)
[connection] id=Apple Wi-Fi Network 1 | type=802-11-wireless
[802-11-wireless] ssid=Apple Wi-Fi Network | mac-address=<MAC 'wlan0' [IF]>
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
          Current Frequency:2.437 GHz (Channel 6)

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
          Current Frequency:5.18 GHz (Channel 36)

##### iwlist scan #######################

Channel occupancy:

      9   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.422 GHz (Channel 3)
      4   APs on   Frequency:2.427 GHz (Channel 4)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.452 GHz (Channel 9)
      7   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      1   APs on   Frequency:5.56 GHz (Channel 112)
      4   APs on   Frequency:5.765 GHz (Channel 153)
      1   APs on   Frequency:5.785 GHz (Channel 157)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Apple Wi-Fi Network' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Apple Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b336f9b809
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HOME-7CCE' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"HOME-7CCE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f5e2f53d2
                    Extra: Last beacon: 18888ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DIRECT-roku-461' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-461"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b336edca50
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Hart Home' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"Hart Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b3726257b
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'belkin.9b0' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"belkin.9b0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001feeb7648
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b37264895
                    Extra: Last beacon: 0ms ago
          Cell 07 - Address: <MAC 'GPS_Cribs' [AC7]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GPS_Cribs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000063ac64d40
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC '2WIRE445' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"2WIRE445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002ef81e2a
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'FCC Van 5' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"FCC Van 5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038521963b7
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'HOME-D531-2.4' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"HOME-D531-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b33123d6c4
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC ' Trojan Virus ' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:" Trojan Virus "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000061cf220a76
                    Extra: Last beacon: 18888ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC '2WIRE880' [AC12]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"2WIRE880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2546e3762
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'HOME-655A-2.4' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"HOME-655A-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2add6cf4a
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'HOME-8C59' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"HOME-8C59"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b32e984ff6
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Tennvolss' [AC15]>
             eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

       Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Tennvolss"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002206df9a
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Baker' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"Baker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2383512bb
                    Extra: Last beacon: 0ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Apple Wi-Fi Network' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Apple Wi-Fi Network"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3373980aa
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HOME-2EFF' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"HOME-2EFF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b32f7fe0c8
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'belkin.9b0' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"belkin.9b0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ff25fcf6
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '2WIRE445' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"2WIRE445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002f2c8153
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DIRECT-roku-461' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-461"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b337221ac9
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FCC Van 5' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FCC Van 5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000385239902c
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Apple Wi-Fi Network' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Apple Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b337223fce
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Tennvolss' [AC15]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Tennvolss"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000221c2f61
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '2WIRE880' [AC12]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"2WIRE880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b25482d999
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC ' Trojan Virus ' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:" Trojan Virus "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000061d04a0ae4
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HOME-655A-2.4' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"HOME-655A-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2addecb6c
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Baker' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"Baker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2383d2071
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'HOME-655A-5' [AC13]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"HOME-655A-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b2addde4cb
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'HOME-D531-5' [AC14]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"HOME-D531-5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3311b46c6
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Cisco_960E1B1B' [AC15]>
                    Channel:112
                    Frequency:5.56 GHz (Channel 112)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Cisco_960E1B1B"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b339dfc2ee
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Hart Home' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Hart Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b376e4d1e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b376e7fd0
                    Extra: Last beacon: 84ms ago
          Cell 18 - Address: <MAC 'HOME-8C59' [AC14]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"HOME-8C59"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b32edfd7e0
                    Extra: Last beacon: 3232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009b376e6355
                    Extra: Last beacon: 3204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'GPS_Cribs' [AC7]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"GPS_Cribs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000063b01e181
                    Extra: Last beacon: 3180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC '\00\00\00\00\00\00\00' [AC21]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023331bc3ea
                    Extra: Last beacon: 3116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'HOME-D531-2.4' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"HOME-D531-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b3314c3603
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ac5e46c477
                    Extra: Last beacon: 2852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC ' Trojan Virus -5G' [AC24]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:" Trojan Virus -5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000061d01a3734
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'FCC Van 5' [AC25]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"FCC Van 5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038526c1e6f
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'UFD' [AC26]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"UFD"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000038526c20c2
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'NETGEAR07-5G' [AC27]>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR07-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b337f9cdce
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'Cisco_7DE2E8C5' [AC28]>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Cisco_7DE2E8C5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b339522298
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     7AF85C9FBD17AD993F1CC33
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[rtl8187]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     A707FEC6B464A70F7A04C69
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     123C230E7AC85A31E4CA28B
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-40-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     32519C773C87BE82120EF0D
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
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
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
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
11n_disable: 1
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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b2 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[53802.157010] ieee80211 phy6: hwaddr <MAC 'wlan1' [IF]>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[53802.165058] rtl8187: Customer ID is 0xFF
[53802.165368] rtl8187: wireless switch is on
[53804.039299] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[53806.606224] wlan1: authenticate with <MAC 'xfinitywifi' [AC6]>
[53806.762363] wlan1: send auth to <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53806.764681] wlan1: authenticated
[53806.768524] wlan1: associate with <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53806.770886] wlan1: RX AssocResp from <MAC 'xfinitywifi' [AC6]> (capab=0x421 status=0 aid=1)
[53806.771674] wlan1: associated
[53806.771699] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[53806.772030] wlan1: deauthenticating from <MAC 'xfinitywifi' [AC6]> by local choice (reason=2)
[53806.825512] wlan1: authenticate with <MAC 'xfinitywifi' [AC6]>
[53806.877902] wlan1: send auth to <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53806.889349] wlan1: authenticated
[53806.892620] wlan1: associate with <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53806.894830] wlan1: RX AssocResp from <MAC 'xfinitywifi' [AC6]> (capab=0x421 status=0 aid=1)
[53806.895418] wlan1: associated
[53816.906198] wlan1: deauthenticating from <MAC 'xfinitywifi' [AC6]> by local choice (reason=3)
[53829.671358] wlan1: authenticate with <MAC 'xfinitywifi' [AC6]>
[53829.824517] wlan1: send auth to <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53829.827169] wlan1: authenticated
[53829.831188] wlan1: associate with <MAC 'xfinitywifi' [AC6]> (try 1/3)
[53829.842623] wlan1: RX AssocResp from <MAC 'xfinitywifi' [AC6]> (capab=0x421 status=0 aid=1)
[53829.843599] wlan1: associated
[53843.756514] wlan1: deauthenticating from <MAC 'xfinitywifi' [AC6]> by local choice (reason=3)
[53846.963215] wlan0: deauthenticating from <MAC 'Apple Wi-Fi Network' [AC1]> by local choice (reason=3)
[53850.229348] wlan0: authenticate with <MAC 'Apple Wi-Fi Network' [AC1]>
[53850.231578] wlan0: send auth to <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53850.232045] wlan0: authenticated
[53850.235805] wlan0: associate with <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53850.240568] wlan0: RX AssocResp from <MAC 'Apple Wi-Fi Network' [AC1]> (capab=0x1511 status=0 aid=2)
[53850.241080] wlan0: associated
[53850.309621] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'Apple Wi-Fi Network' [AC1]>
[53858.489457] wlan0: deauthenticating from <MAC 'Apple Wi-Fi Network' [AC1]> by local choice (reason=3)
[53861.707970] wlan0: authenticate with <MAC 'Apple Wi-Fi Network' [AC1]>
[53861.710179] wlan0: send auth to <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53861.710622] wlan0: authenticated
[53861.712995] wlan0: associate with <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53861.717747] wlan0: RX AssocResp from <MAC 'Apple Wi-Fi Network' [AC1]> (capab=0x1511 status=0 aid=2)
[53861.718252] wlan0: associated
[53861.787749] wlan0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'Apple Wi-Fi Network' [AC1]>
[53872.349567] ieee80211 phy7: hwaddr <MAC 'wlan1' [IF]>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[53872.357701] rtl8187: Customer ID is 0xFF
[53872.358110] rtl8187: wireless switch is on
[53874.232836] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[53876.808101] wlan1: authenticate with <MAC 'Apple Wi-Fi Network' [AC1]>
[53877.019678] wlan1: send auth to <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53877.021322] wlan1: authenticated
[53877.022034] wlan1: associate with <MAC 'Apple Wi-Fi Network' [AC1]> (try 1/3)
[53877.032987] wlan1: RX AssocResp from <MAC 'Apple Wi-Fi Network' [AC1]> (capab=0x1431 status=0 aid=1)
[53877.033874] wlan1: associated
[53877.033906] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

########## wireless info END ############


```

---

### Post by claudia.aguiar on 2014-12-06
Have you tried:

Code:
```
$sudo iw wlan0 set power_save off
```

It solved my problem with connection in a Lenovo g40 70 and Ubuntu 14.04.1 LTS

---

