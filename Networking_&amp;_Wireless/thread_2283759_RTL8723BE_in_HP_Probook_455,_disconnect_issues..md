---
title: "RTL8723BE in HP Probook 455, disconnect issues."
date: 2015-06-24
forum: Networking &amp; Wireless
---

### Post by raig on 2015-06-24
Hi all,

I recently needed a solely GNU/Linux laptop and went with a Ubuntu HP Probook 455 from ebuyer. The device was meant to ship with 14.04, but arrived with 12.04. Regardless I would have done a clean install on an SSD, which is what I've done (currently running 14.04).
Unfortunately, the laptop came with a RTL8723BE wlan card. From my reading the device has various problems under distros of all varieties, including Ubuntu. The various solutions I have seen have not helped my case. I really do not like posting for help, but I have tried the various solutions out there that have worked with other users, none seemed to have helped my case. I am pretty close to doing a complete reinstall and another attempt in frustration.
My Access Point (AP) is not an issue as other Ubuntu devices connect and maintain connection with no issue.

I have ran apt-get update, upgrade and dist-upgrade.

I have tried; building rtlwifi_new from github and successfully built and installed, installing hanipouspilot rtlwifi ppa (in case I missed some build instructions) all with various modprobe configuration settings.
Currently, I found "options rtl8723be msi=1" in "rtl8723be.conf" under "/etc/modprobe.d/" to be most stable i.e. showing available APs and maintains a 2 minutes connection under load before being dropped. I have resorted to using a wlan usb adapter in the mean-time, but this is not suitable for general use.

wireless-info, with APs renamed.
```

########## wireless info START ##########

Report from: 21 Jun 2015 16:36 BST +0100

Booted last: 21 Jun 2015 16:27 BST +0100

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2235]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b466 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
rtl8723be              85054  0 
btcoexist              50304  1 rtl8723be
rtl8723_common         23361  1 rtl8723be
rtl_pci                26690  1 rtl8723be
rtlwifi                64255  2 rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              494362  2 mac80211,rtlwifi
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet6 addr: fe80::3ea8:2aff:fe7f:92f6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2972825 (2.9 MB)  TX bytes:137817 (137.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.30  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c68e:8fff:fec4:8a6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1994649 (1.9 MB)  TX bytes:473979 (473.9 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"MYAP"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'MYAP' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:72   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       914     1  0 16:27 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [MYAP 1] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    MYAP:        Infra, <MAC 'MYAP' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    OtherAPss:     Infra, <MAC 'OtherAPss' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    OtherAPss:          Infra, <MAC 'OtherAPss' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WEP
    *MYAP:       Infra, <MAC 'MYAP' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 91 WPA2
    OtherAPss:        Infra, <MAC 'OtherAPss' [AC6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2 Enterprise
    OtherAPss:        Infra, <MAC 'OtherAPss' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    OtherAPss: Infra, <MAC 'OtherAPss' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    OtherAPss:     Infra, <MAC 'OtherAPss' [AC9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA2
    OtherAPss: Infra, <MAC 'OtherAPss' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    OtherAPss:        Infra, <MAC 'OtherAPss' [AC10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.30
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/MYAP 2]] (600 root)
[connection] id=MYAP 2 | type=802-11-wireless
[802-11-wireless] ssid=MYAP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WorkAP]] (600 root)
[ipv6] method=auto
[connection] id=WorkAP | type=802-11-wireless
[802-11-wireless] ssid=WorkAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MYAP 1]] (600 root)
[connection] id=MYAP 1 | type=802-11-wireless
[802-11-wireless] ssid=MYAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MYAP]] (600 root)
[connection] id=MYAP | type=802-11-wireless
[802-11-wireless] ssid=MYAP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MYAP' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"MYAP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c5bda37cf0
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'OtherAPs' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007099feae9
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'OtherAPs' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a608300715
                    Extra: Last beacon: 12ms ago
          Cell 04 - Address: <MAC 'OtherAPs' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000bdae8ec33
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'OtherAPs' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000708c07c2d
                    Extra: Last beacon: 4192ms ago
          Cell 06 - Address: <MAC 'OtherAPs' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000708d5a23e
                    Extra: Last beacon: 4188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'OtherAPs' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000021d04865b35
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'OtherAPs' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e3b2bb16a
                    Extra: Last beacon: 17420ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'OtherAPs' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e70b66180
                    Extra: Last beacon: 17200ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'OtherAPs' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"OtherAPs"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000073ef4c189
                    Extra: Last beacon: 1556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
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

[rtl8723_common]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
fwlps: Y
ips: Y
msi: Y
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be msi=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

##### dmesg #############################

[  247.538321] wlan0: authenticate with <MAC 'MYAP' [AC1]>
[  247.557452] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 1/3)
[  247.660831] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 2/3)
[  247.663886] wlan0: authenticated
[  247.664270] wlan0: associating with AP with corrupt beacon
[  247.664804] wlan0: associate with <MAC 'MYAP' [AC1]> (try 1/3)
[  247.670765] wlan0: RX AssocResp from <MAC 'MYAP' [AC1]> (capab=0x411 status=0 aid=6)
[  247.670934] wlan0: associated
[  270.383357] wlan0: deauthenticating from <MAC 'MYAP' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  273.345900] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  274.270484] wlan0: authenticate with <MAC 'MYAP' [AC1]>
[  274.280711] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 1/3)
[  274.286395] wlan0: authenticated
[  274.289635] wlan0: associate with <MAC 'MYAP' [AC1]> (try 1/3)
[  274.297108] wlan0: RX AssocResp from <MAC 'MYAP' [AC1]> (capab=0x411 status=0 aid=6)
[  274.297253] wlan0: associated
[  274.297309] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  451.661047] wlan0: Connection to AP <MAC 'MYAP' [AC1]> lost
[  466.070521] wlan0: Connection to AP <MAC address> lost
[  467.516281] wlan0: authenticate with <MAC 'MYAP' [AC1]>
[  467.534897] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 1/3)
[  467.538059] wlan0: authenticated
[  467.542330] wlan0: associate with <MAC 'MYAP' [AC1]> (try 1/3)
[  467.555822] wlan0: RX AssocResp from <MAC 'MYAP' [AC1]> (capab=0x411 status=0 aid=6)
[  467.555967] wlan0: associated
[  563.598105] wlan0: deauthenticating from <MAC 'MYAP' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  564.982428] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  566.691909] wlan0: authenticate with <MAC 'MYAP' [AC1]>
[  566.711252] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 1/3)
[  566.712907] wlan0: authenticated
[  566.714664] wlan0: associate with <MAC 'MYAP' [AC1]> (try 1/3)
[  566.718523] wlan0: RX AssocResp from <MAC 'MYAP' [AC1]> (capab=0x411 status=0 aid=6)
[  566.718709] wlan0: associated
[  566.718727] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  566.756476] wlan0: deauthenticating from <MAC 'MYAP' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  566.789161] wlan0: authenticate with <MAC 'MYAP' [AC1]>
[  566.799356] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 1/3)
[  568.209162] wlan0: send auth to <MAC 'MYAP' [AC1]> (try 2/3)
[  568.211122] wlan0: authenticated
[  568.214712] wlan0: associate with <MAC 'MYAP' [AC1]> (try 1/3)
[  568.220714] wlan0: RX AssocResp from <MAC 'MYAP' [AC1]> (capab=0x411 status=0 aid=6)
[  568.220863] wlan0: associated

########## wireless info END ############


```

