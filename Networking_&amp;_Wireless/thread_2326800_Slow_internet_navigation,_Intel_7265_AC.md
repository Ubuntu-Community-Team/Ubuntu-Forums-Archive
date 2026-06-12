---
title: "Slow internet navigation, Intel 7265 AC"
date: 2016-06-04
forum: Networking &amp; Wireless
---

### Post by TuxManRemove on 2016-06-04
Hello, 
New installation of ubuntu, update and upgrade OS, but with firefox or Chromium, the internet navigation is slow.
How to optimize the WiFi settings?
Thanks!

```
##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5212]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1e4e:0110 Cubeternet
Bus 002 Device 002: ID 8087:0a2a Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3ec0:d94a:cfe0:224a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:26448 (26.4 KB)  TX bytes:10189 (10.1 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WiFi-F37E"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'WiFi-F37E' [AC1]>  
          Bit Rate=86.7 Mb/s   Tx-Power=22 dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       762     1  0 21:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WiFi-F37E
GENERAL.CON-UUID:                       64965904-6975-4a7e-a92b-c975946a4e7f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     86 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   64965904-6975-4a7e-a92b-c975946a4e7f | WiFi-F37E
IP4.ADDRESS[1]:                         192.168.1.82/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = laptop101
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1464981890
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.82
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::3ec0:d94a:cfe0:224a/64
IP6.GATEWAY:                            fe80::1

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:              
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
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

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  *
Sitecom9FB704  <MAC 'Sitecom9FB704' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Sitecom9FA37F  <MAC 'Sitecom9FA37F' [AC4]>  Infra  36    5180 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
WiFi-EC9B      <MAC 'WiFi-EC9B' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
WiFi-F37E      <MAC 'WiFi-F37E' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA1 WPA2  yes     *

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

[[/etc/NetworkManager/system-connections/Vpcwifi 1]] (600 root)
[connection] id=Vpcwifi 1 | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Vpcwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vpcwifi]] (600 root)
[connection] id=Vpcwifi | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vpcwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-F37E]] (600 root)
[connection] id=WiFi-F37E | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WiFi-F37E
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ONO0DB5]] (600 root)
[connection] id=ONO0DB5 | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ONO0DB5
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

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

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'WiFi-F37E' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"WiFi-F37E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002f071e651b9
                    Extra: Last beacon: 852ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Sitecom9FB704' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9FB704"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d905212dc1
                    Extra: Last beacon: 276ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WiFi-EC9B' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"WiFi-EC9B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002f06cbe99b4
                    Extra: Last beacon: 572ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Sitecom9FA37F' [AC4]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9FA37F"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000009d917747e75
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'WiFi-F0A0' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"WiFi-F0A0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001c50b9ee04a
                    Extra: Last beacon: 872ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Sitecom9461DC' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9461DC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000cb09591cb75
                    Extra: Last beacon: 548ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     B6288B9D0247B41459AB90D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     ADE77491D89FDFCBEBF6E35
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions
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
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions
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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.944730] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    3.956384] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.956535] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    4.025310] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.027111] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.505514] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.505706] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.584601] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.588565] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.772832] r8169 0000:01:00.0 enp1s0: link down
[    5.772873] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.885016] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   11.542485] wlp2s0: authenticate with <MAC 'WiFi-F37E' [AC1]>
[   11.547524] wlp2s0: send auth to <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   11.549827] wlp2s0: authenticated
[   11.553791] wlp2s0: associate with <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   11.559332] wlp2s0: RX AssocResp from <MAC 'WiFi-F37E' [AC1]> (capab=0x411 status=0 aid=7)
[   11.563035] wlp2s0: associated
[   11.563071] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   54.536545] wlp2s0: deauthenticating from <MAC 'WiFi-F37E' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   54.624788] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   54.765582] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[   54.765593] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[   54.765601] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[   54.766668] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[   54.767011] iwlwifi 0000:02:00.0: Unsupported splx structure
[   54.782985] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[   54.783136] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   54.846628] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   54.850265] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   54.874647] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   54.876774] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   54.958430] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   58.341935] wlp2s0: authenticate with <MAC 'WiFi-F37E' [AC1]>
[   58.345366] wlp2s0: send auth to <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   58.347078] wlp2s0: authenticated
[   58.348197] wlp2s0: associate with <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   58.354724] wlp2s0: RX AssocResp from <MAC 'WiFi-F37E' [AC1]> (capab=0x411 status=0 aid=7)
[   58.367090] wlp2s0: associated
[   58.367124] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
```

