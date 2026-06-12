---
title: "HP Pavilion drops connection, Ubuntu 14.04."
date: 2015-08-20
forum: Networking &amp; Wireless
---

### Post by nick198 on 2015-08-20
Hello, 

my HP Pavilion Laptop keeps dropping the connection. 
I've followed the steps on this thread: [http://ubuntuforums.org/showthread.php?t=370108&](http://ubuntuforums.org/showthread.php?t=370108&)

It worked for about a day then it started dropping the connection again every 20-30minutes. 

This is the info: 

```


########## wireless info START ##########

Report from: 17 Aug 2015 15:36 CEST +0200

Booted last: 17 Aug 2015 15:29 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:22c8]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b45e Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 18249  0 
sparse_keymap          13890  1 hp_wmi
rtl8723be              87260  0 
btcoexist              55886  1 rtl8723be
rtl8723_common         23427  1 rtl8723be
rtl_pci                27306  1 rtl8723be
rtlwifi                69157  2 rtl_pci,rtl8723be
mac80211              687021  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              521225  2 mac80211,rtlwifi
wmi                    19379  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5351 errors:0 dropped:2 overruns:0 frame:0
          TX packets:3838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5323090 (5.3 MB)  TX bytes:466130 (466.1 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:4c50:44f:ce00:5da5:47e0:b05:e916/64 Scope:Global
          inet6 addr: 2001:4c50:44f:ce00:<IP6 'wlan0' [IF]>/64 Scope:Global
          inet6 addr: 2001:4c50:44f:ce00::9/128 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2714584 (2.7 MB)  TX bytes:343088 (343.0 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Tech_D0050880"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Tech_D0050880' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=10/70  Signal level=-100 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search cm.cablesurf.de

##### network managers ##################

Installed:

    NetworkManager

Running:

root       729     1  0 15:29 ?        00:00:00 NetworkManager

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
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

- Device: wlan0  [Tech_D0050880] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
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
    MeinWlan:        Infra, <MAC 'MeinWlan' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    SveniSvenia:     Infra, <MAC 'SveniSvenia' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Frieden111:      Infra, <MAC 'Frieden111' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    EasyBox-B05D29:  Infra, <MAC 'EasyBox-B05D29' [AC6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Tech_D0054108:   Infra, <MAC 'Tech_D0054108' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Gongie + Kauli:  Infra, <MAC 'Gongie + Kauli' [AN6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    tinawlan:        Infra, <MAC 'tinawlan' [AN7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 64 WPA
    FRITZ!Box 3272:  Infra, <MAC 'FRITZ!Box 3272' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    das_netz:        Infra, <MAC 'das_netz' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Quelle:          Infra, <MAC 'Quelle' [AC10]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    WLAN-173755:     Infra, <MAC 'WLAN-173755' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Telekom_FON:     Infra, <MAC 'Telekom_FON' [AN12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30
    *Tech_D0050880:  Infra, <MAC 'Tech_D0050880' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    WLAN-470C53:     Infra, <MAC 'WLAN-470C53' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2
    WLAN-6DD562:     Infra, <MAC 'WLAN-6DD562' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    Koelle Alaaf:    Infra, <MAC 'Koelle Alaaf' [AN16]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 37 WPA2
    EasyBox-D57634:  Infra, <MAC 'EasyBox-D57634' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Zwergen:         Infra, <MAC 'Zwergen' [AN18]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    61be94:          Infra, <MAC '61be94' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    FRITZ!Box 7490:  Infra, <MAC 'FRITZ!Box 7490' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Tech_D0040524:   Infra, <MAC 'Tech_D0040524' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    FRITZ!Box 3272:  Infra, <MAC 'FRITZ!Box 3272' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    belkin.3b69:     Infra, <MAC 'belkin.3b69' [AN23]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.28
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             195.234.128.9
    DNS:             195.234.128.16

  IPv6 Settings:
    Address:         2001:4c50:44f:ce00::9
    Prefix:          128
    Gateway:         fe80::4632:c8ff:feb0:8b4f

    Address:         2001:4c50:44f:ce00:5da5:47e0:b05:e916
    Prefix:          64
    Gateway:         fe80::4632:c8ff:feb0:8b4f

    Address:         2001:4c50:44f:ce00:<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::4632:c8ff:feb0:8b4f

    Address:         fe80::<IP6 'wlan0' [IF]>
    Prefix:          64
    Gateway:         fe80::4632:c8ff:feb0:8b4f

    Address:         2001:4c50:44f:ce00::9
    Prefix:          128
    Gateway:         ::

    DNS:             2001:4c50:6:4000::9
    DNS:             2001:4c50:6:4000::16

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

[[/etc/NetworkManager/system-connections/Tech_D0050880]] (600 root)
[connection] id=Tech_D0050880 | type=802-11-wireless
[802-11-wireless] ssid=Tech_D0050880 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tech_D0050880' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Tech_D0050880"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000211800b8b5f
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MeinWlan' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=10 dBm  
                    Encryption key:on
                    ESSID:"MeinWlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cad7e18152
                    Extra: Last beacon: 3580ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'SveniSvenia' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"SveniSvenia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b158f71e
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Frieden111' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Frieden111"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ee1be58754
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 05 - Address: <MAC 'WLAN-6DD562' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"WLAN-6DD562"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021e3741d41e
                    Extra: Last beacon: 1376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'EasyBox-B05D29' [AC6]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-B05D29"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000af76ea44e04
                    Extra: Last beacon: 348ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 07 - Address: <MAC 'FRITZ!Box 3272' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 3272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009ae2c1c180
                    Extra: Last beacon: 3920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'EasyBox-D57634' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-D57634"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009aded83175
                    Extra: Last beacon: 1864ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'FRITZ!Box 3272' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 3272"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003a52b477fb1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Quelle' [AC10]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Quelle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000157552219bf3
                    Extra: Last beacon: 400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-031600-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E4D3FCB715C0CB33E42D11E
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   11.949263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.828806] wlan0: authenticate with <MAC 'Tech_D0050880' [AC1]>
[   13.847955] wlan0: send auth to <MAC 'Tech_D0050880' [AC1]> (try 1/3)
[   13.850189] wlan0: authenticated
[   13.851338] wlan0: associate with <MAC 'Tech_D0050880' [AC1]> (try 1/3)
[   13.854469] wlan0: RX AssocResp from <MAC 'Tech_D0050880' [AC1]> (capab=0x411 status=0 aid=2)
[   13.854635] wlan0: associated
[   13.854648] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   14.719002] wlan0: deauthenticating from <MAC 'Tech_D0050880' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   14.750767] wlan0: authenticate with <MAC 'Tech_D0050880' [AC1]>
[   14.760933] wlan0: send auth to <MAC 'Tech_D0050880' [AC1]> (try 1/3)
[   14.762488] wlan0: authenticated
[   14.764230] wlan0: associate with <MAC 'Tech_D0050880' [AC1]> (try 1/3)
[   14.767330] wlan0: RX AssocResp from <MAC 'Tech_D0050880' [AC1]> (capab=0x411 status=0 aid=2)
[   14.767465] wlan0: associated

########## wireless info END ############



```

Thank you!

---

### Post by nick198 on 2015-08-21
Anyone? :/

---

