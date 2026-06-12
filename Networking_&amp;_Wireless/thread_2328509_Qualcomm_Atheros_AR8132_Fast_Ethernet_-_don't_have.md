---
title: "Qualcomm Atheros AR8132 Fast Ethernet - don't have wireless enabled"
date: 2016-06-21
forum: Networking &amp; Wireless
---

### Post by SlAiD on 2016-06-21
Hello there,

I've this Qualcomm Atheros AR8132 Fast Ethernet on my Ubuntu 16 and my Wireless is simply not working for some days.


I'm attaching in code the scriipt used to debug this issue.

Any hint on how to solve this?


Thanks,
R.

```


########## wireless info START ##########

Report from: 21 Jun 2016 22:40 WEST +0100

Booted last: 21 Jun 2016 00:00 WEST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. AR8132 Fast Ethernet [1043:838a]
	Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel modules: ath9k

##### lsusb #############################

Bus 001 Device 007: ID 04a9:173b Canon, Inc. PIXMA MP270 All-In-One Printer
Bus 001 Device 006: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 005: ID 072f:90cc Advanced Card Systems, Ltd ACR38 SmartCard Reader
Bus 001 Device 010: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 18f8:0f97  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               24576  1 eeepc_wmi
ath9k_common           36864  0
ath9k_hw              458752  1 ath9k_common
ath                    24576  2 ath9k_common,ath9k_hw
mac80211              659456  0
cfg80211              499712  3 ath,ath9k_common,mac80211
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:109.48.170.46  Bcast:109.48.175.255  Mask:255.255.240.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19545 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:8600051 (8.6 MB)  TX bytes:2543375 (2.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         109.48.175.254  0.0.0.0         UG    100    0        0 eth0
85.138.243.254  109.48.175.254  255.255.255.255 UGH   100    0        0 eth0
109.48.160.0    0.0.0.0         255.255.240.0   U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2756     1  0 22:28 ?        00:00:07 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     eth0
GENERAL.CON-UUID:                       233953b5-2f35-446f-bbc2-147ec1f1ece5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6,66}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   84f37b34-472c-4baa-a7b2-25499c8676e6 | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   233953b5-2f35-446f-bbc2-147ec1f1ece5 | eth0
IP4.ADDRESS[1]:                         109.48.170.46/20
IP4.GATEWAY:                            109.48.175.254
IP4.ROUTE[1]:                           dst = 85.138.243.254/32, nh = 109.48.175.254, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             212.113.191.129
IP4.DNS[2]:                             62.169.70.160
IP4.DOMAIN[1]:                          netcabo.pt
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.240.0
DHCP4.OPTION[4]:                        domain_name_servers = 212.113.191.129 62.169.70.160
DHCP4.OPTION[5]:                        ip_address = 109.48.170.46
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 85.138.243.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 109.48.175.255
DHCP4.OPTION[11]:                       time_servers = 212.113.176.135 212.113.176.71
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       dhcp_rebinding_time = 12600
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 109.48.175.254
DHCP4.OPTION[18]:                       dhcp_renewal_time = 7200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = netcabo.pt
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1466558895
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       log_servers = 212.113.188.209
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 109.48.160.0
DHCP4.OPTION[29]:                       requested_domain_search = 1
DHCP4.OPTION[30]:                       next_server = 0.0.0.0
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 14400
DHCP4.OPTION[33]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            

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

[[/etc/NetworkManager/system-connections/H_QUASAR]] (600 root)
[connection] id=H_QUASAR | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H_QUASAR 1]] (600 root)
[connection] id=H_QUASAR 1 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-2CB477]] (600 root)
[connection] id=Vodafone-2CB477 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vodafone-2CB477
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tugaleaks]] (600 root)
[connection] id=Tugaleaks | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tugaleaks
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel Star Inn]] (600 root)
[connection] id=Hotel Star Inn | type=wifi
[wifi] ssid=Hotel Star Inn | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-BARRAQUEIRO]] (600 root)
[connection] id=FON_ZON-BARRAQUEIRO | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON-BARRAQUEIRO
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570]] (600 root)
[connection] id=Cabovisao-2570 | type=wifi
[wifi] ssid=Cabovisao-2570 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi FROTA AZUL 874]] (600 root)
[connection] id=WiFi FROTA AZUL 874 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WiFi FROTA AZUL 874
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-8E7609]] (600 root)
[connection] id=MEO-8E7609 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MEO-8E7609
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET 1]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7A00]] (600 root)
[connection] id=ZON-7A00 | type=wifi
[wifi] ssid=ZON-7A00 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Montra Digital]] (600 root)
[connection] id=Montra Digital | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Montra Digital
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-WiFi]] (600 root)
[connection] id=MEO-WiFi | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MEO-WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/guest-ULisboa]] (600 root)
[connection] id=guest-ULisboa | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=guest-ULisboa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/formadores]] (600 root)
[connection] id=formadores | type=wifi
[wifi] ssid=formadores | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Netplus-99F7EB]] (600 root)
[connection] id=Netplus-99F7EB | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Netplus-99F7EB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-4710]] (600 root)
[connection] id=NOS-4710 | type=wifi
[wifi] ssid=NOS-4710 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifi-Moov-Guest]] (600 root)
[connection] id=Wifi-Moov-Guest | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Wifi-Moov-Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-C313B3]] (600 root)
[connection] id=Vodafone-C313B3 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Vodafone-C313B3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RESENDE]] (600 root)
[connection] id=FON_ZON-RESENDE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON-RESENDE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-Almeida]] (600 root)
[connection] id=MEO-Almeida | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MEO-Almeida
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP]] (600 root)
[connection] id=IEFP | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/D.Estefania Pais]] (600 root)
[connection] id=D.Estefania Pais | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=D.Estefania Pais
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/auditoriofd]] (600 root)
[connection] id=auditoriofd | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=auditoriofd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RNE]] (600 root)
[connection] id=FON_ZON-RNE | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON-RNE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wifiRHP]] (600 root)
[connection] id=wifiRHP | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=wifiRHP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-FB50]] (600 root)
[connection] id=NOS-FB50 | type=wifi
[wifi] ssid=NOS-FB50 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/1]] (600 root)
[connection] id=1 | type=wifi | autoconnect=false
[wifi] ssid=1 | mac-address=<MAC address>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP 1]] (600 root)
[connection] id=IEFP 1 | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/rede_pagaime]] (600 root)
[connection] id=rede_pagaime | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=rede_pagaime
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570 1]] (600 root)
[connection] id=Cabovisao-2570 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Cabovisao-2570
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CLARA-GOMES]] (600 root)
[connection] id=CLARA-GOMES | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CLARA-GOMES
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k_common]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/custom-wireless.conf]
options ath9k nohwcrypt

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   33.030455] ath9k: `' invalid for parameter `nohwcrypt'
[   68.412731] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   68.413629] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[ 1160.243411] ath9k: `' invalid for parameter `nohwcrypt' (repeated 3 times)