---

### Post by chili555 on 2016-06-05
First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
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

If these changes do not help, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=8
```If it helps, make it permanent:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Finally, you may get some improved performance with newer firmware:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware*.deb
```Reboot and tell us if your wireless has improved.

---

### Post by TuxManRemove on 2016-06-11
Hi @chilli555, sorry for the delay.

How do you see now?

This computer is new and devolcidad rate in all I do is test 10 or 12 mb / s
while another old laptop (5 years ago) the rate is 60 to 70MB / s
(The other computer uses Windows can not run this scritp)

Is there anything strange?

Thank you very much!

```

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:0123]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5212]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 1e4e:0110 Cubeternet 
Bus 002 Device 002: ID 8087:0a2a Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::3ec0:d94a:cfe0:224a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1719949 (1.7 MB)  TX bytes:108498 (108.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WiFi-F37E"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'WiFi-F37E' [AC1]>   
          Bit Rate=57.8 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:259   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       736     1  0 12:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WiFi-F37E
GENERAL.CON-UUID:                       64965904-6975-4a7e-a92b-c975946a4e7f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     57 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   64965904-6975-4a7e-a92b-c975946a4e7f | WiFi-F37E
IP4.ADDRESS[1]:                         192.168.1.82/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = laptop101
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.1.1
DHCP4.OPTION[11]:                       expiry = 1465726169
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.82
DHCP4.OPTION[17]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::3ec0:d94a:cfe0:224a/64
IP6.GATEWAY:                            fe80::1

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
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

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Sitecom9FB704  <MAC 'Sitecom9FB704' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Sitecom9FA37F  <MAC 'Sitecom9FA37F' [AC4]>  Infra  36    5180 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
WiFi-F37E      <MAC 'WiFi-F37E' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  43      &#9602;&#9604;__  WPA1 WPA2  yes     * 
WiFi-EC9B      <MAC 'WiFi-EC9B' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Vpcwifi 1]] (600 root)
[connection] id=Vpcwifi 1 | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Vpcwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vpcwifi]] (600 root)
[connection] id=Vpcwifi | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vpcwifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-F37E]] (600 root)
[connection] id=WiFi-F37E | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WiFi-F37E
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ONO0DB5]] (600 root)
[connection] id=ONO0DB5 | type=wifi | permissions=user:laptop:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ONO0DB5
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

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

enp1s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'WiFi-F37E' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WiFi-F37E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000039dbe1ea6ef
                    Extra: Last beacon: 656ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Sitecom9FB704' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9FB704"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a8652fc2db7
                    Extra: Last beacon: 4232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WiFi-EC9B' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"WiFi-EC9B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000039dbb367912
                    Extra: Last beacon: 4124ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Sitecom9FA37F' [AC4]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Sitecom9FA37F"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000a86669733ad
                    Extra: Last beacon: 3876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     B6288B9D0247B41459AB90D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     ADE77491D89FDFCBEBF6E35
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
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
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 5
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=8 power_save=0 power_level=5

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    3.683549] iwlwifi 0000:02:00.0: Unsupported splx structure
[    3.684077] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-19.ucode failed with error -2
[    3.684098] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-18.ucode failed with error -2
[    3.684111] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7265D-17.ucode failed with error -2
[    3.692858] iwlwifi 0000:02:00.0: loaded firmware version 16.242414.0 op_mode iwlmvm
[    3.805412] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    3.861140] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    3.861294] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    3.941266] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.942201] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.033131] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    5.708774] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.708947] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[    5.785072] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.788551] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    5.977576] r8169 0000:01:00.0 enp1s0: link down
[    5.977638] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[    6.145260] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   17.492546] wlp2s0: authenticate with <MAC 'WiFi-F37E' [AC1]>
[   17.496690] wlp2s0: send auth to <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   17.498428] wlp2s0: authenticated
[   17.499386] wlp2s0: associate with <MAC 'WiFi-F37E' [AC1]> (try 1/3)
[   17.503840] wlp2s0: RX AssocResp from <MAC 'WiFi-F37E' [AC1]> (capab=0x411 status=0 aid=8)
[   17.515931] wlp2s0: associated
[   17.515976] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


```

