---
title: "Qualcomm Atheros AR9285 on/off/very poor connectivity, Ubuntu 12.04.5 LTS"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by suchismit on 2014-09-27
hi guys,
i am having serious issues with my wireless connectivity i.e. it is very poor and frequently connect/deconnects. i needed your help to fix this issue. i am using Ubuntu 12.04.5 LTS precise. 

here is my lspci/kernel based output :-
i have a Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express). 

```

suchismit@schrilax:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:30a1]
    Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]
05:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
suchismit@schrilax:~$ uname -r
3.2.0-69-generic


```

i followed user bapoumba's 'before posting in networking and wireless' post and did run the update commands as given below and did a reboot but it did not help.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

i am providing the output of the wireless script (please see below). i also followed [ubuntu wifi troubleshooting link]("http://askubuntu.com/questions/235279/my-wifi-adapter-is-not-working-at-all-how-to-troubleshoot/235280#235280") and ran *rfkill list* to check for blocked/disabled switches but did not find any. additionally i installed the latest version of firmware i.e. *sudo apt-get install linux-firmware linux-firmware-nonfree*

i also tried to install extra drivers but did not find any network based additional drivers to install/activate. the drivers returned were all nvidia graphic drivers. i have been experimenting with backported kernel modules from the compat-wireless package and have been unsuccessful thus far. i do not know which is the right one to use. i do not have any package management tools installed which makes it hard. no internet connectivity also means that i have to "download" stuff using a usb.

nothing seems to work. please help.