########## wireless info END ############



```

---

### Post by jeremy31 on 2016-06-21
See if ```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/custom-wireless.conf
```
Reboot and see if it works

---

### Post by SlAiD on 2016-06-21
Hello,

That did fix some issues: I can now see the tick to select "enable" on the wireless network, but wieh I tick it/check it I don't see any networks to connect.

Photo of the screen: [http://imgur.com/0zdOzav](http://imgur.com/0zdOzav)

PS: and I have plenty nearby

---

### Post by jeremy31 on 2016-06-21
There may be another issue.  Run the wireless script again and post new results

You may have to disconnect from ethernet and wait a little while for wifi networks to appear

---

### Post by SlAiD on 2016-06-21
Hi,

I wait around 3 minutes. No luck. :(
Usualy it shows up wifi networks in seconds (1 or 2).


Here is the result again. Thanks!

```


########## wireless info START ##########

Report from: 22 Jun 2016 00:05 WEST +0100

Booted last: 22 Jun 2016 00:00 WEST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################


01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. AR8132 Fast Ethernet [1043:838a]
	Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 007: ID 04a9:173b Canon, Inc. PIXMA MP270 All-In-One Printer
Bus 001 Device 006: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 005: ID 072f:90cc Advanced Card Systems, Ltd ACR38 SmartCard Reader
Bus 001 Device 004: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 18f8:0f97  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################


##### rfkill ############################

0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

##### lsmod #############################

ath9k                 135168  0
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
eeepc_wmi              16384  0
asus_wmi               24576  1 eeepc_wmi
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:45:73:d0  
          inet addr:109.48.170.46  Bcast:109.48.175.255  Mask:255.255.240.0
          inet6 addr: fe80::e2cb:4eff:fe45:73d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14532 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:7998936 (7.9 MB)  TX bytes:1943031 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:38:71:d0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         109.48.175.254  0.0.0.0         UG    100    0        0 eth0
85.138.243.254  109.48.175.254  255.255.255.255 UGH   100    0        0 eth0
109.48.160.0    0.0.0.0         255.255.240.0   U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4


