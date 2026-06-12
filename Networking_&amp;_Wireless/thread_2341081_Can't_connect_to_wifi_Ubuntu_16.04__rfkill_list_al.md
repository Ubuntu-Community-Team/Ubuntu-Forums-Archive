---
title: "Can't connect to wifi: Ubuntu 16.04 : rfkill list all doesn't show wireless"
date: 2016-10-24
forum: Networking &amp; Wireless
---

### Post by renato-francia on 2016-10-24
Hi
I have an Intel  Wireless 3160 in my Dell laptop and recently, after trying to fix my bluetooth, I've lost my wireless. 

The weird part is that when I run this command 

[HTML] lshw -C network[/HTML]
The Network detects my hardware: 

```
*-network               
       description: Network controller
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 83
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:280 memory:d2100000-d2101fff

```

But when running [HTML]rfkill list all[/HTML]  the results are the following: 

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no



```

Here's the output of my wireless analysis 

```


########## wireless info START ##########


Report from: 24 Oct 2016 13:59 PET -0500


Booted last: 24 Oct 2016 00:00 PET -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
	Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:06b2]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:07dc Intel Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 064e:920b Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


mac80211              651264  0
dell_laptop            20480  0
dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dcdbas                 16384  1 dell_laptop
iwlwifi               200704  0
cfg80211              552960  2 iwlwifi,mac80211
compat                 16384  2 cfg80211,mac80211
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915_bpo,dell_wmi,dell_laptop


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d197:7fb3:c56a:b22b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66399642 (66.3 MB)  TX bytes:4113809 (4.1 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search cpe.tdp.com


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1014     1  0 13:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       92726cca-de3e-3a34-a296-74024b801bbf
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{31}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   92726cca-de3e-3a34-a296-74024b801bbf | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.9/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.48.225.130
IP4.DNS[2]:                             200.48.225.146
IP4.DOMAIN[1]:                          cpe.tdp.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 200.48.225.130 200.48.225.146
DHCP4.OPTION[5]:                        ip_address = 192.168.1.9
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.1.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = cpe.tdp.com
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1477338621
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.1.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::d197:7fb3:c56a:b22b/64
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


[[/etc/NetworkManager/system-connections/Sarcletti]] (600 root)
[connection] id=Sarcletti | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Sarcletti
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/M TRAVEL & SERVICES]] (600 root)
[connection] id=M TRAVEL & SERVICES | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=M TRAVEL & SERVICES
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GFOFICINA]] (600 root)
[connection] id=GFOFICINA | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=GFOFICINA
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PASTIPAN]] (600 root)
[connection] id=PASTIPAN | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PASTIPAN
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AIRAMPO]] (600 root)
[connection] id=AIRAMPO | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AIRAMPO
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WeWork 2.4 ghz]] (600 root)
[connection] id=WeWork 2.4 ghz | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WeWork 2.4 ghz
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-F49E-5]] (600 root)
[connection] id=HOME-F49E-5 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-F49E-5
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=attwifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/360-Cafe]] (600 root)
[connection] id=360-Cafe | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=360-Cafe
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GFPrimavera02]] (600 root)
[connection] id=GFPrimavera02 | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=GFPrimavera02
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TocumenFree]] (600 root)
[connection] id=TocumenFree | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TocumenFree
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/loganwifi]] (600 root)
[connection] id=loganwifi | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=loganwifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-CFA2]] (600 root)
[connection] id=ARRIS-CFA2 | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ARRIS-CFA2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/COKI112]] (600 root)
[connection] id=COKI112 | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=COKI112
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WWGuest]] (600 root)
[connection] id=WWGuest | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WWGuest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TONY REGALADO PATISSERIE]] (600 root)
[connection] id=TONY REGALADO PATISSERIE | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=TONY REGALADO PATISSERIE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-FF65-2.4]] (600 root)
[connection] id=HOME-FF65-2.4 | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-FF65-2.4
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SJU-AIRPORT]] (600 root)
[connection] id=SJU-AIRPORT | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SJU-AIRPORT
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-F49E-2.4]] (600 root)
[connection] id=HOME-F49E-2.4 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-F49E-2.4
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ATL Free Wi-Fi]] (600 root)
[connection] id=ATL Free Wi-Fi | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ATL Free Wi-Fi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/LA MORA]] (600 root)
[connection] id=LA MORA | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=LA MORA
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Cherie we're home]] (600 root)
[connection] id=Cherie we're home | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Cherie we're home
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/RED_STB]] (600 root)
[connection] id=RED_STB | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=RED_STB
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Google Starbucks
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PEETS]] (600 root)
[connection] id=PEETS | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=PEETS
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MarketStreet]] (600 root)
[connection] id=MarketStreet | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MarketStreet
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ARRIS-C7A2]] (600 root)
[connection] id=ARRIS-C7A2 | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ARRIS-C7A2
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-F49E-2.4 1]] (600 root)
[connection] id=HOME-F49E-2.4 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HOME-F49E-2.4
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ogawa-Coffee]] (600 root)
[connection] id=Ogawa-Coffee | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Ogawa-Coffee
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Olo Router]] (600 root)
[connection] id=Olo Router | type=wifi | permissions=user:renato:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Olo Router
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Lima (based on set time zone)


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


