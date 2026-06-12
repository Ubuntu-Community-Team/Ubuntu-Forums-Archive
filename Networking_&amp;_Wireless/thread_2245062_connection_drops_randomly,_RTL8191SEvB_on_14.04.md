---
title: "connection drops randomly, RTL8191SEvB on 14.04"
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by painter90 on 2014-09-20
Hi. My internet connection drops randomly. This actually used to happen when I had Ubuntu 12.04 installed previously too. I didn't upgrade, I did a fresh install of 14.04 if it matters.

Sometimes if I disable wireless networking, then re-enable and connect, it will work. Most of the time, I just have to reboot and it works fine. This has been going on for months. It never happened with when I previously had Windows 7. I have had the same wireless router provided by Comcast.

Here is the data I got when running the script from the sticky in this forum: 

```


########## wireless info START ##########

Report from: 20 Sep 2014 20:38 EDT -0400

Booted last: 20 Sep 2014 20:33 EDT -0400

Script from: 17 Sep 2014 18:40 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Kernel driver in use: rtl8192se

##### lsusb #####

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

rtl8192se              63196  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 toshiba_acpi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: 2601:6:3300:1075:226:4dff:fe93:ac31/64 Scope:Global
          inet6 addr: fe80::226:4dff:fe93:ac31/64 Scope:Link
          inet6 addr: 2601:6:3300:1075:68c1:7c3d:f78e:2380/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3130538 (3.1 MB)  TX bytes:615905 (615.9 KB)

##### iwconfig #####

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME-49B2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'HOME-49B2' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:91   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search hsd1.ma.comcast.net

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-49B2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           65 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-3BE9:       Infra, <MAC 'HOME-3BE9' [AC27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Jaylene:         Infra, <MAC 'Jaylene' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    HOME-AD96:       Infra, <MAC 'HOME-AD96' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    R5RMJ:           Infra, <MAC 'R5RMJ' [AC32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA2
    HOME-749E-2.4:   Infra, <MAC 'HOME-749E-2.4' [AC33]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    slashzero:       Infra, <MAC 'slashzero' [AC29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    HOME-9610:       Infra, <MAC 'HOME-9610' [AC21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    HOME-C2D2:       Infra, <MAC 'HOME-C2D2' [AN8]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    HOME-98-2-NET-:  Infra, <MAC 'HOME-98-2-NET-' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HOME-9B2E:       Infra, <MAC 'HOME-9B2E' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    PAPA1:           Infra, <MAC 'PAPA1' [AC37]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 17 WPA2
    HOME-0E42:       Infra, <MAC 'HOME-0E42' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    C27GS:           Infra, <MAC 'C27GS' [AC20]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    HOME-1372:       Infra, <MAC 'HOME-1372' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN18]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 14
    Cisco13154:      Infra, <MAC 'Cisco13154' [AC26]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 14
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    *HOME-49B2:      Infra, <MAC 'HOME-49B2' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    tina:            Infra, <MAC 'tina' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    HOME-7B9D:       Infra, <MAC 'HOME-7B9D' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Main System Network R1: Infra, <MAC 'Main System Network R1' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    HOME-05D6-2.4:   Infra, <MAC 'HOME-05D6-2.4' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    HOME-D2A6:       Infra, <MAC 'HOME-D2A6' [AN26]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Can'tTouchThis:  Infra, <MAC 'Can'tTouchThis' [AC38]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    dani123:         Infra, <MAC 'dani123' [AC31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN29]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    MS:              Infra, <MAC 'MS' [AC24]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    HOME-FA22:       Infra, <MAC 'HOME-FA22' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HOME-C2BE:       Infra, <MAC 'HOME-C2BE' [AN33]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HOME-014C-2.4:   Infra, <MAC 'HOME-014C-2.4' [AN34]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    GXHZK:           Infra, <MAC 'GXHZK' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    GusNetBox:       Infra, <MAC 'GusNetBox' [AN36]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HOME-5A5E:       Infra, <MAC 'HOME-5A5E' [AN37]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WEP
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC40]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 14
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AN40]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    NETGEAR28:       Infra, <MAC 'NETGEAR28' [AN41]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HPCP1525-9b6a9a: Ad-Hoc, <MAC 'HPCP1525-9b6a9a' [AC30]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14
    Cisco46353:      Infra, <MAC 'Cisco46353' [AN44]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    fusion:          Infra, <MAC 'fusion' [AC34]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HOME-FE71:       Infra, <MAC 'HOME-FE71' [AC35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    HOME-5B77:       Infra, <MAC 'HOME-5B77' [AN47]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

  IPv4 Settings:
    Address:         10.0.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76

  IPv6 Settings:
    Address:         2601:6:3300:1075:68c1:7c3d:f78e:2380
    Prefix:          64
    Gateway:         fe80::ea89:2cff:fe07:49b1

    Address:         2601:6:3300:1075:226:4dff:fe93:ac31
    Prefix:          64
    Gateway:         fe80::ea89:2cff:fe07:49b1

    Address:         fe80::226:4dff:fe93:ac31
    Prefix:          64
    Gateway:         fe80::ea89:2cff:fe07:49b1

    DNS:             2001:558:feed::1
    DNS:             2001:558:feed::2

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles #####

==[/etc/NetworkManager/system-connections/HOME-1372]==
[connection] id=HOME-1372 | type=802-11-wireless
[802-11-wireless] ssid=HOME-1372 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/HOME-49B2]==
[connection] id=HOME-49B2 | type=802-11-wireless
[802-11-wireless] ssid=HOME-49B2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/C27GS]==
[connection] id=C27GS | type=802-11-wireless
[802-11-wireless] ssid=C27GS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get #####

Region: America/New_York (based on set time zone)

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels #####

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #####

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.452 GHz (Channel 9)
      22   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'HOME-49B2' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"HOME-49B2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053408b10e2
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HOME-FA22' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HOME-FA22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005340cfb24b
                    Extra: Last beacon: 76ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005340cfbcad
                    Extra: Last beacon: 72ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005340cfc427
                    Extra: Last beacon: 72ms ago
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005340030bcc
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'xfinitywifi' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053400312c6
                    Extra: Last beacon: 48ms ago
          Cell 07 - Address: <MAC 'HOME-98-2-NET-' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"HOME-98-2-NET-"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005342290af8
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HOME-7B9D' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HOME-7B9D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005341f25185
                    Extra: Last beacon: 3468ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'POSADASMARKET' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"POSADASMARKET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005342e7b4ed
                    Extra: Last beacon: 3156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'tina' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"tina"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000534003021a
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053408afd5d
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'xfinitywifi' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-29 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053408b2670
                    Extra: Last beacon: 4ms ago
          Cell 13 - Address: <MAC 'Main System Network R1' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Main System Network R1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053448bf183
                    Extra: Last beacon: 208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'HOME-1372' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HOME-1372"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d21fce176
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d21fceaf0
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'xfinitywifi' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003d21fcf26a
                    Extra: Last beacon: 92ms ago
          Cell 17 - Address: <MAC 'Jaylene' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Jaylene"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005275cbd13c
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC '' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005275cbdba6
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'xfinitywifi' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005275ccee1d
                    Extra: Last beacon: 4ms ago
          Cell 20 - Address: <MAC 'C27GS' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"C27GS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005341fed187
                    Extra: Last beacon: 164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'HOME-9610' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"HOME-9610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005327629c77
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'XerxesRhiyn23' [AC22]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"XerxesRhiyn23"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ef4670183
                    Extra: Last beacon: 3136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'tom' [AC23]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"tom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001b8eb0d80
                    Extra: Last beacon: 3132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'MS' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"MS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000534316815f
                    Extra: Last beacon: 112ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000532686124d
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'Cisco13154' [AC26]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"Cisco13154"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005284972f78
                    Extra: Last beacon: 4ms ago
          Cell 27 - Address: <MAC 'HOME-3BE9' [AC27]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HOME-3BE9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000533bac1187
                    Extra: Last beacon: 2760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC28]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000533bac1a42
                    Extra: Last beacon: 2760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'slashzero' [AC29]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"slashzero"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053434f7bde
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'HPCP1525-9b6a9a' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"HPCP1525-9b6a9a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000534424d316
                    Extra: Last beacon: 2112ms ago
          Cell 31 - Address: <MAC 'dani123' [AC31]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"dani123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053268609a1
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'R5RMJ' [AC32]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"R5RMJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053421ce675
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'HOME-749E-2.4' [AC33]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"HOME-749E-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000525e7987a9
                    Extra: Last beacon: 1776ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'fusion' [AC34]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"fusion"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000534135449c
                    Extra: Last beacon: 1784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 35 - Address: <MAC 'HOME-FE71' [AC35]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"HOME-FE71"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005315a8c763
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 36 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC36]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005315ad8a73
                    Extra: Last beacon: 1436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 37 - Address: <MAC 'PAPA1' [AC37]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"PAPA1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000053426a3c40
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 38 - Address: <MAC 'Can'tTouchThis' [AC38]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Can'tTouchThis"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051a5f0e17a
                    Extra: Last beacon: 716ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 39 - Address: <MAC '' [AC39]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051a5f0ebfb
                    Extra: Last beacon: 712ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 40 - Address: <MAC 'xfinitywifi' [AC40]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000051a5f0f375
                    Extra: Last beacon: 712ms ago

##### module infos #####

[rtl8192se]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C53951858E34882052195CA
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #####

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules #####

lp
rtc

##### modprobe options #####

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

##### rc.local #####

exit 0

##### pm-utils #####

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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   19.743575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   21.761697] wlan0: authenticate with <MAC 'HOME-49B2' [AC1]>
[   21.780212] wlan0: send auth to <MAC 'HOME-49B2' [AC1]> (try 1/3)
[   21.782771] wlan0: authenticated
[   21.784131] wlan0: associate with <MAC 'HOME-49B2' [AC1]> (try 1/3)
[   21.798606] wlan0: RX AssocResp from <MAC 'HOME-49B2' [AC1]> (capab=0xc11 status=0 aid=1)
[   21.800281] wlan0: associated
[   21.800329] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by painter90 on 2014-09-23
bump?

---

### Post by weatherman2 on 2014-09-23
I've never used that exact wireless card, but I recall numerous threads regarding issues with that card's driver.  When I myself encounter problems with a new wireless card I've never seen before, I start googling.

Ubuntu picked driver "rtl8192se" for your card.  So I'd google for "ubuntu rtl8192se" and sift through the most recent results, many of which will be from old threads on this forum.

For example, this one comes up:

[http://ubuntuforums.org/showthread.php?t=2182953](http://ubuntuforums.org/showthread.php?t=2182953)

with a possible solution for 13.10 which might work for you...

---

### Post by painter90 on 2014-09-23
Thanks for the help. I found an almost exactly similar problem:

[http://askubuntu.com/questions/504457/ubuntu-14-04-1-realtek-8191sevb-wifi-doesnt-work](http://askubuntu.com/questions/504457/ubuntu-14-04-1-realtek-8191sevb-wifi-doesnt-work)

And the fix was to upgrade from kernel 3.13 to the latest stable version:

[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

I'm going to give it a try.

---

### Post by varunendra on 2014-09-23
> **weatherman2 said:**
> For example, this one comes up:

[http://ubuntuforums.org/showthread.php?t=2182953](http://ubuntuforums.org/showthread.php?t=2182953)

with a possible solution for 13.10 which might work for you...
As mentioned in that thread, a missing firmware was an unusual case for this driver. Since the wireless_script report shows no firmware errors in its 'dmesg' part, I think that is not the case here.

> **painter90 said:**
> And the fix was to upgrade from kernel 3.13 to the latest stable version
....
I'm going to give it a try.
Many of the Realtek drivers in current versions are known to have such problems, so I'd be curious to see how it goes with latest kernel versions (i.e., kernel 3.15+, not installed by default).

However, you might wish to try some available driver parameters first, as they are easy to test, and easy to remove if don't help -
```
echo "options rtl8192se ips=N swlps=N" | sudo tee /etc/modprobe.d/rtl8192se.conf
```
Reboot and see if the connection is any more stable now.

Oh, and there are two more things that you should change to optimize the connection quality.

**1)** Change the encryption in the router to pure WPA2-PSK with AES (CCMP). Currently it is set to WPA/WPA2 mixed mode with TKIP which can itself be a performance bottleneck.

**2)** As you can see in the report, most of the nearby access-points are at channel 11 (22 of them). This can cause signal interference resulting in a downgraded signal quality. Try channel 1 or one of the least used ones (and farther in number from the more used ones, since adjacent channels overlap each-other to some extent).

Try these two changes in parallel to the driver parameter suggested first, and let us know the result.

You might need the parameters even with the newer kernel/driver, but if not, or if they don't seem to help, you can revert that change by simply deleting the conf file we created with the 'tee' command -
```
sudo rm /etc/modprobe.d/rtl8192se.conf
```

---