##### network managers ##################

Installed:

	NetworkManager

Running:

root       896     1  1 Jun21 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         E0:CB:4E:45:73:D0
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       84f37b34-472c-4baa-a7b2-25499c8676e6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   84f37b34-472c-4baa-a7b2-25499c8676e6 | Wired connection 1
IP4.ADDRESS[1]:                         109.48.170.46/20
IP4.GATEWAY:                            109.48.175.254
IP4.ROUTE[1]:                           dst = 85.138.243.254/32, nh = 109.48.175.254, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             212.113.191.129
IP4.DNS[2]:                             62.169.70.160
IP4.DNS[3]:                             8.8.8.8
IP4.DOMAIN[1]:                          netcabo.pt
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.240.0
DHCP4.OPTION[4]:                        domain_name_servers = 212.113.191.129 62.169.70.160
DHCP4.OPTION[5]:                        ip_address = 109.48.170.46
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 85.138.243.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 109.48.175.255
DHCP4.OPTION[11]:                       time_servers = 212.113.176.135 212.113.176.71
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       dhcp_rebinding_time = 12600
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 109.48.175.254
DHCP4.OPTION[18]:                       dhcp_renewal_time = 7200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = netcabo.pt
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1466564256
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       log_servers = 212.113.188.209
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 109.48.160.0
DHCP4.OPTION[29]:                       requested_domain_search = 1
DHCP4.OPTION[30]:                       next_server = 0.0.0.0
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 14400
DHCP4.OPTION[33]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::e2cb:4eff:fe45:73d0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express) (AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         00:25:D3:38:71:D0
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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



```

---

### Post by jeremy31 on 2016-06-21
I would reboot with the ethernet unplugged.  The last script report shows that the module loads but the report wasn't complete.  I have the same wifi running in 16.04 except it has bluetooth, at least I don't see the bluetooth in the lsusb part of the script

---

### Post by SlAiD on 2016-06-21
Hello,

In the past I had the two connected (ether and wireless). But I've try your way and reboot the PC without the ethernet - didn't work.
I also ran the script again without the ethernet cable plugged.

Here are the results. Any other hint? Thanks for your time! 

```


########## wireless info START ##########

Report from: 22 Jun 2016 00:22 WEST +0100

Booted last: 22 Jun 2016 00:00 WEST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. AR8132 Fast Ethernet [1043:838a]
	Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 007: ID 04a9:173b Canon, Inc. PIXMA MP270 All-In-One Printer
Bus 001 Device 006: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 005: ID 072f:90cc Advanced Card Systems, Ltd ACR38 SmartCard Reader
Bus 001 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 18f8:0f97  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
asus_wmi               24576  1 eeepc_wmi
ath9k                 135168  0
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

	NetworkManager

Running:

root       900     1  5 00:19 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/eth0
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

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express) (AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/H_QUASAR]] (600 root)
[connection] id=H_QUASAR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H_QUASAR 1]] (600 root)
[connection] id=H_QUASAR 1 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-2CB477]] (600 root)
[connection] id=Vodafone-2CB477 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Vodafone-2CB477
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tugaleaks]] (600 root)
[connection] id=Tugaleaks | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Tugaleaks
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel Star Inn]] (600 root)
[connection] id=Hotel Star Inn | type=wifi
[wifi] ssid=Hotel Star Inn | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-BARRAQUEIRO]] (600 root)
[connection] id=FON_ZON-BARRAQUEIRO | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-BARRAQUEIRO
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570]] (600 root)
[connection] id=Cabovisao-2570 | type=wifi
[wifi] ssid=Cabovisao-2570 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi FROTA AZUL 874]] (600 root)
[connection] id=WiFi FROTA AZUL 874 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=WiFi FROTA AZUL 874
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-8E7609]] (600 root)
[connection] id=MEO-8E7609 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=MEO-8E7609
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET 1]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7A00]] (600 root)
[connection] id=ZON-7A00 | type=wifi
[wifi] ssid=ZON-7A00 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Montra Digital]] (600 root)
[connection] id=Montra Digital | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Montra Digital
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-WiFi]] (600 root)
[connection] id=MEO-WiFi | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=MEO-WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/guest-ULisboa]] (600 root)
[connection] id=guest-ULisboa | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=guest-ULisboa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/formadores]] (600 root)
[connection] id=formadores | type=wifi
[wifi] ssid=formadores | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Netplus-99F7EB]] (600 root)
[connection] id=Netplus-99F7EB | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Netplus-99F7EB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-4710]] (600 root)
[connection] id=NOS-4710 | type=wifi
[wifi] ssid=NOS-4710 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifi-Moov-Guest]] (600 root)
[connection] id=Wifi-Moov-Guest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Wifi-Moov-Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-C313B3]] (600 root)
[connection] id=Vodafone-C313B3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Vodafone-C313B3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RESENDE]] (600 root)
[connection] id=FON_ZON-RESENDE | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-RESENDE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-Almeida]] (600 root)
[connection] id=MEO-Almeida | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MEO-Almeida
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP]] (600 root)
[connection] id=IEFP | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/D.Estefania Pais]] (600 root)
[connection] id=D.Estefania Pais | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=D.Estefania Pais
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/auditoriofd]] (600 root)
[connection] id=auditoriofd | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=auditoriofd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RNE]] (600 root)
[connection] id=FON_ZON-RNE | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-RNE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wifiRHP]] (600 root)
[connection] id=wifiRHP | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=wifiRHP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-FB50]] (600 root)
[connection] id=NOS-FB50 | type=wifi
[wifi] ssid=NOS-FB50 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/1]] (600 root)
[connection] id=1 | type=wifi | autoconnect=false
[wifi] ssid=1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP 1]] (600 root)
[connection] id=IEFP 1 | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/rede_pagaime]] (600 root)
[connection] id=rede_pagaime | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=rede_pagaime
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570 1]] (600 root)
[connection] id=Cabovisao-2570 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Cabovisao-2570
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CLARA-GOMES]] (600 root)
[connection] id=CLARA-GOMES | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=CLARA-GOMES
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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