enp3s0    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


##### module infos ######################


[mac80211]
filename:       /lib/modules/4.4.0-45-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
srcversion:     0059B10CD5F6F6A14631DC4
depends:        cfg80211,compat
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-45-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.2.6-0-g1c02865) using backports v4.2.6-1-0-g90118c7
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     6BE4ED42578C9DFBE16CE50
depends:        compat
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
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


[/etc/modprobe.d/iwl-legacy.conf]
options iwl-legacy led_mode=1


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


[   41.185308] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   41.664765] r8169 0000:03:00.0 enp3s0: link down (repeated 2 times)
[   41.664846] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 1681.902273] r8169 0000:03:00.0 enp3s0: link up
[ 1681.902296] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 1731.448313] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1731.448874] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1731.448901] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1731.448917] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1857.464677] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1857.465243] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1857.465253] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1857.465261] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1983.481365] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1983.481373] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1983.481379] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 1983.481383] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2109.497622] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2109.498180] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2109.498214] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[ 2109.498240] [UFW BLOCK] IN=enp3s0 OUT= MAC=01:00:5e:00:00:01:d0:84:b0:8e:38:88:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 


########## wireless info END ############



```


I appreciate any input. Thanks! :)

---

### Post by jeremy31 on 2016-10-24
Did you install backports from a 4.2.6 kernel to try to get bluetooth going?  Uninstall the backports and reboot and the wifi should work.  Right now you likely have a conflict between cfg80211 and iwlwifi/iwlmvm and it doesn't even appear to try loading the wifi firmware

---

### Post by renato-francia on 2016-10-24
Thanks Jeremy31 for the quick reply. I'm kind of a newbie when it comes to setting things up. How do you uninstall the backports and where can I reinstall it?  

Best,

---

### Post by jeremy31 on 2016-10-24
You should be able to find with ```
locate backports
```
Post results

---

### Post by renato-francia on 2016-10-24
Hi, 

Here are the results

```

