---
title: "Ubuntu 14.04, wireless visible, constantly asked password"
date: 2014-11-21
forum: Networking &amp; Wireless
---

### Post by sergio35 on 2014-11-21
Hi there everybody,

I just bought a new computer with windows 8 pre-installed. The computer is a packard bell iMedia s j14g1tu02, no wi-fi card. The wi-fi connection is performed thaks to a usb/wi-fi key that works fine on windows. I just installed Ubuntu 14.04. The usb key seems to work fine since the wirless networks are visible on ubuntu. When I try to connect to my network (freebox_SERANN) I am asked for the password. After 2 minutes waiting for a feedback I am asked once more for the password and so on. The connection is never achieved.

I tried to reboot the wi-fi box and the computer many times.
I tried to change the firmware, first the old linux-firmware_1.34.14_all, than the newer linux-firmware_1.127.8_all. Not solved.
Just before posting I tried to update (sudo apt-get update, sudo apt-get dist-upgrade) and reboot. Not solved.

Anybody has an idea of what my problem could be?
Thanks in advance for any suggestion/help :)

the output of the file wireless-info.txt
```

[COLOR=#000080]
########## wireless info START ##########

Report from: 21 Nov 2014 15:28 CET +0100

Booted last: 21 Nov 2014 15:25 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              630653  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:558c:cce3:89f6:e2be/64 Scope:Global
          inet6 addr: 2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fec8:97da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4890 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5648212 (5.6 MB)  TX bytes:371983 (371.9 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:558c:cce3:89f6:e2be
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         fe80::fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

- Device: wlan0  [freebox_SERANN] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JulienWIFI:      Infra, <MAC 'JulienWIFI' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA Enterprise
    NEUF_8348:       Infra, <MAC 'NEUF_8348' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 4 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WPA2 Enterprise
    NUMERICABLE-ED12:Infra, <MAC 'NUMERICABLE-ED12' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WEP
    NEUF_2A1C:       Infra, <MAC 'NEUF_2A1C' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WEP
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4
    freebox_SERANN:  Infra, <MAC 'freebox_SERANN' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA

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

[[/etc/NetworkManager/system-connections/freebox_SERANN]] (600 root)
[connection] id=freebox_SERANN | type=802-11-wireless
[802-11-wireless] ssid=freebox_SERANN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      8   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freebox_SERANN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"freebox_SERANN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006ff8fff6
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FreeWifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006ff90abd
                    Extra: Last beacon: 36ms ago
          Cell 03 - Address: <MAC 'FreeWifi_secure' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006ff9142c
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'NEUF_8348' [AC4]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"NEUF_8348"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000bfcc1bfe46
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NUMERICABLE-ED12' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"NUMERICABLE-ED12"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000240bfec615
                    Extra: Last beacon: 36ms ago
          Cell 06 - Address: <MAC 'JulienWIFI' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"JulienWIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026d97469c1d
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FreeWifi' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026d9746ae47
                    Extra: Last beacon: 36ms ago
          Cell 08 - Address: <MAC '' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026d9746db07
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'FreeWifi_secure' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026d9746c1d0
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC 'NEUF_2A1C' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"NEUF_2A1C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0dc5df5e3
                    Extra: Last beacon: 36ms ago
          Cell 11 - Address: <MAC 'SFR WiFi FON' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0dc5e0cdc
                    Extra: Last beacon: 36ms ago
          Cell 12 - Address: <MAC 'SFR WiFi Mobile' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c0dc5e1fbf
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     7B1675B5BB89B5DD8E7EBAC
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

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
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  104.040062] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  104.061223] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  104.063795] wlan0: authenticated
[  104.067026] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  104.091103] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  104.091168] wlan0: associated
[  104.091254] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  110.364742] wlan0: deauthenticated from <MAC 'freebox_SERANN' [AC1]> (Reason: 15)
[  111.207764] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  111.228761] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  111.231372] wlan0: authenticated
[  111.234645] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  111.259071] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  111.259142] wlan0: associated
[  118.371589] wlan0: deauthenticated from <MAC 'freebox_SERANN' [AC1]> (Reason: 15)
[  119.199684] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  119.223643] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  119.225580] wlan0: authenticated
[  119.226404] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  119.261276] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  119.261356] wlan0: associated
[  126.378427] wlan0: deauthenticated from <MAC 'freebox_SERANN' [AC1]> (Reason: 15)
[  127.204134] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  127.229462] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  127.233267] wlan0: authenticated
[  127.234395] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  127.259992] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  127.260094] wlan0: associated
[  129.063056] wlan0: deauthenticating from <MAC 'freebox_SERANN' [AC1]> by local choice (reason=3)
[  133.838762] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  133.861696] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  133.876947] wlan0: authenticated
[  133.877718] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  133.900517] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  133.901066] wlan0: associated
[  140.390375] wlan0: deauthenticated from <MAC 'freebox_SERANN' [AC1]> (Reason: 15)
[  152.639890] wlan0: authenticate with <MAC 'freebox_SERANN' [AC1]>
[  152.662022] wlan0: send auth to <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  152.695722] wlan0: authenticated
[  152.699404] wlan0: associate with <MAC 'freebox_SERANN' [AC1]> (try 1/3)
[  152.739365] wlan0: RX AssocResp from <MAC 'freebox_SERANN' [AC1]> (capab=0x411 status=0 aid=2)
[  152.739451] wlan0: associated
[  158.076918] wlan0: deauthenticating from <MAC 'freebox_SERANN' [AC1]> by local choice (reason=3)

########## wireless info END ############
[/COLOR]

```

