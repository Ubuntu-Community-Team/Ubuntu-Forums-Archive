---
title: "wifi not working ubuntu 16.04"
date: 2016-05-16
forum: Networking &amp; Wireless
---

### Post by ol4pro on 2016-05-16
Result of wireless.info below, used folowing

```
sudo wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info

```

Did try service network-manager restart


```

########## wireless info START ##########


Report from: 16 May 2016 16:42 CEST +0200


Booted last: 16 May 2016 00:00 CEST +0200


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-22-generic #39-Ubuntu SMP Thu May 5 16:53:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:213b]


06:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	DeviceName: Ralink RT3290LE 802.11bgn Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


##### lsusb #############################


Bus 002 Device 002: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


wl                   6365184  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  3 wl,mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.15  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:532684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:460351 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:697216927 (697.2 MB)  TX bytes:47025288 (47.0 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search home


##### network managers ##################


Installed:


	NetworkManager


Running:


root      3927     1  0 16:12 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:05:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       68a40876-5a68-417d-a90c-f6a01e13b880
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{11}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   68a40876-5a68-417d-a90c-f6a01e13b880 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.15/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = new-host
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1463420111
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.15
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 10800
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               0.37
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:06:00.0/net/wlan0
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


[[/etc/NetworkManager/system-connections/ICID 1]] (600 root)
[connection] id=ICID 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=ICID
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/H. Sunquest]] (600 root)
[connection] id=H. Sunquest | type=wifi
[wifi] ssid=H. Sunquest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/H. Sunquest P.]] (600 root)
[connection] id=H. Sunquest P. | type=wifi
[wifi] ssid=H. Sunquest P. | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maison]] (600 root)
[connection] id=Maison | type=wifi
[wifi] ssid=Maison | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/H. Sunquest R.]] (600 root)
[connection] id=H. Sunquest R. | type=wifi
[wifi] ssid=H. Sunquest R. | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/EINET-WIFI]] (600 root)
[connection] id=EINET-WIFI | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=EINET-WIFI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VOO-157533]] (600 root)
[connection] id=VOO-157533 | type=wifi
[wifi] ssid=VOO-157533 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Marchant]] (600 root)
[connection] id=Marchant | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=Marchant
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ECA - Guest]] (600 root)
[connection] id=ECA - Guest | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=ECA - Guest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-db40]] (600 root)
[connection] id=bbox2-db40 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=bbox2-db40
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ICID]] (600 root)
[connection] id=ICID | type=802-11-wireless
[802-11-wireless] ssid=ICID | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/bbox2-3ec1]] (600 root)
[connection] id=bbox2-3ec1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=bbox2-3ec1
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotel Melodia]] (600 root)
[connection] id=Hotel Melodia | type=wifi
[wifi] ssid=Hotel Melodia | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Otopeni Airport]] (600 root)
[connection] id=Otopeni Airport | type=wifi
[wifi] ssid=Otopeni Airport | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/VOO-169722]] (600 root)
[connection] id=VOO-169722 | type=wifi
[wifi] ssid=VOO-169722 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Réseau Wi-Fi]] (600 root)
[connection] id=Réseau Wi-Fi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF]> | mac-address-blacklist= | ssid=82;195;169;115;101;97;117;32;87;105;45;70;105;
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotel Favorit]] (600 root)
[connection] id=Hotel Favorit | type=wifi
[wifi] ssid=Hotel Favorit | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Brussels (based on set time zone)


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


eth0      no frequency information.


lo        no frequency information.


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


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


lo        Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/4.4.0-22-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[rt2800pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 


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


[rt2800pci]
nohwcrypt: N


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


lp


##### modprobe options ##################


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


[/etc/modprobe.d/garmin-forerunner-tools.conf]
blacklist garmin_gps


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8069
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  236.078142] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  237.678066] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  239.294027] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  240.901935] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  253.077156] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  254.684919] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  256.320889] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  257.924669] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  315.430843] r8169 0000:05:00.0 eth0: link up
[  315.430879] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  324.548249] r8169 0000:05:00.0 eth0: link down
[  338.371391] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  339.979380] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  340.899149] r8169 0000:05:00.0 eth0: link up
[  341.595252] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  343.195060] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  396.463704] r8169 0000:05:00.0 eth0: link down
[  410.639557] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  410.877028] r8169 0000:05:00.0 eth0: link up
[  412.243405] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068]
[  412.243428] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  413.863346] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  415.475260] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  490.609366] r8169 0000:05:00.0 eth0: link down
[  570.402847] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  572.015971] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  573.615839] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  573.630025] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  573.804883] r8169 0000:05:00.0 eth0: link down
[  573.805050] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  575.823671] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  577.435538] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  579.059487] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  580.659259] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  592.050602] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  593.650515] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  595.270249] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  596.874198] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  607.763482] r8169 0000:05:00.0 eth0: link up
[  609.057404] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  610.673235] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  612.293212] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  613.897200] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  613.897308] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  626.068356] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  627.672196] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  629.288146] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  630.908002] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  643.071143] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  644.695033] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  646.322967] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  647.946778] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  660.051602] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  661.665988] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  663.297770] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  664.909703] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[ 1149.595247] r8169 0000:05:00.0 eth0: link down
[ 1155.827438] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[ 1157.431316] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[ 1159.051155] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[ 1160.659148] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[ 1167.871613] r8169 0000:05:00.0 eth0: link up
[ 1309.037333] r8169 0000:05:00.0 eth0: link down
[ 1342.984085] r8169 0000:05:00.0 eth0: link up
[ 1392.203399] r8169 0000:05:00.0 eth0: link down
[ 1431.929289] r8169 0000:05:00.0 eth0: link up
[ 1642.822163] wl: module license 'MIXED/Proprietary' taints kernel.
[ 1642.832019] wl: module verification failed: signature and/or required key missing - tainting kernel
[ 1885.346612] r8169 0000:05:00.0 eth0: link down
[ 1903.406099] r8169 0000:05:00.0 eth0: link up
[ 2367.622857] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[ 2369.238576] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[ 2370.886475] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[ 2372.506315] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)


########## wireless info END ############
```

