---
title: "Wireless keeps cutting out on ubuntu 14.04 after recent reinstallation"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by joem2305 on 2015-12-01
Apologies for reposting
I recently installed ubuntu 14.04 after having to reinstall it due to a ubiquity bug which caused the hard drive to be wiped, before that my wifi was fine but now I get maybe 30 minutes max of wifi before it cuts out and I have to reboot it. The internet works perfectly fine when wired. I have tried things like switching off iwlwifi with no luck. I've also set the MTU value to 1500 and that hasn't worked either
Here is my wifi information and info about my wifi card
>   description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 07
       serial: 38:63:bb:b0:b6:5d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:51 ioport:d000(size=256) memory:fe914000-fe914fff memory:fe910000-fe913fff memory:fe900000-fe90ffff

>  *-network

########## wireless info START ##########

Report from: 27 Nov 2015 23:44 GMT +0000

Booted last: 27 Nov 2015 23:37 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-53-generic #72~14.04.1-Ubuntu SMP Fri Nov 6 18:17:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]
    Kernel driver in use: rtl8723be

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:808b]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b40e Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
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
cfg80211              498458  2 mac80211,rtlwifi
wmi                    19193  1 hp_wmi

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
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1141708 (1.1 MB)  TX bytes:550026 (550.0 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TALKTALK-64CEEC"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'TALKTALK-64CEEC' [AC1]>   
          Bit Rate=135 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

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

root       802     1  0 23:37 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

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

  Wired Properties
    Carrier:         off

- Device: wlan0  [TALKTALK-64CEEC] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           135 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia9011929: Infra, <MAC 'virginmedia9011929' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2 Enterprise
    BTHub5-7PH6:     Infra, <MAC 'BTHub5-7PH6' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA2
    VM578649-2G:     Infra, <MAC 'VM578649-2G' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    DIRECT-71-HP ENVY 5640 series: Infra, <MAC 'DIRECT-71-HP ENVY 5640 series' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2
    VM070616-2G:     Infra, <MAC 'VM070616-2G' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54
    *TALKTALK-64CEEC:Infra, <MAC 'TALKTALK-64CEEC' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40

  IPv4 Settings:
    Address:         192.168.1.5
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

[[/etc/NetworkManager/system-connections/hydrabooks]] (600 root)
[connection] id=hydrabooks | type=802-11-wireless
[802-11-wireless] ssid=hydrabooks | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_The Cloud]] (600 root)
[connection] id=_The Cloud | type=802-11-wireless
[802-11-wireless] ssid=_The Cloud | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SKY55453]] (600 root)
[connection] id=SKY55453 | type=802-11-wireless
[802-11-wireless] ssid=SKY55453 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK-64CEEC]] (600 root)
[connection] id=TALKTALK-64CEEC | type=802-11-wireless
[802-11-wireless] ssid=TALKTALK-64CEEC | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/virginmedia1632170]] (600 root)
[connection] id=virginmedia1632170 | type=802-11-wireless
[802-11-wireless] ssid=virginmedia1632170 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BTWifi-with-FON]] (600 root)
[connection] id=BTWifi-with-FON | type=802-11-wireless
[802-11-wireless] ssid=BTWifi-with-FON | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Oxford Free Wi-Fi]] (600 root)
[connection] id=Oxford Free Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=Oxford Free Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

      4   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TALKTALK-64CEEC' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-64CEEC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004cb6019de
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'virginmedia9011929' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"virginmedia9011929"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a04953d40a
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-with-FON' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f54823d83
                    Extra: Last beacon: 8ms ago
          Cell 04 - Address: <MAC 'BTHub5-7PH6' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-4 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-7PH6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f5480fc4b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BTWifi-X' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006f5481e830
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'DIRECT-71-HP ENVY 5640 series' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-71-HP ENVY 5640 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e45690522
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM070616-2G' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=30 dBm  
                    Encryption key:on
                    ESSID:"VM070616-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000137ca8932b
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VM578649-2G' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"VM578649-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dedab3f1a9
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'BTHub5-ZPXQ' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"BTHub5-ZPXQ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000013c56d180
                    Extra: Last beacon: 4180ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     C94095C986767A931B924EF
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
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
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     7410431A59C24B1BC33226E
depends:        
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     477882071593B10E01388C8
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
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
options iwlwifi 11n_disable=1

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
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   17.896887] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.163993] r8169 0000:02:00.0 eth0: link down
[   18.164048] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.879888] wlan0: authenticate with <MAC 'TALKTALK-64CEEC' [AC1]>
[   19.902637] wlan0: send auth to <MAC 'TALKTALK-64CEEC' [AC1]> (try 1/3)
[   19.906395] wlan0: authenticated
[   19.907048] wlan0: associate with <MAC 'TALKTALK-64CEEC' [AC1]> (try 1/3)
[   19.910763] wlan0: RX AssocResp from <MAC 'TALKTALK-64CEEC' [AC1]> (capab=0x431 status=0 aid=4)
[   19.910940] wlan0: associated
[   19.910986] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.866553] wlan0: deauthenticating from <MAC 'TALKTALK-64CEEC' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   20.897610] wlan0: authenticate with <MAC 'TALKTALK-64CEEC' [AC1]>
[   20.907836] wlan0: send auth to <MAC 'TALKTALK-64CEEC' [AC1]> (try 1/3)
[   20.910417] wlan0: authenticated
[   20.911067] wlan0: associate with <MAC 'TALKTALK-64CEEC' [AC1]> (try 1/3)
[   20.914791] wlan0: RX AssocResp from <MAC 'TALKTALK-64CEEC' [AC1]> (capab=0x431 status=0 aid=2)
[   20.914929] wlan0: associated

########## wireless info END ############

########## wireless info END ############


---

### Post by praseodym on 2015-12-01
Please run

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
```and reboot. Also change the encryption to pure WPA2-AES (CCMP) instead of mixed mode WPA/WPA2

---

### Post by joem2305 on 2015-12-01
Worked for a while but stopped working again (

---

### Post by jeremy31 on 2015-12-01
I wonder if a fix from another post will work for you. ```
gksudo gedit /etc/default/grub
```
Find the line that begins with GRUB_CMDLINE_LINUX_DEFAULT and add ```
iommu=soft
``` inside of the quotes, yours might look like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash iommu=soft
```
Save and exit gedit, then in terminal ```
sudo update-grub
```
Reboot

---

### Post by joem2305 on 2015-12-03
Well it certainly works better but still keeps cutting out

---