---

### Post by chili555 on 2016-06-11
> How do you see now?What I see is that your CRDA is still unset, although I suggested you set it.

I see that your router still runs in mixed WPA and WPA2 mode, even though I suggested you change it.

I see that the driver loaded the -16 version of the firmware, although I recommended that you install newer firmware which would have installed the newer -17 and -21 versions.

Please review and consider my suggestions above once again.

---

### Post by TuxManRemove on 2016-06-20
> **chili555 said:**
> What I see is that your CRDA is still unset, although I suggested you set it.

I see that your router still runs in mixed WPA and WPA2 mode, even though I suggested you change it.

I see that the driver loaded the -16 version of the firmware, although I recommended that you install newer firmware which would have installed the newer -17 and -21 versions.

Please review and consider my suggestions above once again.

Hello @Chili555
Sorry, I reinstalled the computer and thought I had the changes.
Now I am with personal problems, and really had no strength to continue with this, so I have been slow to respond.

I do not see that IS is set to regdomain 
What line should appear? 
I see other well.
Hoy you see?

Thanks

```
 
Distributor ID:    Ubuntu 
Description:    Ubuntu 16.04 LTS 
Release:    16.04 
Codename:    xenial 
 
##### kernel ############################ 
 
Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux 
 
Parameters: ro, quiet, splash, vt.handoff=7 
 
##### desktop ########################### 
 
Ubuntu 
 
##### lspci ############################# 
 
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05) 
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:0123] 
    Kernel driver in use: r8169 
 
02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59) 
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5212] 
    Kernel driver in use: iwlwifi 
 
##### lsusb ############################# 
 
Bus 001 Device 002: ID 8087:8001 Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub 
Bus 002 Device 003: ID 1e4e:0110 Cubeternet  
Bus 002 Device 002: ID 8087:0a2a Intel Corp.  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 
##### PCMCIA card info ################## 
 
##### rfkill ############################ 
 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
3: hci0: Bluetooth 
    Soft blocked: yes 
    Hard blocked: no 
 
##### lsmod ############################# 
 
iwlmvm                311296  0 
mac80211              737280  1 iwlmvm 
snd_soc_rt5640        114688  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640 
iwlwifi               200704  1 iwlmvm 
snd_soc_core          212992  2 snd_soc_rt5640,snd_soc_ssm4567 
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm 
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core 
 
##### interfaces ######################## 
 
auto lo 
iface lo inet loopback 
 
##### ifconfig ########################## 
 
enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>   
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::e95a:ad50:4cae:7a91/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:213132 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:73611 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:280627079 (280.6 MB)  TX bytes:63641191 (63.6 MB) 
 
##### iwconfig ########################## 
 
lo        no wireless extensions. 
 
enp1s0    no wireless extensions. 
 
wlp2s0    IEEE 802.11abgn  ESSID:"CASAL4"   
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC 'CASAL4' [AN2]>    
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm    
          Retry short limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:on 
          Link Quality=55/70  Signal level=-55 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:43   Missed beacon:0 
 
##### route ############################# 
 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0 
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0 
 
##### resolv.conf ####################### 
 
nameserver 127.0.1.1 
search mundo-R.com 
 
##### network managers ################## 
 
Installed: 
 
    NetworkManager 
 
Running: 
 
root       734     1  0 Jun16 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon 
 
##### NetworkManager info ############### 
 
GENERAL.DEVICE:                         wlp2s0 
GENERAL.TYPE:                           wifi 
GENERAL.NM-TYPE:                        NMDeviceWifi 
GENERAL.VENDOR:                         Intel Corporation 
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265) 
GENERAL.DRIVER:                         iwlwifi 
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic 
GENERAL.FIRMWARE-VERSION:               19.313137.0 
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]> 
GENERAL.MTU:                            0 
GENERAL.STATE:                          100 (connected) 
GENERAL.REASON:                         0 (No reason given) 
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlp2s0 
GENERAL.IP-IFACE:                       wlp2s0 
GENERAL.IS-SOFTWARE:                    no 
GENERAL.NM-MANAGED:                     yes 
GENERAL.AUTOCONNECT:                    yes 
GENERAL.FIRMWARE-MISSING:               no 
GENERAL.NM-PLUGIN-MISSING:              no 
GENERAL.PHYS-PORT-ID:                   -- 
GENERAL.CONNECTION:                     CASAL4 
GENERAL.CON-UUID:                       935f6f01-a371-415b-b128-d781cdf6800c 
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7 
GENERAL.METERED:                        no (guessed) 
CAPABILITIES.CARRIER-DETECT:            no 
CAPABILITIES.SPEED:                     36 Mb/s 
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5,6} 
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   935f6f01-a371-415b-b128-d781cdf6800c | CASAL4 
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   4694aeb2-2824-42ae-abc6-b247c40063ba | CASAL-B 
IP4.ADDRESS[1]:                         192.168.0.19/24 
IP4.GATEWAY:                            192.168.0.1 
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000 
IP4.DNS[1]:                             213.60.205.175 
IP4.DNS[2]:                             213.60.205.173 
IP4.DNS[3]:                             212.51.32.254 
IP4.DOMAIN[1]:                          mundo-R.com 
DHCP4.OPTION[1]:                        requested_subnet_mask = 1 
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1 
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0 
DHCP4.OPTION[4]:                        domain_name_servers = 213.60.205.175 213.60.205.173 212.51.32.254 
DHCP4.OPTION[5]:                        ip_address = 192.168.0.19 
DHCP4.OPTION[6]:                        requested_static_routes = 1 
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1 
DHCP4.OPTION[8]:                        default_ip_ttl = 64 
DHCP4.OPTION[9]:                        requested_time_offset = 1 
DHCP4.OPTION[10]:                       time_offset = 0 
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255 
DHCP4.OPTION[12]:                       requested_interface_mtu = 1 
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1 
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150 
DHCP4.OPTION[15]:                       dhcp_message_type = 5 
DHCP4.OPTION[16]:                       requested_broadcast_address = 1 
DHCP4.OPTION[17]:                       routers = 192.168.0.1 
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800 
DHCP4.OPTION[19]:                       requested_domain_name = 1 
DHCP4.OPTION[20]:                       domain_name = mundo-R.com 
DHCP4.OPTION[21]:                       requested_routers = 1 
DHCP4.OPTION[22]:                       expiry = 1466242774 
DHCP4.OPTION[23]:                       requested_wpad = 1 
DHCP4.OPTION[24]:                       requested_netbios_scope = 1 
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1 
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1 
DHCP4.OPTION[27]:                       network_number = 192.168.0.0 
DHCP4.OPTION[28]:                       requested_domain_search = 1 
DHCP4.OPTION[29]:                       requested_ntp_servers = 1 
DHCP4.OPTION[30]:                       next_server = 192.168.0.1 
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600 
DHCP4.OPTION[32]:                       requested_host_name = 1 
IP6.ADDRESS[1]:                         fe80::e95a:ad50:4cae:7a91/64 
IP6.GATEWAY:                             
 
GENERAL.DEVICE:                         enp1s0 
GENERAL.TYPE:                           ethernet 
GENERAL.NM-TYPE:                        NMDeviceEthernet 
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd. 
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller 
GENERAL.DRIVER:                         r8169 
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI 
GENERAL.FIRMWARE-VERSION:                
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]> 
GENERAL.MTU:                            1500 
GENERAL.STATE:                          20 (unavailable) 
GENERAL.REASON:                         2 (Device is now managed) 
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0 
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
 
SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  *  
wificlientesR  <MAC 'wificlientesR' [AN1]>  Infra  4     2427 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 802.1X  no         
CASAL4         <MAC 'CASAL4' [AN2]>  Infra  4     2427 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA1 WPA2         yes     *  
--             <MAC '--' [AN3]>  Infra  4     2427 MHz  54 Mbit/s  49      &#9602;&#9604;__  --                no         
MOVISTAR_06C8  <MAC 'MOVISTAR_06C8' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2              no         
CASAL5         <MAC 'CASAL5' [AN5]>  Infra  48    5240 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2         no         
GAROTOS        <MAC 'GAROTOS' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2         no         
CASAL-B        <MAC 'CASAL-B' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2         no         
MAR            <MAC 'MAR' [AN8]>  Infra  9     2452 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2         no         
R-wlan87       <MAC 'R-wlan87' [AN9]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no         
 
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
 
[[/etc/NetworkManager/system-connections/CASAL-B]] (600 root) 
[connection] id=CASAL-B | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=CASAL-B 
[ipv4] method=auto 
[ipv6] method=auto 
 
[[/etc/NetworkManager/system-connections/Vpcwifi 1]] (600 root) 
[connection] id=Vpcwifi 1 | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Vpcwifi 
[ipv4] method=auto 
[ipv6] method=auto 
 
[[/etc/NetworkManager/system-connections/Vpcwifi]] (600 root) 
[connection] id=Vpcwifi | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vpcwifi 
[ipv4] method=auto 
[ipv6] method=auto 
 
[[/etc/NetworkManager/system-connections/WiFi-F37E]] (600 root) 
[connection] id=WiFi-F37E | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=WiFi-F37E 
[ipv4] method=auto 
[ipv6] method=auto 
 
[[/etc/NetworkManager/system-connections/ONO0DB5]] (600 root) 
[connection] id=ONO0DB5 | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ONO0DB5 
[ipv4] method=auto 
[ipv6] method=auto 
 
[[/etc/NetworkManager/system-connections/CASAL4]] (600 root) 
[connection] id=CASAL4 | type=wifi | permissions=user:slimbook:; 
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=CASAL4 
[ipv4] method=auto 
[ipv6] method=auto 
 
##### iw reg get ######################## 
 
Region: Europe/Madrid (based on set time zone) 
 
country 00: DFS-UNSET 
    (2402 - 2472 @ 40), (6, 20), (N/A) 
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN 
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN 
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN 
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN 
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN 
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN 
    (57240 - 63720 @ 2160), (N/A, 0), (N/A) 
 
##### iwlist channels ################### 
 
lo        no frequency information. 
 
enp1s0    no frequency information. 
 
wlp2s0    32 channels in total; available frequencies : 
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
          Current Frequency:2.427 GHz (Channel 4) 
 
##### iwlist scan ####################### 
 
lo        Interface doesn't support scanning. 
 
enp1s0    Interface doesn't support scanning. 
 
wlp2s0    Interface doesn't support scanning : Device or resource busy 
 
##### module infos ###################### 
 
[iwlmvm] 
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko 
license:        GPL 
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com> 
description:    The new Intel(R) wireless AGN driver for Linux 
srcversion:     49DC02934CB3D8C312FF8E1 
depends:        iwlwifi,mac80211,cfg80211 
intree:         Y 
vermagic:       4.4.0-24-generic SMP mod_unload modversions  
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool) 
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int) 
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool) 
 
[mac80211] 
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko 
license:        GPL 
description:    IEEE 802.11 subsystem 
srcversion:     2FFAEED0245CA1D97FE1E44 
depends:        cfg80211 
intree:         Y 
vermagic:       4.4.0-24-generic SMP mod_unload modversions  
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool) 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int) 
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int) 
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int) 
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int) 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp) 
 
[iwlwifi] 
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
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
firmware:       iwlwifi-7265D-13.ucode 
firmware:       iwlwifi-7265-13.ucode 
firmware:       iwlwifi-3160-13.ucode 
firmware:       iwlwifi-7260-13.ucode 
firmware:       iwlwifi-8000-13.ucode 
srcversion:     651BF6CBF283F6F817B8F3A 
depends:        cfg80211 
intree:         Y 
vermagic:       4.4.0-24-generic SMP mod_unload modversions  
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
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko 
description:    wireless configuration support 
license:        GPL 
author:         Johannes Berg 
srcversion:     25A45701AAA64DAC1E47D9D 
depends:         
intree:         Y 
vermagic:       4.4.0-24-generic SMP mod_unload modversions  
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
11n_disable: 8 
amsdu_size_8K: 0 
antenna_coupling: 0 
bt_coex_active: Y 
d0i3_disable: Y 
fw_monitor: N 
fw_restart: Y 
lar_disable: N 
led_mode: 0 
nvm_file: (null) 
power_level: 5 
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
 
[/etc/modprobe.d/intel-microcode-blacklist.conf] 
blacklist microcode 
 
[/etc/modprobe.d/iwlwifi.conf] 
remove iwlwifi \ 
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \ 
&& /sbin/modprobe -r mac80211 
options iwlwifi 11n_disable=8 power_save=0 power_level=5 
 
[/etc/modprobe.d/mlx4.conf] 
softdep mlx4_core post: mlx4_en 
 
##### rc.local ########################## 
 
exit 0 
 
##### pm-utils ########################## 
 
##### udev rules ######################## 
 
grep: /etc/udev/rules.d/*net*.rules: No such file or directory 
 
##### dmesg ############################# 
 
[ 2843.632200] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio. 
[ 2843.821417] r8169 0000:01:00.0 enp1s0: link down 
[ 2844.978308] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq 
[ 2845.256915] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready 
[ 2845.257167] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times) 
[ 2845.276309] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated 
[ 2845.317771] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times) 
[ 2845.338689] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready 
[ 2845.340198] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready 
[ 2845.525290] r8169 0000:01:00.0 enp1s0: link down 
[ 2845.525341] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready 
[ 2845.576579] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready 
[ 2848.923256] wlp2s0: authenticate with <MAC 'CASAL4' [AN2]> 
[ 2848.927719] wlp2s0: send auth to <MAC 'CASAL4' [AN2]> (try 1/3) 
[ 2848.929571] wlp2s0: authenticated 
[ 2848.930683] wlp2s0: associate with <MAC 'CASAL4' [AN2]> (try 1/3) 
[ 2848.934709] wlp2s0: RX AssocResp from <MAC 'CASAL4' [AN2]> (capab=0x1411 status=0 aid=6) 
[ 2848.935643] wlp2s0: associated 
[ 2848.935682] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready 
 


```

