---
title: "No iwlwifi with Network controller: Intel Corp. Device (rev 78) on 64-bit 16.04"
date: 2017-04-07
forum: Networking &amp; Wireless
---

### Post by KorkytheKat on 2017-04-07
Installed Ubuntu 64-bit Ubuntu 16.04 on a new Intel machine using the amd64 iso.

**Problem: Internet connection broke during install, and is very slow and frail in the installed system (haven't even been able to update my package lists)**

o/p of lspci

```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 06)
00:08.0 System peripheral: Intel Corporation Sky Lake Gaussian Mixture Model
00:14.0 USB controller: Intel Corporation Device a2af
00:16.0 Communication controller: Intel Corporation Device a2ba
00:17.0 SATA controller: Intel Corporation Device a282
00:1b.0 PCI bridge: Intel Corporation Device a2e9 (rev f0)
00:1b.4 PCI bridge: Intel Corporation Device a2eb (rev f0)
00:1c.0 PCI bridge: Intel Corporation Device a292 (rev f0)
00:1c.4 PCI bridge: Intel Corporation Device a294 (rev f0)
00:1c.5 PCI bridge: Intel Corporation Device a295 (rev f0)
00:1c.6 PCI bridge: Intel Corporation Device a296 (rev f0)
00:1c.7 PCI bridge: Intel Corporation Device a297 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Device a298 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a2c4
00:1f.2 Memory controller: Intel Corporation Device a2a1
00:1f.3 Audio device: Intel Corporation Device a2f0
00:1f.4 SMBus: Intel Corporation Device a2a3
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (2) I219-V
04:00.0 Ethernet controller: Intel Corporation I211 Gigabit Network Connection (rev 03)
05:00.0 Network controller: Intel Corporation Device 24fd (rev 78)
08:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd Device a804

```

Ran the wireless-info script as advised:

```


########## wireless info START ##########

Report from: 07 Apr 2017 14:00 BST +0100

Booted last: 07 Apr 2017 00:00 BST +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.14-040814-generic #201612101431 SMP Sat Dec 10 19:33:51 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I219-V [1458:e000]
    Kernel driver in use: e1000e

04:00.0 Ethernet controller [0200]: Intel Corporation I211 Gigabit Network Connection [8086:1539] (rev 03)
    Subsystem: Gigabyte Technology Co., Ltd I211 Gigabit Network Connection [1458:e000]
    Kernel driver in use: igb

05:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2b Intel Corp. 
Bus 001 Device 004: ID 1c4f:0026 SiGma Micro Keyboard
Bus 001 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 007: ID 13fe:1f21 Kingston Technology Company Inc. 
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

iwlmvm                360448  0
mac80211              757760  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              581632  3 iwlmvm,iwlwifi,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s31f6 Link encap:Ethernet  HWaddr <MAC 'enp0s31f6' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f7300000-f7320000 

enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f7200000-f721ffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1550 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:126674 (126.6 KB)  TX bytes:126674 (126.6 KB)

wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1134 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1601 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:878296 (878.2 KB)  TX bytes:201791 (201.7 KB)

##### iwconfig ##########################

enp4s0    no wireless extensions.

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       806     1  0 10:58 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.8.14-040814-generic
GENERAL.FIRMWARE-VERSION:               22.361476.0
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,0,2,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   698f6959-831a-45ab-932a-af5e436b2e23 | ECwifi
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   17f24a89-b12b-4a1e-993e-2162d9b4caa9 | SKY45449 2
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   ae63c3c7-1660-4b96-92f7-7ae5279a810e | SKY45449 3
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   1d2834f6-c563-4c31-806d-3ed6e221f712 | SKY45449 5

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        I211 Gigabit Network Connection
GENERAL.DRIVER:                         igb
GENERAL.DRIVER-VERSION:                 5.3.0-k
GENERAL.FIRMWARE-VERSION:                0. 6-1
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
SKY45449  <MAC 'SKY45449' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
ECwifi    <MAC 'ECwifi' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/SKY45449 2]] (600 root)
[connection] id=SKY45449 2 | type=wifi | permissions=user:azed:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SKY45449
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKY45449 3]] (600 root)
[connection] id=SKY45449 3 | type=wifi | permissions=user:azed:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SKY45449
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKY45449]] (600 root)
[connection] id=SKY45449 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SKY45449
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKY45449 5]] (600 root)
[connection] id=SKY45449 5 | type=wifi | permissions=user:azed:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SKY45449
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ECwifi]] (600 root)
[connection] id=ECwifi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=ECwifi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp4s0    no frequency information.

enp0s31f6  no frequency information.

lo        no frequency information.

wlp5s0    32 channels in total; available frequencies :
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

enp4s0    Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)

wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'SKY45449' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKY45449"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029d22f4eb6
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ECwifi' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"ECwifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005f9a6928196
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.8.14-040814-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     8CB024DCE8CBAD06752D324
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.8.14-040814-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.8.14-040814-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.14-040814-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.8.14-040814-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-IWL6000G2B_UCODE_API_MAX.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-24.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-24.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-24.ucode
firmware:       iwlwifi-8000C--24.ucode
firmware:       iwlwifi-9260-th-a0-lc-a0--24.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--24.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--24.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--24.ucode
srcversion:     E7651FD3D9AF45F96CD8B2E
depends:        cfg80211
intree:         Y
vermagic:       4.8.14-040814-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.8.14-040814-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.14-040814-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[ 2284.264792] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[ 2309.114992] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2309.121873] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2309.190410] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 2/3)
[ 2309.250575] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 3/3)
[ 2309.255267] wlp5s0: aborting authentication with <MAC 'SKY45449' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2309.264295] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[ 2718.010620] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2718.015971] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2718.064119] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 2/3)
[ 2718.065824] wlp5s0: authenticated
[ 2718.070002] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2718.130303] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2718.133083] wlp5s0: associated
[ 2718.133152] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[ 2742.466360] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2742.472742] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2742.479973] wlp5s0: authenticated
[ 2742.482567] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2742.558599] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 2/3)
[ 2742.587565] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2742.590705] wlp5s0: associated
[ 2760.886139] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2760.894004] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2760.899933] wlp5s0: authenticated
[ 2760.907084] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2760.994615] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 2/3)
[ 2761.023800] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2761.025648] wlp5s0: associated
[ 2764.295341] wlp5s0: deauthenticating from <MAC 'SKY45449' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2765.894796] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2765.900983] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2765.913354] wlp5s0: authenticated
[ 2765.915254] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2765.923273] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2765.924744] wlp5s0: associated
[ 2788.141474] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2788.147759] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2788.152116] wlp5s0: authenticated
[ 2788.155923] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2788.236386] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 2/3)
[ 2788.319527] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2788.321140] wlp5s0: associated
[ 2808.115651] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2808.122004] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2808.124163] wlp5s0: authenticated
[ 2808.128486] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2808.132592] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2808.134315] wlp5s0: associated
[ 2812.293797] wlp5s0: deauthenticating from <MAC 'SKY45449' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2814.003861] wlp5s0: authenticate with <MAC 'SKY45449' [AC1]>
[ 2814.010598] wlp5s0: send auth to <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2814.016587] wlp5s0: authenticated
[ 2814.020704] wlp5s0: associate with <MAC 'SKY45449' [AC1]> (try 1/3)
[ 2814.052354] wlp5s0: RX AssocResp from <MAC 'SKY45449' [AC1]> (capab=0x411 status=0 aid=4)
[ 2814.054586] wlp5s0: associated
[ 2821.999730] wlp5s0: deauthenticating from <MAC 'SKY45449' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

Following a suggestion, here:

[http://askubuntu.com/questions/858546/wifi-not-working-intel-on-hp-spectre-x360-13](http://askubuntu.com/questions/858546/wifi-not-working-intel-on-hp-spectre-x360-13)

I have tried installing a new kernel (4.8) and new firmware (linux-firmware_1.162_all.deb), but to no good effect.

**All solution ideas gratefully received.**

---

### Post by kc1di on 2017-04-08
Hello KorkytheKat and Welcome to Ubuntu,
Try this see if it helps 
In a terminal copy and paste this command and hit enter.```
sudo echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Then reboot and see if it's working for you. 
if this is a HP machine you may also have to blacklist the wmi module like this: ```
sudo echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
good luck

---

### Post by chili555 on 2017-04-08
> **kc1di said:**
> Hello KorkytheKat and Welcome to Ubuntu,
Try this see if it helps 
In a terminal copy and paste this command and hit enter.```
sudo echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Then reboot and see if it's working for you. 
if this is a HP machine you may also have to blacklist the wmi module like this: ```
sudo echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
good luckWhy do think acer-wmi is loaded? According to the wireless script, there are no hard or soft blocks.

---

### Post by chili555 on 2017-04-08
I notice this:> wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'SKY45449' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    [COLOR="#FF0000"]Quality=27/70[/COLOR]  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"SKY45449"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000029d22f4eb6
                    Extra: Last beacon: 1048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR="#FF0000"]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSKIs this a machine you built or a wireless card you installed? I wonder if the antenna wires are connected securely.

As well, please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Then set your regulatory domain explicitly. Check yours:```
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

---

### Post by KorkytheKat on 2017-04-09
Thanks for the replies, kc1di and chili555, which did help

I'm almost too ashamed to continue with this post. (sigh) It's the old story: "First make sure your computer is plugged in."

Started with kc1di's top solution:

sudo echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf 

and then reboot.

Zip, belly-up.

It seemed to me that my problem was one of very weak signal strength (1 Mb/s cf 54Mb/s with my Samsung N110 netbook) - something that chili555 also flagged-up.

I noted, too, what chili said about my router. I should explain, here, that I am in a house-share, and the router is in another part of the house. This added to my fears about signal-strength.

Finally, chili picked-up that my computer was custom-built, which it is, but not by me; by these people:

[https://www.quietpc.com](https://www.quietpc.com)

It's their Sentinel fanless model.

It seemed to me that there were two possibilities:

1. Hardware problem -> e.g., loose wire

Or, and this is the possibility that I am ashamed to say that I considered more likely:

2. a Software problem -> e.g., wrong driver or something.

Handily, my machine was delivered with all the specs / handbooks for its separate components (all in their original boxes).

I opened the "motherboard" box, which was sealed, hoping to get more info about the wireless card. The seal on the box read: "Don't throw this box away, you may need its contents if you upgrade your system."

I dug around inside the box. It mainly contained booklets and leads, but there was also something else: a small rod, with a base attached. There was a lead coming out of the back of the base - a lead which terminated in a couple of male screw-in brass plugs. The rod had the word "Gigabyte" imprinted on it. With a wild surmise, I grasped that the object that I had in my hand was an aerial! (I'm quick like that). I had another look at my computer. There were two female brass sockets on the back, which seemed to exactly match the plugs on the aerial.

I plugged it in. Result: instant full-strength Internet.

Bit of a classic, eh?

Sorry to waste your time.

Hang-on, maybe it wasn't wasted. Important lessons:

1. Ubuntu software works

2. The simplest solution - e.g. plugging the computer in - often works, no matter how dumb it may seem

3. The software would have worked "out of the box" if I had had my aerial plugged-in - I checked with my live USB-install. All my solution efforts added nothing.

I am re-installing to clear up the mess I've made.

Thanks again.

---

### Post by KorkytheKat on 2017-04-09
Sorry, I should have added the "solved"-tag

---

### Post by kc1di on 2017-04-09
Congratulations of finding the problem - I too often jump to software or config problems. 
But glad you discovered the problem and fixed it , Cheers!

---

### Post by chili555 on 2017-04-09
It wasn't a waste of time at all. It is a reminder to all of us to first check the physical layer and that sometimes important clues about it can be read from the wireless script. I actually enjoy catching these clues, often seeing what a few of my colleagues missed!

I can assure you that someday, a searcher will find this thread, check his scan results and find that he, too, needs to secure the antennae! 

I am glad it's working by whatever means.

---

