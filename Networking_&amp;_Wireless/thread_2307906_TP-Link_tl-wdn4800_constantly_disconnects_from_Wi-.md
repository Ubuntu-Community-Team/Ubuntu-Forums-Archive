---
title: "TP-Link tl-wdn4800 constantly disconnects from Wi-Fi [15.10 64bit]"
date: 2015-12-29
forum: Networking &amp; Wireless
---

### Post by lucas52 on 2015-12-29
Hi, as the name of the thread says, I'm having this trouble that wasn't present on 14.04, here is my wireless-info:


> 


########## wireless info START ########## 




Report from: 29 Dec 2015 12:43 ART -0300




Booted last: 29 Dec 2015 00:00 ART -0300




Script from: 27 Sep 2015 00:34 UTC +0000




##### release ###########################




Distributor ID: Ubuntu
Description: Ubuntu 15.10
Release: 15.10
Codename: wily




##### kernel ############################




Linux 4.2.0-22-generic #27-Ubuntu SMP Thu Dec 17 22:57:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux




Parameters: ro, quiet, splash, vt.handoff=7




##### desktop ###########################




Ubuntu




##### lspci #############################




00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
DeviceName: Onboard LAN
Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]




01:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
Subsystem: Qualcomm Atheros Device [168c:3112]
Kernel driver in use: ath9k




##### lsusb #############################




Bus 004 Device 002: ID 8087:8001 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8009 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c07d Logitech, Inc. 
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




##### PCMCIA card info ##################




##### rfkill ############################




0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no




##### lsmod #############################




eeepc_wmi 16384 0
asus_wmi 28672 1 eeepc_wmi
sparse_keymap 16384 1 asus_wmi
ath9k 147456 0
ath9k_common 36864 1 ath9k
ath9k_hw 471040 2 ath9k_common,ath9k
ath 32768 3 ath9k_common,ath9k,ath9k_hw
mac80211 733184 1 ath9k
cfg80211 548864 4 ath,ath9k_common,ath9k,mac80211
mxm_wmi 16384 0
wmi 20480 2 mxm_wmi,asus_wmi
video 36864 1 asus_wmi




##### interfaces ########################




auto lo
iface lo inet loopback




##### ifconfig ##########################




eno1 Link encap:Ethernet HWaddr <MAC 'eno1' [IF]> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Memory:f7f00000-f7f20000 




wlp1s0 Link encap:Ethernet HWaddr <MAC 'wlp1s0' [IF]> 
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::<IP6 'wlp1s0' [IF]>/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:19516 errors:0 dropped:0 overruns:0 frame:0
TX packets:11751 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:15161473 (15.1 MB) TX bytes:1897723 (1.8 MB)




##### iwconfig ##########################




eno1 no wireless extensions.




lo no wireless extensions.




wlp1s0 IEEE 802.11abgn ESSID:"GravityL" 
Mode:Managed Frequency:2.462 GHz Access Point: <MAC 'GravityL' [AN3]> 
Bit Rate=120 Mb/s Tx-Power=16 dBm 
Retry short limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=61/70 Signal level=-49 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:57 Missed beacon:0




##### route #############################




Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 600 0 0 wlp1s0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlp1s0
192.168.0.0 0.0.0.0 255.255.255.0 U 600 0 0 wlp1s0




##### resolv.conf #######################




nameserver 127.0.1.1




##### network managers ##################




Installed:




NetworkManager




Running:




root 759 1 0 10:52 ? 00:00:01 /usr/sbin/NetworkManager --no-daemon




##### NetworkManager info ###############