eth0      no frequency information.

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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
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

[/etc/modprobe.d/custom-wireless.conf]
options ath9k nohwcrypt=1

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   34.776246] ath: phy0: ASPM enabled: 0x42
[   34.776263] ath: EEPROM regdomain: 0x60
[   34.776268] ath: EEPROM indicates we should expect a direct regpair map
[   34.776277] ath: Country alpha2 being used: 00
[   34.776281] ath: Regpair used: 0x60
[   69.252825] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   69.354537] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############



```

---

### Post by jeremy31 on 2016-06-21
I must be doing too much today.```
rfkill unblock wifi
``` As the rfkill shows the wifi as being soft blocked

---

### Post by SlAiD on 2016-06-21
Hi,

Rebooting, but still nothing.
But... it's hard blocked and not soft blocked. (soft is with fn+f2 or fn+f<something>) but the hard blocked I don't have a clue how this came to be that way.

---

### Post by jeremy31 on 2016-06-21
Is there a switch on this to enable/disable wireless, like a slider somewhere?

What make and model computer?  Also post ```
sudo dmidecode | grep -i version
```

I am aware of a new module, asus-wireless that was included upstream just a few months ago but it is not part of the Ubuntu 4.4 kernel

---

### Post by SlAiD on 2016-06-22
Hi,

No switch on this computer.

The output is:
	Version: 1401   
	Version: x.x
	Version: x.xx
	Version: x.x
	Version: Intel(R) Atom(TM) CPU N280   @ 1.66GHz  


Also, computer is Eee PC 1015P (Seashell)  - [https://www.asus.com/Notebooks/Eee_PC_1015P_Seashell/](https://www.asus.com/Notebooks/Eee_PC_1015P_Seashell/)


Thanks for your help!

---

### Post by jeremy31 on 2016-06-22
See if wifi enables after
```
sudo modprobe -r asus_wmi
rfkill unblock all
```

Also use the FN combo for toggling wifi and then ```
dmesg | tail
```
Look for a message about unknown keypress

---

### Post by SlAiD on 2016-06-22
Hello again,


rc@651650656:~$ sudo modprobe -r asus_wmi
[sudo] password for rc: 
modprobe: FATAL: Module asus_wmi is in use.
rc@651650656:~$ rfkill unblock all


After that, the message displaying in the top bar is "wifi disabled by hardware switch".

The second command dosn't show any message like that: 

rc@651650656:~$ dmesg | tail
[ 3679.160727] Bluetooth: SCO socket layer initialized
[ 3679.444616] usbcore: registered new interface driver btusb
[ 3680.577628] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[ 3680.577638] Bluetooth: BNEP filters: protocol multicast
[ 3680.577657] Bluetooth: BNEP socket layer initialized
[ 3681.319104] Bluetooth: RFCOMM TTY layer initialized
[ 3681.319131] Bluetooth: RFCOMM socket layer initialized
[ 3681.319154] Bluetooth: RFCOMM ver 1.11
[ 3696.464238] usb 4-2: reset low-speed USB device number 2 using uhci_hcd
[ 3697.064225] usb 4-2: reset low-speed USB device number 2 using uhci_hcd
rc@651650656:~$ 



:(

---

### Post by SlAiD on 2016-06-23
Hello,

Any more ideas on fixing this?


Thanks.

---

### Post by jeremy31 on 2016-06-23
Try ```
echo " blacklist asus_wmi" | sudo tee /etc/modprobe.d/asus_wmi.conf
```
Reboot

---

### Post by SlAiD on 2016-06-23
Hello agian,

First, thanks for all the help you're giving me.

But I'm sorry to say that I still get the disabled by hardware switch message.


:(

---

### Post by jeremy31 on 2016-06-23
Can you go into BIOS and see if wireless is enabled and possibly reset to defaults

---

### Post by SlAiD on 2016-06-23
Hi,

Yes I can. But,  before that, I ran a bootable instalation of Kali (and then Ubuntu, just to be sure) and both display the wireless without any issues.


Do you still need me to reset it to defauls?


The problem did start to hapen when I was low on battery and I disable wifi since I was not using it. Then when I try to enable it, it didn't show any more wireless networks. Not sure if this info helps.


Thanks.

---

### Post by jeremy31 on 2016-06-23
Shut down the computer and remove power cord and battery.  Press and hold power button for 20 seconds.  Replace battery and power cord and reboot to see if it resets

---

### Post by SlAiD on 2016-06-23
Hello,

That did something.
Here is the print: [https://gyazo.com/44e2b0714669414d556ab2f01822bad2](https://gyazo.com/44e2b0714669414d556ab2f01822bad2)

It says only that wifi is disabled (not by any hardware) but when I click Enable and wait a few minutes, no networks are found and it keeps saying disabled.

---

### Post by jeremy31 on 2016-06-23
Run the script again and post results and use ```
iwlist scan
``` to check for networks just in case it is a network manager bug

---

### Post by SlAiD on 2016-06-23
Hello,

Here is the info:
```


