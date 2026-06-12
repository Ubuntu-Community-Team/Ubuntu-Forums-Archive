---
title: "Netgear A6200 Wireless USB Adapter - Connection Dropped"
date: 2015-03-13
forum: Networking &amp; Wireless
---

### Post by daniel-gr-23 on 2015-03-13
Hi there!

I apologize if this has been asked before, but I searched for days now, finding nothing to solve my problem :(

I set up my A6200 Wireless Adapter as described in another thread ([http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04](http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04)) and it works fine - for a while. But after an unspecified time (seriously, it is different every time, sometimes it lasts half an hour, sometimes only 5 Minutes) the connection is "gone", as in I can't connect to my LAN and/or Internet anymore. It is **still listed as** **active and connected** though, that's why I'm kind of lost on where to look for errors here.

I'll gladly provide more information, sadly I am kind of new to networking with linux machines, so it would be great if someone could help me out. I need the connection for work, and my only workaround is using an android phone tether, as I have no option to plug myself an ethernet cable at the time :D not very satisfying.

Thanks in advance!

Edit: I forgot to provide my version number before, I'm running 14.04!

---

### Post by wildmanne39 on 2015-03-13
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by daniel-gr-23 on 2015-03-14
Hi, thank you for your reply!


This is the wireless-info.txt for when I still had a connection:


```



########## wireless info START ##########


Report from: 14 Mar 2015 10:59 CET +0100


Booted last: 14 Mar 2015 10:56 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7599]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 003: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:074b Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
wmi                    19177  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac6:8eff:fe86:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1971975 (1.9 MB)  TX bytes:520948 (520.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11b  ESSID:"TP-LINK_9D8426"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'TP-LINK_9D8426' [AC1]>   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:166  Invalid misc:7637   Missed beacon:0


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


- Device: wlan0  [Automatisch TP-LINK_9D8426] ----------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           11 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UPC0049402:      Infra, <MAC 'UPC0049402' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    42undSunsdNix:   Infra, <MAC '42undSunsdNix' [AN2]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 55 WPA2
    UPC1381976:      Infra, <MAC 'UPC1381976' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    UPC1071460:      Infra, <MAC 'UPC1071460' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    TMOBILE-84808:   Infra, <MAC 'TMOBILE-84808' [AC7]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    WLAN.Tele2.net:  Infra, <MAC 'WLAN.Tele2.net' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC2114016:      Infra, <MAC 'UPC2114016' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    UPC013280:       Infra, <MAC 'UPC013280' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    UPC1383734:      Infra, <MAC 'UPC1383734' [AC11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    defekt:          Infra, <MAC 'defekt' [AN10]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA2
    UPC7467167:      Infra, <MAC 'UPC7467167' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    GAST:            Infra, <MAC 'GAST' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    *TP-LINK_9D8426: Infra, <MAC 'TP-LINK_9D8426' [AC1]>, Freq 2442 MHz, Rate 11 Mb/s, Strength 84 WPA WPA2
    TMOBILE-30052:   Infra, <MAC 'TMOBILE-30052' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    GAST:            Infra, <MAC 'GAST' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/UPC0049402]] (600 root)
[connection] id=UPC0049402 | type=802-11-wireless
[802-11-wireless] ssid=UPC0049402 | bssid=<MAC 'UPC0049402' [AC5]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Automatisch TP-LINK_9D8426]] (600 root)
[connection] id=Automatisch TP-LINK_9D8426 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_9D8426 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC1071460]] (600 root)
[connection] id=UPC1071460 | type=802-11-wireless
[802-11-wireless] ssid=UPC1071460 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)


##### iwlist scan #######################


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_9D8426' [AC1]>
                    ESSID:"TP-LINK_9D8426"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:84/100  Signal level:-42 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC1381976' [AC2]>
                    ESSID:"UPC1381976"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'UPC1071460' [AC3]>
                    ESSID:"UPC1071460"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'UPC2114016' [AC4]>
                    ESSID:"UPC2114016"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'UPC0049402' [AC5]>
                    ESSID:"UPC0049402"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'WLAN.Tele2.net' [AC6]>
                    ESSID:"WLAN.Tele2.net"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TMOBILE-84808' [AC7]>
                    ESSID:"TMOBILE-84808"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TMOBILE-30052' [AC8]>
                    ESSID:"TMOBILE-30052"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:12/100  Signal level:-88 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '' [AC9]>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 10 - Address: <MAC 'UPC7467167' [AC10]>
                    ESSID:"UPC7467167"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'UPC1383734' [AC11]>
                    ESSID:"UPC1383734"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/bcmwlhigh5.conf]
options bcmwlhigh5 pio=1 qos=0


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   28.984748] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   40.149579] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.788297] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[   50.328045] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[   66.920373] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=192.168.1.103 LEN=290 TOS=0x00 PREC=0x00 TTL=64 ID=88 DF PROTO=UDP SPT=1900 DPT=49816 LEN=270 
[   66.992140] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   67.202465] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=192.168.1.103 LEN=387 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=2061 DPT=49816 LEN=367 
[   67.298154] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[   67.507068] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[   67.817231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=494 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55988 DPT=49816 LEN=474 
[  127.331067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38980 DPT=54958 LEN=522 
[  128.349209] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36802 DPT=54958 LEN=522 
[  129.377986] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51937 DPT=54958 LEN=522 
[  161.891354] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  165.572680] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  187.159634] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=239.192.0.0 LEN=120 TOS=0x00 PREC=0x00 TTL=3 ID=28531 DF PROTO=UDP SPT=3838 DPT=3838 LEN=100 


########## wireless info END ############

```


And this is it shortly after it went out:


```



########## wireless info START ##########


Report from: 14 Mar 2015 11:30 CET +0100


Booted last: 14 Mar 2015 10:56 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7599]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 003: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:074b Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
wmi                    19177  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac6:8eff:fe86:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:380934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:323230841 (323.2 MB)  TX bytes:370208269 (370.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11b  ESSID:"TP-LINK_9D8426"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'TP-LINK_9D8426' [AC1]>   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:49770  Invalid misc:68950   Missed beacon:0


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


- Device: wlan0  [Automatisch TP-LINK_9D8426] ----------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           11 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UPC0049402:      Infra, <MAC 'UPC0049402' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    UPC1381976:      Infra, <MAC 'UPC1381976' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    UPC1071460:      Infra, <MAC 'UPC1071460' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    TMOBILE-84808:   Infra, <MAC 'TMOBILE-84808' [AC5]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    WLAN.Tele2.net:  Infra, <MAC 'WLAN.Tele2.net' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC2114016:      Infra, <MAC 'UPC2114016' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    *TP-LINK_9D8426: Infra, <MAC 'TP-LINK_9D8426' [AC1]>, Freq 2442 MHz, Rate 11 Mb/s, Strength 78 WPA WPA2
    42undSunsdNix:   Infra, <MAC '42undSunsdNix' [AC11]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 10 WPA2
    GAST:            Infra, <MAC 'GAST' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/UPC0049402]] (600 root)
[connection] id=UPC0049402 | type=802-11-wireless
[802-11-wireless] ssid=UPC0049402 | bssid=<MAC 'UPC0049402' [AC3]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Automatisch TP-LINK_9D8426]] (600 root)
[connection] id=Automatisch TP-LINK_9D8426 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_9D8426 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC1071460]] (600 root)
[connection] id=UPC1071460 | type=802-11-wireless
[802-11-wireless] ssid=UPC1071460 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TP-LINK_9D8426' [AC1]>
                    ESSID:"TP-LINK_9D8426"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: <MAC 'UPC0049402' [AC3]>
                    ESSID:"UPC0049402"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'UPC1381976' [AC4]>
                    ESSID:"UPC1381976"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'TMOBILE-84808' [AC5]>
                    ESSID:"TMOBILE-84808"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC1071460' [AC6]>
                    ESSID:"UPC1071460"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC2114016' [AC7]>
                    ESSID:"UPC2114016"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WLAN.Tele2.net' [AC8]>
                    ESSID:"WLAN.Tele2.net"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'GAST' [AC9]>
                    ESSID:"GAST"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC7467167' [AC10]>
                    ESSID:"UPC7467167"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC '42undSunsdNix' [AC11]>
                    ESSID:"42undSunsdNix"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (2) : PSK unknown (6)
          Cell 12 - Address: <MAC 'defekt' [AC12]>
                    ESSID:"defekt"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'UPC013280' [AC13]>
                    ESSID:"UPC013280"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'UPC0046384' [AC14]>
                    ESSID:"UPC0046384"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/bcmwlhigh5.conf]
options bcmwlhigh5 pio=1 qos=0


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   67.817231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=494 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55988 DPT=49816 LEN=474 
[  127.331067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38980 DPT=54958 LEN=522 
[  128.349209] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=36802 DPT=54958 LEN=522 
[  129.377986] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51937 DPT=54958 LEN=522 
[  161.891354] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  165.572680] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  187.159634] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=192.168.1.103 DST=239.192.0.0 LEN=120 TOS=0x00 PREC=0x00 TTL=3 ID=28531 DF PROTO=UDP SPT=3838 DPT=3838 LEN=100 
[  235.099798] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43884 DPT=39922 LEN=522 
[  236.130799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40093 DPT=39922 LEN=522 
[  286.743540] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  288.682373] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  295.680764] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  354.847208] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=40307 DPT=55450 LEN=522 
[  355.866135] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54699 DPT=55450 LEN=522 
[  356.884089] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48039 DPT=55450 LEN=522 
[  367.330939] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48930 DPT=50169 LEN=522 
[  411.595935] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  416.503944] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  425.430269] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60041 DPT=57339 LEN=522 
[  447.846851] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=39693 DF PROTO=TCP SPT=55777 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  471.648567] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40402 DF PROTO=TCP SPT=55894 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  486.642208] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=40406 DF PROTO=TCP SPT=55894 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  510.644809] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46575 DF PROTO=TCP SPT=56002 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  525.656886] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=46579 DF PROTO=TCP SPT=56002 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  547.078995] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43179 DPT=42574 LEN=522 
[  564.799329] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=192.168.1.103 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=32214 DF PROTO=TCP SPT=56189 DPT=16641 WINDOW=29200 RES=0x00 SYN URGP=0 
[  594.744532] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45837 DPT=33838 LEN=522 
[  607.208303] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55264 DPT=36490 LEN=522 
[  661.190400] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  665.293566] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  667.028637] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56829 DPT=57749 LEN=522 
[  714.471931] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47100 DPT=34650 LEN=522 
[  715.493810] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34620 DPT=34650 LEN=522 
[  726.744030] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59014 DPT=60567 LEN=522 
[  786.042256] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  786.560878] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43855 DPT=37236 LEN=522 
[  787.587118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58780 DPT=37236 LEN=522 
[  834.113354] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55901 DPT=36855 LEN=522 
[  835.126933] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38669 DPT=36855 LEN=522 
[  846.481582] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43386 DPT=59582 LEN=522 
[  906.418167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47062 DPT=53882 LEN=522 
[  907.375587] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59168 DPT=53882 LEN=522 
[  908.443501] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34474 DPT=53882 LEN=522 
[  932.659878] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:d8:50:e6:7a:af:33:08:00 SRC=192.168.1.102 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  953.968711] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=44184 DPT=38824 LEN=522 
[  966.546027] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=48690 DPT=51747 LEN=522 
[ 1026.567979] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=52197 DPT=42565 LEN=522 
[ 1027.683578] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58266 DPT=42565 LEN=522 
[ 1028.705362] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=49910 DPT=42565 LEN=522 
[ 1044.752933] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1073.179039] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43126 DPT=50604 LEN=522 
[ 1108.672172] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45506 DPT=36396 LEN=522 
[ 1109.692930] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50747 DPT=36396 LEN=522 
[ 1146.089010] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=46456 DPT=51727 LEN=522 
[ 1147.116242] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54568 DPT=51727 LEN=522 
[ 1167.458325] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1193.637376] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56384 DPT=52632 LEN=522 
[ 1206.007013] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=47100 DPT=48718 LEN=522 
[ 1265.048259] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=192.168.1.103 LEN=290 TOS=0x00 PREC=0x00 TTL=64 ID=94 DF PROTO=UDP SPT=1900 DPT=49816 LEN=270 
[ 1265.052387] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=192.168.1.103 LEN=300 TOS=0x00 PREC=0x00 TTL=64 ID=2696 DF PROTO=UDP SPT=2048 DPT=49816 LEN=280 
[ 1265.053368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=192.168.1.103 LEN=300 TOS=0x00 PREC=0x00 TTL=64 ID=2697 DF PROTO=UDP SPT=2048 DPT=49816 LEN=280 
[ 1282.806959] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=38851 DPT=35460 LEN=522 
[ 1313.726281] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60582 DPT=59439 LEN=522 
[ 1342.946767] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=39180 DPT=54130 LEN=522 
[ 1343.916447] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=44763 DPT=54130 LEN=522 
[ 1377.296940] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=45050 DPT=44736 LEN=522 
[ 1402.749918] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33698 DPT=53752 LEN=522 
[ 1404.087720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35481 DPT=53752 LEN=522 
[ 1433.317486] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33943 DPT=48103 LEN=522 
[ 1462.573815] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59951 DPT=59743 LEN=522 
[ 1463.703025] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=35935 DPT=59743 LEN=522 
[ 1522.588998] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=55265 DPT=44155 LEN=522 
[ 1523.650192] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58756 DPT=44155 LEN=522 
[ 1524.845299] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57877 DPT=44155 LEN=522 
[ 1553.258339] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33064 DPT=49284 LEN=522 
[ 1582.612501] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=34548 DPT=56023 LEN=522 
[ 1583.445707] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=54671 DPT=56023 LEN=522 
[ 1642.352980] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=41254 DPT=40656 LEN=522 
[ 1643.568747] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=58024 DPT=40656 LEN=522 
[ 1644.272315] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=50304 DPT=40656 LEN=522 
[ 1665.124566] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:18:f4:6a:51:6d:de:08:00 SRC=192.168.1.101 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1682.432757] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56230 DPT=57652 LEN=522 
[ 1718.215661] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43082 DPT=53716 LEN=522 
[ 1762.503408] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=60981 DPT=57379 LEN=522 
[ 1763.196898] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59718 DPT=57379 LEN=522 
[ 1764.117476] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=33963 DPT=57379 LEN=522 
[ 1784.558037] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1822.096119] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43575 DPT=58476 LEN=522 
[ 1823.341229] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=43890 DPT=58476 LEN=522 
[ 1882.086776] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57750 DPT=60078 LEN=522 
[ 1883.451578] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=56912 DPT=60078 LEN=522 
[ 1883.948799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=42553 DPT=60078 LEN=522 
[ 1909.383327] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1942.151854] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57564 DPT=50126 LEN=522 
[ 1942.966340] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=49599 DPT=50126 LEN=522 
[ 2001.859538] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=57334 DPT=43839 LEN=522 
[ 2002.873998] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=37119 DPT=43839 LEN=522 
[ 2003.897833] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=192.168.1.103 LEN=542 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=51109 DPT=43839 LEN=522 
[ 2034.260049] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:<MAC 'TP-LINK_9D8426' [AC1]>:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2042.135986] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:7f:ff:fa:6c:ad:f8:bf:d9:eb:08:00 SRC=192.168.1.201 DST=239.255.255.250 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 


########## wireless info END ############



```


Thanks!

---

### Post by wildmanne39 on 2015-03-14
It looks like your firewall is blocking your connection, temporarly disable the firewall and see if that fixes the issue.
Thanks

---

### Post by daniel-gr-23 on 2015-03-15
Hi,

I don't think that's it, I just recently activated it with sudo ufw enable, but for testing purposes I deactivated it again with ufw disable (status inactive now) and tested the connection, however no change :( Is there another firewall I might be missing? I ran your script again with disabled firewall: 

```



########## wireless info START ##########


Report from: 15 Mar 2015 20:44 CET +0100


Booted last: 15 Mar 2015 19:58 CET +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Cinnamon


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7599]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 003: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:074b Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              484040  0 
wmi                    19177  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac6:8eff:fe86:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2366676 (2.3 MB)  TX bytes:293844 (293.8 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"UPC0049402"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'UPC0049402' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:37576   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [UPC0049402] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK_9D8426:  Infra, <MAC 'TP-LINK_9D8426' [AC3]>, Freq 2442 MHz, Rate 11 Mb/s, Strength 95 WPA WPA2
    UPC1381976:      Infra, <MAC 'UPC1381976' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    UPC1071460:      Infra, <MAC 'UPC1071460' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    WLAN.Tele2.net:  Infra, <MAC 'WLAN.Tele2.net' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    TMOBILE-84808:   Infra, <MAC 'TMOBILE-84808' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    UPC2114016:      Infra, <MAC 'UPC2114016' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    defekt:          Infra, <MAC 'defekt' [AN7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 24 WPA2
    UPC0046384:      Infra, <MAC 'UPC0046384' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    UPC1383734:      Infra, <MAC 'UPC1383734' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    TMOBILE-30052:   Infra, <MAC 'TMOBILE-30052' [AN10]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    UPC7467167:      Infra, <MAC 'UPC7467167' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    *UPC0049402:     Infra, <MAC 'UPC0049402' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             195.34.133.21
    DNS:             212.186.211.21


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/UPC0049402]] (600 root)
[connection] id=UPC0049402 | type=802-11-wireless
[802-11-wireless] ssid=UPC0049402 | bssid=<MAC 'UPC0049402' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Automatisch TP-LINK_9D8426]] (600 root)
[connection] id=Automatisch TP-LINK_9D8426 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_9D8426 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC1071460]] (600 root)
[connection] id=UPC1071460 | type=802-11-wireless
[802-11-wireless] ssid=UPC1071460 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC0049402' [AC1]>
                    ESSID:"UPC0049402"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WLAN.Tele2.net' [AC2]>
                    ESSID:"WLAN.Tele2.net"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_9D8426' [AC3]>
                    ESSID:"TP-LINK_9D8426"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: <MAC 'UPC1381976' [AC5]>
                    ESSID:"UPC1381976"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC7467167' [AC6]>
                    ESSID:"UPC7467167"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC1071460' [AC7]>
                    ESSID:"UPC1071460"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29/100  Signal level:-77 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TMOBILE-84808' [AC8]>
                    ESSID:"TMOBILE-84808"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/bcmwlhigh5.conf]
options bcmwlhigh5 pio=1 qos=0


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  595.442472] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26491 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  595.449450] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8101 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  595.995480] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26492 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  596.023933] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8102 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  597.098317] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26493 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  597.188280] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8103 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  599.310768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26494 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  599.496199] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8104 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  601.829638] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.138.143 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=42 ID=64181 DF PROTO=TCP SPT=443 DPT=49792 WINDOW=57 RES=0x00 ACK FIN URGP=0 
[  603.306024] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=89 TOS=0x00 PREC=0x00 TTL=39 ID=48651 DF PROTO=TCP SPT=443 DPT=59681 WINDOW=149 RES=0x00 ACK PSH FIN URGP=0 
[  632.000959] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  632.001910] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  691.257862] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[  726.702832] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=24445 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  728.129531] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=25366 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  729.944892] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=27063 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  739.805588] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=192.168.0.10 DST=239.192.0.0 LEN=120 TOS=0x00 PREC=0x00 TTL=3 ID=4415 DF PROTO=UDP SPT=3838 DPT=3838 LEN=100 
[  758.035015] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2  (repeated 2 times)
[  884.008025] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  887.074436] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1009.984950] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1009.985945] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1014.995445] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1135.860558] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1135.861685] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1142.916396] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1261.841182] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1261.842255] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1270.837453] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1387.920718] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1387.921673] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1396.407979] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1513.898116] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1513.899153] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1516.866388] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1639.671313] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1639.672157] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1643.761419] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1731.190959] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1765.751599] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1765.752573] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1771.581487] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1771.584952] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1891.423497] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1891.424463] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1898.479308] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1898.482667] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2017.299012] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2017.299822] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2026.297275] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2026.300856] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2143.379173] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2143.380339] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2143.381522] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2143.384887] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2144.412140] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2144.415628] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2269.255221] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2269.256189] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2277.334381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2277.337665] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 


########## wireless info END ############

```

Thank you! Also, I'm ready to accept that there might be no viable solution for my case (maybe it's a more complex hardware issue - I don't know). If you think so too, do you know of any comparable wireless adapter (doesn't have to be USB though) that is supported by ubuntu? I found some lists, they are from ~2012 though...

---

### Post by wildmanne39 on 2015-03-15
This is from the new file you posted and the firewall is still blocking the connection, it might not be your only issue but it is most of it I believe. 
```
##### dmesg #############################


[  595.442472] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26491 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  595.449450] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8101 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  595.995480] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26492 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  596.023933] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8102 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  597.098317] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26493 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  597.188280] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8103 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  599.310768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=26494 DF PROTO=TCP SPT=80 DPT=57326 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  599.496199] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=39 ID=8104 DF PROTO=TCP SPT=80 DPT=57327 WINDOW=140 RES=0x00 ACK FIN URGP=0 
[  601.829638] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.138.143 DST=192.168.0.10 LEN=52 TOS=0x00 PREC=0x00 TTL=42 ID=64181 DF PROTO=TCP SPT=443 DPT=49792 WINDOW=57 RES=0x00 ACK FIN URGP=0 
[  603.306024] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=54.225.227.202 DST=192.168.0.10 LEN=89 TOS=0x00 PREC=0x00 TTL=39 ID=48651 DF PROTO=TCP SPT=443 DPT=59681 WINDOW=149 RES=0x00 ACK PSH FIN URGP=0 
[  632.000959] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  632.001910] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  691.257862] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  (repeated 2 times)
[  726.702832] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=24445 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  728.129531] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=25366 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  729.944892] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:fc:94:e3:a5:45:ca:08:00 SRC=64.15.113.89 DST=192.168.0.10 LEN=115 TOS=0x00 PREC=0x00 TTL=58 ID=27063 PROTO=TCP SPT=443 DPT=39387 WINDOW=252 RES=0x00 ACK PSH URGP=0 
[  739.805588] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=192.168.0.10 DST=239.192.0.0 LEN=120 TOS=0x00 PREC=0x00 TTL=3 ID=4415 DF PROTO=UDP SPT=3838 DPT=3838 LEN=100 
[  758.035015] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2  (repeated 2 times)
[  884.008025] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  887.074436] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1009.984950] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1009.985945] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1014.995445] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1135.860558] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1135.861685] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1142.916396] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1261.841182] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1261.842255] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1270.837453] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1387.920718] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1387.921673] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1396.407979] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1513.898116] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1513.899153] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1516.866388] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1639.671313] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1639.672157] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1643.761419] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1731.190959] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1765.751599] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1765.752573] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1771.581487] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1771.584952] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1891.423497] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1891.424463] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1898.479308] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1898.482667] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2017.299012] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2017.299822] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2026.297275] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2026.300856] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2143.379173] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2143.380339] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2143.381522] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2143.384887] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2144.412140] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2144.415628] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2269.255221] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2269.256189] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:fc:94:e3:a5:45:ca:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2277.334381] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2277.337665] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:40:00:00:f4:ec:38:9d:84:27:08:00 SRC=192.168.0.51 DST=239.192.0.0 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 


########## wireless info END ############
```
If you install GUFW then you will have a graqphical enterphace, if I rememer correctly UFW reactivates itself with every reboot.
I am not sure that this module will cause issues but it does not need to be loaded so we will blacklist it.
```
echo "blacklist cfg80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

### Post by daniel-gr-23 on 2015-03-16
Hi, 

I'm afraid it's still not working :( thanks for the advice though, it's weird that the firewall would block something because I checked with ufw status, but now I disabled again in the GUI and there doesn't seem to be any UFW log entries anymore. After a fresh reboot I tried again for about half an hour, then the connection was gone again and I am now back to usb tethering via android tablet.

I also added the entry to the blacklist of course, but I'm afraid it didn't change a thing.

I'd also like to notice that the connection drop occured while uploading a big email (~15MB), however I don't think the capacity of the connection is a real issue, as I'm also using btsync for extended periods of time, and the connection drop always occured after 20-30 min regardless of btsync activity.

 Thanks so much again for sticking with me so far, I know troubleshooting from the distance like this can be really annoying :)

Greetings

```



########## wireless info START ##########


Report from: 16 Mar 2015 15:21 CET +0100


Booted last: 16 Mar 2015 14:56 CET +0100


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


Cinnamon


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7599]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 003: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 008: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:074b Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


