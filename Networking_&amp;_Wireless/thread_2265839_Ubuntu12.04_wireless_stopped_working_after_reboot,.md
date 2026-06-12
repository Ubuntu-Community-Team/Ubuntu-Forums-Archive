---
title: "Ubuntu12.04 wireless stopped working after reboot, connection seems to be established"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by eto2 on 2015-02-18
Hi all,

after 6 month of running without problems, my wireless connection stopped working from one evening to the next day. I haven't updated or changed anything inbetween. Here is the output of the "wireless_info_script". Thank you million times in advance!

```

########## wireless info START ##########

Report from: 19 Feb 2015 01:15 CST +0800

Booted last: 19 Feb 2015 01:13 CST +0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:25:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I218-LM [8086:155a] (rev 04)
    Subsystem: Dell Device [1028:05cb]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4470]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 1bcf:053a Sunplus Innovation Technology Inc. Targa Silvercrest OMC807-C optische Funkmaus
Bus 002 Device 003: ID 0c45:64d2 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
Bus 001 Device 006: ID 04f3:0111 Elan Microelectronics Corp. 

##### PCMCIA card info ##################

##### rfkill ############################

0: nfc0: (null)
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            17425  0 
dcdbas                 14936  1 dell_laptop
iwlmvm                167447  0 
mac80211              623607  1 iwlmvm
iwlwifi               179516  1 iwlmvm
wmi                    19256  1 dell_wmi
cfg80211              499466  3 iwlmvm,mac80211,iwlwifi

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
          Interrupt:20 Memory:f7e00000-f7e20000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.10.1.248  Bcast:10.10.7.255  Mask:255.255.248.0
          inet6 addr: 2401:de00:1:6:fef8:aeff:fe78:e367/64 Scope:Global
          inet6 addr: 2401:de00:1:6:8c22:fe64:905d:59c9/64 Scope:Global
          inet6 addr: fe80::fef8:aeff:fe78:e367/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2130 (2.1 KB)  TX bytes:24226 (24.2 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"IHEP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'IHEP' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.10.0.1       0.0.0.0         UG    0      0        0 wlan0
10.10.0.0       0.0.0.0         255.255.248.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.0.1
search ihep.ac.cn

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [IHEP] --------------------------------------------------------
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

  Wireless Access Points (* = current AP)
    PHICOMM_zf:      Infra, <MAC 'PHICOMM_zf' [AC13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TP-LINK_5C7C12:  Infra, <MAC 'TP-LINK_5C7C12' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    flytv:           Infra, <MAC 'flytv' [AN3]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    mengmeng:        Infra, <MAC 'mengmeng' [AC29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WEP
    eduroam:         Infra, <MAC 'eduroam' [AC28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 99
    IHEP:            Infra, <MAC 'IHEP' [AC2]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 70
    eduroam:         Infra, <MAC 'eduroam' [AC3]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 69
    eduroam:         Infra, <MAC 'eduroam' [AC12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    eduroam:         Infra, <MAC 'eduroam' [AC17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    IHEP:            Infra, <MAC 'IHEP' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    eduroam:         Infra, <MAC 'eduroam' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32
    eduroam:         Infra, <MAC 'eduroam' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    IHEP:            Infra, <MAC 'IHEP' [AC16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    eduroam:         Infra, <MAC 'eduroam' [AC23]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25
    IHEP:            Infra, <MAC 'IHEP' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29
    Tenda_N:         Infra, <MAC 'Tenda_N' [AC22]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA
    ZhaoGY:          Infra, <MAC 'ZhaoGY' [AN17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    MERCURY_4666EA:  Infra, <MAC 'MERCURY_4666EA' [AC14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    eduroam:         Infra, <MAC 'eduroam' [AC20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65
    IHEP:            Infra, <MAC 'IHEP' [AC19]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60
    IHEP:            Infra, <MAC 'IHEP' [AC25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40
    *IHEP:           Infra, <MAC 'IHEP' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 81
    lily:            Infra, <MAC 'lily' [AC27]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60 WPA2
    yaoayao:         Infra, <MAC 'yaoayao' [AC24]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WEP
    eduroam:         Infra, <MAC 'eduroam' [AC26]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    IHEP:            Infra, <MAC 'IHEP' [AC21]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29

  IPv4 Settings:
    Address:         10.10.1.248
    Prefix:          21 (255.255.248.0)
    Gateway:         10.10.0.1

    DNS:             202.38.128.58
    DNS:             202.38.128.10

  IPv6 Settings:
    Address:         2401:de00:1:6:8c22:fe64:905d:59c9
    Prefix:          64
    Gateway:         fe80::21a:a9ff:fe16:1377

    Address:         2401:de00:1:6:fef8:aeff:fe78:e367
    Prefix:          64
    Gateway:         fe80::21a:a9ff:fe16:1377

    Address:         fe80::fef8:aeff:fe78:e367
    Prefix:          64
    Gateway:         fe80::21a:a9ff:fe16:1377

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
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/HP-nomodel.2EEAB2]] (600 root)
[connection] id=HP-nomodel.2EEAB2 | type=802-11-wireless
[802-11-wireless] ssid=HP-nomodel.2EEAB2 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/IHEP]] (600 root)
[connection] id=IHEP | type=802-11-wireless
[802-11-wireless] ssid=IHEP | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Helmholtz-Institut Mainz]] (600 root)
[connection] id=Helmholtz-Institut Mainz | type=802-11-wireless
[802-11-wireless] ssid=Helmholtz-Institut Mainz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/XueRenDaShaNeiWang]] (600 root)
[connection] id=XueRenDaShaNeiWang | type=802-11-wireless
[802-11-wireless] ssid=XueRenDaShaNeiWang | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KPHSelect]] (600 root)
[ipv6] method=auto
[connection] id=KPHSelect | type=802-11-wireless
[802-11-wireless] ssid=KPHSelect | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KPHguest]] (600 root)
[connection] id=KPHguest | type=802-11-wireless
[802-11-wireless] ssid=KPHguest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/eduroam 1]] (600 root)
[connection] id=eduroam 1 | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7240]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7240 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7240 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/winulum]] (600 root)
[connection] id=winulum | type=802-11-wireless
[802-11-wireless] ssid=winulum | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/BESIII_SDU]] (600 root)
[connection] id=BESIII_SDU | type=802-11-wireless
[802-11-wireless] ssid=BESIII_SDU | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Days Inn]] (600 root)
[connection] id=Days Inn | type=802-11-wireless
[802-11-wireless] ssid=Days Inn | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Uni-Mainz]] (600 root)
[ipv6] method=auto
[connection] id=Uni-Mainz | type=802-11-wireless
[802-11-wireless] ssid=Uni-Mainz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Grand Mercure Zhongya]] (600 root)
[connection] id=Grand Mercure Zhongya | type=802-11-wireless
[802-11-wireless] ssid=Grand Mercure Zhongya | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/KPHselect]] (600 root)
[ipv6] method=auto
[connection] id=KPHselect | type=802-11-wireless
[802-11-wireless] ssid=KPHselect | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MeinFernbus1]] (600 root)
[connection] id=MeinFernbus1 | type=802-11-wireless
[802-11-wireless] ssid=MeinFernbus1 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      10   APs on   Frequency:2.412 GHz (Channel 1)
      12   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.745 GHz

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'IHEP' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b9e3ee73b
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC 'IHEP' [AC2]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000726262a60b
                    Extra: Last beacon: 20ms ago
          Cell 03 - Address: <MAC 'eduroam' [AC3]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000726262a7e2
                    Extra: Last beacon: 20ms ago
          Cell 04 - Address: <MAC 'IHEP' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007270fa9185
                    Extra: Last beacon: 16392ms ago
          Cell 05 - Address: <MAC 'eduroam' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007270fa988b
                    Extra: Last beacon: 16388ms ago
          Cell 06 - Address: <MAC 'IHEP' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072844f0180
                    Extra: Last beacon: 5012ms ago
          Cell 07 - Address: <MAC 'eduroam' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072844f0825
                    Extra: Last beacon: 5012ms ago
          Cell 08 - Address: <MAC 'IHEP' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000020904aa180
                    Extra: Last beacon: 16360ms ago
          Cell 09 - Address: <MAC 'IHEP' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072836e0180
                    Extra: Last beacon: 16344ms ago
          Cell 10 - Address: <MAC 'eduroam' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072836e0825
                    Extra: Last beacon: 16340ms ago
          Cell 11 - Address: <MAC 'IHEP' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007286b51180
                    Extra: Last beacon: 16336ms ago
          Cell 12 - Address: <MAC 'eduroam' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007286b51824
                    Extra: Last beacon: 16336ms ago
          Cell 13 - Address: <MAC 'PHICOMM_zf' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"PHICOMM_zf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001544ec140
                    Extra: Last beacon: 16324ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'MERCURY_4666EA' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MERCURY_4666EA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c2e850d9
                    Extra: Last beacon: 4860ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'eduroam' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c1372a888
                    Extra: Last beacon: 15628ms ago
          Cell 16 - Address: <MAC 'IHEP' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c2b96a191
                    Extra: Last beacon: 4812ms ago
          Cell 17 - Address: <MAC 'eduroam' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c2b96a88f
                    Extra: Last beacon: 4812ms ago
          Cell 18 - Address: <MAC 'xueshiyan' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"xueshiyan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000063304127ff
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'IHEP' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007282931445
                    Extra: Last beacon: 20ms ago
          Cell 20 - Address: <MAC 'eduroam' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007282931db4
                    Extra: Last beacon: 20ms ago
          Cell 21 - Address: <MAC 'IHEP' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c1372a19d
                    Extra: Last beacon: 15628ms ago
          Cell 22 - Address: <MAC 'Tenda_N' [AC22]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Tenda_N"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d74cbc018c
                    Extra: Last beacon: 15612ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'eduroam' [AC23]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b9be1989c
                    Extra: Last beacon: 15608ms ago
          Cell 24 - Address: <MAC 'yaoayao' [AC24]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"yaoayao"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002dc084275
                    Extra: Last beacon: 20ms ago
          Cell 25 - Address: <MAC 'IHEP' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"IHEP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000034aef0419d
                    Extra: Last beacon: 4484ms ago
          Cell 26 - Address: <MAC 'eduroam' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000034aeeeb8a2
                    Extra: Last beacon: 4584ms ago
          Cell 27 - Address: <MAC 'lily' [AC27]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"lily"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000013d5043b0367
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'eduroam' [AC28]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"eduroam"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b9e3fd825
                    Extra: Last beacon: 4552ms ago
          Cell 29 - Address: <MAC 'mengmeng' [AC29]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"mengmeng"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005907949ca
                    Extra: Last beacon: 20ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     0916A821F768F66B7252B54
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.11.0-17-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D03D6FD9CB4C5CA28E703EF
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.11.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     90DCEBFC3CB64C8138032A1
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
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
filename:       /lib/modules/3.11.0-17-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     3894641168D4783E1F722B2
depends:        
intree:         Y
vermagic:       3.11.0-17-generic SMP mod_unload modversions 
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    2.490210] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.495373] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S (repeated 2 times)
[    2.506333] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   10.834110] wlan0: authenticate with <MAC 'IHEP' [AC1]>
[   10.835855] wlan0: send auth to <MAC 'IHEP' [AC1]> (try 1/3)
[   10.881767] wlan0: authenticated
[   10.883649] wlan0: associate with <MAC 'IHEP' [AC1]> (try 1/3)
[   10.909822] wlan0: RX AssocResp from <MAC 'IHEP' [AC1]> (capab=0x421 status=0 aid=1)
[   10.940715] wlan0: associated
[   10.940743] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