########## wireless info START ##########

Report from: 23 Jun 2016 22:56 WEST +0100

Booted last: 23 Jun 2016 00:00 WEST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:25:16 UTC 2016 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
	Subsystem: ASUSTeK Computer Inc. AR8132 Fast Ethernet [1043:838a]
	Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 009: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 001 Device 008: ID 072f:90cc Advanced Card Systems, Ltd ACR38 SmartCard Reader
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 012: ID 18f8:0f97  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0
ath9k                 135168  0
asus_wmi               24576  1 eeepc_wmi
ath9k_common           36864  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    24576  3 ath9k_common,ath9k,ath9k_hw
mac80211              659456  1 ath9k
cfg80211              499712  4 ath,ath9k_common,ath9k,mac80211
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi
video                  36864  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:109.48.190.165  Bcast:109.48.191.255  Mask:255.255.240.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94695 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:164979341 (164.9 MB)  TX bytes:10945295 (10.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         109.48.191.254  0.0.0.0         UG    100    0        0 eth0
85.138.243.254  109.48.191.254  255.255.255.255 UGH   100    0        0 eth0
109.48.176.0    0.0.0.0         255.255.240.0   U     100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 8.8.8.8
nameserver 8.8.4.4

##### network managers ##################

Installed:

	NetworkManager

Running:

root       871     1  0 21:45 ?        00:00:09 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8132 Fast Ethernet
GENERAL.DRIVER:                         atl1c
GENERAL.DRIVER-VERSION:                 1.0.1.1-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       84f37b34-472c-4baa-a7b2-25499c8676e6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   84f37b34-472c-4baa-a7b2-25499c8676e6 | Wired connection 1
IP4.ADDRESS[1]:                         109.48.190.165/20
IP4.GATEWAY:                            109.48.191.254
IP4.ROUTE[1]:                           dst = 85.138.243.254/32, nh = 109.48.191.254, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             212.113.191.129
IP4.DNS[2]:                             62.169.70.160
IP4.DNS[3]:                             8.8.8.8
IP4.DOMAIN[1]:                          netcabo.pt
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.240.0
DHCP4.OPTION[4]:                        domain_name_servers = 212.113.191.129 62.169.70.160
DHCP4.OPTION[5]:                        ip_address = 109.48.190.165
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 85.138.243.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 109.48.191.255
DHCP4.OPTION[11]:                       time_servers = 212.113.176.135 212.113.176.71
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       dhcp_rebinding_time = 12600
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 109.48.191.254
DHCP4.OPTION[18]:                       dhcp_renewal_time = 7200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = netcabo.pt
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1466729140
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       log_servers = 212.113.188.209
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[28]:                       network_number = 109.48.176.0
DHCP4.OPTION[29]:                       requested_domain_search = 1
DHCP4.OPTION[30]:                       next_server = 0.0.0.0
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 14400
DHCP4.OPTION[33]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9285 Wireless Network Adapter (PCI-Express) (AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card)
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/H_QUASAR]] (600 root)
[connection] id=H_QUASAR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/H_QUASAR 1]] (600 root)
[connection] id=H_QUASAR 1 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=H_QUASAR
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-2CB477]] (600 root)
[connection] id=Vodafone-2CB477 | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Vodafone-2CB477
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tugaleaks]] (600 root)
[connection] id=Tugaleaks | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Tugaleaks
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Hotel Star Inn]] (600 root)
[connection] id=Hotel Star Inn | type=wifi
[wifi] ssid=Hotel Star Inn | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-BARRAQUEIRO]] (600 root)
[connection] id=FON_ZON-BARRAQUEIRO | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-BARRAQUEIRO
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570]] (600 root)
[connection] id=Cabovisao-2570 | type=wifi
[wifi] ssid=Cabovisao-2570 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi FROTA AZUL 874]] (600 root)
[connection] id=WiFi FROTA AZUL 874 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=WiFi FROTA AZUL 874
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-8E7609]] (600 root)
[connection] id=MEO-8E7609 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=MEO-8E7609
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET 1]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7A00]] (600 root)
[connection] id=ZON-7A00 | type=wifi
[wifi] ssid=ZON-7A00 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Montra Digital]] (600 root)
[connection] id=Montra Digital | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Montra Digital
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-WiFi]] (600 root)
[connection] id=MEO-WiFi | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=MEO-WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/guest-ULisboa]] (600 root)
[connection] id=guest-ULisboa | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=guest-ULisboa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/formadores]] (600 root)
[connection] id=formadores | type=wifi
[wifi] ssid=formadores | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Netplus-99F7EB]] (600 root)
[connection] id=Netplus-99F7EB | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Netplus-99F7EB
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-4710]] (600 root)
[connection] id=NOS-4710 | type=wifi
[wifi] ssid=NOS-4710 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wifi-Moov-Guest]] (600 root)
[connection] id=Wifi-Moov-Guest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Wifi-Moov-Guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vodafone-C313B3]] (600 root)
[connection] id=Vodafone-C313B3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Vodafone-C313B3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RESENDE]] (600 root)
[connection] id=FON_ZON-RESENDE | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-RESENDE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MEO-Almeida]] (600 root)
[connection] id=MEO-Almeida | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MEO-Almeida
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP]] (600 root)
[connection] id=IEFP | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/D.Estefania Pais]] (600 root)
[connection] id=D.Estefania Pais | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=D.Estefania Pais
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/auditoriofd]] (600 root)
[connection] id=auditoriofd | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=auditoriofd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON-RNE]] (600 root)
[connection] id=FON_ZON-RNE | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=FON_ZON-RNE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wifiRHP]] (600 root)
[connection] id=wifiRHP | type=wifi | permissions=user:rc:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=wifiRHP
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NOS-FB50]] (600 root)
[connection] id=NOS-FB50 | type=wifi
[wifi] ssid=NOS-FB50 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/1]] (600 root)
[connection] id=1 | type=wifi | autoconnect=false
[wifi] ssid=1 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FON_ZON_FREE_INTERNET]] (600 root)
[connection] id=FON_ZON_FREE_INTERNET | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FON_ZON_FREE_INTERNET
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/IEFP 1]] (600 root)
[connection] id=IEFP 1 | type=wifi
[wifi] ssid=IEFP | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/rede_pagaime]] (600 root)
[connection] id=rede_pagaime | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=rede_pagaime
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-2570 1]] (600 root)
[connection] id=Cabovisao-2570 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Cabovisao-2570
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CLARA-GOMES]] (600 root)
[connection] id=CLARA-GOMES | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=CLARA-GOMES
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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