```

########## wireless info START ##########

Report from: 27 Sep 2014 13:54 EDT -0400

Booted last: 27 Sep 2014 12:35 EDT -0400

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-69-generic #103-Ubuntu SMP Tue Sep 2 05:02:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Qualcomm Atheros Device [168c:30a1]
    Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:e000]

05:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:081b Logitech, Inc. Webcam C310
Bus 001 Device 003: ID 045e:0752 Microsoft Corp. 
Bus 001 Device 004: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 004: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                  96902  0 
mac80211              561944  1 ath9k
ath9k_common           13858  1 ath9k
ath9k_hw              405835  2 ath9k,ath9k_common
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              558268  3 ath9k,mac80211,ath
compat                 38485  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::6670:2ff:fe81:b9bd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:193897 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47100735 (47.1 MB)  TX bytes:752578 (752.5 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: connecting

- Device: wlan0  [UB_Secure] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    eduroam:         Infra, <MAC 'eduroam' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    UB_Secure:       Infra, <MAC 'UB_Secure' [AC18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    Erik's Wi-Fi Network: Infra, <MAC 'Erik's Wi-Fi Network' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    eduroam:         Infra, <MAC 'eduroam' [AC17]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    eduroam:         Infra, <MAC 'eduroam' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    UB_Gaming:       Infra, <MAC 'UB_Gaming' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92
    UB_Wireless:     Infra, <MAC 'UB_Wireless' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55
    UB_Guest:        Infra, <MAC 'UB_Guest' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57
    UB_Guest:        Infra, <MAC 'UB_Guest' [AC15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30
    UB_Gaming:       Infra, <MAC 'UB_Gaming' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    UB_Guest:        Infra, <MAC 'UB_Guest' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59
    UB_Wireless:     Infra, <MAC 'UB_Wireless' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    UB_Gaming:       Infra, <MAC 'UB_Gaming' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    UB_Guest:        Infra, <MAC 'UB_Guest' [AC16]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52
    UB_Wireless:     Infra, <MAC 'UB_Wireless' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35
    UB_Gaming:       Infra, <MAC 'UB_Gaming' [AC14]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34
    UB_Wireless:     Infra, <MAC 'UB_Wireless' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27
    eduroam:         Infra, <MAC 'eduroam' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    UB_Secure:       Infra, <MAC 'UB_Secure' [AN19]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    UB_Secure:       Infra, <MAC 'UB_Secure' [AN20]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    UB_Secure:       Infra, <MAC 'UB_Secure' [AN21]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise

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

[[/etc/NetworkManager/system-connections/UB_Wireless]] (600 root)
[connection] id=UB_Wireless | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=UB_Wireless | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UB_Secure]] (600 root)
[ipv6] method=auto
[connection] id=UB_Secure | type=802-11-wireless
[802-11-wireless] ssid=UB_Secure | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/VPML-Robot-Net]] (600 root)
[connection] id=VPML-Robot-Net | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=VPML-Robot-Net | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UB_Gaming]] (600 root)
[connection] id=UB_Gaming | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=UB_Gaming | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/UB_Guest]] (600 root)
[connection] id=UB_Guest | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=UB_Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

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

      4   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      9   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Erik's Wi-Fi Network' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Erik's Wi-Fi Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000428b37f9454
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UB_Gaming' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8e3dc822
                    Extra: Last beacon: 8236ms ago
          Cell 03 - Address: <MAC 'UB_Wireless' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8e3dc822
                    Extra: Last beacon: 8248ms ago
          Cell 04 - Address: <MAC 'UB_Guest' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8eb3b822
                    Extra: Last beacon: 444ms ago
          Cell 05 - Address: <MAC 'eduroam' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8eb55022
                    Extra: Last beacon: 432ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
          Cell 06 - Address: <MAC 'eduroam' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8d3bfa37
                    Extra: Last beacon: 12104ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
          Cell 07 - Address: <MAC 'UB_Wireless' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8d3bad96
                    Extra: Last beacon: 12104ms ago
          Cell 08 - Address: <MAC 'UB_Gaming' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8d3b7ebb
                    Extra: Last beacon: 12104ms ago
          Cell 09 - Address: <MAC 'UB_Guest' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8c9b0775
                    Extra: Last beacon: 12104ms ago
          Cell 10 - Address: <MAC 'eduroam' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8daff022
                    Extra: Last beacon: 12268ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : 802.1x Proprietary
          Cell 11 - Address: <MAC 'UB_Wireless' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8c9a8259
                    Extra: Last beacon: 12104ms ago
          Cell 12 - Address: <MAC 'UB_Wireless' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"UB_Wireless"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8daff02c
                    Extra: Last beacon: 12252ms ago
          Cell 13 - Address: <MAC 'UB_Gaming' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8c9a5d20
                    Extra: Last beacon: 12104ms ago
          Cell 14 - Address: <MAC 'UB_Gaming' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"UB_Gaming"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8daff022
                    Extra: Last beacon: 12240ms ago
          Cell 15 - Address: <MAC 'UB_Guest' [AC15]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8d3c2913
                    Extra: Last beacon: 12104ms ago
          Cell 16 - Address: <MAC 'UB_Guest' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"UB_Guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8daff022
                    Extra: Last beacon: 12280ms ago
          Cell 17 - Address: <MAC 'eduroam' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008fc8c9ad899
                    Extra: Last beacon: 12104ms ago
          Cell 18 - Address: <MAC 'UB_Secure' [AC18]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"UB_Secure"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/ath9k.ko
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F757CA803A7BB06F1C19F5B
depends:        ath9k_hw,mac80211,compat,ath9k_common,ath,cfg80211
vermagic:       3.2.0-69-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

[mac80211]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
srcversion:     B4440B9D19D120DB125A744
depends:        cfg80211,compat
vermagic:       3.2.0-69-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath9k_common]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/ath9k_common.ko
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     41DFB94EFCC2CF90E61DC51
depends:        compat,ath,ath9k_hw
vermagic:       3.2.0-69-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/ath9k_hw.ko
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     45E5A2994263F8CEFDDF191
depends:        compat,ath
vermagic:       3.2.0-69-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     95E684D2AC104014677558F
depends:        cfg80211
vermagic:       3.2.0-69-generic SMP mod_unload modversions 

[cfg80211]
filename:       /lib/modules/3.2.0-69-generic/updates/cw-3.10/cfg80211.ko
version:        backported from Linux (v3.10.17-0-g14e9c7d) using backports v3.10.17-2-0-g3301d6b
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     B3F4616FCDE92AAB7A4FFB0
depends:        compat
vermagic:       3.2.0-69-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
btcoex_enable: 0
enable_diversity: 0
nohwcrypt: 1

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

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:04:00.0 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[ 4677.098271] wlan0: authenticate with <MAC 'UB_Secure' [AN19]>
[ 4677.114096] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 1/3)
[ 4677.217655] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 2/3)
[ 4677.321354] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 3/3)
[ 4677.425052] wlan0: authentication with <MAC 'UB_Secure' [AN19]> timed out
[ 4678.279059] wlan0: authenticate with <MAC 'UB_Secure' [AN21]>
[ 4678.300942] wlan0: send auth to <MAC 'UB_Secure' [AN21]> (try 1/3)
[ 4678.302921] wlan0: authenticated
[ 4678.306430] wlan0: associate with <MAC 'UB_Secure' [AN21]> (try 1/3)
[ 4678.312139] wlan0: RX AssocResp from <MAC 'UB_Secure' [AN21]> (capab=0x431 status=0 aid=1)
[ 4678.312183] wlan0: associated
[ 4680.001904] wlan0: authenticate with <MAC 'UB_Secure' [AN21]>
[ 4680.017709] wlan0: send auth to <MAC 'UB_Secure' [AN21]> (try 1/3)
[ 4680.121137] wlan0: send auth to <MAC 'UB_Secure' [AN21]> (try 2/3)
[ 4680.228820] wlan0: send auth to <MAC 'UB_Secure' [AN21]> (try 3/3)
[ 4680.332514] wlan0: authentication with <MAC 'UB_Secure' [AN21]> timed out
[ 4685.004100] wlan0: deauthenticating from <MAC 'UB_Secure' [AN21]> by local choice (reason=3)
[ 4686.199986] wlan0: authenticate with <MAC 'UB_Secure' [AC18]>
[ 4686.221574] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 1/3)
[ 4686.422644] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 2/3)
[ 4686.626046] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 3/3)
[ 4686.829447] wlan0: authentication with <MAC 'UB_Secure' [AC18]> timed out
[ 4691.207159] wlan0: deauthenticating from <MAC 'UB_Secure' [AC18]> by local choice (reason=3)
[ 4691.372688] wlan0: authenticate with <MAC 'UB_Secure' [AC18]>
[ 4691.394415] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 1/3)
[ 4691.595463] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 2/3)
[ 4691.798870] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 3/3)
[ 4692.002270] wlan0: authentication with <MAC 'UB_Secure' [AC18]> timed out
[ 4695.226408] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4732.915388] wlan0: authenticate with <MAC 'UB_Secure' [AN19]>
[ 4732.936488] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 1/3)
[ 4732.938039] wlan0: authenticated
[ 4732.942228] wlan0: associate with <MAC 'UB_Secure' [AN19]> (try 1/3)
[ 4732.965815] wlan0: RX AssocResp from <MAC 'UB_Secure' [AN19]> (capab=0x431 status=0 aid=2)
[ 4732.965866] wlan0: associated
[ 4732.967299] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4735.917908] wlan0: authenticate with <MAC 'UB_Secure' [AN20]>
[ 4735.939620] wlan0: send auth to <MAC 'UB_Secure' [AN20]> (try 1/3)
[ 4736.086214] wlan0: send auth to <MAC 'UB_Secure' [AN20]> (try 2/3)
[ 4736.200553] wlan0: send auth to <MAC 'UB_Secure' [AN20]> (try 3/3)
[ 4736.348130] wlan0: authentication with <MAC 'UB_Secure' [AN20]> timed out
[ 4737.194139] wlan0: authenticate with <MAC 'UB_Secure' [AN19]>
[ 4737.215950] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 1/3)
[ 4737.317279] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 2/3)
[ 4737.420972] wlan0: send auth to <MAC 'UB_Secure' [AN19]> (try 3/3)
[ 4737.524683] wlan0: authentication with <MAC 'UB_Secure' [AN19]> timed out
[ 4740.926044] wlan0: deauthenticating from <MAC 'UB_Secure' [AN19]> by local choice (reason=3)
[ 4743.040467] wlan0: no IPv6 routers present
[ 4744.983541] wlan0: authenticate with <MAC 'UB_Secure' [AC18]>
[ 4745.005146] wlan0: direct probe to <MAC 'UB_Secure' [AC18]> (try 1/3)

########## wireless info END ############


```

