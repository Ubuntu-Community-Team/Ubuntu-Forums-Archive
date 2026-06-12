---
title: "Qualcomm Atheros AR9285 Adapter keeps dropping wifi connection ubuntu 14.04.3 LTS"
date: 2015-09-27
forum: Networking &amp; Wireless
---

### Post by yash7 on 2015-09-27
Hey, this is the first time I am posting a thread, normally I find solution through threads posted earlier. I couldn't find a solution for this problem. My wifi keeps dropping on Ubuntu 14.04.3 LTS, I tried everything and even re-installed it thrice that didn't work. Need your help. I hate restarting my computer during work just to get connected to wifi again. It usually works fine if I don't move my computer, as soon as I move it, the wifi gets disconnected. I ran the code and here is the result.

```
########## wireless info START ##########


Report from: 28 Sep 2015 00:30 IST +0530


Booted last: 27 Sep 2015 23:31 IST +0530


Script from: 14 Jul 2015 17:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-49-generic #65~14.04.1-Ubuntu SMP Wed Sep 9 10:03:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Lenovo Device [17aa:3979]
    Kernel driver in use: alx


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lenovo Device [17aa:30a1]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 141379  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
cfg80211              498458  4 ath,ath9k_common,ath9k,mac80211
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop


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
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53424213 (53.4 MB)  TX bytes:6142051 (6.1 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"sweet home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'sweet home' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:540   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       761     1  0 Sep27 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [sweet home] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
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
    schin:           Infra, <MAC 'schin' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA
    spunk:           Infra, <MAC 'spunk' [AC11]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ms:              Infra, <MAC 'ms' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA
    jmd:             Infra, <MAC 'jmd' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA
    *sweet home:     Infra, <MAC 'sweet home' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2
    ishu1:           Infra, <MAC 'ishu1' [AC6]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA
    infection3:      Infra, <MAC 'infection3' [AC7]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    MGMNT:           Infra, <MAC 'MGMNT' [AC8]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 25 WEP
    Virus.detected:  Infra, <MAC 'Virus.detected' [AC12]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 32 WPA2


  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/P Mukharji]] (600 root)
[connection] id=P Mukharji | type=802-11-wireless
[802-11-wireless] ssid=P Mukharji | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tata-Photon-Max-Wi-Fi-1D87]] (600 root)
[connection] id=Tata-Photon-Max-Wi-Fi-1D87 | type=802-11-wireless
[802-11-wireless] ssid=Tata-Photon-Max-Wi-Fi-1D87 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/P Mukharji_EXT]] (600 root)
[connection] id=P Mukharji_EXT | type=802-11-wireless
[802-11-wireless] ssid=P Mukharji_EXT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/sweet home]] (600 root)
[connection] id=sweet home | type=802-11-wireless
[802-11-wireless] ssid=sweet home | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Tata-Photon-Max-Wi-Fi-F779]] (600 root)
[connection] id=Tata-Photon-Max-Wi-Fi-F779 | type=802-11-wireless
[802-11-wireless] ssid=Tata-Photon-Max-Wi-Fi-F779 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.472 GHz (Channel 13)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'sweet home' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key on
                    ESSID:"sweet home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001206b30c57
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'schin' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key on
                    ESSID:"schin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000047ec69619
                    Extra: Last beacon: 2220ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000047f97b485
                    Extra: Last beacon: 1912ms ago
          Cell 04 - Address: <MAC 'ms' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key on
                    ESSID:"ms"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007aacbde2f
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'jmd' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key on
                    ESSID:"jmd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e203d11cf
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ishu1' [AC6]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key on
                    ESSID:"ishu1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000328ca13c20
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'infection3' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key on
                    ESSID:"infection3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000328b97f1cc
                    Extra: Last beacon: 13440ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'MGMNT' [AC8]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption keyn
                    ESSID:"MGMNT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000328b97fafe
                    Extra: Last beacon: 13440ms ago
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000047f930736
                    Extra: Last beacon: 2220ms ago
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000047f930a47
                    Extra: Last beacon: 2216ms ago
          Cell 11 - Address: <MAC 'spunk' [AC11]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key on
                    ESSID:"spunk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001e251717c
                    Extra: Last beacon: 1928ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i
/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Virus.detected' [AC12]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key on
                    ESSID:"Virus.detected"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c9461d4c1
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC '' [AC13]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000328c9ce74a
                    Extra: Last beacon: 348ms ago


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CED1D76477A777795A07D73
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512
parm:           debug debugging mask (uint)
parm:           nohwcryptoisable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.16.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5375B0354B6CF7C84FC1934
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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
# PCI device 0x1969:0x1091 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  664.926766] wlan0: deauthenticating from <MAC 'sweet home' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  667.156155] ath: phy0: ASPM enabled: 0x42
[  669.814879] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  670.748006] wlan0: authenticate with <MAC 'sweet home' [AC1]>
[  670.754762] wlan0: send auth to <MAC 'sweet home' [AC1]> (try 1/3)
[  670.756800] wlan0: authenticated
[  670.757040] ath9k 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  670.757045] ath9k 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  670.759301] wlan0: associate with <MAC 'sweet home' [AC1]> (try 1/3)
[  670.761941] wlan0: RX AssocResp from <MAC 'sweet home' [AC1]> (capab=0x411 status=0 aid=2)
[  670.762012] wlan0: associated
[  670.762049] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

### Post by praseodym on 2015-09-27
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by yash7 on 2015-09-28
Praseodym - I can't really change the router settings. Also, it is not just with my home router. It happens with office wifi, and when I go to cafe's as well. Is it any other way?

---

### Post by praseodym on 2015-09-28
Try Wicd instead of the network-manager:

```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```

---

### Post by yash7 on 2015-09-28
I am guessing it works fine now. I will use it for a day tomorrow at work and will let you know. Thank you so much!

---

### Post by yash7 on 2015-09-29
Hey, the wifi still drops at times, but it is less frequent. So, I can use it fine. If you do have any other better solution it would be nice to try.

---

