---
title: "Slow wireless transfer ubuntu to win 7 also blocks other wireless traffic"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by mbenson1000 on 2015-01-24
I'm quite new to ubuntu and have found an issue with transfering large files to my windows 7 file server.
I've gone through all of the ususal fixes:
alter wins in  nsswitch.conf and install winbind
Checked my workgroup and added a netbios name in samba config
altered settings on windoze machine  turned of rdc etc

The file transfer starts off quick (or at least the copy progress bar jumps very quickly) but then then it stops (no information on tranfer speed or progress change)  When it starts to show information it is around 2mb/s

The other odd thing I've noticed is that while the file is tranferring (at this very slow rate) other devices on wireless struggle to use the wireless router.

The router is a BT home hub and I noticed it has its own workgroup called HOME.
I've changed the workgroup on both the server and the ubuntu machine to match this still the same issue.

I've attached network details

Any help on this would be great as I'm at a loss.  The only thing I can think of is a driver issue....


```

########## wireless info START ##########

Report from: 24 Jan 2015 21:35 GMT +0000

Booted last: 24 Jan 2015 21:21 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

06:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1301]
    Kernel driver in use: iwlwifi

08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 14)
    Subsystem: Sony Corporation Device [104d:9035]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183d Ricoh Co., Ltd Sony Vaio Integrated Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630669  1 iwldvm
iwlwifi               169932  1 iwldvm
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
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.48  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:fbff:fe56:e02c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50943 errors:0 dropped:82 overruns:0 frame:0
          TX packets:89710 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8705002 (8.7 MB)  TX bytes:127129207 (127.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Belkin.9403"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Belkin.9403' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:264   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Belkin.9403] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 Enterprise
    *Belkin.9403:    Infra, <MAC 'Belkin.9403' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2
    NETGEAR56:       Infra, <MAC 'NETGEAR56' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    BTBusinessHub-248: Infra, <MAC 'BTBusinessHub-248' [AC7]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    DIRECT-roku-086-B19099: Infra, <MAC 'DIRECT-roku-086-B19099' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2
    SKY7430C:        Infra, <MAC 'SKY7430C' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    BTOpenzone:      Infra, <MAC 'BTOpenzone' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 60
    BTHomeHub-22C8:  Infra, <MAC 'BTHomeHub-22C8' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WEP
    Himalaya:        Infra, <MAC 'Himalaya' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2 Enterprise
    BTOpenzone-H:    Infra, <MAC 'BTOpenzone-H' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    FurbersHome:     Infra, <MAC 'FurbersHome' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         192.168.2.48
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             8.8.4.4
    DNS:             8.8.8.8

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

[[/etc/NetworkManager/system-connections/Freebox-5D6005]] (600 root)
[connection] id=Freebox-5D6005 | type=802-11-wireless
[802-11-wireless] ssid=Freebox-5D6005 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Belkin.9403]] (600 root)
[connection] id=Belkin.9403 | type=802-11-wireless
[802-11-wireless] ssid=Belkin.9403 | mac-address=<MAC 'wlan0' [IF]> | mtu=1430
[ipv4] method=manual
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Belkin.9403 1]] (600 root)
[connection] id=Belkin.9403 1 | type=802-11-wireless
[802-11-wireless] ssid=Belkin.9403 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.22 GHz (Channel 44)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Belkin.9403' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Belkin.9403"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000235a1dd93
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIRECT-roku-086-B19099' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-086-B19099"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca16ad5a3b
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR56' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR56"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000098e7a4f595a
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BTHomeHub-22C8' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"BTHomeHub-22C8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cf15682fb4
                    Extra: Last beacon: 84ms ago
          Cell 05 - Address: <MAC 'FurbersHome' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"FurbersHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000062d095150
                    Extra: Last beacon: 4336ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'BTOpenzone-H' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone-H"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001cf15682990
                    Extra: Last beacon: 84ms ago
          Cell 07 - Address: <MAC 'BTBusinessHub-248' [AC7]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"BTBusinessHub-248"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064dba11042
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'BTOpenzone' [AC8]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000064dba11854
                    Extra: Last beacon: 84ms ago
          Cell 09 - Address: <MAC 'BTWifi-with-FON' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dc3d5ee00c
                    Extra: Last beacon: 84ms ago
          Cell 10 - Address: <MAC 'BTWifi-X' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dc3d5e846b
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'BTWifi-with-FON' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000235a2c5d1
                    Extra: Last beacon: 4060ms ago
          Cell 12 - Address: <MAC 'BTWifi-X' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000235a32ba4
                    Extra: Last beacon: 4032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'Himalaya' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"Himalaya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'NETGEAR56-5G' [AC14]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR56-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000098e7d57c2af
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     9ABCB275EC05F363D958754
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-44-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     716D089263B1757F5069E63
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
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
filename:       /lib/modules/3.13.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-44-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:8C:3B:4B:F1:08:ED:36:B6:06:2F:81:27:82:F7:7C:37:B9:85:37
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x11ab:0x4363 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by mbenson1000 on 2015-01-25
To add more info.
I'v just tried a usb ralink wifi dongle from my Raspberry Pi.  This exhibits exactly the same behaviour.
So it looks like it's not down to the wireless adapter.
Wired also gives similar transfer rates of 2mb/s as well

Hopping back into windoze (I'm dual booting this machine) I get transfer rates of 5mb/s wireless and 10mb/s wired.

The most worrying aspect of this is the fact that at the low transfer rate of 2mb/s on wireless Ubuntu is jamming up the whole home network.

Any help would be great.

Thanks

---

### Post by mbenson1000 on 2015-03-01
Ok.  While no one else has given me any ideas I've not been sat on my hands.

I've so far replaced my modem/router, Replaced my network switches and even built a new ubuntu server to act as a secondary file server.

None of these have made a difference.
Most of my further testing has been ubuntu to ubuntu.
The max transfer speeds I'm getting wired are 11MiB/s on a gigabit LAN and 3MiB/s wireless on an N based network.
I've tried moving server & client ont the same switch to remove any cabling issues.
I've tried adding NFS shares which give almost identical transfer rates (although these max out the client CPU so I've carried on further testing on samba)

Using the Iperf tool on the 2 exterme ends of my network (30m of cable through 2 switches and the router) and I get:

 Wired
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   114 MBytes  95.0 Mbits/sec

Wireless

[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.1 sec  33.2 MBytes  27.7 Mbits/sec

I've checked HD rates and these show a write rate of 75MB/s

All testing so far has been writing to the server which has tended to be slowest.

I could really do with some help on this as I'm running out of ideas.  I have wireshark installed but I need some help to know what to look for.

Thanks,

---

### Post by mbenson1000 on 2015-03-08
Oh Samba,  I'm so so sorry for blaming you for all my problems :oops:
It turns out I had 2 problems.  Both of them hardware/network related.
The first problem was 1 bad CAT 6 cable.  Yes the one I've been carrying round to connect my laptop to the wired network.  Once I'd replaced that all of a sudden the wired transfer rates went through the roof.  Now averaging around 65MB/s wich is getting close to the maximum the HD can handle so I'm fairly satisfied with that.  Looks like I have some buffer issues that I need to sort as it does drop off half way throught the transfer of a 1.3GB file but on this I can see the light at the end of the network tunnel.
The second issue is with the Intel 5100agn card.  It tells me I have 150Mb/s connection however with iperf the maximum I can get gives a transfer rate of 3MB/s (sorry for mixing my bits and bytes).  In theory 150Mb/s should allow for 150/8=18.75MB/s so I'm miles away.
Turns out this adapter has serious issues with wireless N.  This may explain why nautilus was showing the transfer hitting 100% and then staying there until the actual transfer finished (several minutes later) and could also explain the network saturation issues I've been having (which I think manifest as a saturation of the routers DNS).
This looks like it has been an issue for a very long time.  The more I read the more it looks like Ubuntu can't seem to handle adapters with transfer rates greater than 54Mb/s.  Please correct me if I'm wrong.
I verified the wifi issues by disabling the internal intel card and using a Ralink usb adapter which is n capable but is only displaying transfer rates of 54Mb/s.  This has resulted in breaking the 3MB/s transfer rate to almost double.

Does anyone know of a good usb wifi adapter that can handle n or above transfer rates?

I would really appreciate some advice as I'm feeling like I'm talking to myself......quite literally :cry:

---

### Post by jeremy31 on 2015-03-08
Look at the results from ```
iwlist scan
``` and see if the encryption is CCMP only for your access point, if it is a mixed CCMP TKIP it will hurt your wifi speed.  Intel cards using iwlwifi are helped with this command ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

---

### Post by mbenson1000 on 2015-03-08
> **jeremy31 said:**
> Look at the results from ```
iwlist scan
``` and see if the encryption is CCMP only for your access point, if it is a mixed CCMP TKIP it will hurt your wifi speed.  Intel cards using iwlwifi are helped with this command ```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