---

### Post by varunendra on 2014-09-29
You are using kernel 3.2 series. Kernel 3.8 and later have support for your Ethernet card, and the latest kernel - 3.13 series, may have the best support for your hardware.

If a clean installation is not a problem for you, right now the best option for you is to install Ubuntu 14.04.1. Its live DVD/USB may give you an option to 'Upgrade' (thus trying to keep your programs/settings), but I'm not sure about that.

If you don't want to do a clean install for some reason, the next best option is to upgrade your Hardware Enablement Stack to get the benefit of the latest kernel and other packages. A simple update won't automatically upgrade it, a user has to opt it manually. Details here : [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Since you don't have a working internet connection, you may try the "--print-uris" option of "apt-get" to get the download URIs of the required packages, then install them manually with "dpkg -i <package(s) name or *>".

If this sounds complex, and a clean install is not an option, please show us the output of -
```
apt-get install --install-recommends --print-uris linux-generic-lts-trusty xserver-xorg-lts-trusty libgl1-mesa-glx-lts-trusty
```
It will pretend to install the packages (if their info is in the apt-cache), but instead of actually installing them, will return their download URIs. You can use these URIs to download them on another system > copy to the target system > install with 'dpkg'.

However, as a general precaution, you should backup your data and current system state (using clonezilla or whatever you prefer) before upgrading these. Just in case something doesn't go well and you need to start over..

---