GENERAL.DEVICE: wlp1s0
GENERAL.TYPE: wifi
GENERAL.NM-TYPE: NMDeviceWifi
GENERAL.VENDOR: Qualcomm Atheros
GENERAL.PRODUCT: AR93xx Wireless Network Adapter
GENERAL.DRIVER: ath9k
GENERAL.DRIVER-VERSION: 4.2.0-22-generic
GENERAL.FIRMWARE-VERSION: N/A
GENERAL.HWADDR: <MAC 'wlp1s0' [IF]>
GENERAL.MTU: 0
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE: wlp1s0
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: GravityL
GENERAL.CON-UUID: e7bd9a26-1710-45e1-b029-edf62db0a3f2
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/3
CAPABILITIES.CARRIER-DETECT: no
CAPABILITIES.SPEED: 150 Mb/s
CAPABILITIES.IS-SOFTWARE: no
WIFI-PROPERTIES.WEP: yes
WIFI-PROPERTIES.WPA: yes
WIFI-PROPERTIES.WPA2: yes
WIFI-PROPERTIES.TKIP: yes
WIFI-PROPERTIES.CCMP: yes
WIFI-PROPERTIES.AP: yes
WIFI-PROPERTIES.ADHOC: yes
WIFI-PROPERTIES.2GHZ: yes
WIFI-PROPERTIES.5GHZ: yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: e7bd9a26-1710-45e1-b029-edf62db0a3f2 | GravityL
IP4.ADDRESS[1]: 192.168.0.100/24
IP4.GATEWAY: 192.168.0.1
IP4.ROUTE[1]: dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]: 192.168.0.1
IP4.DNS[2]: 8.8.8.8
DHCP4.OPTION[1]: network_number = 192.168.0.0
DHCP4.OPTION[2]: requested_domain_search = 1
DHCP4.OPTION[3]: requested_host_name = 1
DHCP4.OPTION[4]: requested_time_offset = 1
DHCP4.OPTION[5]: requested_broadcast_address = 1
DHCP4.OPTION[6]: requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]: requested_domain_name = 1
DHCP4.OPTION[8]: expiry = 1451404369
DHCP4.OPTION[9]: requested_wpad = 1
DHCP4.OPTION[10]: next_server = 192.168.0.1
DHCP4.OPTION[11]: broadcast_address = 192.168.0.255
DHCP4.OPTION[12]: dhcp_message_type = 5
DHCP4.OPTION[13]: requested_subnet_mask = 1
DHCP4.OPTION[14]: routers = 192.168.0.1
DHCP4.OPTION[15]: dhcp_lease_time = 600
DHCP4.OPTION[16]: ip_address = 192.168.0.100
DHCP4.OPTION[17]: subnet_mask = 255.255.255.0
DHCP4.OPTION[18]: requested_static_routes = 1
DHCP4.OPTION[19]: requested_domain_name_servers = 1
DHCP4.OPTION[20]: domain_name_servers = 192.168.0.1 8.8.8.8
DHCP4.OPTION[21]: requested_netbios_scope = 1
DHCP4.OPTION[22]: requested_netbios_name_servers = 1
DHCP4.OPTION[23]: requested_ntp_servers = 1
DHCP4.OPTION[24]: requested_routers = 1
DHCP4.OPTION[25]: requested_interface_mtu = 1
DHCP4.OPTION[26]: requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]: ntp_servers = 200.192.232.8 190.228.30.178
DHCP4.OPTION[28]: dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]: fe80::<IP6 'wlp1s0' [IF]>/64
IP6.GATEWAY: 




GENERAL.DEVICE: eno1
GENERAL.TYPE: ethernet
GENERAL.NM-TYPE: NMDeviceEthernet
GENERAL.VENDOR: Intel Corporation
GENERAL.PRODUCT: Ethernet Connection (2) I218-V
GENERAL.DRIVER: e1000e
GENERAL.DRIVER-VERSION: 3.2.5-k
GENERAL.FIRMWARE-VERSION: 0.1-4
GENERAL.HWADDR: <MAC 'eno1' [IF]>
GENERAL.MTU: 1500
GENERAL.STATE: 20 (unavailable)
GENERAL.REASON: 2 (Device is now managed)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:19.0/net/eno1
GENERAL.IP-IFACE: 
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: --
GENERAL.CON-UUID: --
GENERAL.CON-PATH: --
CAPABILITIES.CARRIER-DETECT: yes
CAPABILITIES.SPEED: unknown
CAPABILITIES.IS-SOFTWARE: no
WIRED-PROPERTIES.CARRIER: off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 




SSID BSSID MODE CHAN FREQ RATE SIGNAL BARS SECURITY ACTIVE * 
cristian <MAC 'cristian' [AN1]> Infra 11 2462 MHz 54 Mbit/s 50 &#9602;&#9604;__ WEP no 
mateo10 <MAC 'mateo10' [AN2]> Infra 6 2437 MHz 54 Mbit/s 34 &#9602;&#9604;__ WEP no 
GravityL <MAC 'GravityL' [AN3]> Infra 11 2462 MHz 54 Mbit/s 72 &#9602;&#9604;&#9606;_ WPA2 yes * 




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
managed=true




##### NetworkManager profiles ###########




[[/etc/NetworkManager/system-connections/GravityL]] (600 root)
[connection] id=GravityL | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=GravityL
[ipv4] method=auto
[ipv6] method=ignore




##### iw reg get ########################




Region: America/Argentina/Buenos_Aires (based on set time zone)




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




eno1 no frequency information.




lo no frequency information.




wlp1s0 32 channels in total; available frequencies :
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
Current Frequency:2.462 GHz (Channel 11)




##### iwlist scan #######################




wlp1s0 Interface doesn't support scanning : Device or resource busy




eno1 Interface doesn't support scanning.




lo Interface doesn't support scanning.




##### module infos ######################




