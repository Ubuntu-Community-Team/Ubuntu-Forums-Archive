---
title: "Intel PRO LAN 2100 3B on Lubuntu 14.04 LTS done goofed"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by bass3 on 2014-07-03
So I just installed Lubuntu on an older system, which is exactly why I chose Lubuntu. I have tried third-party software to connect to wireless networks, but to no success. Whenever I use WiFi Radar, the wireless card reports the SSID (wifi names), however it doesn't show the signal strength. When I enter the password or attempt to connect to an open network, it will make my entire system wait while my wifi card sits it's happy a#$ stuck in a loop so it can laugh at my futile attempts of making it work.
I also do not have the wireless dock or "systray item" as MicroNerds would love to call it. (Microsoft + their fanbase = MicroNerds befitting isn't it?:p)

P.S. I would love to get my username changed to BassAutonima (my name), how do I do that in these forums? Not trying to be lazy, just trying to be efficient with my time instead of wasting it searching for a way to do such a thing.

If any information is required, I used the wireless script and I can post anything from there to shed light upon my situation, however I believe it is very similar to this post, however the solution isn't going to be same because I've tried it. [lubuntu 13.04 fresh install, no wifi]("http://ubuntuforums.org/showthread.php?t=2149983")

---

### Post by praseodym on 2014-07-04
Please show the terminal outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
pccardctl info
lsmod
iwconfig
ifconfig -a
rfkill list
cat /etc/resolv.conf
```

---

### Post by bass3 on 2014-07-04
Okay, I know this is a self-righteous bump, but it is a bump nonetheless. I really am stumped on this because out of the 7 years I have used Linux, my wireless cards have always been detected automatically. This is a first and I really need a working machine in order to code and design. In other words, I make my living through my laptop. Here is any and all relevant information I have come up with, please help me swiftly.

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux ba55machine 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

##### lspci #####

01:04.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
    Subsystem: Intel Corporation MIM2000/Centrino [8086:2527]
    Kernel driver in use: ipw2100

01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VM (MOB) Ethernet Controller [8086:103e] (rev 83)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1745]
    Kernel driver in use: e100

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

ipw2100                76916  0 
libipw                 33144  1 ipw2100
cfg80211              409394  2 libipw,ipw2100

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         205.127.250.129 0.0.0.0         UG    0      0        0 eth0
205.127.250.128 0.0.0.0         255.255.255.128 U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search public.slcpl.org

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         205.127.250.192
    Prefix:          25 (255.255.255.128)
    Gateway:         205.127.250.129

    DNS:             205.171.2.65
    DNS:             205.171.3.65
    DNS:             8.8.8.8

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2100
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    Connection3937:  Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    CableWiFi:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    XMission:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Katers:          Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    THE_LOTUS:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WEP
    XMission:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    DDGuest WiFi:    Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    XMission:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    CenturyLink8062: Infra, <MAC address removed>, Freq 2442 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    mmwifi2g:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    XMission:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    xfinitywifi:     Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    XMission:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    XMission:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    myLGNet541B:     Infra, <MAC address removed>, Freq 2457 MHz, Rate 54 Mb/s, Strength 0 WEP
    XMission:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    XMission:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    AMX:             Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2
    CableWiFi:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    FoxFi84:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    \0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA
    CableWiFi:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    SLR_Office:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    XMission:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    George Eliot Salon: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    xfinitywifi:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0
    CableWiFi:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0
    SLRoasting:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA2
    tamember:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2
    slcpl_guest:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    slcpl_staff:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    qcomg:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA2 Enterprise
    Grand Poo-bah:   Infra, <MAC address removed>, Freq 2432 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2

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

##### iwlist #####

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:56  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 388ms ago
          Cell 02 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:56  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 372ms ago
          Cell 03 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:50  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 840ms ago
          Cell 04 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3644ms ago
          Cell 05 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:59  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 188ms ago
          Cell 06 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:55  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 176ms ago
          Cell 07 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:42  Signal level:0  Noise level:0
                    Extra: Last beacon: 720ms ago
          Cell 08 - Address: <MAC address removed>
                    ESSID:"Connection3937"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5884ms ago
          Cell 09 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3376ms ago
          Cell 10 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 196ms ago
          Cell 11 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3368ms ago
          Cell 12 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 836ms ago
          Cell 13 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:25  Signal level:0  Noise level:0
                    Extra: Last beacon: 0ms ago
          Cell 14 - Address: <MAC address removed>
                    ESSID:"SLR_Office"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:53  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12176ms ago
          Cell 15 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:41  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 1824ms ago
          Cell 16 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    Extra: Last beacon: 13700ms ago
          Cell 17 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:48  Signal level:0  Noise level:0
                    Extra: Last beacon: 372ms ago
          Cell 18 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4848ms ago
          Cell 19 - Address: <MAC address removed>
                    ESSID:"AMX"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2232ms ago
          Cell 20 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2232ms ago
          Cell 21 - Address: <MAC address removed>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:41  Signal level:0  Noise level:0
                    Extra: Last beacon: 3952ms ago
          Cell 22 - Address: <MAC address removed>
                    ESSID:"George Eliot Salon"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3952ms ago
          Cell 23 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1040ms ago
          Cell 24 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 2440ms ago
          Cell 25 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:48  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 1820ms ago
          Cell 26 - Address: <MAC address removed>
                    ESSID:"CableWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:55  Signal level:0  Noise level:0
                    Extra: Last beacon: 4744ms ago
          Cell 27 - Address: <MAC address removed>
                    ESSID:"SLRoasting"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:51  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3472ms ago
          Cell 28 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:48  Signal level:0  Noise level:0
                    Extra: Last beacon: 384ms ago
          Cell 29 - Address: <MAC address removed>
                    ESSID:"mmwifi2g"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12172ms ago
          Cell 30 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:53  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 396ms ago
          Cell 31 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 3164ms ago
          Cell 32 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 376ms ago
          Cell 33 - Address: <MAC address removed>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:59  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1340ms ago
          Cell 34 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 392ms ago
          Cell 35 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:33  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2972ms ago
          Cell 36 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:61  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 2524ms ago
          Cell 37 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:31  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 2500ms ago
          Cell 38 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:58  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 844ms ago
          Cell 39 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:50  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 2748ms ago
          Cell 40 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:44  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 3644ms ago
          Cell 41 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:53  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 2448ms ago
          Cell 42 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    Extra: Last beacon: 4068ms ago
          Cell 43 - Address: <MAC address removed>
                    ESSID:"XMission"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:25  Signal level:0  Noise level:0
                    Extra: Last beacon: 3460ms ago
          Cell 44 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 14508ms ago
          Cell 45 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3184ms ago
          Cell 46 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:50  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 1996ms ago
          Cell 47 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 180ms ago
          Cell 48 - Address: <MAC address removed>
                    ESSID:""
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:41  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1840ms ago
          Cell 49 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 204ms ago
          Cell 50 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:33  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 3380ms ago
          Cell 51 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 8904ms ago
          Cell 52 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 828ms ago
          Cell 53 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3656ms ago
          Cell 54 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1020ms ago
          Cell 55 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:29  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1032ms ago
          Cell 56 - Address: <MAC address removed>
                    ESSID:"CableWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    Extra: Last beacon: 6264ms ago
          Cell 57 - Address: <MAC address removed>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:35  Signal level:0  Noise level:0
                    Extra: Last beacon: 5076ms ago
          Cell 58 - Address: <MAC address removed>
                    ESSID:"slcpl_guest"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:33  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7544ms ago
          Cell 59 - Address: <MAC address removed>
                    ESSID:"CableWiFi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:5.5 Mb/s; 11 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    Extra: Last beacon: 11936ms ago
          Cell 60 - Address: <MAC address removed>
                    ESSID:"slcpl_staff"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:23  Signal level:0  Noise level:0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 400ms ago
          Cell 61 - Address: <MAC address removed>
                    ESSID:"Grand Poo-bah"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:27  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12284ms ago

##### iwlist channel #####

eth1      14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Current Channel=0

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ipw2x00/ipw2100.ko
firmware:       ipw2100-1.3.fw
firmware:       ipw2100-1.3-p.fw
firmware:       ipw2100-1.3-i.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        git-1.2.2
description:    Intel(R) PRO/Wireless 2100 Network Driver
srcversion:     0137FFF532FA941B87505FD
alias:          pci:v00008086d00001043sv00008086sd000025A0bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002598bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002596bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002593bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002591bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002592bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002590bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002587bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002586bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002585bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002581bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002583bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002582bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002580bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002570bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002567bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002566bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002565bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002561bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002563bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002562bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002560bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002555bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002554bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002553bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002551bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002550bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Dbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Cbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd0000252Bbc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002529bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002528bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002527bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002523bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002522bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002526bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002525bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002524bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002521bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002520bc*sc*i*
depends:        libipw,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           debug:debug level (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           channel:channel (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)

##### modules #####

lp

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

##### udev rules #####

# PCI device 0x8086:0x103e (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1043 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   22.532643] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   22.532656] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   22.534084] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[   28.662636] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   28.663380] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   29.201970] ipw2100: Fatal interrupt. Scheduling firmware restart.

########## wireless info END ############



If you want anything else, PLEASE ASK ME!!!

---

### Post by bass3 on 2014-07-04
lspci command had the results of:
01:04.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
    Subsystem: Intel Corporation MIM2000/Centrino [8086:2527]
    Kernel driver in use: ipw2100
--
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VM (MOB) Ethernet Controller [8086:103e] (rev 83)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1745]
    Kernel driver in use: e100

lsusb had:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

pccardctl info had:
The program 'pccardctl' is currently not installed. You can install it by typing:
sudo apt-get install pcmciautils

o.0 I'm giving you the results asIrun them so I'm shocked that something name PC-CARD-ConTroL isn't a preloaded-modulein the installation!

Anyways, lsmod gave:
Module                  Size  Used by
snd_intel8x0           33110  2 
snd_ac97_codec        105709  1 snd_intel8x0
joydev                 17101  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                85501  2 snd_ac97_codec,snd_intel8x0
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
pcmcia                 51828  0 
ipw2100                76916  0 
libipw                 33144  1 ipw2100
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
yenta_socket           40201  0 
lib80211               14040  1 libipw
pcmcia_rsrc            18319  1 yenta_socket
cfg80211              409394  2 libipw,ipw2100
pcmcia_core            22328  3 pcmcia,pcmcia_rsrc,yenta_socket
snd                    60871  12 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_seq_midi
psmouse                91033  0 
soundcore              12600  1 snd
lpc_ich                16864  0 
serio_raw              13230  0 
shpchp                 32128  0 
irda                  107386  0 
crc_ccitt              12627  1 irda
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342263  10 bnep,rfcomm
binfmt_misc            13140  1 
i915                  705396  2 
drm_kms_helper         46907  1 i915
drm                   243792  3 i915,drm_kms_helper
asus_laptop            23897  0 
i2c_algo_bit           13197  1 i915
sparse_keymap          13708  1 asus_laptop
input_polldev          13648  1 asus_laptop
video                  18903  1 i915
mac_hid                13037  0 
parport_pc             31981  1 
ppdev                  17391  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
firewire_ohci          35529  0 
e100                   35945  0 
firewire_core          61867  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
mii                    13654  1 e100

iwconfig gave:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

(I am connected through a wired connection so if I need to run a command again without internet,just tell me.)
ifconfig -a gave:
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:f9:ea:2d  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fef9:ea2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56131302 (56.1 MB)  TX bytes:17007565 (17.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:04:23:92:df:40  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:4 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3783 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:392313 (392.3 KB)  TX bytes:392313 (392.3 KB)

rfkill list gave:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
and last but not least; cat gave:
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

Sorry about posting after you twice, I had already started that reply and was having issues including the screenshot when you had posted. XD Gomen,Gomen!

---

### Post by chili555 on 2014-07-04
We'd like to also see:```
sudo iwlist eth1 auth
```Thanks.>  I'm shocked that something name PC-CARD-ConTroL isn't a preloaded-modulein the installation!pccardctrl is a utility for PCMCIA cards. Remember those? Me neither.

---

### Post by bass3 on 2014-07-04
Wow, you guys are insanely fast compared to other forums! Anyways, here are the results, and what appears to be the barrier for me:
eth1      Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current WPA version :
        Unknown
          Current Key management :
        Unknown
          Current Pairwise cipher :
        CCMP
        Unknown
          Current Pairwise cipher :
        CCMP
        Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : no
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : yes
          Current Roaming control : no
          Current Privacy invoked : no

Again, you guys are the cream of the crop for the ubuntu community, and I say that because you have helped other people in similar situations and I have read the posts. Keep trolling, and keep being epic dear sirs.

---

### Post by chili555 on 2014-07-04
This is really praseodym's thread but he's 128 time zones away! I wonder if he might suggest that you check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Now are you able to connect?

---

### Post by praseodym on 2014-07-05
Which of the similar named networks do you want to connect to? Please mark it/them. Chili is right: Try pure WPA2-AES (CCMP), a fixed channel and no MAC filter if you have access to the router.

---