---

### Post by Pilot6 on 2015-06-24
You can install this driver

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

---

### Post by howefield on 2015-06-24
Thanks for that Pilot6, I too have the same laptop from the same vendor ect ect as raig so will try your ppa suggestion later.

@raig, just curious, why would you think the machine would come installed with 14.04 ?

---

### Post by raig on 2015-06-25
@Pilot6; this is a dkms packaged version of Larry Fingers rtlwifi_new on git, correct? I've ran that in addition to the ppa listed (mentioned towards the end of my post). For the sake of this thread I'll try it again and report how it gets on.

@howefield; the ebuyer listings were originally 14.04 during pre-order, they were delivered with 12.04, leading them to quickly change the listing details. See; [http://www.omgubuntu.co.uk/2015/05/new-ubuntu-laptops-available-from-ebuyer-2-2](http://www.omgubuntu.co.uk/2015/05/new-ubuntu-laptops-available-from-ebuyer-2-2) and [http://ubuntuforums.org/showthread.php?t=2280428](http://ubuntuforums.org/showthread.php?t=2280428) (that thread didn't resolve me issues either..). Do let me know how you get on.

---

### Post by howefield on 2015-06-25
PPA didn't work for me with 15.04, didn't try 14.04, but to be honest want to run the development version on it so will most likely just swap out the wireless card and vow to never buy from ebuyer/hp again.

@raig : it was always 12.04 when I saw it but didn't mind upgrading, never thought for a minute there would be a hardware problem with a preinstalled machine. It did seem strange that they used 12.04 but now I know why.

---

### Post by Pilot6 on 2015-06-25
Yeo need to uninstall lwfinger driver first. We have different namings, but same driver. They conflict.

---

### Post by jeremy31 on 2015-06-25
Sometimes these just need ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` and a reboot for disconnect issues

---

### Post by raig on 2015-06-26
My current partition is still flaky at best (with lwfingers driver uninstalled). I installed 14.04 and updated in a new partition, adding ppa:hanipouspilot/rtlwifi with Pilot6's instructions work flawlessly. My rtl8723be.conf file is currently set as "options rtl8723be msi=1", I had previously tried msi=1, ips=0 and fwlps=0.
 How does the ppa differ from lwfingers? I might as well go to latest release - I'll mark this as solved after testing on 15.04; so others with the same device know more info.

---

### Post by G_Lee on 2015-06-27
Hey, I'm currently on a similar product.  It was supposed to come with Ubuntu 14 but came with Ubuntu 12.  I reinstalled it.  The Wifi decided not to work without a whole load of messing around and glitchiness.  I was daft enough to upgrade to 15 and this caused the Desktop environment to refuse to work.  I guess it was something to do with the proprietry driver not being very good at talking to the latest version of Linux for the following reason:

Being interested to try and learn more about this stuff I tried installing Arch Linux.  After a great deal of confusion over how it's clearly a modern laptop but wasn't booting in UEFI mode, and multiple repartitionings, I noticed that the boot mode was set to "legacy" - though the installation still refused to boot with a BIOS partition.  So eventually I chose UEFI mode and configured stuff correctly.  I installed the proprietry graphics driver and XFCE4, and after a reboot I had a more or less identical problem to wwhen Ubuntu 15 was installed.  Eventually I installed the free driver (annoying cos I suspect that it slims the chances that Fallout+WIne's going to work :p ) and it worked.  I haven't checked out how to set up the Wifi on this but luckily I am largely just using an ethernet cable.  The sound's also now causing me a headache.

Like I suppose I was asking for it by choosing Arch.  It's simply a steep learning curve.  Just I think that these hardware manufacturers aren't making things easy for us.

---

### Post by raig on 2015-06-27
Wireless works fine on the latest 15.04 with Pilot6's ppa instructions, /etc/modprobe.d/rtl8723be.conf having "options msi=1" set and furthermore, often requiring network management reset ("sudo service network-manager restart") on start up - I should really add that to start up commands. @howefield might find that useful.
So I've now set this as solved, despite the start up quirk.
I usually run proprietary free wlan cards for this experience (old Broadcom drivers set the precedent for avoiding proprietary), I can see this card getting swapped out after sourcing a free driver wlan card with a single antenna connection.

@G_Lee; Fallout + Wine is also on my list. :p, being an Ubuntu inept is challenging. For what it's worth I'm running; Kaveri Radeon R6 Graphics with X.Org X server - AMD/ATI/ display wrapper from xserver-xorg-video-ati (open source, tested). There are other proprietary options available, which I haven't tested yet.

---

### Post by janmes2 on 2016-02-23
Dont know about other wifi like intel/broadcom etc but I also have the realtek rtl8723be wifi card and tried installing loads of drivers and multiple options but no jy. After about a month, i added this simple line to grub and low and behold all is working well.

here it is....

press Ctrl+Alt+T to open up a terminal 


run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer

---

### Post by david506 on 2016-03-28
Hi, 

I am new arround. Also with Linux. 
I switched from Windows to Zorin 9(based on Ubuntu 14.04). I have an HP 455 G2 with not working RTL8723BE wireless device. 
I tried some indications from
[http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04)
and from Pilot6.
None of it worked for me. 
After first try, I was able to turn on/off the wireless connection from connection icon, near battery indicator in taskbar. But I could not see any wireless access point.

Now, I am stuck. I dont't know to much linux commands. What should I do?

---

### Post by jeremy31 on 2016-03-28
Post the result of ```
modinfo -p rtl8723be
```

I want to see if the most recent revision is loaded

---

### Post by david506 on 2016-04-02
Meanwhile I installed Ubuntu 14.04


I followed Pillot6 instruction


  > sudo add-apt-repository ppa:hanipouspilot/rtlwifi
  sudo apt-get update
  sudo apt-get install rtlwifi-new-dkms linux-firmware


I had no errors, but no result.


Bellow  my wifi card info

> swlps: (bool)
swenc:using hardware crypto (default 0 [hardware])
 (bool)
ips:using no link power save (default 1 is open)
 (bool)
fwlps:using linked fw control power save (default 1 is open)
 (bool)
msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
debug:Set debug level (0-5) (default 0) (int)
disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)


---

