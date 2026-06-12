---
title: "connection issues with realtek 10ec:b723 ubuntu 14.04"
date: 2015-03-10
forum: Networking &amp; Wireless
---

### Post by Hanjonah on 2015-03-10
Hey all, 

my internet connection is unstable, disconnects, cannot be connected again within the session but I have to reboot everytime... I ve tried several things to get it working ( I am afraid maybe too much ) but it still won't work. I hope somebody can help me with this as I would like to continue using linux although I don't understand much of what the script says...

I d appreciate it!






```

########## wireless info START ##########

Report from: 10 Mar 2015 23:21 EET +0200

Booted last: 10 Mar 2015 23:20 EET +0200

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2246]
    Kernel driver in use: r8169

09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04ca:7032 Lite-On Technology Corp. 
Bus 002 Device 003: ID 138a:003f Validity Sensors, Inc. 
Bus 002 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
rtl8723be             125361  0 
rtl8723_common         23914  1 rtl8723be
btcoexist              54531  1 rtl8723be
rtl_pci                39740  1 rtl8723be
rtlwifi               105368  2 rtl_pci,rtl8723be
mac80211              572528  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              505345  2 mac80211,rtlwifi
compat                 15137  5 cfg80211,mac80211,btcoexist,rtlwifi,rtl8723be
wmi                    19177  1 hp_wmi

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
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fda4:9947:6c09:c200:c238:96ff:fe1e:54c9/64 Scope:Global
          inet6 addr: fe80::c238:96ff:fe1e:54c9/64 Scope:Link
          inet6 addr: fda4:9947:6c09:c200:b18c:60de:358:49ac/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:797 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:334068 (334.0 KB)  TX bytes:116325 (116.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"sofisofi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'sofisofi' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [sofisofi] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
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
    iskelehouse54:   Infra, <MAC 'iskelehouse54' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    abant:           Infra, <MAC 'abant' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    cok_ugrastik_ak: Infra, <MAC 'cok_ugrastik_ak' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    ileynat:         Infra, <MAC 'ileynat' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    SUPERONLINE_WiFi_3299: Infra, <MAC 'SUPERONLINE_WiFi_3299' [AN5]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    ANGEL:           Infra, <MAC 'ANGEL' [AC6]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Airties:         Infra, <MAC 'Airties' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    ram:             Infra, <MAC 'ram' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    *sofisofi:       Infra, <MAC 'sofisofi' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA2
    d:               Infra, <MAC 'd' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    TD854W_1:        Infra, <MAC 'TD854W_1' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    asnakn:          Infra, <MAC 'asnakn' [AN12]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    Emre:            Infra, <MAC 'Emre' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         fda4:9947:6c09:c200:b18c:60de:358:49ac
    Prefix:          64
    Gateway:         ::

    Address:         fda4:9947:6c09:c200:c238:96ff:fe1e:54c9
    Prefix:          64
    Gateway:         ::

    Address:         fe80::c238:96ff:fe1e:54c9
    Prefix:          64
    Gateway:         ::

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ISIK_WiFiT]] (600 root)
[connection] id=ISIK_WiFiT | type=802-11-wireless
[802-11-wireless] ssid=ISIK_WiFiT | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HP01781C]] (600 root)
[connection] id=HP01781C | type=802-11-wireless
[802-11-wireless] ssid=HP01781C | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ISIK_WIFI_DK]] (600 root)
[connection] id=ISIK_WIFI_DK | type=802-11-wireless
[802-11-wireless] ssid=ISIK_WIFI_DK | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HShome]] (600 root)
[connection] id=HShome | type=802-11-wireless
[802-11-wireless] ssid=HShome | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NetMASTER Uydunet-7DD5]] (600 root)
[connection] id=NetMASTER Uydunet-7DD5 | type=802-11-wireless
[802-11-wireless] ssid=NetMASTER Uydunet-7DD5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ISIK_WiFi]] (600 root)
[connection] id=ISIK_WiFi | type=802-11-wireless
[802-11-wireless] ssid=ISIK_WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/komsukomsa]] (600 root)
[connection] id=komsukomsa | type=802-11-wireless
[802-11-wireless] ssid=komsukomsa | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sofisofi]] (600 root)
[connection] id=sofisofi | type=802-11-wireless
[802-11-wireless] ssid=sofisofi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Istanbul (based on set time zone)

country TR:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 20), (N/A, 20)
    (5250 - 5330 @ 20), (N/A, 20), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'sofisofi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"sofisofi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000286295310c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'abant' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"abant"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000189889f714a
                    Extra: Last beacon: 3468ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Airties' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Airties"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001202723aa
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'iskelehouse54' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"iskelehouse54"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000050464544e6c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'd' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000034252f47ea1
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ANGEL' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ANGEL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000067a8d5b18d
                    Extra: Last beacon: 2484ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TD854W_1' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"TD854W_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f23903d17c
                    Extra: Last beacon: 1756ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'sevgiyanar' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"sevgiyanar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010e298751c
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (0) :
          Cell 09 - Address: <MAC 'ram' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ram"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028c3b183f0
                    Extra: Last beacon: 204ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'sevdanur' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"sevdanur"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a6340d9b
                    Extra: Last beacon: 4196ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'ileynat' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ileynat"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004f420b99c0
                    Extra: Last beacon: 3856ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     5D113E08097276ABF2EF3C6
depends:        rtlwifi,rtl8723-common,rtl_pci,compat,btcoexist,mac80211
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)

parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7C41A4007A6094567567091
depends:        mac80211,rtlwifi
vermagic:       3.13.0-46-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.13.0-46-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     44A5F49216740D2B9E16476
depends:        mac80211,compat,cfg80211
vermagic:       3.13.0-46-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.0-46-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
srcversion:     2E526B72B7E114629FB8EA1
depends:        cfg80211,compat
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.18.1-0-g39ca484) using backports v3.18.1-1-0-g5e9ec4c
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     07F008E2B6279F6399E5939
depends:        compat
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
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
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    9.407113] rtl8723be: Using firmware rtlwifi/rtl8723befw.bin
[    9.437365] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.437902] rtlwifi: rtlwifi: wireless switch is on
[   12.318301] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   13.219976] wlan0: authenticate with <MAC 'sofisofi' [AC1]>
[   13.230116] wlan0: send auth to <MAC 'sofisofi' [AC1]> (try 1/3)
[   13.232502] wlan0: authenticated
[   13.235274] wlan0: associate with <MAC 'sofisofi' [AC1]> (try 1/3)
[   13.245825] wlan0: RX AssocResp from <MAC 'sofisofi' [AC1]> (capab=0x431 status=0 aid=4)
[   13.245987] wlan0: associated
[   13.246051] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by Hanjonah on 2015-03-14
is there anything I typed wrong or is there nobody who can help me?

---

### Post by jeremy31 on 2015-03-14
Try changing the router to channel 8 or 9 and this usually helps too since you are already using 3.18 backports
```
[COLOR=#000000][FONT=Ubuntu Mono]echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot[/FONT][/COLOR]

---

### Post by Hanjonah on 2015-03-20
thank you so much jeremy. it has worked out just perfect!!

---