wmi                    19177  0 
ndiswrapper           283985  0 


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


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.70  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::4013:46ff:fe87:c58d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:760 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:242036 (242.0 KB)  TX bytes:162478 (162.4 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac6:8eff:fe86:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7132886 (7.1 MB)  TX bytes:4597605 (4.5 MB)


##### iwconfig ##########################


usb0      no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"UPC0049402"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'UPC0049402' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:45195   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: usb0  [Kabelnetzwerkverbindung 2] ------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC 'usb0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.42.70
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129


    DNS:             192.168.42.129


- Device: wlan0  [UPC0049402] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    TP-LINK_9D8426:  Infra, <MAC 'TP-LINK_9D8426' [AC3]>, Freq 2442 MHz, Rate 11 Mb/s, Strength 94 WPA WPA2
    UPC1381976:      Infra, <MAC 'UPC1381976' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    UPC1071460:      Infra, <MAC 'UPC1071460' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    WLAN.Tele2.net:  Infra, <MAC 'WLAN.Tele2.net' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    TMOBILE-84808:   Infra, <MAC 'TMOBILE-84808' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    UPC013280:       Infra, <MAC 'UPC013280' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    UPC2114016:      Infra, <MAC 'UPC2114016' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    TMOBILE-30052:   Infra, <MAC 'TMOBILE-30052' [AN8]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    UPC7467167:      Infra, <MAC 'UPC7467167' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    GAST:            Infra, <MAC 'GAST' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    defekt:          Infra, <MAC 'defekt' [AN11]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 19 WPA2
    GAST:            Infra, <MAC 'GAST' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    UPC1383734:      Infra, <MAC 'UPC1383734' [AN13]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    *UPC0049402:     Infra, <MAC 'UPC0049402' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    Address:         192.168.0.52
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0


    DNS:             195.34.133.21
    DNS:             212.186.211.21


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/UPC0049402]] (600 root)
[connection] id=UPC0049402 | type=802-11-wireless
[802-11-wireless] ssid=UPC0049402 | bssid=<MAC 'UPC0049402' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Automatisch TP-LINK_9D8426]] (600 root)
[connection] id=Automatisch TP-LINK_9D8426 | type=802-11-wireless
[802-11-wireless] ssid=TP-LINK_9D8426 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC1071460]] (600 root)
[connection] id=UPC1071460 | type=802-11-wireless
[802-11-wireless] ssid=UPC1071460 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


