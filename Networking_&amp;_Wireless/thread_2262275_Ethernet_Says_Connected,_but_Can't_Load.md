---
title: "Ethernet Says Connected, but Can't Load"
date: 2015-01-24
forum: Networking &amp; Wireless
---

### Post by Tyler_Petresky on 2015-01-24
Hey everyone,

I recently decided to load up Ubuntu again and am having quite a few issues in regards to networking. Wifi works fine (albeit extremely slow), but I want to use ethernet for the added speed and stability. Whenever I try to use ethernet it says it is connected in the top right, but it won't connect to any web pages and whenever I try to ping [www.google.com]("http://www.google.com") it says that no host could be determined. However, I already tried going to the connection information and adding 8.8.8.8 and 8.8.4.4, so that wasn't the issue.

Here is my output to all of the usually requested commands that everyone asks for to hopefully help you guys help me. I realize it is a long file, so I attached the tar as well. This is per the forum instructions, btw. :)

I have searched all over the internet trying to solve the problem and have tried loads of different commands, but to no avail. Hopefully you all can help me a little.

Thanks,
Tyler

[ATTACH]259448[/ATTACH]

```

########## wireless info START ##########

Report from: 23 Jan 2015 23:51 EST -0500

Booted last: 23 Jan 2015 23:36 EST -0500

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
    Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:0768 Microsoft Corp. Sidewinder X4
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback
##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.25  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::be5f:f4ff:fe66:783b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:631 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:279902 (279.9 KB)  TX bytes:69833 (69.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.53  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76d0:2bff:fe3c:f2c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29154414 (29.1 MB)  TX bytes:1441007 (1.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"The Asus of Spades"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'The Asus of Spades' [AC1]>   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:50   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search Belkin
nameserver 192.168.2.1
nameserver 127.0.1.1
search Belkin

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [The Asus of Spades] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
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
    Frank the Flamingo: Infra, <MAC 'Frank the Flamingo' [AC6]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 26 WPA2
    50 Shades of Wifi: Infra, <MAC '50 Shades of Wifi' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2
    No Internet Access: Infra, <MAC 'No Internet Access' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    AMG:             Infra, <MAC 'AMG' [AC5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 74 WPA2
    hose 4 bros:     Infra, <MAC 'hose 4 bros' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    JAG:             Infra, <MAC 'JAG' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Abraham Linksys: Infra, <MAC 'Abraham Linksys' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Chromecast9832:  Infra, <MAC 'Chromecast9832' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74
    belkin.7be.guests: Infra, <MAC 'belkin.7be.guests' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    *The Asus of Spades: Infra, <MAC 'The Asus of Spades' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA2
    MMHC:            Infra, <MAC 'MMHC' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    belkin.7be:      Infra, <MAC 'belkin.7be' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    Absinthe Party:  Infra, <MAC 'Absinthe Party' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    NSA:             Infra, <MAC 'NSA' [AN14]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    HULK:            Infra, <MAC 'HULK' [AN15]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    J5NET:           Infra, <MAC 'J5NET' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA
    FBI Surveillance:Infra, <MAC 'FBI Surveillance' [AN17]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    MMHC-guest:      Infra, <MAC 'MMHC-guest' [AN18]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54

  IPv4 Settings:
    Address:         192.168.1.53
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Ethernet connection 1] ----------------------------------------
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
    Address:         192.168.2.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4

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

[[/etc/NetworkManager/system-connections/The Asus of Spades]] (600 root)
[connection] id=The Asus of Spades | type=802-11-wireless
[802-11-wireless] ssid=The Asus of Spades | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'The Asus of Spades' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"The Asus of Spades"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a596718ed
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '50 Shades of Wifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"50 Shades of Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000066014f18484
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Chromecast9832' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Chromecast9832"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013d1960cb
                    Extra: Last beacon: 4ms ago
          Cell 04 - Address: <MAC 'Absinthe Party' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Absinthe Party"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000682955181
                    Extra: Last beacon: 1120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'AMG' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"AMG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000016bd2906
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Frank the Flamingo' [AC6]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Frank the Flamingo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000196c6cc2b81
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Abraham Linksys' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"Abraham Linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007ac771211
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'belkin.7be' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"belkin.7be"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ba68c4f14
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'belkin.7be.guests' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"belkin.7be.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ba68c67c9
                    Extra: Last beacon: 4ms ago
          Cell 10 - Address: <MAC 'JAG' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"JAG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006f2dcedaa0e
                    Extra: Last beacon: 368ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: Y
ips: Y
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.610758] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  176.033895] wlan0: authenticate with <MAC 'The Asus of Spades' [AC1]>
[  176.053471] wlan0: send auth to <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  176.057411] wlan0: authenticated
[  176.061129] wlan0: associate with <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  176.078555] wlan0: RX AssocResp from <MAC 'The Asus of Spades' [AC1]> (capab=0x411 status=0 aid=5)
[  176.078712] wlan0: associated
[  176.078723] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  176.138146] wlan0: deauthenticating from <MAC 'The Asus of Spades' [AC1]> by local choice (reason=2)
[  176.171436] wlan0: authenticate with <MAC 'The Asus of Spades' [AC1]>
[  176.181630] wlan0: send auth to <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  176.191027] wlan0: authenticated
[  176.192975] wlan0: associate with <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  176.198535] wlan0: RX AssocResp from <MAC 'The Asus of Spades' [AC1]> (capab=0x411 status=0 aid=5)
[  176.198691] wlan0: associated
[  610.575444] wlan0: deauthenticating from <MAC 'The Asus of Spades' [AC1]> by local choice (reason=3)
[  663.351257] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  665.054956] wlan0: authenticate with <MAC 'The Asus of Spades' [AC1]>
[  665.074660] wlan0: send auth to <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  665.081169] wlan0: authenticated
[  665.082256] wlan0: associate with <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  665.085802] wlan0: RX AssocResp from <MAC 'The Asus of Spades' [AC1]> (capab=0x411 status=0 aid=2)
[  665.085956] wlan0: associated
[  665.085965] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  666.112671] wlan0: deauthenticating from <MAC 'The Asus of Spades' [AC1]> by local choice (reason=2)
[  666.144891] wlan0: authenticate with <MAC 'The Asus of Spades' [AC1]>
[  666.155076] wlan0: send auth to <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  666.156619] wlan0: authenticated
[  666.158152] wlan0: associate with <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  666.165885] wlan0: RX AssocResp from <MAC 'The Asus of Spades' [AC1]> (capab=0x411 status=0 aid=2)
[  666.166048] wlan0: associated
[  674.241945] wlan0: deauthenticated from <MAC 'The Asus of Spades' [AC1]> (Reason: 15)
[  675.526193] wlan0: authenticate with <MAC 'The Asus of Spades' [AC1]>
[  675.545829] wlan0: send auth to <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  675.547405] wlan0: authenticated
[  675.549471] wlan0: associate with <MAC 'The Asus of Spades' [AC1]> (try 1/3)
[  675.556155] wlan0: RX AssocResp from <MAC 'The Asus of Spades' [AC1]> (capab=0x411 status=0 aid=2)
[  675.556316] wlan0: associated

########## wireless info END ############


```

---

### Post by mooreted on 2015-01-24
I think you need to look at your router and Network Manager settings. You have the Ethernet gateway set to 192.168.2.1 however, your DNS is set to 192.168.1.1.

The easiest way is to set up your router then set Network Manager to get IP addresses automatically through DHCP. I think you have conflicting IP and DNS settings.

Disclaimer: I am not a network expert.

---

### Post by Tyler_Petresky on 2015-01-24
Thanks for the reply!

I just checked the network settings and it is already set to use DHCP in order to set the information automatically.

---

### Post by mooreted on 2015-01-24
Well, the two network segments .1 and .2 are confusing to me. My router's IP address is 192.168.1.1. There is no other IP address. So look around and see why you have 192.168.2.1, what is it for? 192.168.1 is a whole different network than 192.168.2.

Like I said, I'm not a network guy so I'm just guessing.

---

