---
title: "Atheros AR9462 wifi restarts network manager every few seconds"
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by stianlagstad on 2016-01-22
Ubuntu 15.10 on an Acer aspire v3-571g. Wireless on windows7 on the same machine works great. Ethernet works, but only when wifi is disabled. If I enable wifi, then it looks as though network manager restarts every second or every other second. I've tried using WICD instead of network-manager, but was unable to find any wireless networks then.

Any ideas?

Wireless info:
```



########## wireless info START ##########


Report from: 22 Jan 2016 10:23 CET +0100


Booted last: 22 Jan 2016 00:00 CET +0100


Script from: 30 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-25-generic #30-Ubuntu SMP Mon Jan 18 12:31:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0647]
    Kernel driver in use: tg3


03:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 003 Device 003: ID 04ca:3006 Lite-On Technology Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 002: ID 0461:4e22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath3k                  20480  0
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
bluetooth             516096  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
mac80211              733184  1 ath9k
cfg80211              548864  4 ath,ath9k_common,ath9k,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0f0  Link encap:Ethernet  HWaddr <MAC 'enp2s0f0' [IF]>  
          inet addr:10.54.216.138  Bcast:10.54.216.255  Mask:255.255.255.0
          inet6 addr: fe80::ba88:e3ff:feaa:4467/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4374594 (4.3 MB)  TX bytes:584313 (584.3 KB)
          Interrupt:16 


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp2s0f0  no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.54.216.1     0.0.0.0         UG    100    0        0 enp2s0f0
10.54.216.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f0
10.184.12.107   10.54.216.1     255.255.255.255 UGH   100    0        0 enp2s0f0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f0


##### resolv.conf #######################


nameserver 127.0.1.1
search helsesorost.guest


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0f0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM57785 Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               sb
GENERAL.HWADDR:                         <MAC 'enp2s0f0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0f0
GENERAL.IP-IFACE:                       enp2s0f0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       f8678bbd-c5c2-4c0b-ba85-411fb191b0e1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f8678bbd-c5c2-4c0b-ba85-411fb191b0e1 | Wired connection 1
IP4.ADDRESS[1]:                         10.54.216.138/24
IP4.GATEWAY:                            10.54.216.1
IP4.ROUTE[1]:                           dst = 10.184.12.107/32, nh = 10.54.216.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
IP4.DOMAIN[1]:                          helsesorost.guest
DHCP4.OPTION[1]:                        network_number = 10.54.216.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1453483031
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       domain_name = helsesorost.guest
DHCP4.OPTION[12]:                       broadcast_address = 10.54.216.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 10.54.216.1
DHCP4.OPTION[16]:                       ip_address = 10.54.216.138
DHCP4.OPTION[17]:                       dhcp_lease_time = 28800
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 14400
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 25200
DHCP4.OPTION[23]:                       domain_name_servers = 208.67.222.222 208.67.220.220
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 10.184.12.107
IP6.ADDRESS[1]:                         fe80::ba88:e3ff:feaa:4467/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9462 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.2.0-25-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/vb22a-2015]] (600 root)
[connection] id=vb22a-2015 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=vb22a-2015
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/5000MHz]] (600 root)
[connection] id=5000MHz | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=5000MHz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/uio]] (600 root)
[connection] id=uio | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=uio
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ååååålesund]] (600 root)
[connection] id=Ååååålesund | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF]> | mac-address-blacklist= | ssid=195;133;195;165;195;165;195;165;195;165;108;101;115;117;110;100;
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Oslo (based on set time zone)


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


enp2s0f0  no frequency information.


lo        no frequency information.


wlp3s0    32 channels in total; available frequencies :
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


enp2s0f0  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlp3s0    Interface doesn't support scanning : Network is down


##### module infos ######################


[ath3k]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     BC24BEB84AA8FE42E66C237
depends:        bluetooth
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512


[ath9k]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     681B59FC4C4EB63D7B98108
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/4.2.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-25-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        A4:10:30:FB:DF:1D:C9:62:B4:BB:7D:16:44:C3:33:7E:C4:16:DB:86
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


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
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


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
blacklist acer_wmi


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


[    3.872399] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.645280] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[    8.248807] NetworkManager[579]: segfault at 0 ip 0000000000497b07 sp 00007ffeb6577b60 error 4 in NetworkManager[400000+1bf000]
[    8.708559] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   12.092517] NetworkManager[1018]: segfault at 0 ip 0000000000497b07 sp 00007ffe0f9499e0 error 4 in NetworkManager[400000+1bf000]
[   12.538239] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   15.959516] NetworkManager[1034]: segfault at 0 ip 0000000000497b07 sp 00007ffe46ba2290 error 4 in NetworkManager[400000+1bf000]
[   16.362782] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   19.802375] NetworkManager[1319]: segfault at 0 ip 0000000000497b07 sp 00007ffd52b93300 error 4 in NetworkManager[400000+1bf000]
[   20.258865] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   23.468237] NetworkManager[1685]: segfault at 0 ip 0000000000497b07 sp 00007fff49fd06a0 error 4 in NetworkManager[400000+1bf000]
[   23.752946] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   26.739153] NetworkManager[1693]: segfault at 0 ip 0000000000497b07 sp 00007ffff4c99840 error 4 in NetworkManager[400000+1bf000]
[   26.992064] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   30.412640] NetworkManager[1707]: segfault at 0 ip 0000000000497b07 sp 00007ffd70501f80 error 4 in NetworkManager[400000+1bf000]
[   30.744875] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   34.181935] NetworkManager[1716]: segfault at 0 ip 0000000000497b07 sp 00007ffd0dd8aef0 error 4 in NetworkManager[400000+1bf000]
[   34.497888] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   37.935751] NetworkManager[1752]: segfault at 0 ip 0000000000497b07 sp 00007ffc6c364350 error 4 in NetworkManager[400000+1bf000]
[   38.251995] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   41.693224] NetworkManager[1793]: segfault at 0 ip 0000000000497b07 sp 00007ffe685e5830 error 4 in NetworkManager[400000+1bf000]
[   42.008395] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   45.464881] NetworkManager[1822]: segfault at 0 ip 0000000000497b07 sp 00007ffea12841f0 error 4 in NetworkManager[400000+1bf000]
[   45.758165] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   49.200058] NetworkManager[1831]: segfault at 0 ip 0000000000497b07 sp 00007ffc9f4dace0 error 4 in NetworkManager[400000+1bf000]
[   49.545371] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   53.025888] NetworkManager[1846]: segfault at 0 ip 0000000000497b07 sp 00007ffec07d6780 error 4 in NetworkManager[400000+1bf000]
[   53.265885] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   56.742759] NetworkManager[1863]: segfault at 0 ip 0000000000497b07 sp 00007fff1cfec940 error 4 in NetworkManager[400000+1bf000]
[   57.020875] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   60.487224] NetworkManager[1887]: segfault at 0 ip 0000000000497b07 sp 00007fff12d8a2c0 error 4 in NetworkManager[400000+1bf000]
[   60.766493] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[   64.253380] NetworkManager[1894]: segfault at 0 ip 0000000000497b07 sp 00007ffd81936580 error 4 in NetworkManager[400000+1bf000]
[   64.541347] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)


########## wireless info END ############



```

---

### Post by praseodym on 2016-01-22
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Change "false" to "true", save and close the editor.

Reboot

---

### Post by stianlagstad on 2016-01-26
> **praseodym said:**
> ```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```
Change "false" to "true", save and close the editor.

Reboot

Thank you for answering. Unfortunately everything in that file was already set to true. See the contents:

```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

Right now I'm using ethernet with wifi enabled, and this is what the network manager does:
 [IMG]http://s17.postimg.org/ih1dsuyjx/ezgif_2331528322.gif[/IMG]

It seems to refresh or restart every 3-ish seconds.

---

### Post by stianlagstad on 2016-02-04
The problem introduces a memory leak of some kind if I don't disable wifi. unity-panel-service will take more and more resources the longer I keep wifi enabled, eventually making everything stop working.

I still haven't found a solution to this problem, but the same network at a different location (it's [eduroam]("https://en.wikipedia.org/wiki/Eduroam")) works like it should. This makes me think that there's some compatability issue between the router at the first location and the driver I have installed. I must be the driver, because it'll connect normally on Windows 7 with the same laptop.

---

