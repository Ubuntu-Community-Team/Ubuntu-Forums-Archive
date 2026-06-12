---
title: "Ubuntu 14.04 detecting wifi, but not connecting"
date: 2014-09-20
forum: Networking &amp; Wireless
---

### Post by claudia3 on 2014-09-20
Hi,

I am experiencing a problem with internet connection via wifi. The network manager is recognizing the available networks, and also is accepting the password, which is correct, but keeps in a state of connecting without finally connecting at all. I've checked that there is not any soft or hardblock. I also checked that the propietary drivers are installed. And I do not have this problem with another wifi which is from a different provider, so I thought that maybe it has something to do with the router. But connecting with ethernet cable to the router in which I have the problems is working fine. I am not sure of how to proceed.h

Edited:
I've just read the post "Before posting in Networking and Wireless" and therefore I've run the script wireless, and I attach the result. I saw the name Broadcom near [0280] and went to the Broadcom Guide but after doing the suggested fix it is still not connecting.

```



########## wireless info START ##########

Report from: 21 Sep 2014 00:37 CEST +0200

Booted last: 21 Sep 2014 00:31 CEST +0200

Script from: 17 Sep 2014 18:40 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Hewlett-Packard Company Device [103c:162d]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: wl

##### lsusb #####

Bus 002 Device 004: ID 174f:1118 Syntek 
Bus 002 Device 003: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:0005 Validity Sensors, Inc. VFS301 Fingerprint Reader
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 hp_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6631:50ff:fe92:33f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5196 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:939642 (939.6 KB)  TX bytes:5627173 (5.6 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::ce52:afff:fe8e:2e80/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:2863
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2225 (2.2 KB)  TX bytes:7173 (7.1 KB)
          Interrupt:17 

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search homestation

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Orange-14B1:     Infra, <MAC 'Orange-14B1' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    VodafoneGAB8:    Infra, <MAC 'VodafoneGAB8' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA
    BAU_KSAR:        Infra, <MAC 'BAU_KSAR' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA
    VodafoneA7CB:    Infra, <MAC 'VodafoneA7CB' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WPA
    Orange-454C:     Infra, <MAC 'Orange-454C' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    vodafone6F62:    Infra, <MAC 'vodafone6F62' [AN6]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 19 WPA
    JAZZTEL_AWifi:   Infra, <MAC 'JAZZTEL_AWifi' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 64 WEP
    WLAN_6F:         Infra, <MAC 'WLAN_6F' [AC7]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WEP
    MOVISTAR_DEF2:   Infra, <MAC 'MOVISTAR_DEF2' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    Orange-704a:     Infra, <MAC 'Orange-704a' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    WLAN_1B89:       Infra, <MAC 'WLAN_1B89' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    VF-Recaredo:     Infra, <MAC 'VF-Recaredo' [AN12]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 7 WPA

- Device: eth0  [Auto Ethernet] ------------------------------------------------
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
    Address:         192.168.1.36
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             80.58.61.250
    DNS:             80.58.61.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles #####

==[/etc/NetworkManager/system-connections/MOVISTAR_DEF2]==
[connection] id=MOVISTAR_DEF2 | type=802-11-wireless
[802-11-wireless] ssid=MOVISTAR_DEF2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/vodafone5DB6]==
[connection] id=vodafone5DB6 | type=802-11-wireless
[802-11-wireless] ssid=vodafone5DB6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/eduroam]==
[connection] id=eduroam | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/WLAN_2E08]==
[connection] id=WLAN_2E08 | type=802-11-wireless
[802-11-wireless] ssid=WLAN_2E08 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/LASERSCAN]==
[connection] id=LASERSCAN | type=802-11-wireless
[802-11-wireless] ssid=LASERSCAN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/Casa]==
[connection] id=Casa | type=802-11-wireless
[802-11-wireless] ssid=Casa | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/pepephone_ADSLNP25]==
[connection] id=pepephone_ADSLNP25 | type=802-11-wireless
[802-11-wireless] ssid=pepephone_ADSLNP25 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/Orange-33b0]==
[connection] id=Orange-33b0 | type=802-11-wireless
[802-11-wireless] ssid=Orange-33b0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/EasyBox-FD2407]==
[connection] id=EasyBox-FD2407 | type=802-11-wireless
[802-11-wireless] ssid=EasyBox-FD2407 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/RBWbgn]==
[connection] id=RBWbgn | type=802-11-wireless
[802-11-wireless] ssid=RBWbgn | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/conferences]==
[connection] id=conferences | type=802-11-wireless
[802-11-wireless] ssid=conferences | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

==[/etc/NetworkManager/system-connections/pepephone_ADSLXRQ3]==
[connection] id=pepephone_ADSLXRQ3 | type=802-11-wireless
[802-11-wireless] ssid=pepephone_ADSLXRQ3 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/WLAN_F7DD]==
[connection] id=WLAN_F7DD | type=802-11-wireless
[802-11-wireless] ssid=WLAN_F7DD | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/WLAN_80]==
[connection] id=WLAN_80 | type=802-11-wireless
[802-11-wireless] ssid=WLAN_80 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/wifi_cosmocaixa_bcn]==
[connection] id=wifi_cosmocaixa_bcn | type=802-11-wireless
[802-11-wireless] ssid=wifi_cosmocaixa_bcn | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

==[/etc/NetworkManager/system-connections/AP-CID-INF2]==
[connection] id=AP-CID-INF2 | type=802-11-wireless
[802-11-wireless] ssid=AP-CID-INF2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

==[/etc/NetworkManager/system-connections/Gaestehaus]==
[connection] id=Gaestehaus | type=802-11-wireless
[802-11-wireless] ssid=Gaestehaus | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get #####

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #####

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Orange-14B1' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Orange-14B1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'JAZZTEL_AWifi' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"JAZZTEL_AWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
          Cell 03 - Address: <MAC 'MOVISTAR_DEF2' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:on
                    ESSID:"MOVISTAR_DEF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'VodafoneA7CB' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"VodafoneA7CB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BAU_KSAR' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"BAU_KSAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VodafoneGAB8' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"VodafoneGAB8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'WLAN_6F' [AC7]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"WLAN_6F"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 100ms ago
          Cell 08 - Address: <MAC 'WLAN_1B89' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"WLAN_1B89"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 22764ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos #####

[wl]
filename:       /lib/modules/3.13.0-35-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #####

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules #####

lp
rtc

##### modprobe options #####

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
blacklist b43
blacklist ssb

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

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local #####

exit 0

##### pm-utils #####

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[  424.245653] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

### Post by varunendra on 2014-09-23
Hi claudia3!

Please try this in a terminal -
```
sudo apt-get purge bcmwl-kernel-source
```
..followed by a reboot. Does the wifi work now? If not, please post a fresh report of the wireless_script.

---

### Post by claudia3 on 2014-09-26
That solved it!!!! Thanks so much!!!!

---

### Post by varunendra on 2014-09-26
Pleased to hear that!

Just remember NOT to install the proprietary STA driver again that the "Additional Drivers" program may propose, the native one you are using now is better for your card. What we did with the above command was just removing the proprietary driver along with its settings, as it blocks the native one from loading, and sometimes doesn't work well itself as in your case.

Enjoy!

---

