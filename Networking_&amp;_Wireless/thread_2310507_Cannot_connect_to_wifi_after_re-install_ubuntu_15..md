---
title: "Cannot connect to wifi after re-install ubuntu 15.10 with intel 7260 wireless card"
date: 2016-01-19
forum: Networking &amp; Wireless
---

### Post by bolong2 on 2016-01-19
Hello - 
I encountered a very strange problem this morning. I used Xubuntu for a couple of month and today I tried Arch Linux. After Installed Arch I found my wifi is not working and I thought maybe it's the driver issue. So I wiped out and re-formatted my hard drive and then installed ubuntu. After the installation I found that the wi-fi is still not working. I can see my router in the wireless network menu but every time I tried to connect it gives me a message says"Disconnected from wireless network". I am pretty sure that it isn't a driver problem since I used the same version before(15.10) and the wifi works out of box. I also tried re-format my hard drive and install different versions of ubuntu(lubuntu, xubuntu with 14.04lts and 15.10) for many times but still cannot fix my wireless network.

Can someone give me some advice why the problem cannot be fixed even I wipe out the disk and re-install the system? I will do want I can to fix it since that's the only laptop I got and school has already started. Thanks for you help!

```


########## wireless info START ##########


Report from: 29 Dec 2130 22:34 EST -0500


Booted last: 29 Dec 2130 00:00 EST -0500


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


sed: can't read /home/bolong/.dmrc: No such file or directory


Could not be determined.


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c070]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 0781:5580 SanDisk Corp. SDCZ80 Flash Drive
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 13d3:5657 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                294912  0
mac80211              733184  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


wlp1s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       571     1  0 22:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-AC 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-16-generic
GENERAL.FIRMWARE-VERSION:               15.227938.0
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4954a33f-de73-4b66-a133-db36eb765779 | DDW365A3


SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR19-5G                     <MAC 'NETGEAR19-5G' [AC10]>  Infra  153   5765 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
DDW365A3                         <MAC 'DDW365A3' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
WARNING! VIRUS DETECTED!         <MAC 'WARNING! VIRUS DETECTED!' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Bluecow                          <MAC 'Bluecow' [AC3]>  Infra  4     2427 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
NETGEAR99                        <MAC 'NETGEAR99' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
NINJA                            <MAC 'NINJA' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
AriGold                          <MAC 'AriGold' [AN7]>  Infra  7     2442 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
--                               <MAC '' [AC9]>  Infra  36    5180 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
a nise apartment 520             <MAC 'a nise apartment 520' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
NETGEAR38                        <MAC 'NETGEAR38' [AC29]>  Infra  3     2422 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
I can hear you having sex-guest  <MAC 'I can hear you having sex-guest' [AC2]>  Infra  2     2417 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  --         no        
Bluecow-guest                    <MAC 'Bluecow-guest' [AC4]>  Infra  4     2427 MHz  54 Mbit/s  52      &#9602;&#9604;__  --         no        
Hallelujah                       <MAC 'Hallelujah' [AC12]>  Infra  157   5785 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        
NETGEAR20                        <MAC 'NETGEAR20' [AC30]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
NETGEAR20-5G                     <MAC 'NETGEAR20-5G' [AC11]>  Infra  157   5785 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
--                               <MAC '' [AC27]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
belkin.8e7                       <MAC 'belkin.8e7' [AN17]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
EMHOSU7                          <MAC 'EMHOSU7' [AC24]>  Infra  52    5260 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
NETGEAR19                        <MAC 'NETGEAR19' [AC26]>  Infra  11    2462 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2       no        
ATT9i7P4J4                       <MAC 'ATT9i7P4J4' [AN20]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
ATT6N8D9S8                       <MAC 'ATT6N8D9S8' [AN21]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
bxrp_5G                          <MAC 'bxrp_5G' [AC18]>  Infra  149   5745 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
544001                           <MAC '544001' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
TG1672GE2                        <MAC 'TG1672GE2' [AC14]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
artarch                          <MAC 'artarch' [AC19]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
Hallelujah                       <MAC 'Hallelujah' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
Rishi1                           <MAC 'Rishi1' [AC31]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
Yoga                             <MAC 'Yoga' [AC20]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        
600 Stinchcomb Apt4              <MAC '600 Stinchcomb Apt4' [AN29]>  Infra  6     2437 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
call me ouba                     <MAC 'call me ouba' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
TheBatcave                       <MAC 'TheBatcave' [AC21]>  Infra  149   5745 MHz  54 Mbit/s  17      &#9602;___  WPA2       no        
2WIRE433                         <MAC '2WIRE433' [AC15]>  Infra  10    2457 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
DDW3650B                         <MAC 'DDW3650B' [AN33]>  Infra  10    2457 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
TG862G12                         <MAC 'TG862G12' [AC22]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
xiaoqiang                        <MAC 'xiaoqiang' [AN35]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WEP        no        
ATT764                           <MAC 'ATT764' [AN36]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
APT7                             <MAC 'APT7' [AC34]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
bxrp                             <MAC 'bxrp' [AC23]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
ATT115                           <MAC 'ATT115' [AN39]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
Home                             <MAC 'Home' [AC25]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
WEILIANG                         <MAC 'WEILIANG' [AN41]>  Infra  9     2452 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
DRatcliff                        <MAC 'DRatcliff' [AN42]>  Infra  9     2452 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
Manjeet Singh                    <MAC 'Manjeet Singh' [AN43]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
TP-LINK_11E2                     <MAC 'TP-LINK_11E2' [AN44]>  Infra  9     2452 MHz  54 Mbit/s  20      &#9602;___  --         no        
Bluecow                          <MAC 'Bluecow' [AN45]>  Infra  36    5180 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        
EMHOSU7                          <MAC 'EMHOSU7' [AC28]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        


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
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/DDW365A3]] (600 root)
[connection] id=DDW365A3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=DDW365A3
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


wlp1s0    32 channels in total; available frequencies :
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


Channel occupancy:


      6   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      2   APs on   Frequency:2.427 GHz (Channel 4)
      7   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      10   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.26 GHz (Channel 52)
      2   APs on   Frequency:5.745 GHz
      1   APs on   Frequency:5.765 GHz
      2   APs on   Frequency:5.785 GHz


wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'WARNING! VIRUS DETECTED!' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"WARNING! VIRUS DETECTED!"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d227253be8
                    Extra: Last beacon: 14036ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'I can hear you having sex-guest' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"I can hear you having sex-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d227256a55
                    Extra: Last beacon: 13936ms ago
          Cell 03 - Address: <MAC 'Bluecow' [AC3]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Bluecow"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000182e11ecade
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Bluecow-guest' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"Bluecow-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000182e11ed952
                    Extra: Last beacon: 92ms ago
          Cell 05 - Address: <MAC 'DDW365A3' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"DDW365A3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000deb44dade4
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'NINJA' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"NINJA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014cdbfab8
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'a nise apartment 520' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"a nise apartment 520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013f20181a6
                    Extra: Last beacon: 12856ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR99' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR99"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004ba0d10bac8
                    Extra: Last beacon: 2684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c44a4b2e3
                    Extra: Last beacon: 12508ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'NETGEAR19-5G' [AC10]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR19-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001605760d2e
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'NETGEAR20-5G' [AC11]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR20-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a44264003a
                    Extra: Last beacon: 10032ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Hallelujah' [AC12]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Hallelujah"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b738218954
                    Extra: Last beacon: 10064ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC '544001' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"544001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000225e76d9
                    Extra: Last beacon: 27872ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'TG1672GE2' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TG1672GE2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000a4b5f58d34e
                    Extra: Last beacon: 13528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '2WIRE433' [AC15]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"2WIRE433"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000032ba9f770
                    Extra: Last beacon: 27480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Hallelujah' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Hallelujah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000111156180
                    Extra: Last beacon: 27352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'call me ouba' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"call me ouba"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf8e90719d
                    Extra: Last beacon: 12892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'bxrp_5G' [AC18]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"bxrp_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004edc67404c
                    Extra: Last beacon: 10264ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'artarch' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"artarch"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000043c721a6c64
                    Extra: Last beacon: 14160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Yoga' [AC20]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Yoga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008bfadc3f50
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'TheBatcave' [AC21]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TheBatcave"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a4b60419024
                    Extra: Last beacon: 24692ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'TG862G12' [AC22]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"TG862G12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002acadb7ccf
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'bxrp' [AC23]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"bxrp"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004edccb419a
                    Extra: Last beacon: 2820ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'EMHOSU7' [AC24]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"EMHOSU7"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000401a97b803b
                    Extra: Last beacon: 12128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'Home' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e0615b8c17
                    Extra: Last beacon: 12864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'NETGEAR19' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR19"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001608dc81e8
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC '' [AC27]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c442c2570
                    Extra: Last beacon: 13988ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'EMHOSU7' [AC28]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"EMHOSU7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000401ad25019f
                    Extra: Last beacon: 12876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'NETGEAR38' [AC29]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000018921ccd80
                    Extra: Last beacon: 13772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'NETGEAR20' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR20"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a442bb81ff
                    Extra: Last beacon: 2824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'Rishi1' [AC31]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Rishi1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000678ace614a
                    Extra: Last beacon: 28584ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'able' [AC32]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"able"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003cbd9d9a3c
                    Extra: Last beacon: 27924ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 33 - Address: <MAC 'HP-Print-C1-Deskjet 3510 series' [AC33]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-C1-Deskjet 3510 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000042cfbeb168a
                    Extra: Last beacon: 27408ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 34 - Address: <MAC 'APT7' [AC34]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"APT7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003b15d404233
                    Extra: Last beacon: 27400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 35 - Address: <MAC 'SBG6580BE' [AC35]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SBG6580BE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000aa819ec82
                    Extra: Last beacon: 14116ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 36 - Address: <MAC 'OUDOM' [AC36]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OUDOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013f19d8224
                    Extra: Last beacon: 14100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 37 - Address: <MAC '' [AC37]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000123dc3c4142
                    Extra: Last beacon: 14068ms ago
          Cell 38 - Address: <MAC 'Mfgsystems' [AC38]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Mfgsystems"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000123dc3c4627
                    Extra: Last beacon: 14068ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D59CBA6E05CEA656524E14B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.2.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75057B888CB98F986AD50C3
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y


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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    4.035915] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.80.2.3.d.bseq
[    4.054962] iwlwifi 0000:01:00.0: loaded firmware version 15.227938.0 op_mode iwlmvm
[    4.105873] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.105957] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[    4.270250] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.327284] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.537065] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    6.037062] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    6.037266] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[    6.256183] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)


########## wireless info END ############



```

---

### Post by bolong2 on 2016-01-20
1/20 updated wireless-info.txt file. Still can't find where the problem is. Thanks.

---

### Post by jeremy31 on 2016-01-21
The one thing that sticks out is the contents of /etc/NetworkManager/NetworkManager.conf as it shows managed=true

I would edit the file ```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
and change it to managed=false
Save, exit, reboot

---

### Post by bolong2 on 2016-01-23
Did it. But still not working. Will try to install ubuntu again. It's wired since I cannot connect to wifi even on the bootable usb.

---