eth0      no frequency information.

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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F7E3AF932B15681132EA595
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath9k_hw]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BF9F4930086BABAAF3CD9BA
depends:        ath
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[ath]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 686 
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

[/etc/modprobe.d/asus_wmi.conf]
 blacklist asus_wmi

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

[/etc/modprobe.d/custom-wireless.conf]
options ath9k nohwcrypt=1

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   66.838502] ath: phy0: ASPM enabled: 0x42
[   66.838515] ath: EEPROM regdomain: 0x60
[   66.838521] ath: EEPROM indicates we should expect a direct regpair map
[   66.838529] ath: Country alpha2 being used: 00
[   66.838534] ath: Regpair used: 0x60
[  101.032297] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  101.033639] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  101.126583] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############



```

The command says wlan0     Failed to read scan data : Network is down

---

### Post by jeremy31 on 2016-06-23
Try this one again  ```
echo "blacklist asus_wmi" | sudo tee /etc/modprobe.d/asus_wmi.conf
```
As asus_wmi still loaded and I noticed a space in the original command, then reboot

---

### Post by SlAiD on 2016-06-23
Return:

blacklist asus_wmi


However, after reboot, I still see the wifi disabled...

---

### Post by jeremy31 on 2016-06-23
This is a bit experimental but there is a new module in newer kernels that may help.  You will need to download a few files
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600-generic_4.6.0-040600.201606100558_i386.deb
```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-headers-4.6.0-040600_4.6.0-040600.201606100558_all.deb
```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.6-yakkety/linux-image-4.6.0-040600-generic_4.6.0-040600.201606100558_i386.deb
```