---

### Post by sergio35 on 2014-11-23
Some more info:

```

tulkas@tulkas-iMedia-S2883:~$ dmesg | grep rtl8192cu
[    8.295964] rtl8192cu: Chip version 0x11
[    8.333502] rtl8192cu: MAC address: 44:94:fc:fb:bf:68
[    8.333505] rtl8192cu: Board Type 0
[    8.333616] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    8.333915] usbcore: registered new interface driver rtl8192cu
[   13.330481] rtl8192cu: MAC auto ON okay!
[   13.343104] rtl8192cu: Tx queue select: 0x05

```

```

tulkas@tulkas-iMedia-S2883:~$ dmesg | grep wlan0
[   13.701691] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.702254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18438.183744] wlan0: authenticate with 72:25:63:dd:fc:9c
[18438.196739] wlan0: send auth to 72:25:63:dd:fc:9c (try 1/3)
[18438.199088] wlan0: authenticated
[18438.200690] wlan0: associate with 72:25:63:dd:fc:9c (try 1/3)
[18438.234217] wlan0: RX AssocResp from 72:25:63:dd:fc:9c (capab=0x411 status=0 aid=2)
[18438.234275] wlan0: associated
[18438.234845] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[18444.656546] wlan0: deauthenticated from 72:25:63:dd:fc:9c (Reason: 15)
[18445.497580] wlan0: authenticate with 72:25:63:dd:fc:9c
[18445.518542] wlan0: send auth to 72:25:63:dd:fc:9c (try 1/3)
[18445.547669] wlan0: authenticated
[18445.548709] wlan0: associate with 72:25:63:dd:fc:9c (try 1/3)
[18445.558241] wlan0: RX AssocResp from 72:25:63:dd:fc:9c (capab=0x411 status=0 aid=2)
[18445.558327] wlan0: associated
[18452.663405] wlan0: deauthenticated from 72:25:63:dd:fc:9c (Reason: 15)
[18453.505564] wlan0: authenticate with 72:25:63:dd:fc:9c
[18453.529230] wlan0: send auth to 72:25:63:dd:fc:9c (try 1/3)
[18453.543311] wlan0: authenticated
[18453.544667] wlan0: associate with 72:25:63:dd:fc:9c (try 1/3)
[18453.563458] wlan0: RX AssocResp from 72:25:63:dd:fc:9c (capab=0x411 status=0 aid=2)
[18453.563516] wlan0: associated
[18460.670251] wlan0: deauthenticated from 72:25:63:dd:fc:9c (Reason: 15)
[18461.489328] wlan0: authenticate with 72:25:63:dd:fc:9c
[18461.512014] wlan0: send auth to 72:25:63:dd:fc:9c (try 1/3)
[18461.514667] wlan0: authenticated
[18461.516729] wlan0: associate with 72:25:63:dd:fc:9c (try 1/3)
[18461.542623] wlan0: RX AssocResp from 72:25:63:dd:fc:9c (capab=0x411 status=0 aid=2)
[18461.542677] wlan0: associated
[18463.187739] wlan0: deauthenticating from 72:25:63:dd:fc:9c by local choice (reason=3)
[18489.561379] wlan0: authenticate with 72:25:63:dd:fc:9c
[18489.582507] wlan0: send auth to 72:25:63:dd:fc:9c (try 1/3)
[18489.599272] wlan0: authenticated
[18489.600642] wlan0: associate with 72:25:63:dd:fc:9c (try 1/3)
[18489.61

```

---

### Post by wildmanne39 on 2014-11-23
Hi, with an ethernet connection do:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.9
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You should set your routers encryption to just wpa2 (AES) (CCMP) if you have that option and not TKIP. 
Reboot

---

### Post by grahammechanical on 2014-11-23
Wrong password? It is not our user password but the wireless passphrase or key. Also called WPA-PSK key. Or even network security key.

The fact that Ubuntu is detecting wireless access points proves that Ubuntu has a driver for that USB WiFI stick. This confirms it.
> 

