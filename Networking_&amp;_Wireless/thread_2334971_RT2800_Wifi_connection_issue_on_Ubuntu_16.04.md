---
title: "RT2800 Wifi connection issue on Ubuntu 16.04"
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by pushpraj4u on 2016-08-24
Hi,

I am having issues connecting to wifi from my Ubuntu laptop. Kernel logs show below error.
 > [  138.493356] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)

Below is the information generated after running wireless-info script.
```
########## wireless info START ##########

Report from: 24 Aug 2016 16:37 IST +0530


Booted last: 24 Aug 2016 00:00 IST +0530


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:17f6]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b370 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. VFS491
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto eth0
iface eth0 inet manual


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:172.26.17.11  Bcast:172.26.17.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:1 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:75150 (75.1 KB)  TX bytes:22271 (22.2 KB)


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
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.26.17.2     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
172.26.1.11     172.26.17.2     255.255.255.255 UGH   100    0        0 eth0
172.26.17.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search xpanxion.co.in


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2528     1  0 16:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168e-3_0.0.4 03/27/12
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       bee80c86-827b-4dba-98c4-88e28bbcf38c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{9,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bee80c86-827b-4dba-98c4-88e28bbcf38c | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   681b428f-beaf-8932-dce4-687ed5bae28e | Ifupdown (eth0)
IP4.ADDRESS[1]:                         172.26.17.11/24
IP4.GATEWAY:                            172.26.17.2
IP4.ROUTE[1]:                           dst = 172.26.1.11/32, nh = 172.26.17.2, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.26.1.4
IP4.DNS[2]:                             172.26.1.5
IP4.DOMAIN[1]:                          xpanxion.co.in
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 172.26.1.4 172.26.1.5
DHCP4.OPTION[5]:                        ip_address = 172.26.17.11
DHCP4.OPTION[6]:                        filename = boot\x86\wdsnbp.com
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 172.26.1.11
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 172.26.17.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 151200
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 172.26.17.2
DHCP4.OPTION[17]:                       dhcp_renewal_time = 86400
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = xpanxion.co.in
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1472209563
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 172.26.17.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 172.26.1.11
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 172800
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0
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


no-auto-default=<MAC 'eth0' [IF1]>,


[ifupdown]
managed=true


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/AIRTEL_E5172_FBB4]] (600 root)
[connection] id=AIRTEL_E5172_FBB4 | type=802-11-wireless
[802-11-wireless] ssid=AIRTEL_E5172_FBB4 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/L!nuxWorld 1]] (600 root)
[connection] id=L!nuxWorld 1 | type=802-11-wireless
[802-11-wireless] ssid=L!nuxWorld | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/airtel]] (600 root)
[connection] id=airtel | type=802-11-wireless
[802-11-wireless] ssid=airtel | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ForBroadband_SMS_Idea_9623450000]] (600 root)
[connection] id=ForBroadband_SMS_Idea_9623450000 | type=802-11-wireless
[802-11-wireless] ssid=ForBroadband_SMS_Idea_9623450000 | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/test2]] (600 root)
[connection] id=test2 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=test2 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Hotspot]] (600 root)
[connection] id=Hotspot | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=pushpraj | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/L!nuxWorld 2]] (600 root)
[connection] id=L!nuxWorld 2 | type=802-11-wireless
[802-11-wireless] ssid=L!nuxWorld | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/My ASUS]] (600 root)
[connection] id=My ASUS | type=802-11-wireless
[802-11-wireless] ssid=My ASUS | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kashid]] (600 root)
[connection] id=kashid | type=802-11-wireless
[802-11-wireless] ssid=kashid | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF2]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/test1]] (600 root)
[connection] id=test1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Rohit
[ipv4] method=shared
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/Cheko]] (600 root)
[connection] id=Cheko | type=802-11-wireless
[802-11-wireless] ssid=Cheko | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MANA_NET]] (600 root)
[connection] id=MANA_NET | type=802-11-wireless
[802-11-wireless] ssid=MANA_NET | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=XPX | type=802-11-wireless
[802-11-wireless] ssid=XPXWiFi | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AIRTEL-SYD]] (600 root)
[connection] id=AIRTEL-SYD | type=802-11-wireless
[802-11-wireless] ssid=AIRTEL-SYD | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/L!nuxWorld]] (600 root)
[connection] id=L!nuxWorld | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=L!nuxWorld
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/flyraven broadband 9762171174]] (600 root)
[connection] id=flyraven broadband 9762171174 | type=802-11-wireless
[802-11-wireless] ssid=flyraven broadband 9762171174 | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/GTPA]] (600 root)
[connection] id=GTPA | type=802-11-wireless
[802-11-wireless] ssid=GTPA | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/XPXTWC]] (600 root)
[connection] id=XPXTWC | type=802-11-wireless
[802-11-wireless] ssid=XPXTWC | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Rohit]] (600 root)
[connection] id=Rohit | type=802-11-wireless
[802-11-wireless] ssid=Rohit | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DIRECT-9A-BRAVIA]] (600 root)
[connection] id=DIRECT-9A-BRAVIA | type=802-11-wireless
[802-11-wireless] ssid=DIRECT-9A-BRAVIA | mac-address=<MAC 'wlan0' [IF2]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Asia/Kolkata (based on set time zone)


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


lo        Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down


eth0      Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1814:0x3290 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   18.596164] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3290, rev 0015 detected
[   18.599857] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 3290 detected
[   33.830683] r8169 0000:04:00.0 eth0: link down (repeated 2 times)
[   33.830735] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.202699] r8169 0000:04:00.0 eth0: link up
[   36.202710] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   41.259023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.259057] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt3290.bin'
[   41.310428] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.37
[   42.932629] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   44.532664] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   48.580660] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   50.184702] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   51.804716] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   53.404736] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   65.676813] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   67.276829] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   68.892844] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   70.492854] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   82.680952] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   84.280973] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   85.896966] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[   87.496995] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[   99.685081] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  101.289015] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  102.905037] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  104.505130] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  116.677191] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  118.277253] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  119.893188] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  121.493214] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  133.673271] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  135.273371] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)
[  136.893369] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000068] (repeated 2 times)
[  138.493356] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)


########## wireless info END ############

```

I searched for solution in forums but none of them worked. Disabling RT2800 module at boot also not worked. Network connection bar shows **Wi-Fi Networks "device not ready"**

please help.


Thanks,
Pushpraj

---

