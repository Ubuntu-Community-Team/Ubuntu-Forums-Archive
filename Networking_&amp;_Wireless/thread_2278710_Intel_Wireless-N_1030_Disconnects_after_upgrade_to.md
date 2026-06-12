---
title: "Intel Wireless-N 1030 Disconnects after upgrade to 15.04"
date: 2015-05-18
forum: Networking &amp; Wireless
---

### Post by carlo10 on 2015-05-18
Hello,

I have recently installed lubuntu on my Asus u36SD and I am encountering as well frequent disconnections. I thought I solved my problem with [this]("http://ubuntuforums.org/showthread.php?t=2264585&highlight=Intel+Corporation+Centrino+Wireless-N+1030") post but after upgrading I keep disconnecting from my WiFi and the I cannot connect after suspension neither. Any suggestion?

```


########## wireless info START ##########


Report from: 17 May 2015 21:26 CEST +0200


Booted last: 17 May 2015 20:10 CEST +0200


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN [8086:5305]
    Kernel driver in use: iwlwifi


05:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c


##### lsusb #############################


Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b1b9 Chicony Electronics Co., Ltd Asus Integrated Webcam
Bus 003 Device 003: ID 8086:0189 Intel Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                237568  0 
mac80211              720896  1 iwldvm
iwlwifi               196608  1 iwldvm
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
cfg80211              540672  3 iwlwifi,mac80211,iwldvm
mxm_wmi                16384  1 nouveau
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915,nouveau,asus_wmi


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
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:580930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384413 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:680359422 (680.3 MB)  TX bytes:164570171 (164.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 1030 [Rainbow Peak] (Centrino Wireless-N 1030 BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-16-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8151 v2.0 Gigabit Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


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


[[/etc/NetworkManager/system-connections/Bbox-B3AF85]] (600 root)
[connection] id=Bbox-B3AF85 | type=802-11-wireless
[802-11-wireless] ssid=Bbox-B3AF85 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-2648]] (600 root)
[connection] id=bbox2-2648 | type=wifi
[wifi] ssid=bbox2-2648 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Thomson907FDF]] (600 root)
[connection] id=Thomson907FDF | type=802-11-wireless
[802-11-wireless] ssid=Thomson907FDF | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


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


##### iwlist scan #######################


Channel occupancy:


      7   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'bbox2-2648' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"bbox2-2648"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000043be86e
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'telenet-E2C92' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"telenet-E2C92"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002be8ee70ef6
                    Extra: Last beacon: 96ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TELENETHOMESPOT' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"TELENETHOMESPOT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002be8ee71eef
                    Extra: Last beacon: 96ms ago
          Cell 04 - Address: <MAC 'TelenetWiFree' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"TelenetWiFree"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002be8ee72288
                    Extra: Last beacon: 96ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'bbox2-8258' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"bbox2-8258"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001955dd4bc6
                    Extra: Last beacon: 636ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'PROXIMUS_FON' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"PROXIMUS_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b6b65e9b3c
                    Extra: Last beacon: 96ms ago
          Cell 07 - Address: <MAC 'PROXIMUS_AUTO_FON' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"PROXIMUS_AUTO_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b6b65d760c
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'Joelle' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Joelle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e4dd4c792f
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'PROXIMUS_FON' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"PROXIMUS_FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010630b8e178
                    Extra: Last beacon: 96ms ago
          Cell 10 - Address: <MAC 'WiFi-2.4-77F7' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WiFi-2.4-77F7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010630b8c32c
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HP-Print-1D-Deskjet 3520 series' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-1D-Deskjet 3520 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000026a72244551
                    Extra: Last beacon: 96ms ago
          Cell 12 - Address: <MAC 'devolo-000B3BEB9DDA' [AC12]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"devolo-000B3BEB9DDA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000032339042
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'telenet-5FD6A' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"telenet-5FD6A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000456cf49173
                    Extra: Last beacon: 380ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'SpeedTouch1B0F30' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"SpeedTouch1B0F30"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 lo        Interface doesn't support scanning.


Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000535ea66bb5
                    Extra: Last beacon: 96ms ago
          Cell 15 - Address: <MAC 'TelenetWiFree' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TelenetWiFree"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000456cf49173
                    Extra: Last beacon: 312ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     259D494A97B601F302CD790
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/3.19.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     ADFD966DF2A9D56EE93BE48
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.19.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/sleep.d/30_disable_gpe01] (777 root)
case "$1" in
    thaw|resume)
        echo disable > /sys/firmware/acpi/interrupts/gpe01 2>/dev/null
        ;;
    *)
        ;;
esac
exit $?


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x008a (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 4021.431212] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[ 4021.437888] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[ 4034.085416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4042.626344] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled
[ 4042.633026] iwlwifi 0000:03:00.0: Radio type=0x2-0x2-0x1
[ 4281.712063] wlan0: authenticate with <MAC 'bbox2-2648' [AC1]>
[ 4281.712810] wlan0: send auth to <MAC 'bbox2-2648' [AC1]> (try 1/3)
[ 4281.719144] wlan0: authenticated
[ 4281.723251] wlan0: associate with <MAC 'bbox2-2648' [AC1]> (try 1/3)
[ 4281.726405] wlan0: RX AssocResp from <MAC 'bbox2-2648' [AC1]> (capab=0x431 status=0 aid=3)
[ 4281.738666] wlan0: associated


########## wireless info END ############



```

---

### Post by chili555 on 2015-05-18
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Reboot and let us hear your further report.

---

### Post by carlo10 on 2015-06-03
Thanks for the reply.

Unfortunately my modem does not support N speed. I have tried what you told me, but after a while the network keep disconnecting.

---

### Post by chili555 on 2015-06-04
Let's try a driver parameter. From the terminal:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if it's now working as expected.

---

### Post by carlo10 on 2015-06-28
Hello,

sorry for the late reply. Still have the same problem, after a while I am disconnected from the network and I can't connect again (before it was sufficient to disable the wifi and re-enable it again, now the trick doesn't seem to work anymore and I have to reboot)

---

### Post by chili555 on 2015-06-29
May we please see a new wireless_script result? Recall that you posted it in your original post.

---

