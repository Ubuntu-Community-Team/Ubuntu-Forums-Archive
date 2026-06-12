---
title: "HP 355 G2 WLAN does not connect to internet"
date: 2015-10-24
forum: Networking &amp; Wireless
---

### Post by grojal14 on 2015-10-24
Good evening,
I have a HP Laptop, Model 355 G2, installed Ubuntu 14.04 and my WLAN isn't working. First, when I started Ubuntu, I had an internet connection via WLAN for 10 Minutes, then it stopped. I was shown that I'm still connected with the router but I wasn't able to open any site in the browser. To reconnect didn't solve the problem. Then I did some researches in the internet and found this sites:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=2220169&highlight=hp+355+g2+wlan](http://ubuntuforums.org/showthread.php?t=2220169&highlight=hp+355+g2+wlan) 
[*][https://www.bitblokes.de/2015/01/lenovo-notebook-z40-wlan-karte-rtl8723be-realtek-unter-linux-mint-17-1-aktivieren/](https://www.bitblokes.de/2015/01/lenovo-notebook-z40-wlan-karte-rtl8723be-realtek-unter-linux-mint-17-1-aktivieren/) 
[*][http://ubuntuforums.org/showthread.php?t=2243691&p=13119513#post13119513](http://ubuntuforums.org/showthread.php?t=2243691&p=13119513#post13119513) 
[*][http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04) 
[*][http://ubuntuforums.org/showthread.php?t=2243978](http://ubuntuforums.org/showthread.php?t=2243978) 
[*][https://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182](https://forum.ubuntuusers.de/topic/kein-internet-seit-ubuntu-13-10-auf-lenovo-b54/#post-6266182) 
[*][http://wiki.ubuntuusers.de/wlan/karten/realtek](http://wiki.ubuntuusers.de/wlan/karten/realtek) 
[*][https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek) 
[/LIST]


I followed those instructions and now there is no connection for ten minutes, but I am connected with the router. The only way to get in the internet is a LAN connection.

```



########## wireless info START ##########

Report from: 25 Oct 2015 01:10 CEST +0200

Booted last: 24 Oct 2015 16:12 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-31-generic #36~14.04.1-Ubuntu SMP Thu Oct 8 10:21:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:22c2]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 004 Device 003: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 004 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0bda:5775 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 138a:0050 Validity Sensors, Inc. 
Bus 003 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:076c Microsoft Corp. Comfort Mouse 4500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be              94208  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
hp_wmi                 16384  0 
rtl_pci                28672  1 rtl8723be
sparse_keymap          16384  1 hp_wmi
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              708608  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1445293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096480403 (2.0 GB)  TX bytes:72810353 (72.8 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2098519 (2.0 MB)  TX bytes:42492 (42.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'dlink' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       807     1  0 Oct24 ?        00:00:09 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [dlink] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Jena Netz:       Infra, <MAC 'Jena Netz' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    HP-Print-B2-Deskjet 2540 series: Infra, <MAC 'HP-Print-B2-Deskjet 2540 series' [AC3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    iptime:          Infra, <MAC 'iptime' [AC9]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 84 WPA
    Schnucki:        Infra, <MAC 'Schnucki' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    rosenduft:       Infra, <MAC 'rosenduft' [AC10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA
    ALICE-WLAN38:    Infra, <MAC 'ALICE-WLAN38' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 60 WPA
    *dlink:          Infra, <MAC 'dlink' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    o2-WLAN63:       Infra, <MAC 'o2-WLAN63' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2
    DIGGADIGGENSEN_Network: Infra, <MAC 'DIGGADIGGENSEN_Network' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    o2-WLAN57:       Infra, <MAC 'o2-WLAN57' [AN10]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Telekom:         Infra, <MAC 'Telekom' [AC11]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54
    Tenda_3EF680:    Infra, <MAC 'Tenda_3EF680' [AC8]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA

  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

- Device: eth0  [Automatisches Ethernet] ---------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=802-11-wireless
[802-11-wireless] ssid=dlink | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box 7312]] (600 root)
[connection] id=FRITZ!Box 7312 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box 7312 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7170]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7170 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7170 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN-335349]] (600 root)
[connection] id=WLAN-335349 | type=802-11-wireless
[802-11-wireless] ssid=WLAN-335349 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FRITZ!Box Fon WLAN 7360]] (600 root)
[connection] id=FRITZ!Box Fon WLAN 7360 | type=802-11-wireless
[802-11-wireless] ssid=FRITZ!Box Fon WLAN 7360 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'dlink' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000068bf928e06
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ALICE-WLAN38' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000500302af4
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-B2-Deskjet 2540 series' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-B2-Deskjet 2540 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004e7c0f7ad08
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Jena Netz' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"Jena Netz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004e7d0a4df89
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'DIGGADIGGENSEN_Network' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"DIGGADIGGENSEN_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002777ecd229
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Schnucki' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Schnucki"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e22ac9ea3
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'o2-WLAN63' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000227ddf1216b
                    Extra: Last beacon: 192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Tenda_3EF680' [AC8]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Tenda_3EF680"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000014215db8183
                    Extra: Last beacon: 3896ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'iptime' [AC9]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"iptime"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001cab7417e
                    Extra: Last beacon: 2544ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'rosenduft' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"rosenduft"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a84c235
                    Extra: Last beacon: 2504ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Telekom' [AC11]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"Telekom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017b9f508580
                    Extra: Last beacon: 1804ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     B60F970654516A3D2F6FC24
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-31-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-31-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        64:74:3F:49:0D:D0:7D:39:34:C7:63:FC:5F:D3:1B:D2:24:B7:15:20
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
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
minstrel_vht_only: Y
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

[28365.845004] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[28365.845277] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[28366.391085] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[28367.559115] r8169 0000:02:00.0 eth0: link up
[28367.559139] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[28368.154814] wlan0: authenticate with <MAC 'dlink' [AC1]>
[28368.176935] wlan0: send auth to <MAC 'dlink' [AC1]> (try 1/3)
[28368.179986] wlan0: authenticated
[28368.184244] wlan0: associate with <MAC 'dlink' [AC1]> (try 1/3)
[28368.190287] wlan0: RX AssocResp from <MAC 'dlink' [AC1]> (capab=0xc11 status=0 aid=2)
[28368.191887] wlan0: associated
[28368.191954] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[28368.213370] wlan0: deauthenticating from <MAC 'dlink' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[28368.226309] wlan0: authenticate with <MAC 'dlink' [AC1]>
[28368.238122] wlan0: send auth to <MAC 'dlink' [AC1]> (try 1/3)
[28368.243093] wlan0: authenticated
[28368.244287] wlan0: associate with <MAC 'dlink' [AC1]> (try 1/3)
[28368.249639] wlan0: RX AssocResp from <MAC 'dlink' [AC1]> (capab=0xc11 status=0 aid=2)
[28368.250875] wlan0: associated

########## wireless info END ############



```

I hope I broke no Forum rules caused by not reading something.
And I would like to ask for appologizeing my english, I'm no native speaker.

Thank you for trying to help me!

Many greetings from Germany

Edit: the config file  /etc/modprobe.d/rtl8723be.conf is empty and in one of the sites it is written, that I should copy and paste something in it at a defined position to solve the problem.

---

### Post by grojal14 on 2015-11-12
It's me again,
if multi posting is forbidden, I'm sorry, but I wait for two weeks for an answer. My personal internet research brought no solutions too. Is this Problem impossible to solve?


Thank you
Grojal

---

### Post by howefield on 2015-11-12
Hello grojal14,

Unfortunately not a solution, but just 2 points to note, firstly I have moved your post to the "*Networking & Wireless*" forum where it is more likely to catch the eye of the very expert users here and secondly, please feel free to bump your post once a day, maybe a little more often than that if no response to your thread..

---

### Post by grojal14 on 2015-11-14
Hi howefield,
thank you very much for moving this post and the explanation of bumping my thread, I asked because in some Forums this is forbidden... I hope that this problem will be solved soon, so I can use my laptop at university.

Grojal

---

### Post by grojal14 on 2015-11-16
Is it possible that if I will wait, this problem will be solved in an update?

LG Grojal

---

### Post by grojal14 on 2015-11-23
So I'll bump this thread, I need the WLAN working for the university and hope for a solution.

---

### Post by ozzie1 on 2015-11-23
when you say you can connect to the router, can you ping it or open the config page? have you tried connecting to other wireless networks? are other devices connected to this network?

edit: have you tried this?
```
$ echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

---

### Post by grojal14 on 2015-11-24
To the first part: my router is working, I'm connected with my tablet and smartphone.
But today I hoped, that it could help if I will try your code again, did it and now it's working for 2 hours... I'll wait a little bit longer, but I hope that this problem is solved magically because I tried this code 4 weeks ago... But for now I am so happy, thank you!

Grojal

---

