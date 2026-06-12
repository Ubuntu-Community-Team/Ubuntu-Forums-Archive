---
title: "no wlan with xubuntu 14 on Lenovo"
date: 2015-03-20
forum: Networking &amp; Wireless
---

### Post by parker6 on 2015-03-20
Hello, i am a newbie, I have installed xubuntu 14 on my laptop and the wlan connection does not work. I run the wireless_script, the result is below. what can I do ? Please Help...!! Many THANKS..!!

########## wireless info START ##########

Report from: 21 Mar 2015 12:21 HKT +0800

Booted last: 21 Mar 2015 12:17 HKT +0800

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:051b]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 004: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              529837  0 
cordic                 12518  1 brcmsmac
brcmutil               15066  1 brcmsmac
b43                   356470  0 
mac80211              546067  2 b43,brcmsmac
cfg80211              409394  3 b43,brcmsmac,mac80211
ssb                    51854  1 b43
bcma                   42043  3 b43,brcmsmac
ideapad_laptop         17872  0 
sparse_keymap          13708  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e206:e6ff:fea9:93e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2032 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2577585 (2.5 MB)  TX bytes:317928 (317.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

eth2      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'dlink' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr : off
          Power Management: off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:590  Invalid misc:673   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan1  [dlink 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Aidan & Adrian 2.4G: Infra, <MAC 'Aidan <MAC 'Aidan <MAC address> Adrian 2.4G' [AN1]> Adrian 2.4G' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA2
    Default:         Infra, <MAC 'Default' [AC15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    cal'shome:       Infra, <MAC 'cal'shome' [AC4]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Default:         Infra, <MAC 'Default' [AC6]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 52 WPA2
    jim:             Infra, <MAC 'jim' [AC20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    TP-LINK_ACA618:  Infra, <MAC 'TP-LINK_ACA618' [AC37]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    kyle ting:       Infra, <MAC 'kyle ting' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Apple jj:        Infra, <MAC 'Apple jj' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA2
    LieBaoWiFi383:   Infra, <MAC 'LieBaoWiFi383' [AC27]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2
    HoFamily:        Infra, <MAC 'HoFamily' [AN10]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA2
    Christopher:     Infra, <MAC 'Christopher' [AC18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    FNW:             Infra, <MAC 'FNW' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    dlink-EE04:      Infra, <MAC 'dlink-EE04' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Tenda_03C08C:    Infra, <MAC 'Tenda_03C08C' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA
    1315 2.4:        Infra, <MAC '1315 2.4' [AC19]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 30 WPA2
    FAI-PC_Network:  Infra, <MAC 'FAI-PC_Network' [AC38]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TPTP:            Infra, <MAC 'TPTP' [AC26]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WEP
    bellashome:      Infra, <MAC 'bellashome' [AC8]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 35 WEP
    Lam-Home-TP-LINK-2.4G: Infra, <MAC 'Lam-Home-TP-LINK-2.4G' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    Chan:            Infra, <MAC 'Chan' [AN20]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA
    Vincent_WiFi:    Infra, <MAC 'Vincent_WiFi' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    En-trak AP:      Infra, <MAC 'En-trak AP' [AC11]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Billy:           Infra, <MAC 'Billy' [AC32]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    TP-LINK_B99120:  Infra, <MAC 'TP-LINK_B99120' [AC16]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    ChanKY:          Infra, <MAC 'ChanKY' [AN25]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 32 WPA
    Glulumi Family (2.4GHz): Infra, <MAC 'Glulumi Family (2.4GHz)' [AC28]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Tracy:           Infra, <MAC 'Tracy' [AN27]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Tenda_03A5F4:    Infra, <MAC 'Tenda_03A5F4' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA
    CWWPS:           Infra, <MAC 'CWWPS' [AN29]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    Edward_2.4:      Infra, <MAC 'Edward_2.4' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Stamp:           Infra, <MAC 'Stamp' [AN31]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    summerho:        Infra, <MAC 'summerho' [AC30]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    2002:            Infra, <MAC '2002' [AN33]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    lee's home:      Infra, <MAC 'lee's home' [AN34]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Home Network 2.4Ghz: Infra, <MAC 'Home Network 2.4Ghz' [AN35]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    DR500GW-E0C306:  Infra, <MAC 'DR500GW-E0C306' [AC13]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA2
    CSL:             Infra, <MAC 'CSL' [AN37]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 29
    UnionPay:        Infra, <MAC 'UnionPay' [AN38]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27
    WONGHIM:         Infra, <MAC 'WONGHIM' [AN39]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 35 WPA
    LiFamily2:       Infra, <MAC 'LiFamily2' [AC17]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    LAM HOME:        Infra, <MAC 'LAM HOME' [AN41]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    snoopylam:       Infra, <MAC 'snoopylam' [AN42]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    dlink:           Infra, <MAC 'dlink' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39
    *dlink:          Infra, <MAC 'dlink' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37
    dlink-AA00:      Infra, <MAC 'dlink-AA00' [AN45]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    SIUPOPO2.4GHZ:   Infra, <MAC 'SIUPOPO2.4GHZ' [AC33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    xspeed1:         Infra, <MAC 'xspeed1' [AN47]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Ching01:         Infra, <MAC 'Ching01' [AN48]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA
    CSL Auto Connect:Infra, <MAC 'CSL Auto Connect' [AN49]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA2 Enterprise
    Wi-Fi.HK via CSL:Infra, <MAC 'Wi-Fi.HK via CSL' [AN50]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22

  IPv4 Settings:
    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: eth2 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth2' [IF]>

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

no-auto-default=<MAC 'eth2' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/dlink 1]] (600 root)
[connection] id=dlink 1 | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Asia/Hong_Kong (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth2      no frequency information.

wlan1     13 channels in total; available frequencies :
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
          Current Frequency=2.457 GHz (Channel 10)

##### iwlist scan #######################

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.432 GHz (Channel 5)
      11   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      6   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)

lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'dlink' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key: off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000020a802a28
                    Extra: Last beacon: 136ms ago
          Cell 02 - Address: <MAC 'Edward_2.4' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key :0n
                    ESSID:"Edward_2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000828373ef189
                    Extra: Last beacon: 1876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Aidan <MAC 'Aidan <MAC address> Adrian 2.4G' [AN1]> Adrian 2.4G' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key: on
                    ESSID:"Aidan & Adrian 2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000016d27511c
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'cal'shome' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key: on
                    ESSID:"cal'shome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000137b32bae25
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'dlink' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key : 0ff
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000752a68c176
                    Extra: Last beacon: 2232ms ago
          Cell 06 - Address: <MAC 'Default' [AC6]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key: on
                    ESSID:"Default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001788e9e009a
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Tenda_03C08C' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"Tenda_03C08C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001399d0d71aa
                    Extra: Last beacon: 2208ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'bellashome' [AC8]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key: on
                    ESSID:"bellashome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000495e65c80e
                    Extra: Last beacon: 248ms ago
          Cell 09 - Address: <MAC 'Apple jj' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key: on
                    ESSID:"Apple jj"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ea1e2c084
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'kyle ting' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key: on
                    ESSID:"kyle ting"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    ESSID:""
                    Mode:Master
                    Extra:tsf=0000000a1c724d80
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'En-trak AP' [AC11]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key: on
                    ESSID:"En-trak AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000011fee04d9195
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Lam-Home-TP-LINK-2.4G' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key: on
                    ESSID:"Lam-Home-TP-LINK-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000064ccb199
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'DR500GW-E0C306' [AC13]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key: on
                    ESSID:"DR500GW-E0C306"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000005cc79175
                    Extra: Last beacon: 17116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'chelsea' [AC14]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"chelsea"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000074f022173
                    Extra: Last beacon: 18764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Default' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key: on
                    ESSID:"Default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000043f4b2108f
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'TP-LINK_B99120' [AC16]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: on
                    ESSID:"TP-LINK_B99120"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011436eb5d80
                    Extra: Last beacon: 18708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'LiFamily2' [AC17]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key : on
                    ESSID:"LiFamily2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d2cb25a180
                    Extra: Last beacon: 1072ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Christopher' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key: on
                    ESSID:"Christopher"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000891c0180
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC '1315 2.4' [AC19]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"1315 2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000003bff79160
                    Extra: Last beacon: 1556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'jim' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key : On
                    ESSID:"jim"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f1ecb194
                    Extra: Last beacon: 1240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'CMCC-WEB' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key: off
                    ESSID:"CMCC-WEB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076ea279e
                    Extra: Last beacon: 18408ms ago
          Cell 22 - Address: <MAC 'CMCC' [AC22]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key : on
                    ESSID:"CMCC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076ea34c2
                    Extra: Last beacon: 18404ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 23 - Address: <MAC 'Universities via CSL' [AC23]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key : on
                    ESSID:"Universities via CSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076ea45b9
                    Extra: Last beacon: 18400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC 'UnionPay' [AC24]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key: off
                    ESSID:"UnionPay"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076ea4edd
                    Extra: Last beacon: 18400ms ago
          Cell 25 - Address: <MAC 'CSL Auto Connect' [AC25]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"CSL Auto Connect"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076ea56f1
                    Extra: Last beacon: 18396ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 26 - Address: <MAC 'TPTP' [AC26]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"TPTP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000041a00181
                    Extra: Last beacon: 1192ms ago
          Cell 27 - Address: <MAC 'LieBaoWiFi383' [AC27]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key: on
                    ESSID:"LieBaoWiFi383"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000011c0e52a181
                    Extra: Last beacon: 1188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'Glulumi Family (2.4GHz)' [AC28]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key: on
                    ESSID:"Glulumi Family (2.4GHz)"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000016e2fc180
                    Extra: Last beacon: 1592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'ROOM1630' [AC29]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key: on
                    ESSID:"ROOM1630"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005cdb7211c5
                    Extra: Last beacon: 1544ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'summerho' [AC30]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"summerho"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009d71dc180
                    Extra: Last beacon: 256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'belleungwifi' [AC31]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"belleungwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009e90d8d6e
                    Extra: Last beacon: 16736ms ago
          Cell 32 - Address: <MAC 'Billy' [AC32]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key: on
                    ESSID:"Billy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000013ac2ab1150
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'SIUPOPO2.4GHZ' [AC33]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key : on
                    ESSID:"SIUPOPO2.4GHZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000381dcd05703
                    Extra: Last beacon: 2176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC '
[[code/]]("http://ubuntuforums.org/misc.php?do=bbcode#code")

---