---

### Post by chili555 on 2016-06-20
I am sorry you are having problems. I hope evrything will work out well for you.

Let's try to get the CRDA setting corrected. What do these terminal commands tell us?```
sudo iw reg get
```And also:```
cat /etc/default/crda
```Your wireless script suggests you are in Spain:> ##### iw reg get ######################## 
 
Region: Europe/Madrid (based on set time zone) Is that correct? If so, let's set your CRDA. ```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=ES
```Proofread carefully, save and close the text editor.

Next, I'd like to try newer firmware. With a working internet connection, open a terminal and do:```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware*.deb

```Reboot and tell us if your wireless is now working correctly.

---

### Post by TuxManRemove on 2016-06-23
Hello,
Thanks,
I do it.

With LAN cable the result of speed test is 143 Mbs
With wifi, the result is 18 to 20 Mb

---

### Post by chili555 on 2016-06-24
Assuming that you did all the things I recommended above, then I think we have reached the limits of the device and driver combination. I regret that I have no other suggestions.

---

### Post by TuxManRemove on 2016-06-25
> **chili555 said:**
> Assuming that you did all the things I recommended above, then I think we have reached the limits of the device and driver combination. I regret that I have no other suggestions.

Hello,
Thanks for your time.
One last question, I turned on the router the wifi  5Ghz with another name SSID and I turn off the 2.4Ghz.
But the computer can not find the new 5Ghz network.
Should we do something in the linux setup to work in 5Ghz?
Thank you

---

### Post by chili555 on 2016-06-25
Does your Intel support 5 gHz? Not all do, including mine. Find out with:```
iw list
```Here is the response from my card:```
Frequencies:
			* 2412 MHz [1] (22.0 dBm)
			* 2417 MHz [2] (22.0 dBm)
			* 2422 MHz [3] (22.0 dBm)
			* 2427 MHz [4] (22.0 dBm)
			* 2432 MHz [5] (22.0 dBm)
			* 2437 MHz [6] (22.0 dBm)
			* 2442 MHz [7] (22.0 dBm)
			* 2447 MHz [8] (22.0 dBm)
			* 2452 MHz [9] (22.0 dBm)
			* 2457 MHz [10] (22.0 dBm)
			* 2462 MHz [11] (22.0 dBm)
			* 2467 MHz [12] (disabled)
			* 2472 MHz [13] (disabled)
