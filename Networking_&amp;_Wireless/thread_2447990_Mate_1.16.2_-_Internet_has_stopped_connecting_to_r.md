---
title: "Mate 1.16.2 - Internet has stopped connecting to router - not wifi or wired"
date: 2020-07-30
forum: Networking &amp; Wireless
---

### Post by loufou on 2020-07-30
Disclaimer: I'm not knowledgeable about linux, have used it for years tho and have to troubleshoot things once in a while.

My internet has stopped connecting, it might have broken after I forced a shutdown on the laptop after it froze on me. At the moment I'm using the internet using USB tethering on my phone, so there's no issue. But can't pick up my hotspot, router wifi, doesnt pick up internet via cable/wired. I'm breaking my brain trying all sorts of things from other threads but think I need to ask help now. Here is the code:



```
########## wireless info START ##########


Report from: 30 Jul 2020 19:44 AEST +1000


Booted last: 30 Jul 2020 00:00 AEST +1000


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-186-generic #216-Ubuntu SMP Wed Jul 1 05:34:05 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


MATE


##### lspci #############################


07:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8170]
	Kernel driver in use: iwlwifi


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Toshiba America Info Systems RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1179:f920]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 007: ID 04ca:7046 Lite-On Technology Corp. TOSHIBA Web Camera - HD
Bus 002 Device 006: ID 8087:07dc Intel Corp. 
Bus 002 Device 009: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


##### secure boot #######################


EFI variables are not supported on this system


##### lsmod #############################


iwlmvm                315392  0
mac80211              741376  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 toshiba_acpi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
3: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>
4: enp0s20u2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20u2' [IF3]> brd <MAC address>
    inet 192.168.42.21/24 brd 192.168.42.255 scope global dynamic enp0s20u2
       valid_lft 3082sec preferred_lft 3082sec
    inet6 fe80::d359:a085:b38:9c81/64 scope link 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


enp8s0    no wireless extensions.


enp0s20u2  no wireless extensions.


wlp7s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


default via 192.168.42.129 dev enp0s20u2  proto static  metric 100 
169.254.0.0/16 dev enp0s20u2  scope link  metric 1000 
192.168.42.0/24 dev enp0s20u2  proto kernel  scope link  src 192.168.42.21  metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       777     1  0 19:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s20u2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Google
GENERAL.PRODUCT:                        Pixel 3
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20u2' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-2/2-2:1.0/net/enp0s20u2
GENERAL.IP-IFACE:                       enp0s20u2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       7efb4d43-c6a5-320f-b9b5-6eb696f8bc9d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{12}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7efb4d43-c6a5-320f-b9b5-6eb696f8bc9d | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.21/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.21
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3149
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1799
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1596105339
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = tux
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3599
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::d359:a085:b38:9c81/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/enp8s0
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


GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-186-generic
GENERAL.FIRMWARE-VERSION:               17.948900127.0
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/wlp7s0
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
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Computerbank 1]] (600 root)
[connection] id=Computerbank 1 | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=Computerbank
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Telstra6502]] (600 root)
[connection] id=Telstra6502 | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=Telstra6502
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/KINGS ARI]] (600 root)
[connection] id=KINGS ARI | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=KINGS ARI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Guz Houz]] (600 root)
[connection] id=Guz Houz | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=Guz Houz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UniWireless]] (600 root)
[connection] id=UniWireless | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=UniWireless
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/OPTUS_B70915]] (600 root)
[connection] id=OPTUS_B70915 | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=OPTUS_B70915
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR23]] (600 root)
[connection] id=NETGEAR23 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=NETGEAR23
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Computerbank]] (600 root)
[connection] id=Computerbank | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Computerbank
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/KINGS ARI 5G]] (600 root)
[connection] id=KINGS ARI 5G | type=wifi | permissions=user:user:;
[wifi] mac-address=<MAC 'wlp7s0' [IF2]> | mac-address-blacklist= | ssid=KINGS ARI 5G
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: Australia/Melbourne (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp8s0    no frequency information.


enp0s20u2  no frequency information.


wlp7s0    32 channels in total; available frequencies :
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


enp8s0    Interface doesn't support scanning.


enp0s20u2  Interface doesn't support scanning.


wlp7s0    Interface doesn't support scanning : Network is down


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-186-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     E019964B658E1C3A061CE1E
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-186-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


[mac80211]
filename:       /lib/modules/4.4.0-186-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     99CE83DF3174103BD44F6DF
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-186-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-186-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     3560CDB1B1A4B9CBC0C111F
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-186-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-186-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5744BD0DD0E28A05E59A01C
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-186-generic SMP mod_unload modversions 
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
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


[    5.063034] iwlwifi 0000:07:00.0: loaded firmware version 17.948900127.0 op_mode iwlmvm
[    5.095807] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[    5.096152] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    5.096796] iwlwifi 0000:07:00.0: RF_KILL bit toggled to disable radio.
[    5.096847] iwlwifi 0000:07:00.0: L1 Enabled - LTR Enabled
[    5.125372] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.261747] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[    5.770031] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[    5.773543] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[    5.839752] r8169 0000:08:00.0 enp8s0: link down
[    5.839830] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   28.436876] rndis_host 2-2:1.0 enp0s20u2: renamed from usb0
[   28.456017] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2: link is not ready


########## wireless info END ############
```

Help would be much appreciated I am in lockdown and seriously need my laptop to work.

---

### Post by TheFu on 2020-07-30
Is there a reason you've assumed the router is fine?  That would be the first thing to check.  Can your phone connect to the wifi on the router?  If not, get a new router.

I cannot help with wifi (generally, wifi either works or it doesn't due to drivers) and generally can't help much with realtek issues, but general networking ... 

> Hard blocked: yes
That's why the wired ethernet doesn't work.  Use rfkill to unblock it. If that doesn't work, check the BIOS settings to ensure the onboard ethernet is not disabled.

BTW, you know that Nexus4 is highly hackable, right?

---

### Post by loufou on 2020-07-30
Hi thanks for your response. Yes the router was the first thing I checked. Other devices in the house picks up wifi no problem, also my housemate's laptop is picking up wifi no problem. I even called the router technical support to see if they could suggest anything. The problem is in my laptop.

---

### Post by praseodym on 2020-07-31
Wifi is "hard blocked". Any button, switch, key or key combo?

---

### Post by loufou on 2020-08-03
I have tried the wifi button on the laptop, I press it, check "rfkill list all" but wireless LAN remains "Hard blocked". I've tried this button multiple times, checking every time I press it. 

I also went into BIOS, even though "built-in LAN" was "Enabled", I toggled it off and on and rebooted. Still no effect.

I don't know what to do from here on please advise...

---

### Post by TheFu on 2020-08-03
Run
```
$ rfkill list
```

In the output, there will be device numbers - I think.
Run 
```
$ rfkill unblock {put the number of the device here}
```
run 
```
$ rfkill list
```
to see it is unblocked and can be used.  From the rfkill manpage:
```
       unblock index|type
              Enable the device corresponding to the given index. If the device  is
              hard-blocked,  e.g. via a hardware switch, it will remain unavailable
              though it is now soft-unblocked.

```

Hard blocked means either a switch, keyboard combination or BIOS setting has to be fixed.  I suppose the HW could be dead too.  Most laptop have a Fn+{some function key} method to toggle the hard block/unblock. They specific key usually has a little wifi icon. 

But this doesn't usually impact wired connections at all.  Those almost always "just work" by connecting a CAT5e cable between the computer and the switch.

---