Install with ```
dpkg -i linux*.deb
``` and hopefully things work after a reboot.  If for some reason you can't boot into the new kernel, press SHIFT after shutdown to get the Grub menu where you can select advanced options and choose to boot from the 4.4 kernel.  Even if this fix works, I suggest filing a bug report, a guide is located [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078) and I would file the bug against linux as this seems to be a kernel issue

---

### Post by SlAiD on 2016-06-24
Hello,

rc@651650656:~$ uname -a 
Linux 651650656 4.6.0-040600-generic #201606100558 SMP Fri Jun 10 10:11:23 UTC 2016 i686 i686 i686 GNU/Linux


I'm sorry to say that... it did not work.
I still see wifi disabled (not disabled by hardware as previously seen).


I'm now thinking on reinstlaling from scratch. :(

Any more hints?

And once again thanks for your help.

---

### Post by jeremy31 on 2016-06-24
Can it be enabled with ```
rfkill unblock all
```
Check airplane mode in Network Manager and you could try ```
sudo ifconfig wlan0 up
```

---

### Post by SlAiD on 2016-06-24
Hi,

sudo ifconfig wlan0 up gives me:

[sudo] password for rc: 
SIOCSIFFLAGS: Operation not possible due to RF-kill
rc@651650656:~$ rfkill unblock wlan0
Bogus unblock argument 'wlan0'.
rc@651650656:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
rc@651650656:~$ rfkill list Wireless LAN
Bogus list argument 'Wireless'.
rc@651650656:~$ rfkill unblock Wireless LAN
Bogus unblock argument 'Wireless'.
rc@651650656:~$ rfkill unblock phy0
Bogus unblock argument 'phy0'.

Not sure what is the argument to use here. Any help on this?


Airplane mode is off.


Not sure if this is relevant, but I found a topic EXACTLY like mine while searching for rfkull: [http://ubuntuforums.org/showthread.php?t=1781350](http://ubuntuforums.org/showthread.php?t=1781350)

I didn't try any info there since it might mess up your help here.

Should I do it?


Thanks.

---

### Post by jeremy31 on 2016-06-24
Close the lid, wait a couple minutes and open it and see if the block is cleared.

What solution from the other post, as you already had ```
options ath9k nohwcrypt
``` at the beginning and it wouldn't let the driver load

---

### Post by SlAiD on 2016-06-24
Hi,

What do you mean by close the lid? 


I see that there where some sugestions on the post - didn't read the whole post - buit I was just letting you know about it, 
You're right,I've already try that.

---

### Post by jeremy31 on 2016-06-24
Close it so it goes into suspend.  A lot of posts I found mentioned resetting the BIOS to defaults helped

---

### Post by SlAiD on 2016-06-24
Hello,

Resetting the BIOS to default valies **did work**!

I'm sorry for not doing it sooner. But as it was working on the LiveCD I assume - incorrectly - that this was not needed.
Sorry for that. 

I'd like to thank you one more time for your time and efford.


Have a nice day! :)

---

### Post by jeremy31 on 2016-06-24
Now reboot and use grub to use the 4.4.0 kernel in Advanced options.  If wifi still works, we will uninstall the 4.6 kernel as it will not be updated with Ubuntu security patches, post ```
dpkg -l | grep 4.6
```

