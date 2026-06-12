---
title: "weak wifi signal in AR9287 Wireless Network Adapter (PCI-Express) - Ubuntu 16.04.2 LT"
date: 2017-07-07
forum: Networking &amp; Wireless
---

### Post by kunalv-shah on 2017-07-07
Hello,

I am running Ubuntu 16.04.2 LTS - Linux 4.4.0-83-generic on my desktop. I have PCI Wifi Card installed in one of the PCI slots of the motherboard. the card is Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:30a4]. It has two antennas that are projected towards my wifi router. I have dual boot with windows 10. When I am in windows 10, my machine has good connectivity with wifi router. The signal streght is great - mostly in 80%. However, when I boot in ubuntu, it drops to 30%. sometimes it even disconnects and I have to manually connect. 

I have tried solutions mentioned in couple of threads 

[https://ubuntuforums.org/showthread.php?t=2202993](https://ubuntuforums.org/showthread.php?t=2202993)

[https://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver](https://askubuntu.com/questions/334200/atheros-wireless-ar9285-driver)

but unable to resolve the issue. Can anyone please help me with this?

I am attaching information.txt file

Thanks
Kunal Shah


```



########## wireless info START ##########


Report from: 07 Jul 2017 11:52 IST +0530


Booted last: 07 Jul 2017 00:00 IST +0530


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description: Ubuntu 16.04.2 LTS
Release: 16.04
Codename: xenial


##### kernel ############################


Linux 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
Subsystem: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:30a4]
Kernel driver in use: ath9k


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 1058:1078 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
3: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no


##### lsmod #############################


ath9k 147456 0
ath9k_common 36864 1 ath9k
ath9k_hw 466944 2 ath9k_common,ath9k
ath 32768 3 ath9k_common,ath9k,ath9k_hw
mac80211 737280 1 ath9k
cfg80211 565248 4 ath,ath9k_common,ath9k,mac80211
eeepc_wmi 16384 0
asus_wmi 28672 1 eeepc_wmi
sparse_keymap 16384 1 asus_wmi
mxm_wmi 16384 0
wmi 20480 2 mxm_wmi,asus_wmi
video 40960 2 i915_bpo,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0 Link encap:Ethernet HWaddr <MAC 'enp3s0' [IF1]> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:997 errors:0 dropped:0 overruns:0 frame:0
TX packets:997 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1 
RX bytes:84664 (84.6 KB) TX bytes:84664 (84.6 KB)


wlp2s0 Link encap:Ethernet HWaddr <MAC 'wlp2s0' [IF2]> 
inet addr:192.168.0.10 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::9113:47e9:44b6:bf54/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:4785 errors:0 dropped:0 overruns:0 frame:0
TX packets:4583 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:3839954 (3.8 MB) TX bytes:914170 (914.1 KB)


##### iwconfig ##########################


lo no wireless extensions.


enp3s0 no wireless extensions.


wlp2s0 IEEE 802.11bgn ESSID:"70150801" 
Mode:Managed Frequency:2.452 GHz Access Point: <MAC '70150801' [AC1]> 
Bit Rate=144.4 Mb/s Tx-Power=16 dBm 
Retry short limit:7 RTS thrff Fragment thrff
Power Managementn
Link Quality=40/70 Signal level=-70 dBm 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:20 Invalid misc:84 Missed beacon:0


##### route #############################


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.0.1 0.0.0.0 UG 600 0 0 wlp2s0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlp2s0
192.168.0.0 0.0.0.0 255.255.255.0 U 600 0 0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


NetworkManager


Running:


root 1016 1 0 11:27 ? 00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE: wlp2s0
GENERAL.TYPE: wifi
GENERAL.NM-TYPE: NMDeviceWifi
GENERAL.VENDOR: Qualcomm Atheros
GENERAL.PRODUCT: AR9287 Wireless Network Adapter (PCI-Express)
GENERAL.DRIVER: ath9k
GENERAL.DRIVER-VERSION: 4.4.0-83-generic
GENERAL.FIRMWARE-VERSION: N/A
GENERAL.HWADDR: <MAC 'wlp2s0' [IF2]>
GENERAL.MTU: 0
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE: wlp2s0
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: 70150801
GENERAL.CON-UUID: 7276517a-9530-4cf4-bf74-f12975166b5c
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED: no (guessed)
CAPABILITIES.CARRIER-DETECT: no
CAPABILITIES.SPEED: 58 Mb/s
CAPABILITIES.IS-SOFTWARE: no
WIFI-PROPERTIES.WEP: yes
WIFI-PROPERTIES.WPA: yes
WIFI-PROPERTIES.WPA2: yes
WIFI-PROPERTIES.TKIP: yes
WIFI-PROPERTIES.CCMP: yes
WIFI-PROPERTIES.AP: yes
WIFI-PROPERTIES.ADHOC: yes
WIFI-PROPERTIES.2GHZ: yes
WIFI-PROPERTIES.5GHZ: no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: 7276517a-9530-4cf4-bf74-f12975166b5c | 70150801
IP4.ADDRESS[1]: 192.168.0.10/24
IP4.GATEWAY: 192.168.0.1
IP4.ROUTE[1]: dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]: 8.8.8.8
IP4.DNS[2]: 8.8.4.4
DHCP4.OPTION[1]: requested_routers = 1
DHCP4.OPTION[2]: requested_domain_search = 1
DHCP4.OPTION[3]: requested_time_offset = 1
DHCP4.OPTION[4]: requested_domain_name = 1
DHCP4.OPTION[5]: requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]: requested_broadcast_address = 1
DHCP4.OPTION[7]: requested_netbios_scope = 1
DHCP4.OPTION[8]: requested_wpad = 1
DHCP4.OPTION[9]: next_server = 0.0.0.0
DHCP4.OPTION[10]: expiry = 1499408404
DHCP4.OPTION[11]: requested_interface_mtu = 1
DHCP4.OPTION[12]: requested_subnet_mask = 1
DHCP4.OPTION[13]: dhcp_lease_time = 4294967295
DHCP4.OPTION[14]: dhcp_message_type = 5
DHCP4.OPTION[15]: ip_address = 192.168.0.10
DHCP4.OPTION[16]: requested_static_routes = 1
DHCP4.OPTION[17]: requested_domain_name_servers = 1
DHCP4.OPTION[18]: routers = 192.168.0.1
DHCP4.OPTION[19]: broadcast_address = 192.168.0.255
DHCP4.OPTION[20]: requested_ntp_servers = 1
DHCP4.OPTION[21]: requested_netbios_name_servers = 1
DHCP4.OPTION[22]: domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[23]: requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]: subnet_mask = 255.255.255.0
DHCP4.OPTION[25]: network_number = 192.168.0.0
DHCP4.OPTION[26]: requested_host_name = 1
DHCP4.OPTION[27]: dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]: fe80::9113:47e9:44b6:bf54/64
IP6.GATEWAY: 


GENERAL.DEVICE: enp3s0
GENERAL.TYPE: ethernet
GENERAL.NM-TYPE: NMDeviceEthernet
GENERAL.VENDOR: Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER: r8169
GENERAL.DRIVER-VERSION: 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION: 
GENERAL.HWADDR: <MAC 'enp3s0' [IF1]>
GENERAL.MTU: 1500
GENERAL.STATE: 20 (unavailable)
GENERAL.REASON: 2 (Device is now managed)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE: 
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: --
GENERAL.CON-UUID: --
GENERAL.CON-PATH: --
GENERAL.METERED: unknown
CAPABILITIES.CARRIER-DETECT: yes
CAPABILITIES.SPEED: unknown
CAPABILITIES.IS-SOFTWARE: no
WIRED-PROPERTIES.CARRIER: off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID BSSID MODE CHAN FREQ RATE SIGNAL BARS SECURITY ACTIVE * 
70150801 <MAC '70150801' [AC1]> Infra 9 2452 MHz 54 Mbit/s 51 &#9602;&#9604;__ WPA2 yes * 
Airtel-B310-2B4A <MAC 'Airtel-B310-2B4A' [AC2]> Infra 11 2462 MHz 54 Mbit/s 25 &#9602;___ WPA1 WPA2 no 


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


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=AndroidAP
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SIDESYNC_HOTSPOT_78:55]] (600 root)
[connection] id=SIDESYNC_HOTSPOT_78:55 | type=wifi | permissions=user:kunalshah:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=SIDESYNC_HOTSPOT_78:55
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Reliance WiPod4G|LTE-15F6]] (600 root)
[connection] id=Reliance WiPod4G|LTE-15F6 | type=wifi | permissions=user:kunalshah:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Reliance WiPod4G|LTE-15F6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/70150801]] (600 root)
[connection] id=70150801 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=70150801
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Lenovo K6 POWER]] (600 root)
[connection] id=Lenovo K6 POWER | type=wifi | permissions=user:kunalshah:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Lenovo K6 POWER
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


country CN: DFS-FCC
(2402 - 2482 @ 40), (N/A, 20), (N/A)
(5170 - 5250 @ 80), (N/A, 23), (N/A)
(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
(5735 - 5835 @ 80), (N/A, 30), (N/A)
(57240 - 59400 @ 2160), (N/A, 28), (N/A)
(59400 - 63720 @ 2160), (N/A, 44), (N/A)
(63720 - 65880 @ 2160), (N/A, 28), (N/A)


##### iwlist channels ###################


lo no frequency information.


enp3s0 no frequency information.


wlp2s0 13 channels in total; available frequencies :
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
Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


lo Interface doesn't support scanning.


enp3s0 Interface doesn't support scanning.


Channel occupancy:


1 APs on Frequency:2.452 GHz (Channel 9)
1 APs on Frequency:2.462 GHz (Channel 11)


wlp2s0 Scan completed :
Cell 01 - Address: <MAC '70150801' [AC1]>
Channel:9
Frequency:2.452 GHz (Channel 9)
Quality=40/70 Signal level=-70 dBm 
Encryption keyn
ESSID:"70150801"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
9 Mb/s; 12 Mb/s; 18 Mb/s
Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
Mode:Master
Extra:tsf=0000001100f11189
Extra: Last beacon: 56ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Cell 02 - Address: <MAC 'Airtel-B310-2B4A' [AC2]>
Channel:11
Frequency:2.462 GHz (Channel 11)
Quality=31/70 Signal level=-79 dBm 
Encryption keyn
ESSID:"Airtel-B310-2B4A"
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
24 Mb/s; 36 Mb/s; 54 Mb/s
Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
Mode:Master
Extra:tsf=0000000ca8b01732
Extra: Last beacon: 56ms ago
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename: /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless LAN cards.
author: Atheros Communications
srcversion: D578DE67B7E1EB3760B717B
depends: mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 
parm: debugebugging mask (uint)
parm: nohwcryptisable hardware encryption (int)
parm: blink:Enable LED blink on activity (int)
parm: led_active_high:Invert LED polarity (int)
parm: btcoex_enable:Enable wifi-BT coexistence (int)
parm: bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm: ps_enable:Enable WLAN PowerSave (int)
parm: use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename: /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license: Dual BSD/GPL
description: Shared library for Atheros wireless 802.11n LAN cards.
author: Atheros Communications
srcversion: 5E13CACC8C4252BB4B57367
depends: ath9k_hw,cfg80211,ath
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 


[ath9k_hw]
filename: /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license: Dual BSD/GPL
description: Support for Atheros 802.11n wireless LAN cards.
author: Atheros Communications
srcversion: C1B110E703660933E3BFE1A
depends: ath
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 


[ath]
filename: /lib/modules/4.4.0-83-generic/kernel/drivers/net/wireless/ath/ath.ko
license: Dual BSD/GPL
description: Shared library for Atheros wireless LAN cards.
author: Atheros Communications
srcversion: 3FCDBF7CE71CB8FB980D59D
depends: cfg80211
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 


[mac80211]
filename: /lib/modules/4.4.0-83-generic/kernel/net/mac80211/mac80211.ko
license: GPL
description: IEEE 802.11 subsystem
srcversion: EFF66BE1B3C123F1C2078FB
depends: cfg80211
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 
parm: minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm: max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm: max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm: beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm: probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm: ieee80211_default_rc_algoefault rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename: /lib/modules/4.4.0-83-generic/kernel/net/wireless/cfg80211.ko
description: wireless configuration support
license: GPL
author: Johannes Berg
srcversion: 48C96882CCDC964173BE1D1
depends: 
intree: Y
vermagic: 4.4.0-83-generic SMP mod_unload modversions 
parm: bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm: ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm: cfg80211_disable_40mhz_24ghzisable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 1
ps_enable: 1
use_chanctx: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1
options ath9k nohwcrypt=1 ps_enable=1


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


[ 1340.921304] ath9k: ath9k: Driver unloaded
[ 1350.333636] ath: EEPROM regdomain: 0x809c
[ 1350.333637] ath: EEPROM indicates we should expect a country code
[ 1350.333638] ath: doing EEPROM country->regdmn map search
[ 1350.333639] ath: country maps to regdmn code: 0x52
[ 1350.333639] ath: Country alpha2 being used: CN
[ 1350.333640] ath: Regpair used: 0x52
[ 1350.336479] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[ 1350.358077] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[ 1351.906067] wlp2s0: authenticate with <MAC '70150801' [AC1]>
[ 1351.929995] wlp2s0: send auth to <MAC '70150801' [AC1]> (try 1/3)
[ 1351.931723] wlp2s0: authenticated
[ 1351.932961] wlp2s0: associate with <MAC '70150801' [AC1]> (try 1/3)
[ 1351.937212] wlp2s0: RX AssocResp from <MAC '70150801' [AC1]> (capab=0x431 status=0 aid=1)
[ 1351.937338] wlp2s0: associated
[ 1351.937452] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 1394.121999] wlp2s0: deauthenticating from <MAC '70150801' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1394.194468] ath9k: ath9k: Driver unloaded
[ 1399.264139] ath: EEPROM regdomain: 0x809c
[ 1399.264141] ath: EEPROM indicates we should expect a country code
[ 1399.264142] ath: doing EEPROM country->regdmn map search
[ 1399.264142] ath: country maps to regdmn code: 0x52
[ 1399.264143] ath: Country alpha2 being used: CN
[ 1399.264143] ath: Regpair used: 0x52
[ 1399.267390] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
[ 1399.294214] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[ 1400.859049] wlp2s0: authenticate with <MAC '70150801' [AC1]>
[ 1400.883399] wlp2s0: send auth to <MAC '70150801' [AC1]> (try 1/3)
[ 1400.885532] wlp2s0: authenticated
[ 1400.886127] wlp2s0: associate with <MAC '70150801' [AC1]> (try 1/3)
[ 1400.892537] wlp2s0: RX AssocResp from <MAC '70150801' [AC1]> (capab=0x431 status=0 aid=1)
[ 1400.892651] wlp2s0: associated
[ 1400.892731] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


########## wireless info END ############
```

---

### Post by ajgreeny on 2017-07-07
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by kunalv-shah on 2017-07-08
> **ajgreeny said:**
> Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

Thank you, point noted. When I first posted, I thought of making it more readable but was unaware of CODE tag. Now it will come handy.

---

### Post by chili555 on 2017-07-09
I'm not sure I know the exact answer, but I have an informed guess. Please open a terminal and do:```
sudo -i
echo "options ath9k bt_ant_diversity=1"  >  /etc/modprobe.d/ath9k.conf
exit
```Reboot and show us:```
sudo nmcli dev wifi list
```

---