[COLOR=#000080]wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/COLOR]
If the USB stick was connected to the Freebox we would see RUNNING as well as UP BROADCAST MULTICAST as we do with the wired connection eth0

> [COLOR=#000080]          Cell 01 - Address: <MAC 'freebox_SERANN' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"freebox_SERANN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006ff8fff6
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK[/COLOR]

Notice, it says Encryption key: on. And WPA version 1 and Authentication suites (1) : PSK.
> 
[COLOR=#000080]- Device: wlan0  [freebox_SERANN] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (need authentication)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes[/COLOR]

Do you see State: connecting (need authentication)?

If you ask me, it is down to the wrong passphrase.

Regards.

---

### Post by sergio35 on 2014-11-24
I switched to channel 3, because channel 1 was quite busy.
I changed the option on the IPv6: "ignore automatically obtenued routes". now the wi-fi password is asked just once.
On the other hand the connection is established once every 10 attempts. For the lucky attempt the connection is lost in just 2 minutes and it is very slow.

@wild man: thanks a lot for the help. The actions I have already taken are in any way in conflict with the commands you suggested me?
@grahammechanical: thanks for the interest, unfortunately the password is correct.

---

### Post by wildmanne39 on 2014-11-24
The settings should be okay for now, but the best channels are 1,6 and 11 usually.
Your signal strength is only 4, how far are you from the router, any walls,ceilings or anything in the way?

---

### Post by sergio35 on 2014-11-24
> **Wild Man said:**
> The settings should be okay for now, but the best channels are 1,6 and 11 usually.
Your signal strength is only 4, how far are you from the router, any walls,ceilings or anything in the way?

I am 10-15 m away from the router, two doors in the way, and I keep them opened. Using Windows the signal is not the best ever, but fast enough to look at movies on streaming. On Ubuntu is just enough to search "hello" on google, some seconds for the results and then connection is lost. I am quite confused.

---

### Post by wildmanne39 on 2014-11-24
Have you changed to the new driver yet? post back if you have problems with the install. It is possible that it will not compile on that kernel but it should.

---

### Post by sergio35 on 2014-11-24
ok, so the first command:

```

tulkas@tulkas-iMedia-S2883:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
[sudo] password for tulkas: 
Sorry, try again.
[sudo] password for tulkas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.8 git-man libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl liberror-perl libfakeroot
  libstdc++-4.8-dev
Suggested packages:
  debhelper debian-keyring g++-multilib g++-4.8-multilib gcc-4.8-doc
  libstdc++6-4.8-dbg git-daemon-run git-daemon-sysvinit git-doc git-el
  git-email git-gui gitk gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
  libstdc++-4.8-doc
The following NEW packages will be installed:
  build-essential dkms dpkg-dev fakeroot g++ g++-4.8 git git-man
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  liberror-perl libfakeroot libstdc++-4.8-dev
0 upgraded, 14 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 12,3 MB/13,0 MB of archives.
After this operation, 54,0 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://fr.archive.ubuntu.com/ubuntu/ trusty/main libstdc++-4.8-dev amd64 4.8.2-19ubuntu1 [1 050 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ trusty/main g++-4.8 amd64 4.8.2-19ubuntu1 [7 038 kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ trusty/main g++ amd64 4:4.8.2-1ubuntu6 [1 490 B]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ trusty-updates/main dpkg-dev all 1.17.5ubuntu5.3 [726 kB]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ trusty/main build-essential amd64 11.6ubuntu6 [4 838 B]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ trusty/main dkms all 2.2.0.3-1.1ubuntu5 [64,4 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ trusty/main libfakeroot amd64 1.20-3ubuntu2 [25,4 kB]
Get:8 http://fr.archive.ubuntu.com/ubuntu/ trusty/main fakeroot amd64 1.20-3ubuntu2 [55,0 kB]
Get:9 http://fr.archive.ubuntu.com/ubuntu/ trusty/main liberror-perl all 0.17-1.1 [21,1 kB]
Get:10 http://fr.archive.ubuntu.com/ubuntu/ trusty/main git-man all 1:1.9.1-1 [698 kB]
Get:11 http://fr.archive.ubuntu.com/ubuntu/ trusty/main git amd64 1:1.9.1-1 [2 555 kB]
Get:12 http://fr.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-perl all 1.19.02-3 [50,0 kB]
Get:13 http://fr.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-diff-xs-perl amd64 0.04-2build4 [12,6 kB]
Get:14 http://fr.archive.ubuntu.com/ubuntu/ trusty/main libalgorithm-merge-perl all 0.08-2 [12,7 kB]
Fetched 12,3 MB in 15s (806 kB/s)                                              
Selecting previously unselected package libstdc++-4.8-dev:amd64.
(Reading database ... 233830 files and directories currently installed.)
Preparing to unpack .../libstdc++-4.8-dev_4.8.2-19ubuntu1_amd64.deb ...
Unpacking libstdc++-4.8-dev:amd64 (4.8.2-19ubuntu1) ...
Selecting previously unselected package g++-4.8.
Preparing to unpack .../g++-4.8_4.8.2-19ubuntu1_amd64.deb ...
Unpacking g++-4.8 (4.8.2-19ubuntu1) ...
Selecting previously unselected package g++.
Preparing to unpack .../g++_4%3a4.8.2-1ubuntu6_amd64.deb ...
Unpacking g++ (4:4.8.2-1ubuntu6) ...
Selecting previously unselected package dpkg-dev.
Preparing to unpack .../dpkg-dev_1.17.5ubuntu5.3_all.deb ...
Unpacking dpkg-dev (1.17.5ubuntu5.3) ...
Selecting previously unselected package build-essential.
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) ...
Selecting previously unselected package dkms.
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5) ...
Selecting previously unselected package libfakeroot:amd64.
Preparing to unpack .../libfakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking libfakeroot:amd64 (1.20-3ubuntu2) ...
Selecting previously unselected package fakeroot.
Preparing to unpack .../fakeroot_1.20-3ubuntu2_amd64.deb ...
Unpacking fakeroot (1.20-3ubuntu2) ...
Selecting previously unselected package liberror-perl.
Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
Unpacking liberror-perl (0.17-1.1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a1.9.1-1_all.deb ...
Unpacking git-man (1:1.9.1-1) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a1.9.1-1_amd64.deb ...
Unpacking git (1:1.9.1-1) ...
Selecting previously unselected package libalgorithm-diff-perl.
Preparing to unpack .../libalgorithm-diff-perl_1.19.02-3_all.deb ...
Unpacking libalgorithm-diff-perl (1.19.02-3) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Preparing to unpack .../libalgorithm-diff-xs-perl_0.04-2build4_amd64.deb ...
Unpacking libalgorithm-diff-xs-perl (0.04-2build4) ...
Selecting previously unselected package libalgorithm-merge-perl.
Preparing to unpack .../libalgorithm-merge-perl_0.08-2_all.deb ...
Unpacking libalgorithm-merge-perl (0.08-2) ...
Preparing to unpack .../linux-headers-3.13.0-39-generic_3.13.0-39.66_amd64.deb ...
Unpacking linux-headers-3.13.0-39-generic (3.13.0-39.66) over (3.13.0-39.66) ...
Preparing to unpack .../linux-headers-generic_3.13.0.39.46_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.39.46) over (3.13.0.39.46) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libstdc++-4.8-dev:amd64 (4.8.2-19ubuntu1) ...
Setting up g++-4.8 (4.8.2-19ubuntu1) ...
Setting up g++ (4:4.8.2-1ubuntu6) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up dpkg-dev (1.17.5ubuntu5.3) ...
Setting up build-essential (11.6ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu5) ...
Setting up libfakeroot:amd64 (1.20-3ubuntu2) ...
Setting up fakeroot (1.20-3ubuntu2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up liberror-perl (0.17-1.1) ...
Setting up git-man (1:1.9.1-1) ...
Setting up git (1:1.9.1-1) ...
Setting up libalgorithm-diff-perl (1.19.02-3) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build4) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up linux-headers-3.13.0-39-generic (3.13.0-39.66) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-39-generic /boot/vmlinuz-3.13.0-39-generic
Setting up linux-headers-generic (3.13.0.39.46) ...

```

and the second
```

tulkas@tulkas-iMedia-S2883:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 390, done.
remote: Total 390 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (390/390), 1.76 MiB | 244.00 KiB/s, done.
Resolving deltas: 100% (199/199), done.
Checking connectivity... done.


```


```

tulkas@tulkas-iMedia-S2883:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 390, done.
remote: Total 390 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (390/390), 1.76 MiB | 244.00 KiB/s, done.
Resolving deltas: 100% (199/199), done.
Checking connectivity... done.
tulkas@tulkas-iMedia-S2883:~$ sudo dkms add ./rtl8192cu-fixes

Creating symlink /var/lib/dkms/8192cu/1.9/source ->
                 /usr/src/8192cu-1.9

DKMS: add completed.

```


```

tulkas@tulkas-iMedia-S2883:~$ sudo dkms install 8192cu/1.9
[sudo] password for tulkas: 

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.13.0-39-generic -C /lib/modules/3.13.0-39-generic/build M=/var/lib/dkms/8192cu/1.9/build........................
cleaning build area....

DKMS: build completed.

8192cu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-39-generic/updates/dkms/

depmod......

Backing up initrd.img-3.13.0-39-generic to /boot/initrd.img-3.13.0-39-generic.old-dkms
Making new initrd.img-3.13.0-39-generic
(If next boot fails, revert to initrd.img-3.13.0-39-generic.old-dkms image)
update-initramfs..........

DKMS: install completed.
tulkas@tulkas-iMedia-S2883:~$ echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rtl8192cu



```

---

### Post by wildmanne39 on 2014-11-24
Looks good reboot and see if you can connect.
Thanks

---

### Post by sergio35 on 2014-11-24
Rebooted, still the same, I am sorry :(

---

### Post by wildmanne39 on 2014-11-24
Run the wireless script again and post the new wireless-info.txt.
Thanks

---

### Post by sergio35 on 2014-11-24
Ok, thank you.

```

########## wireless info START ##########

Report from: 24 Nov 2014 21:04 CET +0100

Booted last: 24 Nov 2014 20:40 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################

rtl_usb                18448  0 
rtlwifi                63475  1 rtl_usb
rtl8192c_common        53172  0 
mac80211              630653  2 rtl_usb,rtlwifi
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr f8:0f:41:c8:97:da  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:15a6:be7c:c7e3:c550/64 Scope:Global
          inet6 addr: 2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fec8:97da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8789543 (8.7 MB)  TX bytes:2113977 (2.1 MB)

wlan0     Link encap:Ethernet  HWaddr 44:94:fc:fb:bf:68  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:49 overruns:0 frame:0
          TX packets:0 errors:0 dropped:16 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1422 (1.4 KB)  TX bytes:588 (588.0 B)


##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F8:0F:41:C8:97:DA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:15a6:be7c:c7e3:c550
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         fe80::fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        44:94:FC:FB:BF:68

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JulienWIFI:      Infra, D6:FE:AF:AB:61:70, Freq 2462 MHz, Rate 44 Mb/s, Strength 49 WPA
    FreeWifi_secure: Infra, D6:FE:AF:AB:61:73, Freq 2462 MHz, Rate 44 Mb/s, Strength 49 WPA Enterprise
    FreeWifi_secure: Infra, AE:8E:87:99:B4:02, Freq 2422 MHz, Rate 44 Mb/s, Strength 43 WPA Enterprise
    SFR WiFi Mobile: Infra, 72:17:33:F2:2A:23, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2 Enterprise
    NUMERICABLE-ED12:Infra, 00:1A:2B:41:F8:C4, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WEP
    NEUF_2A1C:       Infra, 00:17:33:F2:2A:20, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WEP
    FreeWifi:        Infra, D6:FE:AF:AB:61:72, Freq 2462 MHz, Rate 44 Mb/s, Strength 50
    FreeWifi:        Infra, AE:8E:87:99:B4:01, Freq 2422 MHz, Rate 44 Mb/s, Strength 43
    SFR WiFi FON:    Infra, 72:17:33:F2:2A:21, Freq 2462 MHz, Rate 54 Mb/s, Strength 7
    NEUF_8348:       Infra, 00:25:15:1A:83:4C, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA
    freebox_SERANN:  Infra, AE:8E:87:99:B4:00, Freq 2422 MHz, Rate 44 Mb/s, Strength 43 WPA



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

no-auto-default=F8:0F:41:C8:97:DA,

[ifupdown]
managed=false

##### NetworkManager profiles ###########



```

---

### Post by wildmanne39 on 2014-11-24
There is a lot of information missing from the file you posted, was that everything in that file? did you enter your password when asked for it? the first file you posted was complete. If the file is to large for the forum it will create the file in a tar.gz format.

What is the name of the network you want to connect too?

---

### Post by sergio35 on 2014-11-24
That's true, it was in a tar.gz...sorry
The network name is FREEBOX_SERANN

```


########## wireless info START ##########

Report from: 24 Nov 2014 21:28 CET +0100

Booted last: 24 Nov 2014 20:40 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 013: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

rtl_usb                18448  0 
rtlwifi                63475  1 rtl_usb
rtl8192c_common        53172  0 
mac80211              630653  2 rtl_usb,rtlwifi
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:15a6:be7c:c7e3:c550/64 Scope:Global
          inet6 addr: 2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fec8:97da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27322513 (27.3 MB)  TX bytes:4675915 (4.6 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:78 overruns:0 frame:0
          TX packets:0 errors:0 dropped:16 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1422 (1.4 KB)  TX bytes:588 (588.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:15a6:be7c:c7e3:c550
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         fe80::fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JulienWIFI:      Infra, <MAC 'JulienWIFI' [AC8]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 49 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC11]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 49 WPA Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC3]>, Freq 2422 MHz, Rate 44 Mb/s, Strength 43 WPA Enterprise
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA2 Enterprise
    NUMERICABLE-ED12:Infra, <MAC 'NUMERICABLE-ED12' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WEP
    NEUF_2A1C:       Infra, <MAC 'NEUF_2A1C' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WEP
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC10]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 50
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC2]>, Freq 2422 MHz, Rate 44 Mb/s, Strength 43
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7
    NEUF_8348:       Infra, <MAC 'NEUF_8348' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA
    freebox_SERANN:  Infra, <MAC 'freebox_SERANN' [AC1]>, Freq 2422 MHz, Rate 44 Mb/s, Strength 43 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN12]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 23 WPA2 Enterprise
    SFR_D860:        Infra, <MAC 'SFR_D860' [AN13]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 7 WPA
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AN14]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 23

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

[[/etc/NetworkManager/system-connections/freebox_SERANN]] (600 root)
[connection] id=freebox_SERANN | type=802-11-wireless
[802-11-wireless] ssid=freebox_SERANN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      8   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freebox_SERANN' [AC1]>
                    ESSID:"freebox_SERANN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=43/100  
          Cell 02 - Address: <MAC 'FreeWifi' [AC2]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=54/100  Signal level=42/100  
          Cell 03 - Address: <MAC 'FreeWifi_secure' [AC3]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=48/100  Signal level=43/100  
          Cell 04 - Address: <MAC 'NEUF_8348' [AC4]>
                    ESSID:"NEUF_8348"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=95/100  Signal level=43/100  
          Cell 05 - Address: <MAC 'SFR WiFi Mobile' [AC5]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=17/100  Signal level=26/100  
          Cell 06 - Address: <MAC 'NEUF_2A1C' [AC6]>
                    ESSID:"NEUF_2A1C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=0/100  Signal level=26/100  
          Cell 07 - Address: <MAC 'SFR WiFi FON' [AC7]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=20/100  Signal level=16/100  
          Cell 08 - Address: <MAC 'JulienWIFI' [AC8]>
                    ESSID:"JulienWIFI"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=77/100  Signal level=49/100  
          Cell 09 - Address: <MAC '' [AC9]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=47/100  
          Cell 10 - Address: <MAC 'FreeWifi' [AC10]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=72/100  Signal level=48/100  
          Cell 11 - Address: <MAC 'FreeWifi_secure' [AC11]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=66/100  Signal level=48/100  
          Cell 12 - Address: <MAC 'NUMERICABLE-ED12' [AC12]>
                    ESSID:"NUMERICABLE-ED12"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=0/100  Signal level=92/100  

##### module infos ######################

[rtl_usb]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9A4393167BB287C0A5DC011
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
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
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist rtl8192cu

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
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############

```

---

### Post by wildmanne39 on 2014-11-24
Please install rfkill application then run:
```
rfkill list all
```
and post the result of the command here.
Go into your router and change the channel to 1 and encryption set it to just wpa (AES) (CCMP) not TKIP then save the settings.
Also what country are you in?
Thanks

---

### Post by sergio35 on 2014-11-25
Hi,

rfkill was akready installed. So I tried the command, but no output on terminal was given...is that strange?

```

tulkas@tulkas-iMedia-S2883:~$ rfkill list all
tulkas@tulkas-iMedia-S2883:~$ 

```

I changed to channel 1 and changed the encryption and saved settings, but the connection is still the same.

(Connection name FREEBOX_SERANN)

I am in France.

Thanks ;)

```


########## wireless info START ##########

Report from: 25 Nov 2014 08:53 CET +0100

Booted last: 25 Nov 2014 08:24 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fec8:97da/64 Scope:Link
          inet6 addr: 2a01:e35:2ea4:74c0:3c6d:3abb:3d04:3d44/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14647155 (14.6 MB)  TX bytes:2206772 (2.2 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:38 overruns:0 frame:0
          TX packets:0 errors:0 dropped:20 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:399 (399.0 B)  TX bytes:471 (471.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:3c6d:3abb:3d04:3d44
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         fe80::fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

- Device: wlan0  [freebox_SERANN] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connecting (configuring)
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    JulienWIFI:      Infra, <MAC 'JulienWIFI' [AC4]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 50 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC7]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 49 WPA Enterprise
    NEUF_8348:       Infra, <MAC 'NEUF_8348' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 42 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA2 Enterprise
    NUMERICABLE-ED12:Infra, <MAC 'NUMERICABLE-ED12' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WEP
    NEUF_2A1C:       Infra, <MAC 'NEUF_2A1C' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC6]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 48
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26
    SFR_D860:        Infra, <MAC 'SFR_D860' [AN9]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 7 WPA
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC13]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 7
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AN11]>, Freq 2437 MHz, Rate 16 Mb/s, Strength 0 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC2]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 44 WPA Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC1]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 44
    SFR_D860:        Infra, <MAC 'SFR_D860' [AN9]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7 WPA
    freebox_SERANN:  Infra, <MAC 'freebox_SERANN' [AC12]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 46 WPA
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC13]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7

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

[[/etc/NetworkManager/system-connections/freebox_SERANN]] (600 root)
[connection] id=freebox_SERANN | type=802-11-wireless
[802-11-wireless] ssid=freebox_SERANN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      9   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FreeWifi' [AC1]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=93/100  Signal level=42/100  
          Cell 02 - Address: <MAC 'FreeWifi_secure' [AC2]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=95/100  Signal level=42/100  
          Cell 03 - Address: <MAC 'NEUF_8348' [AC3]>
                    ESSID:"NEUF_8348"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=96/100  Signal level=42/100  
          Cell 04 - Address: <MAC 'JulienWIFI' [AC4]>
                    ESSID:"JulienWIFI"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=96/100  Signal level=52/100  
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=87/100  Signal level=49/100  
          Cell 06 - Address: <MAC 'FreeWifi' [AC6]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=87/100  Signal level=51/100  
          Cell 07 - Address: <MAC 'FreeWifi_secure' [AC7]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=86/100  Signal level=49/100  
          Cell 08 - Address: <MAC 'NUMERICABLE-ED12' [AC8]>
                    ESSID:"NUMERICABLE-ED12"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=96/100  Signal level=72/100  
          Cell 09 - Address: <MAC 'SFR WiFi FON' [AC9]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=92/100  Signal level=36/100  
          Cell 10 - Address: <MAC 'NEUF_2A1C' [AC10]>
                    ESSID:"NEUF_2A1C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=96/100  Signal level=39/100  
          Cell 11 - Address: <MAC 'SFR WiFi Mobile' [AC11]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=88/100  Signal level=36/100  
          Cell 12 - Address: <MAC 'freebox_SERANN' [AC12]>
                    ESSID:"freebox_SERANN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=92/100  Signal level=43/100  
          Cell 13 - Address: <MAC 'SFR WiFi FON' [AC13]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=50/100  Signal level=7/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist rtl8192cu

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
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.105976] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   15.964992] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   64.489960] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:2, no_gkey_mc_cnt:0
[   66.537884] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:1, no_gkey_mc_cnt:0 (repeated 8 times)
[   92.035705] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:2, no_gkey_mc_cnt:0
[   93.059728] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:1, no_gkey_mc_cnt:0 (repeated 10 times)
[  119.684044] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:2, no_gkey_mc_cnt:0 (repeated 2 times)
[  122.756044] rtw_tkip_decrypt(wlan0) no_gkey_bc_cnt:1, no_gkey_mc_cnt:0 (repeated 2 times)

########## wireless info END ############



```

---

### Post by sergio35 on 2014-11-25
I don't know how it is possible, but ten minutes ago I switched on the computer and the wireless connection was ON and stable (quality 98%).
Before labeling this topic as SOLVED I would wait to reboot the system and see if the solution is stable. In every case a big "THANKS" to all those who helped me, in particular Wild Man.

 Here the output:

```


########## wireless info START ##########

Report from: 25 Nov 2014 17:07 CET +0100

Booted last: 25 Nov 2014 16:50 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 008: ID 14cd:6116 Super Top M6116 SATA Bridge
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81254 (81.2 KB)  TX bytes:64424 (64.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:29d0:a3ed:b099:9774/64 Scope:Global
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          inet6 addr: 2a01:e35:2ea4:74c0:4694:fcff:fefb:bf68/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6447 errors:0 dropped:5921 overruns:0 frame:0
          TX packets:6371 errors:0 dropped:19 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6050232 (6.0 MB)  TX bytes:1470383 (1.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"freebox_SERANN"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'freebox_SERANN' [AC1]>   
          Bit Rate:300 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=96/100  Signal level=48/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

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

- Device: wlan0  [freebox_SERANN] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           300 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    JulienWIFI:      Infra, <MAC 'JulienWIFI' [AC9]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 48 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC12]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 48 WPA Enterprise
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 43 WPA2 Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC3]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 47 WPA Enterprise
    NEUF_8348:       Infra, <MAC 'NEUF_8348' [AC4]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 34 WPA
    NUMERICABLE-ED12:Infra, <MAC 'NUMERICABLE-ED12' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 88 WEP
    NEUF_2A1C:       Infra, <MAC 'NEUF_2A1C' [AC7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 43
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC11]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 48
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC2]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 47
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC14]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 11 WPA2 Enterprise
    SFR_D860:        Infra, <MAC 'SFR_D860' [AC15]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 7 WPA
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC13]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 2
    *freebox_SERANN: Infra, <MAC 'freebox_SERANN' [AC1]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 96 WPA

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:29d0:a3ed:b099:9774
    Prefix:          64
    Gateway:         ::

    Address:         2a01:e35:2ea4:74c0:4694:fcff:fefb:bf68
    Prefix:          64
    Gateway:         ::

    Address:         fe80::4694:fcff:fefb:bf68
    Prefix:          64
    Gateway:         ::

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

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

[[/etc/NetworkManager/system-connections/freebox_SERANN]] (600 root)
[connection] id=freebox_SERANN | type=802-11-wireless
[802-11-wireless] ssid=freebox_SERANN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      11   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freebox_SERANN' [AC1]>
                    ESSID:"freebox_SERANN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=98/100  Signal level=48/100  
          Cell 02 - Address: <MAC 'FreeWifi' [AC2]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=100/100  Signal level=47/100  
          Cell 03 - Address: <MAC 'FreeWifi_secure' [AC3]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=100/100  Signal level=47/100  
          Cell 04 - Address: <MAC 'NEUF_8348' [AC4]>
                    ESSID:"NEUF_8348"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=36/100  Signal level=43/100  
          Cell 05 - Address: <MAC 'NUMERICABLE-ED12' [AC5]>
                    ESSID:"NUMERICABLE-ED12"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=20/100  Signal level=74/100  
          Cell 06 - Address: <MAC 'SFR WiFi Mobile' [AC6]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=48/100  Signal level=28/100  
          Cell 07 - Address: <MAC 'NEUF_2A1C' [AC7]>
                    ESSID:"NEUF_2A1C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=20/100  Signal level=26/100  
          Cell 08 - Address: <MAC 'SFR WiFi FON' [AC8]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=48/100  Signal level=23/100  
          Cell 09 - Address: <MAC 'JulienWIFI' [AC9]>
                    ESSID:"JulienWIFI"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=50/100  
          Cell 10 - Address: <MAC '' [AC10]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=20/100  Signal level=48/100  
          Cell 11 - Address: <MAC 'FreeWifi' [AC11]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=48/100  Signal level=50/100  
          Cell 12 - Address: <MAC 'FreeWifi_secure' [AC12]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=29/100  Signal level=48/100  
          Cell 13 - Address: <MAC 'SFR WiFi FON' [AC13]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality=18/100  Signal level=10/100  
          Cell 14 - Address: <MAC 'SFR WiFi Mobile' [AC14]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=6/100  Signal level=19/100  
          Cell 15 - Address: <MAC 'SFR_D860' [AC15]>
                    ESSID:"SFR_D860"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=56/100  Signal level=10/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist rtl8192cu

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
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.322196] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   17.162063] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by sergio35 on 2014-11-26
It was too nice to be true. Yesterday evening, at around 21h (when all the neighbour are home??) the connection went down and the signal become very noisy. So I went to sleep. This morning I am experiencing the same problems as before one again. Here the output:

```

########## wireless info START ##########

Report from: 26 Nov 2014 08:23 CET +0100

Booted last: 26 Nov 2014 08:10 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-40-generic #69-Ubuntu SMP Thu Nov 13 17:53:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: Acer Incorporated [ALI] Device [1025:085e]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 003: ID 04ca:007d Lite-On Technology Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              484040  0 
wmi                    19177  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e35:2ea4:74c0:bc7d:bd91:3e23:7287/64 Scope:Global
          inet6 addr: 2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da/64 Scope:Global
          inet6 addr: fe80::fa0f:41ff:fec8:97da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8842685 (8.8 MB)  TX bytes:857835 (857.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::4694:fcff:fefb:bf68/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:7 overruns:0 frame:0
          TX packets:0 errors:0 dropped:19 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e35:2ea4:74c0:bc7d:bd91:3e23:7287
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         2a01:e35:2ea4:74c0:fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    Address:         fe80::fa0f:41ff:fec8:97da
    Prefix:          64
    Gateway:         fe80::207:cbff:fe48:af00

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC12]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 54 WPA Enterprise
    NEUF_8348:       Infra, <MAC 'NEUF_8348' [AC3]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 36 WPA
    JulienWIFI:      Infra, <MAC 'JulienWIFI' [AC4]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 56 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC7]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 51 WPA Enterprise
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2 Enterprise
    NUMERICABLE-ED12:Infra, <MAC 'NUMERICABLE-ED12' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WEP
    NEUF_2A1C:       Infra, <MAC 'NEUF_2A1C' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC6]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 54
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 43
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC2]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 47
    freebox_SERANN:  Infra, <MAC 'freebox_SERANN' [AC1]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 54 WPA

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