/etc/modprobe.d/backports.conf
/home/renato/.berkshelf/cookbooks/poise-2.7.1/files/halite_gem/poise/backports
/home/renato/.berkshelf/cookbooks/poise-2.7.1/files/halite_gem/poise/backports.rb
/home/renato/.berkshelf/cookbooks/poise-2.7.1/files/halite_gem/poise/backports/not_passed.rb
/home/renato/.berkshelf/cookbooks/poise-2.7.1/files/halite_gem/poise/backports/verify_path.rb
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/_markupbase.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/datetime.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/html
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/misc.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/socket.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/socketserver.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/total_ordering.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/xmlrpc
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/_encoded_words.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/_header_value_parser.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/_parseaddr.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/_policybase.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/base64mime.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/charset.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/encoders.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/errors.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/feedparser.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/generator.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/header.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/headerregistry.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/iterators.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/message.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/parser.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/policy.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/quoprimime.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/utils.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/application.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/audio.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/base.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/image.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/message.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/multipart.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/nonmultipart.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/email/mime/text.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/html/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/html/entities.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/html/parser.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http/client.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http/cookiejar.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http/cookies.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/http/server.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/badcert.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/badkey.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/dh512.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/https_svn_python_org_root.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/keycert.passwd.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/keycert.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/keycert2.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/nokia.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/nullbytecert.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/nullcert.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/pystone.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/sha256.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/ssl_cert.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/ssl_key.passwd.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/ssl_key.pem
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/ssl_servers.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/test/support.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/error.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/parse.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/request.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/response.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/urllib/robotparser.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/xmlrpc/__init__.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/xmlrpc/client.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/src/future/backports/xmlrpc/server.py
/home/renato/.vim/bundle/youcompleteme/third_party/ycmd/third_party/python-future/tests/test_future/test_backports.py
/home/renato/Downloads/backports-3.16-1
/home/renato/Downloads/backports-3.16-1.tar.xz
/usr/lib/python2.7/dist-packages/twisted/conch/ssh/_cryptography_backports.py
/usr/lib/python2.7/dist-packages/twisted/conch/ssh/_cryptography_backports.pyc
/usr/local/rvm/gems/ruby-2.3.1/gems/rack-1.6.4/lib/rack/backports
/usr/local/rvm/gems/ruby-2.3.1/gems/rack-1.6.4/lib/rack/backports/uri
/usr/local/rvm/gems/ruby-2.3.1/gems/rack-1.6.4/lib/rack/backports/uri/common_18.rb
/usr/local/rvm/gems/ruby-2.3.1/gems/rack-1.6.4/lib/rack/backports/uri/common_192.rb
/usr/local/rvm/gems/ruby-2.3.1/gems/rack-1.6.4/lib/rack/backports/uri/common_193.rb
/usr/share/doc/xorg/reference/squeeze-backports.html
/usr/share/doc/xorg/reference/squeeze-backports.txt
/var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz
/var/lib/app-info/yaml/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_InRelease
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-amd64_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_i18n_Translation-en
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_main_source_Sources
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-amd64_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-i386_Packages
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_i18n_Translation-en
/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_InRelease
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_main_source_Sources
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_multiverse_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_restricted_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-amd64_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_binary-i386_Packages
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_dep11_Components-amd64.yml.gz
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_i18n_Translation-en
/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_xenial-backports_universe_source_Sources
/var/lib/gems/2.3.0/gems/puma-3.4.0/lib/puma/rack/backports
/var/lib/gems/2.3.0/gems/puma-3.4.0/lib/puma/rack/backports/uri
/var/lib/gems/2.3.0/gems/puma-3.4.0/lib/puma/rack/backports/uri/common_18.rb
/var/lib/gems/2.3.0/gems/puma-3.4.0/lib/puma/rack/backports/uri/common_192.rb
/var/lib/gems/2.3.0/gems/puma-3.4.0/lib/puma/rack/backports/uri/common_193.rb
/var/lib/gems/2.3.0/gems/puma-3.5.0/lib/puma/rack/backports
/var/lib/gems/2.3.0/gems/puma-3.5.0/lib/puma/rack/backports/uri
/var/lib/gems/2.3.0/gems/puma-3.5.0/lib/puma/rack/backports/uri/common_18.rb
/var/lib/gems/2.3.0/gems/puma-3.5.0/lib/puma/rack/backports/uri/common_192.rb
/var/lib/gems/2.3.0/gems/puma-3.5.0/lib/puma/rack/backports/uri/common_193.rb
/var/lib/gems/2.3.0/gems/puma-3.6.0/lib/puma/rack/backports
/var/lib/gems/2.3.0/gems/puma-3.6.0/lib/puma/rack/backports/uri
/var/lib/gems/2.3.0/gems/puma-3.6.0/lib/puma/rack/backports/uri/common_18.rb
/var/lib/gems/2.3.0/gems/puma-3.6.0/lib/puma/rack/backports/uri/common_192.rb
/var/lib/gems/2.3.0/gems/puma-3.6.0/lib/puma/rack/backports/uri/common_193.rb
/var/lib/gems/2.3.0/gems/rack-1.6.4/lib/rack/backports
/var/lib/gems/2.3.0/gems/rack-1.6.4/lib/rack/backports/uri
/var/lib/gems/2.3.0/gems/rack-1.6.4/lib/rack/backports/uri/common_18.rb
/var/lib/gems/2.3.0/gems/rack-1.6.4/lib/rack/backports/uri/common_192.rb
/var/lib/gems/2.3.0/gems/rack-1.6.4/lib/rack/backports/uri/common_193.rb
/var/www/github/pentest-env/cookbooks/poise/files/halite_gem/poise/backports
/var/www/github/pentest-env/cookbooks/poise/files/halite_gem/poise/backports.rb
/var/www/github/pentest-env/cookbooks/poise/files/halite_gem/poise/backports/not_passed.rb
/var/www/github/pentest-env/cookbooks/poise/files/halite_gem/poise/backports/verify_path.rb

```

---

### Post by jeremy31 on 2016-10-25
Lets see ```
history | grep backport
```

Did the computer have Ubuntu on it when you bought it?

---

### Post by renato-francia on 2016-10-25
Nope. It came with Windows(Which I use mainly for gaming) and installed ubuntu in a partition I created. 

```

 1901  cd ~/Desktop/backports-3.16-1
 1911  tar xvf backports-3.16-1.tar.xz backports-3.16-1/
 1913  cd backports-3.16-1/
 1993  locate backports
 1994  locate backports < backports.txt
 1995  locate backports > backports.txt
 1997  vim backports.txt 
 1998  gedit backports.txt 
 2001  history | grep backport
 2005  history | grep backport



```

---

### Post by jeremy31 on 2016-10-25
Might as well try this
```
cd ~/Desktop/backports-3.16-1
sudo make uninstall
```

Reboot

I am a bit confused as I expected to see backports-4.2.6-1 being listed somewhere, with any luck removing the 3.16 backports will return the original kernel modules

---

### Post by renato-francia on 2016-10-25
I'm current getting this error. 

```