```As you see, there is no 5 gHz.

---

### Post by TuxManRemove on 2016-06-25
Hello,
I do not understand well this:

```
 iw list
Wiphy phy0
    max # scan SSIDs: 20
    max scan IEs length: 439 bytes
    Retry short limit: 7
    Retry long limit: 4
    Coverage class: 0 (up to 0m)
    Device supports RSN-IBSS.
    Device supports AP-side u-APSD.
    Supported Ciphers:
        * WEP40 (00-0f-ac:1)
        * WEP104 (00-0f-ac:5)
        * TKIP (00-0f-ac:2)
        * CCMP (00-0f-ac:4)
        * CMAC (00-0f-ac:6)
    Available Antennas: TX 0 RX 0
    Supported interface modes:
         * IBSS
         * managed
         * AP
         * AP/VLAN
         * monitor
         * P2P-client
         * P2P-GO
         * P2P-device
    Band 1:
        Capabilities: 0x11e3
            RX LDPC
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-15
        Bitrates (non-HT):
            * 1.0 Mbps
            * 2.0 Mbps (short preamble supported)
            * 5.5 Mbps (short preamble supported)
            * 11.0 Mbps (short preamble supported)
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 2412 MHz [1] (20.0 dBm)
            * 2417 MHz [2] (20.0 dBm)
            * 2422 MHz [3] (20.0 dBm)
            * 2427 MHz [4] (20.0 dBm)
            * 2432 MHz [5] (20.0 dBm)
            * 2437 MHz [6] (20.0 dBm)
            * 2442 MHz [7] (20.0 dBm)
            * 2447 MHz [8] (20.0 dBm)
            * 2452 MHz [9] (20.0 dBm)
            * 2457 MHz [10] (20.0 dBm)
            * 2462 MHz [11] (20.0 dBm)
            * 2467 MHz [12] (20.0 dBm) (no IR)
            * 2472 MHz [13] (20.0 dBm) (no IR)
    Band 2:
        Capabilities: 0x11e3
            RX LDPC
            HT20/HT40
            Static SM Power Save
            RX HT20 SGI
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 4 usec (0x05)
        HT TX/RX MCS rate indexes supported: 0-15
        Bitrates (non-HT):
            * 6.0 Mbps
            * 9.0 Mbps
            * 12.0 Mbps
            * 18.0 Mbps
            * 24.0 Mbps
            * 36.0 Mbps
            * 48.0 Mbps
            * 54.0 Mbps
        Frequencies:
            * 5180 MHz [36] (20.0 dBm) (no IR)
            * 5200 MHz [40] (20.0 dBm) (no IR)
            * 5220 MHz [44] (20.0 dBm) (no IR)
            * 5240 MHz [48] (20.0 dBm) (no IR)
            * 5260 MHz [52] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5280 MHz [56] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5300 MHz [60] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5320 MHz [64] (20.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5500 MHz [100] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5520 MHz [104] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5540 MHz [108] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5560 MHz [112] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5580 MHz [116] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5600 MHz [120] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5620 MHz [124] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5640 MHz [128] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5660 MHz [132] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5680 MHz [136] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5700 MHz [140] (22.0 dBm) (no IR, radar detection)
              DFS state: usable (for 126 sec)
              DFS CAC time: 60000 ms
            * 5720 MHz [144] (disabled)
            * 5745 MHz [149] (disabled)
            * 5765 MHz [153] (disabled)
            * 5785 MHz [157] (disabled)
            * 5805 MHz [161] (disabled)
            * 5825 MHz [165] (disabled)
    Supported commands:
         * new_interface
         * set_interface
         * new_key
         * start_ap
         * new_station
         * new_mpath
         * set_mesh_config
         * set_bss
         * authenticate
         * associate
         * deauthenticate
         * disassociate
         * join_ibss
         * join_mesh
         * remain_on_channel
         * set_tx_bitrate_mask
         * frame
         * frame_wait_cancel
         * set_wiphy_netns
         * set_channel
         * set_wds_peer
         * start_sched_scan
         * probe_client
         * set_noack_map
         * register_beacons
         * start_p2p_device
         * set_mcast_rate
         * channel_switch
         * Unknown command (104)
         * Unknown command (105)
         * connect
         * disconnect
    Supported TX frame types:
         * IBSS: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * managed: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * AP/VLAN: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * mesh point: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-client: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-GO: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
         * P2P-device: 0x00 0x10 0x20 0x30 0x40 0x50 0x60 0x70 0x80 0x90 0xa0 0xb0 0xc0 0xd0 0xe0 0xf0
    Supported RX frame types:
         * IBSS: 0x40 0xb0 0xc0 0xd0
         * managed: 0x40 0xd0
         * AP: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * AP/VLAN: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * mesh point: 0xb0 0xc0 0xd0
         * P2P-client: 0x40 0xd0
         * P2P-GO: 0x00 0x20 0x40 0xa0 0xb0 0xc0 0xd0
         * P2P-device: 0x40 0xd0
    WoWLAN support:
         * wake up on disconnect
         * wake up on magic packet
         * wake up on pattern match, up to 20 patterns of 16-128 bytes,
           maximum packet offset 0 bytes
         * can do GTK rekeying
         * wake up on GTK rekey failure
         * wake up on EAP identity request
         * wake up on 4-way handshake
         * wake up on rfkill release
         * wake up on TCP connection
    software interface modes (can always be added):
         * AP/VLAN
         * monitor
    valid interface combinations:
         * #{ managed } <= 1, #{ AP, P2P-client, P2P-GO } <= 1, #{ P2P-device } <= 1,
           total <= 3, #channels <= 2
    HT Capability overrides:
         * MCS: ff ff ff ff ff ff ff ff ff ff
         * maximum A-MSDU length
         * supported channel width
         * short GI for 40 MHz
         * max A-MPDU length exponent
         * min MPDU start spacing
    Device supports TX status socket option.
    Device supports HT-IBSS.
    Device supports SAE with AUTHENTICATE command
    Device supports low priority scan.
    Device supports scan flush.
    Device supports per-vif TX power setting
    P2P GO supports CT window setting
    P2P GO supports opportunistic powersave setting
    Driver supports a userspace MPM
    Device supports static SMPS
    Device supports dynamic SMPS

```

---

### Post by TuxManRemove on 2016-06-26
> **chili555 said:**
> Does your Intel support 5 gHz? Not all do, including mine. Find out with:```
iw list
```Here is the response from my card:```
Frequencies:
            * 2412 MHz [1] (22.0 dBm)
            * 2417 MHz [2] (22.0 dBm)
            * 2422 MHz [3] (22.0 dBm)
            * 2427 MHz [4] (22.0 dBm)
            * 2432 MHz [5] (22.0 dBm)
            * 2437 MHz [6] (22.0 dBm)
            * 2442 MHz [7] (22.0 dBm)
            * 2447 MHz [8] (22.0 dBm)
            * 2452 MHz [9] (22.0 dBm)
            * 2457 MHz [10] (22.0 dBm)
            * 2462 MHz [11] (22.0 dBm)
            * 2467 MHz [12] (disabled)
            * 2472 MHz [13] (disabled)
```As you see, there is no 5 gHz.

Hello @chili555, 
Viewing these data, the driver supports it, right?

 * 5180 MHz [36] (20.0 dBm) (no IR)
 * 5200 MHz [40] (20.0 dBm) (no IR)
 * 5220 MHz [44] (20.0 dBm) (no IR)
 * 5240 MHz [48] (20.0 dBm) (no IR)

---