---

### Post by SlAiD on 2016-06-24
Hi,

Yes, it does work.

The command you requested:
```

rc@651650656:~$ dpkg -l | grep 4.6
ii  consolekit                                          0.4.6-5                                             i386         framework for defining and tracking users, sessions and seats
ii  findutils                                           4.6.0+git+20160126-2                                i386         utilities for finding files--find, xargs
ii  gnome-software                                      3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 i386         Software Center for GNOME
ii  gnome-software-common                               3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 all          Software Center for GNOME (common files)
ii  indicator-datetime                                  15.10+16.04.20160406-0ubuntu1                       i386         Simple clock
ii  indicator-sound                                     12.10.2+16.04.20160406-0ubuntu1                     i386         System sound indicator.
ii  libcairo-gobject2:i386                              1.14.6-1                                            i386         Cairo 2D vector graphics library (GObject library)
ii  libcairo2:i386                                      1.14.6-1                                            i386         Cairo 2D vector graphics library
ii  libck-connector0:i386                               0.4.6-5                                             i386         ConsoleKit libraries
ii  libcolamd2.9.1:i386                                 1:4.4.6-1                                           i386         column approximate minimum degree ordering library for sparse matrices
ii  libdaemon0:i386                                     0.14-6                                              i386         lightweight C library for daemons - runtime library
ii  libdrm-amdgpu1:i386                                 2.4.67-1ubuntu0.16.04.1                             i386         Userspace interface to amdgpu-specific kernel DRM services -- runtime
ii  libdrm-intel1:i386                                  2.4.67-1ubuntu0.16.04.1                             i386         Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau2:i386                                2.4.67-1ubuntu0.16.04.1                             i386         Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1:i386                                 2.4.67-1ubuntu0.16.04.1                             i386         Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libdrm2:i386                                        2.4.67-1ubuntu0.16.04.1                             i386         Userspace interface to kernel DRM services -- runtime
ii  libevdev2:i386                                      1.4.6+dfsg-1                                        i386         wrapper library for evdev devices
ii  libgpm2:i386                                        1.20.4-6.1                                          i386         General Purpose Mouse - shared library
ii  libltdl7:i386                                       2.4.6-0.1                                           i386         System independent dlopen wrapper for GNU libtool
ii  libminiupnpc10:i386                                 1.9.20140610-2ubuntu2                               i386         UPnP IGD client lightweight library
ii  libpam-ck-connector:i386                            0.4.6-5                                             i386         ConsoleKit PAM module
ii  libqtassistantclient4:i386                          4.6.3-7                                             i386         Qt Assistant client library (runtime)
ii  libsuitesparseconfig4.4.6:i386                      1:4.4.6-1                                           i386         configuration routines for all SuiteSparse modules
ii  linux-headers-4.6.0-040600                          4.6.0-040600.201606100558                           all          Header files related to Linux kernel version 4.6.0
ii  linux-headers-4.6.0-040600-generic                  4.6.0-040600.201606100558                           i386         Linux kernel headers for version 4.6.0 on 32 bit x86 SMP
ii  linux-image-4.6.0-040600-generic                    4.6.0-040600.201606100558                           i386         Linux kernel image for version 4.6.0 on 32 bit x86 SMP
ii  obex-data-server                                    0.4.6-0ubuntu4                                      i386         D-Bus service for OBEX client and server side functionality
ii  ubuntu-software                                     3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1 i386         Utility for browsing, installing, and removing software
ii  xserver-xorg-video-tdfx                             1:1.4.6-1build2                                     i386         X.Org X server -- tdfx display driver
rc@651650656:~$ 

```

Can I just use Synaptic and remove the 4.6* kernel while booted with 4.4?

---

### Post by jeremy31 on 2016-06-24
That should work

---

### Post by SlAiD on 2016-06-24
Hmm... I can't find the linux-headers for the 4.6 in Synaptic.

Any manual command to remove each of the ones I listed before?

If you wish I can open a new topic. Since the issue with the wiresless is resolved.

---

### Post by jeremy31 on 2016-06-24
See if ```
sudo dpkg -r linux-headers-4.6.0-040600
sudo dpkg -r linux-headers-4.6.0-040600-generic
```
Does the trick

---

### Post by SlAiD on 2016-06-24
I had to run the -generic first but it works.

Once again, thanks!

---

### Post by jeremy31 on 2016-06-24
Great, you can use thread tools near the top of the page to mark as solved

---

### Post by SlAiD on 2016-06-24
Done. Thanks!

---