usb0      no frequency information.


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)


usb0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC0049402' [AC1]>
                    ESSID:"UPC0049402"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:82/100  Signal level:-43 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC013280' [AC2]>
                    ESSID:"UPC013280"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_9D8426' [AC3]>
                    ESSID:"TP-LINK_9D8426"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:76/100  Signal level:-47 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: <MAC 'WLAN.Tele2.net' [AC5]>
                    ESSID:"WLAN.Tele2.net"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC1381976' [AC6]>
                    ESSID:"UPC1381976"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:37/100  Signal level:-72 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC1071460' [AC7]>
                    ESSID:"UPC1071460"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TMOBILE-84808' [AC8]>
                    ESSID:"TMOBILE-84808"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/bcmwlhigh5.conf]
options bcmwlhigh5 pio=1 qos=0


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
blacklist cfg80211


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   28.262802] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   39.381070] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-03-17
Go into your router and change the encryption to just wpa2 AES CCMP only not mixed mode and not TKIP. 
Change the channel to 1 or 11.
Go into network manager top right corner of the screen and set your settings to match the screenshots.
Thanks

---

### Post by daniel-gr-23 on 2015-03-17
Hi, I changed the settings according to your instructions, with no luck I'm afraid. However I am not entirely confident in the router settings, so I attached them in screenshots, along with another fresh wireless log. (e.g. I don't know about CCMP)