[[/etc/NetworkManager/system-connections/freebox_SERANN]] (600 root)
[connection] id=freebox_SERANN | type=802-11-wireless
[802-11-wireless] ssid=freebox_SERANN | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NUMERICABLE-ED12]] (600 root)
[connection] id=NUMERICABLE-ED12 | type=802-11-wireless
[802-11-wireless] ssid=NUMERICABLE-ED12 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      8   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'freebox_SERANN' [AC1]>
                    ESSID:"freebox_SERANN"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=60/100  Signal level=46/100  
          Cell 02 - Address: <MAC 'FreeWifi' [AC2]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=46/100  Signal level=47/100  
          Cell 03 - Address: <MAC 'NEUF_8348' [AC3]>
                    ESSID:"NEUF_8348"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality=67/100  Signal level=43/100  
          Cell 04 - Address: <MAC 'JulienWIFI' [AC4]>
                    ESSID:"JulienWIFI"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Quality=74/100  Signal level=51/100  
          Cell 05 - Address: <MAC '' [AC5]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=48/100  Signal level=50/100  
          Cell 06 - Address: <MAC 'FreeWifi' [AC6]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality=81/100  Signal level=52/100  
          Cell 07 - Address: <MAC 'FreeWifi_secure' [AC7]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=62/100  Signal level=49/100  
          Cell 08 - Address: <MAC 'NUMERICABLE-ED12' [AC8]>
                    ESSID:"NUMERICABLE-ED12"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=20/100  Signal level=74/100  
          Cell 09 - Address: <MAC 'SFR WiFi Mobile' [AC9]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=21/100  Signal level=38/100  
          Cell 10 - Address: <MAC 'NEUF_2A1C' [AC10]>
                    ESSID:"NEUF_2A1C"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Quality=31/100  Signal level=42/100  
          Cell 11 - Address: <MAC 'SFR WiFi FON' [AC11]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:54 Mb/s
                    Quality=64/100  Signal level=42/100  
          Cell 12 - Address: <MAC 'FreeWifi_secure' [AC12]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality=92/100  Signal level=47/100  

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-40-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        35:72:8C:DB:88:AA:70:FD:D3:AC:D1:53:A3:7B:51:31:92:A4:7F:D8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
blacklist rtl8192cu

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
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.118274] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   17.006332] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



```

---

### Post by temiroff on 2015-02-15
same problem Have no idea what should I do ?
     sudo lshw -class network[sudo] password for alex: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:90:cb:c8
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:50 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 30:46:9a:2e:8d:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.59+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE 802.11g


dmesg | grep wlan0
[   17.732097] wlan0: ethernet device 30:46:9a:2e:8d:a7 using NDIS driver: bcmn43xx64, version: 0x50a4f1e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   17.734494] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   19.916063] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.916267] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.863911] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