[ath9k]
filename: /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless LAN cards.
author: Atheros Communications
srcversion: 681B59FC4C4EB63D7B98108
depends: ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512
parm: debugebugging mask (uint)
parm: nohwcryptisable hardware encryption (int)
parm: blink:Enable LED blink on activity (int)
parm: btcoex_enable:Enable wifi-BT coexistence (int)
parm: bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm: ps_enable:Enable WLAN PowerSave (int)
parm: use_chanctx:Enable channel context for concurrency (int)




[ath9k_common]
filename: /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license: Dual BSD/GPL
description: Shared library for Atheros wireless 802.11n LAN cards.
author: Atheros Communications
srcversion: 619327754B562F78060585E
depends: ath9k_hw,cfg80211,ath
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512




[ath9k_hw]
filename: /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless LAN cards.
author: Atheros Communications
srcversion: F987BF2735D3EF13C4E4E3D
depends: ath
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512




[ath]
filename: /lib/modules/4.2.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license: Dual BSD/GPL
description: Shared library for Atheros wireless LAN cards.
author: Atheros Communications
srcversion: F1417AD8012BEEF1598B307
depends: cfg80211
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512




[mac80211]
filename: /lib/modules/4.2.0-22-generic/kernel/net/mac80211/mac80211.ko
license: GPL
description: IEEE 802.11 subsystem
srcversion: 065F4A11FE84275F51A59F2
depends: cfg80211
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512
parm: minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm: max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm: max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm: beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm: probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm: ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)




[cfg80211]
filename: /lib/modules/4.2.0-22-generic/kernel/net/wireless/cfg80211.ko
description: wireless configuration support
license: GPL
author: Johannes Berg
srcversion: 1F1A25B2E9C847110BD9ED9
depends: 
intree: Y
vermagic: 4.2.0-22-generic SMP mod_unload modversions 
signer: Build time autogenerated kernel key
sig_key: 5B:A1:35:31:092:78:49D6:FB5:54:A5:53:44:38:BE:AF:AB
sig_hashalgo: sha512
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)




##### module parameters #################




[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
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




[ 1.955000] ath: EEPROM regdomain: 0x21
[ 1.955001] ath: EEPROM indicates we should expect a direct regpair map
[ 1.955002] ath: Country alpha2 being used: AU
[ 1.955002] ath: Regpair used: 0x21
[ 2.414796] ath9k 0000:01:00.0 wlp1s0: renamed from wlan0
[ 3.721239] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[ 3.948764] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[ 6.896675] wlp1s0: authenticate with <MAC 'GravityL' [AN3]>
[ 6.902779] wlp1s0: send auth to <MAC 'GravityL' [AN3]> (try 1/3)
[ 6.905507] wlp1s0: authenticated
[ 6.909257] wlp1s0: associate with <MAC 'GravityL' [AN3]> (try 1/3)
[ 6.915269] wlp1s0: RX AssocResp from <MAC 'GravityL' [AN3]> (capab=0x431 status=0 aid=2)
[ 6.915316] wlp1s0: associated
[ 6.915329] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[ 6605.061462] wlp1s0: deauthenticating from <MAC 'GravityL' [AN3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6607.366160] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[ 6607.922962] wlp1s0: authenticate with <MAC 'GravityL' [AN3]>
[ 6607.931666] wlp1s0: send auth to <MAC 'GravityL' [AN3]> (try 1/3)
[ 6607.933550] wlp1s0: authenticated
[ 6607.934646] wlp1s0: associate with <MAC 'GravityL' [AN3]> (try 1/3)
[ 6607.945392] wlp1s0: RX AssocResp from <MAC 'GravityL' [AN3]> (capab=0x431 status=0 aid=1)
[ 6607.945438] wlp1s0: associated
[ 6607.945445] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[ 6609.031047] wlp1s0: deauthenticating from <MAC 'GravityL' [AN3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6611.892706] wlp1s0: authenticate with <MAC 'GravityL' [AN3]>
[ 6611.901408] wlp1s0: send auth to <MAC 'GravityL' [AN3]> (try 1/3)
[ 6611.904510] wlp1s0: authenticated
[ 6611.908351] wlp1s0: associate with <MAC 'GravityL' [AN3]> (try 1/3)
[ 6611.928295] wlp1s0: RX AssocResp from <MAC 'GravityL' [AN3]> (capab=0x431 status=0 aid=1)
[ 6611.928360] wlp1s0: associated




########## wireless info END ############

Thanks a lot.

---

### Post by praseodym on 2015-12-29
Try deactivating the hardware encryption of the driver:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```
Alternatively use Wicd instead:
```
wget http://www.elektronenblitz63.de/download/wicd-1.6.x_addon01441.tar.gz
sudo apt-get install --reinstall wicd
tar xvf wicd-1.6.x_addon01441.tar.gz
cd wicd-1.6.x_addon01441
sudo ./install_wicd_addon
sudo service network-manager stop
sudo killall wpa_supplicant
sudo service wicd restart
```
Deactivate the Network-Manager or uninstall it.

---