Also I think it's odd that there is still a IPv6 entry in the log when I have it disabled.

Thank you for your continued support!

```


########## wireless info START ##########


Report from: 17 Mar 2015 20:02 CET +0100


Booted last: 17 Mar 2015 19:53 CET +0100


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


Cinnamon


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7599]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0846:9050 NetGear, Inc. 
Bus 001 Device 003: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:074b Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


wmi                    19177  0 
ndiswrapper           283985  0 


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
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2ac6:8eff:fe86:3590/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14209548 (14.2 MB)  TX bytes:1465482 (1.4 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"UPC0049402"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'UPC0049402' [AC1]>   
          Bit Rate=144 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:70/100  Signal level:-51 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:112797   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [UPC0049402] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    UPC1381976:      Infra, <MAC 'UPC1381976' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    WLAN.Tele2.net:  Infra, <MAC 'WLAN.Tele2.net' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    UPC1071460:      Infra, <MAC 'UPC1071460' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    TMOBILE-84808:   Infra, <MAC 'TMOBILE-84808' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    UPC7467167:      Infra, <MAC 'UPC7467167' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    defekt:          Infra, <MAC 'defekt' [AN6]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 17 WPA2
    GAST:            Infra, <MAC 'GAST' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    TMOBILE-30052:   Infra, <MAC 'TMOBILE-30052' [AC5]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    *UPC0049402:     Infra, <MAC 'UPC0049402' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 79 WPA2


  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    Address:         192.168.0.52
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/UPC0049402]] (600 root)
[connection] id=UPC0049402 | type=802-11-wireless
[802-11-wireless] ssid=UPC0049402 | bssid=<MAC 'UPC0049402' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'UPC0049402' [AC1]>
                    ESSID:"UPC0049402"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC1071460' [AC2]>
                    ESSID:"UPC1071460"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'UPC013280' [AC3]>
                    ESSID:"UPC013280"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'GAST' [AC4]>
                    ESSID:"GAST"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:7/100  Signal level:-91 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'TMOBILE-30052' [AC5]>
                    ESSID:"TMOBILE-30052"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:9/100  Signal level:-90 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'WLAN.Tele2.net' [AC6]>
                    ESSID:"WLAN.Tele2.net"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC1381976' [AC7]>
                    ESSID:"UPC1381976"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ndiswrapper]
filename:       /lib/modules/3.13.0-46-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


lp
rtc
ndiswrapper
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/bcmwlhigh5.conf]
options bcmwlhigh5 pio=1 qos=0


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
blacklist cfg80211


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v0846p9050d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   21.830819] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e42e00, 32000, 9
[   21.830820] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e4ab00, 32000, 9
[   21.830821] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e52800, 32000, 9
[   21.830822] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e5a500, 32000, 9
[   21.830823] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e62200, 32000, 8
[   21.830824] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e69f00, 32000, 9
[   21.830825] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e71c00, 32000, 9
[   21.830827] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e79900, 32000, 9
[   21.830828] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e81600, 32000, 9
[   21.830829] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e89300, 32000, 8
[   21.830830] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e91000, 32000, 8
[   21.830831] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90012e98d00, 32000, 9
[   21.864005] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   22.120228] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x61e3d15, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9050.F.conf
[   22.121399] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   28.303979] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   39.389437] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

---

### Post by sanapalask on 2015-04-01
Even I am having the same issue with Ubuntu 14.04 with Netgear A6200 wireless Usb adapter.  I set up my A6200 Wireless Adapter as described in another thread ([http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04](http://askubuntu.com/questions/460277/how-to-get-netgear-a6200-to-work-on-14-04)) and it works fine for less than a minute. In less than a minute I cant connect to internet anymore. It is still listed as active and connected though. I would really appreciate your help here. If you issue is resolved can you please share your resolution steps.

---