---

### Post by praseodym on 2016-05-16
There is another driver loaded:
```

sudo modprobe -rfv wl rt2800pci
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -v rt2800pci
```
Reconnect. Check then
```

rfkill list
iwconfig
iwlist chan
sudo iwlist scan
```

---

### Post by ol4pro on 2016-05-16
It worked beautifully,   2 question I do have, copy and paste is nice, however would like to learn something from this.

What does the -rfv wl do?
and what do the second part (reconnect do?)

How you came by that conclusion, the part "Error - WPDMA TX/RX busy" in the # dmesg # notice is what means "another driver loaded" ?

---

### Post by praseodym on 2016-05-17
First one unloads both drivers, 2nd one uninstalls the Broadcom driver (module name wl), third one loads the right one (Ralink, module rt2800pci) again. See also

```
man modprobe
```

---

### Post by adept-james on 2016-06-16
Hi i have a similar problem my wifi signal is really bad its only been happening since i went from 15.10 to 16.04. Here is the output from the command run by OP:

```

########## wireless info START ##########

Report from: 16 Jun 2016 11:19 BST +0100

Booted last: 16 Jun 2016 00:00 BST +0100

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

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

08:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 81)
    DeviceName: IntelWLAN Intel 3165NGWG Stone Peak 1 ac 1x1 + BT 4 LE PCIe+USB NGFF 2230WW
    Subsystem: Intel Corporation Dual Band Wireless AC 3165 [8086:4010]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:8093]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 0bda:57c4 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF2]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr1    Link encap:Ethernet  HWaddr <MAC 'virbr1' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0-nic Link encap:Ethernet  HWaddr <MAC 'virbr0-nic' [IF4]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr1-nic Link encap:Ethernet  HWaddr <MAC 'virbr1' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF6]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fdb4:3052:4f41:1900:a8b5:7754:8305:661a/64 Scope:Global
          inet6 addr: fdb4:3052:4f41:1900:8b1d:e1d6:c7a8:593f/64 Scope:Global
          inet6 addr: fe80::a7ba:b895:2a96:861e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22910 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26140279 (26.1 MB)  TX bytes:1906396 (1.9 MB)

##### iwconfig ##########################

lo        no wireless extensions.

virbr1-nic  no wireless extensions.

virbr0    no wireless extensions.

virbr1    no wireless extensions.

virbr0-nic  no wireless extensions.

eno1      no wireless extensions.

wlo1      IEEE 802.11abgn  ESSID:"TALKTALK4F4119"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'TALKTALK4F4119' [AC1]>   
          Bit Rate=325 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       807     1  0 10:44 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         virbr0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'virbr0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0
GENERAL.IP-IFACE:                       virbr0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     virbr0
GENERAL.CON-UUID:                       d85ae83c-94d2-4805-91cf-ed4b543bbed8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{10}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d85ae83c-94d2-4805-91cf-ed4b543bbed8 | virbr0
IP4.ADDRESS[1]:                         192.168.122.1/24
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3165 (Dual Band Wireless AC 3165)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlo1' [IF6]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     TALKTALK4F4119 1
GENERAL.CON-UUID:                       5c4b9db7-6401-4313-9deb-c60fb4586be5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     390 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   034177fa-5050-4622-a01c-694bcdf31c6d | TALKTALK4F4119
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   5c4b9db7-6401-4313-9deb-c60fb4586be5 | TALKTALK4F4119 1
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1466157698
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_routers = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fdb4:3052:4f41:1900:a8b5:7754:8305:661a/64
IP6.ADDRESS[2]:                         fdb4:3052:4f41:1900:8b1d:e1d6:c7a8:593f/64
IP6.ADDRESS[3]:                         fe80::a7ba:b895:2a96:861e/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:12:cf:f7:93:b4:30:52:4f:41:19
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:a6:b3:26:c8:2a:af:95:a1:c2:5e:75:d:cc:af:90:bf

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
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

GENERAL.DEVICE:                         virbr1
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'virbr1' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr1
GENERAL.IP-IFACE:                       virbr1
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            

GENERAL.DEVICE:                         virbr0-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'virbr0-nic' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         41 (The device's existing connection was assumed)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr0-nic
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         virbr1-nic
GENERAL.TYPE:                           tun
GENERAL.NM-TYPE:                        NMDeviceTun
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         tun
GENERAL.DRIVER-VERSION:                 1.6
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'virbr1' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         41 (The device's existing connection was assumed)
GENERAL.UDI:                            /sys/devices/virtual/net/virbr1-nic
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TALKTALK4F4119       <MAC 'TALKTALK4F4119' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  56      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
TALKTALK4F4119       <MAC 'TALKTALK4F4119' [AC7]>  Infra  8     2447 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
EE-BrightBox-k5axn3  <MAC 'EE-BrightBox-k5axn3' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
SKY2B64C             <MAC 'SKY2B64C' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
BTHub3-9TSZ          <MAC 'BTHub3-9TSZ' [AC4]>  Infra  7     2442 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
BTWiFi-with-FON      <MAC 'BTWiFi-with-FON' [AC6]>  Infra  7     2442 MHz  54 Mbit/s  24      &#9602;___  --         no        
BTWiFi               <MAC 'BTWiFi' [AC5]>  Infra  7     2442 MHz  54 Mbit/s  22      &#9602;___  --         no        
BTHub5-P5C9          <MAC 'BTHub5-P5C9' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
TP-LINK_AE8E68       <MAC 'TP-LINK_AE8E68' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/TALKTALK4F4119]] (600 root)
[connection] id=TALKTALK4F4119 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=TALKTALK4F4119
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_The Cloud]] (600 root)
[connection] id=_The Cloud | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=_The Cloud
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK7D2987]] (600 root)
[connection] id=TALKTALK7D2987 | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=TALKTALK7D2987
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK-FDE37C]] (600 root)
[connection] id=TALKTALK-FDE37C | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=TALKTALK-FDE37C
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SKYE612C]] (600 root)
[connection] id=SKYE612C | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=SKYE612C
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TNCAPCEC2AF]] (600 root)
[connection] id=TNCAPCEC2AF | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=TNCAPCEC2AF
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TALKTALK4F4119 1]] (600 root)
[connection] id=TALKTALK4F4119 1 | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=TALKTALK4F4119
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BrightBox-wdmtjc]] (600 root)
[connection] id=BrightBox-wdmtjc | type=wifi | permissions=user:officepc:;
[wifi] mac-address=<MAC 'wlo1' [IF6]> | mac-address-blacklist= | ssid=BrightBox-wdmtjc
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

virbr1-nic  no frequency information.

virbr0    no frequency information.

virbr1    no frequency information.

virbr0-nic  no frequency information.

eno1      no frequency information.

wlo1      32 channels in total; available frequencies :
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
          Current Frequency:5.18 GHz (Channel 36)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

virbr1-nic  Interface doesn't support scanning.

virbr0    Interface doesn't support scanning.

virbr1    Interface doesn't support scanning.

virbr0-nic  Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'TALKTALK4F4119' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK4F4119"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000087d3f79e
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'EE-BrightBox-k5axn3' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"EE-BrightBox-k5axn3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000012b4266f23ed
                    Extra: Last beacon: 848ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_AE8E68' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_AE8E68"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001fce70fa3ecb
                    Extra: Last beacon: 836ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BTHub3-9TSZ' [AC4]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BTHub3-9TSZ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000083af00c737
                    Extra: Last beacon: 652ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BTWiFi' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000083af019f06
                    Extra: Last beacon: 648ms ago
          Cell 06 - Address: <MAC 'BTWiFi-with-FON' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000083af01a80e
                    Extra: Last beacon: 648ms ago
          Cell 07 - Address: <MAC 'TALKTALK4F4119' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK4F4119"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000080ef799c
                    Extra: Last beacon: 632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'SKY2B64C' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKY2B64C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dafb3512c8
                    Extra: Last beacon: 528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

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

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   40.855839] virbr0: port 1(virbr0-nic) entered listening state (repeated 2 times)
[   41.202288] virbr0: port 1(virbr0-nic) entered disabled state
[   41.207255] device virbr0-nic left promiscuous mode
[   41.207284] virbr0: port 1(virbr0-nic) entered disabled state
[   41.250474] device virbr1-nic entered promiscuous mode
[   41.396131] virbr1: port 1(virbr1-nic) entered listening state (repeated 2 times)
[   41.414474] virbr1: port 1(virbr1-nic) entered disabled state
[   77.508714] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   77.594786] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   81.165481] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[   81.171792] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[   81.174990] wlo1: authenticated
[   81.178966] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[   81.182831] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[   81.183865] wlo1: associated
[   81.183899] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[  105.376664] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC1]>
[  105.381862] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  105.383235] wlo1: authenticated
[  105.387387] wlo1: associate with <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  105.388521] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC1]> (capab=0x11 status=0 aid=2)
[  105.389519] wlo1: associated
[  105.400984] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'TALKTALK4F4119' [AC1]>
[  148.480118] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[  148.481533] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  148.483548] wlo1: authenticated
[  148.487057] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  148.490893] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[  148.491479] wlo1: associated
[  211.551138] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC1]>
[  211.555883] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  211.556669] wlo1: authenticated
[  211.560813] wlo1: associate with <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  211.561936] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC1]> (capab=0x11 status=0 aid=2)
[  211.562500] wlo1: associated
[  211.591168] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'TALKTALK4F4119' [AC1]>
[  294.558133] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[  294.563972] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  294.566614] wlo1: authenticated
[  294.566834] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  294.570722] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[  294.579600] wlo1: associated
[  400.835550] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC1]>
[  400.841362] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  400.842782] wlo1: authenticated
[  400.843977] wlo1: associate with <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  400.845155] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC1]> (capab=0x11 status=0 aid=2)
[  400.845668] wlo1: associated
[  400.932367] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'TALKTALK4F4119' [AC1]>
[  637.424170] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[  637.430417] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  637.432235] wlo1: authenticated
[  637.435392] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  637.439363] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[  637.439946] wlo1: associated
[  757.368093] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC1]>
[  757.375435] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  757.376365] wlo1: authenticated
[  757.376937] wlo1: associate with <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[  757.378247] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC1]> (capab=0x11 status=0 aid=2)
[  757.378828] wlo1: associated
[  757.391891] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'TALKTALK4F4119' [AC1]>
[  877.479074] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[  877.483701] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  877.485623] wlo1: authenticated
[  877.486738] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[  877.490646] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[  877.491135] wlo1: associated
[ 1013.818983] wlo1: deauthenticating from <MAC 'TALKTALK4F4119' [AC7]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1021.571272] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1021.572079] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 1021.587780] r8169 0000:09:00.0 eno1: link down
[ 1021.587867] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[ 1028.739987] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[ 1028.834669] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[ 1032.273011] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC7]>
[ 1032.278412] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[ 1032.280341] wlo1: authenticated
[ 1032.281246] wlo1: associate with <MAC 'TALKTALK4F4119' [AC7]> (try 1/3)
[ 1032.287824] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC7]> (capab=0x411 status=0 aid=1)
[ 1032.289358] wlo1: associated
[ 1032.289400] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[ 2045.518814] wlo1: authenticate with <MAC 'TALKTALK4F4119' [AC1]>
[ 2045.521557] wlo1: send auth to <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[ 2045.522454] wlo1: authenticated
[ 2045.525462] wlo1: associate with <MAC 'TALKTALK4F4119' [AC1]> (try 1/3)
[ 2045.526649] wlo1: RX AssocResp from <MAC 'TALKTALK4F4119' [AC1]> (capab=0x11 status=0 aid=2)
[ 2045.527600] wlo1: associated
[ 2045.605029] wlo1: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'TALKTALK4F4119' [AC1]>

########## wireless info END ############


```

Please help cant seem to use internet at all it cuts off and says page timed out 50% of the time. And when i use vpn it simply wont work at all.

---

### Post by adept-james on 2016-06-16
help bump ~#

---

### Post by knight2 on 2016-11-27
Is your "Intel 3165 Stone Peak" WiFi working now in Ubuntu 16.04? Thank you.

---