Generating local configuration database from kernel ...Kernel version parse failed!
Makefile:40: recipe for target 'uninstall' failed
make: *** [uninstall] Error 1

```

Plus these backlogs not installed and put there. These are just packages that I downloaded temporarily to see them :)

---

### Post by jeremy31 on 2016-10-26
Post results for ```
dkms status
```

Since you have a dual boot, use the Grub menu to select Advanced Options for Ubuntu and boot into an older kernel if there is one avaiable, see if wireless works

---

### Post by renato-francia on 2016-10-26
Hi, 
It worked when I login into a previous version of ubuntu. Is there a way to revert or this is not recommended? 

```

btusb-lp1542743, 0.1, 4.4.0-43-generic, x86_64: installed
btusb-lp1542743, 0.1, 4.4.0-45-generic, x86_64: installed
virtualbox, 5.0.24, 4.4.0-43-generic, x86_64: installed
virtualbox, 5.0.24, 4.4.0-45-generic, x86_64: installed

```

Best,

---

### Post by jeremy31 on 2016-10-27
The safest option would be to ```
wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v4.2.6/backports-4.2.6-1.tar.gz
tar -zxvf backports-4.2.6-1.tar.gz
```

Reboot into the 4.4.0-45 kernel, then
```
cd backports-4.2.6-1
sudo make uninstall
```
With a little luck it should replace the correct modules and wifi will work after a reboot

---

### Post by renato-francia on 2016-10-27
Tried that. Unfortunately, it didn't work. 

Then I tried to revert back and install bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb but no luck so far :( .

---

### Post by jeremy31 on 2016-10-28
> **renato-francia said:**
> Tried that. Unfortunately, it didn't work. 

Then I tried to revert back and install bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.1_amd64.deb but no luck so far :( .
bcmwl-kernel-source will do no good as you have an Intel wifi device, bcmwl only works for some Broadcom wifi

When booted into an older kernel, do ```
sudo apt-get install --reinstall linux-image-4.4.0-45-generic linux-image-extra-4.4.0-45-generic
```
Reboot

---

### Post by renato-francia on 2016-11-02
I've tried this 
```

[COLOR=#000000][FONT=&quot]sudo apt-get install --reinstall linux-image-4.4.0-21-generic linux-image-extra-4.4.0-21-generic[/FONT][/COLOR]

```

Since [COLOR=#000000][FONT=&quot]image-4.4.0-21-generic was the one image where the wifi worked. 

Unfortunately  this didn't solve the problem [/FONT][/COLOR]

---

### Post by jeremy31 on 2016-11-02
You need to try running the command I posted while using 4.4.0-21 as you need to repair the -45 kernel modules. It will be fixed with the next kernel through normal updates

---

### Post by renato-francia on 2016-11-17
Hi, I've been using using an old version of my kernel and tried to use the command but still no wifi. I've noticed that there was an error when finding the kernel's headers. I'm not very proficient in Ubuntu so I don't know if this is what is causing the problem. 

I've taken the time to dig the headers and understand that they are files that define an interface for the functions in the system. Since it's not defined, maybe this is the problem? Any help would be appreciated 


```

Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/57.5 MB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 307688 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-21-generic_4.4.0-21.37_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Done.
Unpacking linux-image-4.4.0-21-generic (4.4.0-21.37) over (4.4.0-21.37) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Preparing to unpack .../linux-image-extra-4.4.0-21-generic_4.4.0-21.37_amd64.deb ...
Unpacking linux-image-extra-4.4.0-21-generic (4.4.0-21.37) over (4.4.0-21.37) ...
Setting up linux-image-4.4.0-21-generic (4.4.0-21.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(4.4.0-21.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(4.4.0-21.37 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-4.4.0-47-generic
Found kernel: /boot/vmlinuz-4.4.0-45-generic
Found kernel: /boot/vmlinuz-4.4.0-21-generic
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-4.4.0-47-generic
Found kernel: /boot/vmlinuz-4.4.0-45-generic
Found kernel: /boot/vmlinuz-4.4.0-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


Setting up linux-image-extra-4.4.0-21-generic (4.4.0-21.37) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.4.0-21-generic cannot be found.
Please install the linux-headers-4.4.0-21-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-21-generic /boot/vmlinuz-4.4.0-21-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-4.4.0-47-generic
Found kernel: /boot/vmlinuz-4.4.0-45-generic
Found kernel: /boot/vmlinuz-4.4.0-21-generic
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-4.4.0-47-generic
Found kernel: /boot/vmlinuz-4.4.0-45-generic
Found kernel: /boot/vmlinuz-4.4.0-21-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


```

---

### Post by jeremy31 on 2016-11-18
It looks like you now have the 4.4.0-47 kernel, does it work?

---

