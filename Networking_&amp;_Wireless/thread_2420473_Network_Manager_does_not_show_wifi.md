---
title: "Network Manager does not show wifi"
date: 2019-06-06
forum: Networking &amp; Wireless
---

### Post by antoinepiro on 2019-06-06
Hello community,

I am a bit lost ... I don't know much in how all of this network stuff work and unfortunately for me after cleaning old kernel versions and rebooting I lost my wifi connection and do not seem to be able to reconnect !
I went through a lot of different posts but none seem to answer my problem for now .. :/
Indeed my network manager does not show any wifi and the command lshw -C network returns :

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Wireless 8265 / 8275
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3a:00.0
       version: 78
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:ec100000-ec101fff
  *-network
       description: Ethernet interface
       product: Ethernet Connection (4) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: enp0s31f6
       version: 21
       serial: 8c:16:45:22:ab:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k duplex=full firmware=0.1-4 ip=134.157.181.249 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:122 memory:ec200000-ec21ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

If you need me to run more command please let me know.

Thank you :)

---

### Post by jeremy31 on 2019-06-06
See the wireless script link in my signature and post results

---

### Post by antoinepiro on 2019-06-06
Hello Jeremy :) 

Here are the info :

```
########## wireless info START ##########

Report from: 06 Jun 2019 12:24 CEST +0200

Booted last: 06 Jun 2019 00:00 CEST +0200

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.15.0-38-generic #41~16.04.1-Ubuntu SMP Wed Oct 10 20:16:04 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-V [8086:15d8] (rev 21)
	Subsystem: Lenovo Ethernet Connection (4) I219-V [17aa:224b]
	Kernel driver in use: e1000e

3a:00.0 Network controller [0280]: Intel Corporation Wireless 8265 / 8275 [8086:24fd] (rev 78)
	Subsystem: Intel Corporation Dual Band Wireless-AC 8265 [8086:1010]
	Kernel modules: iwlwifi, wl

##### lsusb #############################

Bus 002 Device 002: ID 0bda:0316 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 138a:0097 Validity Sensors, Inc. 
Bus 001 Device 004: ID 04f2:b5ab Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 89e5:101b  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

wl                   6447104  0
iwlwifi               282624  0
intel_wmi_thunderbolt    16384  0
wmi_bmof               16384  0
cfg80211              622592  2 wl,iwlwifi
wmi                    24576  2 intel_wmi_thunderbolt,wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 134.157.181.249/26 brd 134.157.181.255 scope global dynamic enp0s31f6
       valid_lft 13635sec preferred_lft 13635sec
    inet6 fe80::dd3f:886d:dfa4:221b/64 scope link 
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether <MAC 'docker0' [IF2]> brd <MAC address>
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

docker0   no wireless extensions.

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 134.157.181.254 dev enp0s31f6  proto static  metric 100 
134.157.181.192/26 dev enp0s31f6  proto kernel  scope link  src 134.157.181.249  metric 100 
169.254.0.0/16 dev enp0s31f6  scope link  metric 1000 
172.17.0.0/16 dev docker0  proto kernel  scope link  src 172.17.0.1 linkdown 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']
nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1020     1  0 12:11 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/docker0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       00e67741-a5e6-42b3-a8f3-94f84249585d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{19}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   00e67741-a5e6-42b3-a8f3-94f84249585d | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (4) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       1939642e-d6ea-3604-8a74-f5f802706e29
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{18}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1939642e-d6ea-3604-8a74-f5f802706e29 | Wired connection 1
IP4.ADDRESS[1]:                         134.157.181.249/26
IP4.GATEWAY:                            134.157.181.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             134.157.181.102
IP4.DNS[2]:                             134.157.0.129
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1559830287
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 14400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 134.157.181.249
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 7200
DHCP4.OPTION[19]:                       routers = 134.157.181.254
DHCP4.OPTION[20]:                       broadcast_address = 134.157.181.255
DHCP4.OPTION[21]:                       domain_name_servers = 134.157.181.102 134.157.0.129
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 12600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.192
DHCP4.OPTION[27]:                       network_number = 134.157.181.192
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 134.157.181.222
IP6.ADDRESS[1]:                         fe80::dd3f:886d:dfa4:221b/64
IP6.GATEWAY:                            

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/10-ubuntu-fan.conf]]
[keyfile]
unmanaged-devices+=interface-name:fan-*

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/_SNCF_WIFI_INOUI]] (600 root)
[connection] id=_SNCF_WIFI_INOUI | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=_SNCF_WIFI_INOUI
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Honor 5C]] (600 root)
[connection] id=Honor 5C | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Honor 5C
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/G6_2325]] (600 root)
[connection] id=G6_2325 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=G6_2325
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KEENEYE-WIFI-2]] (600 root)
[connection] id=KEENEYE-WIFI-2 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=KEENEYE-WIFI-2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KEENEYE-WIFI-5]] (600 root)
[connection] id=KEENEYE-WIFI-5 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=KEENEYE-WIFI-5
[ipv4] method=manual
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone de Thomas]] (600 root)
[connection] id=iPhone de Thomas | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iPhone de Thomas
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AP-Badge-GK]] (600 root)
[connection] id=AP-Badge-GK | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=AP-Badge-GK
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR01]] (600 root)
[connection] id=NETGEAR01 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR01
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR01-5G]] (600 root)
[connection] id=NETGEAR01-5G | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR01-5G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Le Château]] (600 root)
[connection] id=Le Château | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=76;101;32;67;104;195;162;116;101;97;117;
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iMac de Emmeline]] (600 root)
[connection] id=iMac de Emmeline | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=iMac de Emmeline
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Bbox-9DA6552C]] (600 root)
[connection] id=Bbox-9DA6552C | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Bbox-9DA6552C
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-B055]] (600 root)
[connection] id=Livebox-B055 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-B055
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=dlink
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Livebox-3916]] (600 root)
[connection] id=Livebox-3916 | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Livebox-3916
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SFR-66af]] (600 root)
[connection] id=SFR-66af | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SFR-66af
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ENAC_Auth]] (600 root)
[connection] id=ENAC_Auth | type=wifi | permissions=user:antoine:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ENAC_Auth
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

docker0   no frequency information.

enp0s31f6  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

docker0   Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.15.0-38-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-38-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[iwlwifi]
filename:       /lib/modules/4.15.0-38-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     C57A4F9C9842C4EC8599634
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-38-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/r8168-dkms.conf]
alias	pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*	r8168
alias	pci:v000010ECd00008168sv*sd*bc*sc*i*			r8168

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  148.171033] iwlwifi 0000:3a:00.0: enabling device (0000 -> 0002)
[  148.176256] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-34.ucode failed with error -2
[  148.176444] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-33.ucode failed with error -2
[  148.176764] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-32.ucode failed with error -2
[  148.176973] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-31.ucode failed with error -2
[  148.177644] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-30.ucode failed with error -2
[  148.177654] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-29.ucode failed with error -2
[  148.177660] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-28.ucode failed with error -2
[  148.177666] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-27.ucode failed with error -2
[  148.177671] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-26.ucode failed with error -2
[  148.177677] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-25.ucode failed with error -2
[  148.177681] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-24.ucode failed with error -2
[  148.177686] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-23.ucode failed with error -2
[  148.177692] iwlwifi 0000:3a:00.0: Direct firmware load for iwlwifi-8265-22.ucode failed with error -2
[  148.177693] iwlwifi 0000:3a:00.0: no suitable firmware found!
[  148.177696] iwlwifi 0000:3a:00.0: minimum version required: iwlwifi-8265-22
[  148.177697] iwlwifi 0000:3a:00.0: maximum version supported: iwlwifi-8265-34
[  148.177699] iwlwifi 0000:3a:00.0: check git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
[  148.270937] wl: loading out-of-tree module taints kernel.
[  148.270940] wl: module license 'MIXED/Proprietary' taints kernel.
[  148.276676] wl: module verification failed: signature and/or required key missing - tainting kernel
[  149.313166] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[  152.942598] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  152.942643] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[  160.603083] IPv6: ADDRCONF(NETDEV_UP): docker0: link is not ready

########## wireless info END ############
```

Hope that is what you expected

---

### Post by jeremy31 on 2019-06-06
Try ```
sudo apt remove bcmwl-kernel-source && sudo apt install --reinstall linux-firmware
```
Reboot

---

### Post by antoinepiro on 2019-06-06
Wow :) Thx so much !
Could you explain what does these two commands do so i can understand what did i do wrong please ? :)

---

### Post by jeremy31 on 2019-06-06
You had a broadcom driver installed and the firmware for the Intel wifi was missing

---

### Post by antoinepiro on 2019-06-06
Got it ! Thank you again :)

---