Thanks for your advice.

I checked and I don't have mixed mode.
I'd tried iwlwifi 11n_disable=0 as others had recommeneded this but this stopped my laptop connecting to any routers.  The option 8 has boosted me from transfer rates of 3MB/s up to 13MB/s which is a massive step forward.:p

Out of interest what does the option 8 actually do?

Also why is it ubuntu is so behind the curve on wifi performance?  It seems that getting wireless 'n' let alone 'ac' is a real headache???

---

### Post by jeremy31 on 2015-03-08
> **mbenson1000 said:**
> Thanks for your advice.

I checked and I don't have mixed mode.
I'd tried iwlwifi 11n_disable=0 as others had recommeneded this but this stopped my laptop connecting to any routers.  The option 8 has boosted me from transfer rates of 3MB/s up to 13MB/s which is a massive step forward.:p

Out of interest what does the option 8 actually do?

Also why is it ubuntu is so behind the curve on wifi performance?  It seems that getting wireless 'n' let alone 'ac' is a real headache???

I think there is a good explanation of what the 8 option does at the bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1319630)
Ubuntu can usually do no better than the Linux kernel and when you figure 98%+ of all computers are running Windows or Apple software you aren't going to see a lot of support from the manufacturers and we are lucky to get the support from some of them to be able to include the firmware many of these devices need with the ISO image

---

