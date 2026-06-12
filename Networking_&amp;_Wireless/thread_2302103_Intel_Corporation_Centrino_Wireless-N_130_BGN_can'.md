---
title: "Intel Corporation Centrino Wireless-N 130 BGN can't conect, Ubuntu 15.04"
date: 2015-11-07
forum: Networking &amp; Wireless
---

### Post by kpfu-tcp-ip on 2015-11-07
Hi, I can't connect to any wifi AP, I tried to connect by NetworkManager and from command line by wpa_supplicant, but i cant.
I tried to fix this problem almost two day ;(
Please help me
Sorry for my bad englsh.

There is my wireless-info.txt
```


########## wireless info START ##########


Report from: 08 Nov 2015 00:43 MSK +0300


Booted last: 07 Nov 2015 19:51 MSK +0300


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-32-generic #37-Ubuntu SMP Wed Oct 21 10:23:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 130 [8086:0896] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 130 BGN [8086:5005]
    Kernel driver in use: iwlwifi


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0b6]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 010: ID 1076:8002 GCT Semiconductor, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1008  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: samsung-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
5: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwldvm                237568  0 
mac80211              724992  1 iwldvm
iwlwifi               196608  1 iwldvm
cfg80211              540672  3 iwlwifi,mac80211,iwldvm
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:7339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5708246 (5.7 MB)  TX bytes:1705729 (1.7 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    100    0        0 eth1
10.0.0.0        0.0.0.0         255.255.255.0   U     100    0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root     10906     1  0 Nov07 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth1
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         GCT SEMICONDUCTOR Inc
GENERAL.PRODUCT:                        Modem Yota
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'eth1' [IF]>
GENERAL.MTU:                            1400
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/net/eth1
GENERAL.IP-IFACE:                       eth1
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       aeb19eec-45f9-4634-a691-aaec76497a97
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{10}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   aeb19eec-45f9-4634-a691-aaec76497a97 | Wired connection 2
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 10.0.0.10/24, gw = 10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.0.1
IP4.DNS[2]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_broadcast_address = 1
DHCP4.OPTION[3]:                        requested_domain_name = 1
DHCP4.OPTION[4]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        expiry = 1446932853
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        next_server = 0.0.0.0
DHCP4.OPTION[9]:                        broadcast_address = 10.0.0.255
DHCP4.OPTION[10]:                       dhcp_message_type = 5
DHCP4.OPTION[11]:                       requested_subnet_mask = 1
DHCP4.OPTION[12]:                       routers = 10.0.0.1
DHCP4.OPTION[13]:                       dhcp_lease_time = 300
DHCP4.OPTION[14]:                       ip_address = 10.0.0.10
DHCP4.OPTION[15]:                       requested_static_routes = 1
DHCP4.OPTION[16]:                       requested_domain_name_servers = 1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 150
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       domain_name_servers = 10.0.0.1
DHCP4.OPTION[20]:                       dhcp_rebinding_time = 225
DHCP4.OPTION[21]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       network_number = 10.0.0.0
DHCP4.OPTION[24]:                       requested_host_name = 1
DHCP4.OPTION[25]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'eth1' [IF]>/64, gw = ::


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Wireless-N 130 (BGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-32-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{41,20,32,7,33}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6b630ea0-1a6a-49e5-8a93-aefe00c813fb | Ashtaroth72
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   6784c80b-132f-4d85-b020-b2656342adde | 409
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   8745586c-5c8c-4622-97c7-a7ab1fc2a61a | wifi.tattele.com
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   0498babd-747f-4929-9d0d-c985b964d1b4 | IloveCocaine
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   4bfd02f2-c129-45a6-a629-31e18e1e19a1 | TP1111
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168e-3_0.0.4 03/27/12
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


SSID              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TP                <MAC 'TP' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
409               <MAC '409' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
wifi.tattele.com  <MAC 'wifi.tattele.com' [AN3]>  Infra  10    2457 MHz  54 Mbit/s  39      &#9602;&#9604;__  --         no        
wifi.tattele.com  <MAC 'wifi.tattele.com' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  --         no        


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


[[/etc/NetworkManager/system-connections/654]] (600 root)
[connection] id=654 | type=802-11-wireless
[802-11-wireless] ssid=654 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DIRECT-V3-BRAVIA]] (600 root)
[connection] id=DIRECT-V3-BRAVIA | type=wifi
[wifi] ssid=DIRECT-V3-BRAVIA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ShantiHostel]] (600 root)
[connection] id=ShantiHostel | type=802-11-wireless
[802-11-wireless] ssid=ShantiHostel | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/36-k]] (600 root)
[connection] id=36-k | type=802-11-wireless
[802-11-wireless] ssid=36-k | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/409]] (600 root)
[connection] id=409 | type=wifi
[wifi] ssid=409 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ashtaroth72 1]] (600 root)
[connection] id=Ashtaroth72 1 | type=wifi
[wifi] ssid=Ashtaroth72 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/409 1]] (600 root)
[connection] id=409 1 | type=wifi
[wifi] ssid=409 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/353-4]] (600 root)
[connection] id=353-4 | type=802-11-wireless
[802-11-wireless] ssid=353-4 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/tatinet-429(11)6]] (600 root)
[connection] id=tatinet-429(11)6 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=tatinet-429(11)6 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/tatinet-473(11)7]] (600 root)
[connection] id=tatinet-473(11)7 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=tatinet-473(11)7 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/wifi.tattele.com 1]] (600 root)
[connection] id=wifi.tattele.com 1 | type=wifi
[wifi] ssid=wifi.tattele.com | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/wifi.tattele.com]] (600 root)
[connection] id=wifi.tattele.com | type=wifi
[wifi] ssid=wifi.tattele.com | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=ignore
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/nanana]] (600 root)
[connection] id=nanana | type=802-11-wireless
[802-11-wireless] ssid=nanana | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/romaska]] (600 root)
[connection] id=romaska | type=wifi
[wifi] ssid=romaska | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TATTELECOM_E3A1 1]] (600 root)
[connection] id=TATTELECOM_E3A1 1 | type=wifi
[wifi] ssid=TATTELECOM_E3A1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/452]] (600 root)
[connection] id=452 | type=802-11-wireless
[802-11-wireless] ssid=452 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DOMwifi]] (600 root)
[connection] id=DOMwifi | type=802-11-wireless
[802-11-wireless] ssid=DOMwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PNG_Network]] (600 root)
[connection] id=PNG_Network | type=wifi
[wifi] ssid=PNG_Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kgu]] (600 root)
[connection] id=kgu | type=802-11-wireless
[802-11-wireless] ssid=kgu | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/256-d]] (600 root)
[connection] id=256-d | type=802-11-wireless
[802-11-wireless] ssid=256-d | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/yMap4uuuk]] (600 root)
[connection] id=yMap4uuuk | type=wifi
[wifi] ssid=yMap4uuuk | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/dd-wrt]] (600 root)
[connection] id=dd-wrt | type=802-11-wireless
[802-11-wireless] ssid=dd-wrt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Megaline Wi-Fi]] (600 root)
[connection] id=Megaline Wi-Fi | type=wifi
[wifi] ssid=Megaline Wi-Fi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/,&#1080;&#1091;&#1091;&#1091;&#1091;]] (600 root)
[connection] id=,&#1080;&#1091;&#1091;&#1091;&#1091; | type=802-11-wireless
[802-11-wireless] ssid=44;208;184;209;131;209;131;209;131;209;131; | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidA]] (600 root)
[connection] id=AndroidA | type=wifi
[wifi] ssid=AndroidA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Airport]] (600 root)
[connection] id=Airport | type=wifi
[wifi] ssid=Airport | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TATTELECOM_E3A1]] (600 root)
[connection] id=TATTELECOM_E3A1 | type=wifi
[wifi] ssid=TATTELECOM_E3A1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Ashtaroth72]] (600 root)
[connection] id=Ashtaroth72 | type=wifi
[wifi] ssid=Ashtaroth72 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/IloveCocaine]] (600 root)
[connection] id=IloveCocaine | type=wifi | autoconnect=false
[wifi] ssid=dasdasdae1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hse]] (600 root)
[connection] id=hse | type=802-11-wireless
[802-11-wireless] ssid=hse | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/1102]] (600 root)
[connection] id=1102 | type=802-11-wireless
[802-11-wireless] ssid=1102 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/tatinet-454(6)5]] (600 root)
[connection] id=tatinet-454(6)5 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=tatinet-454(6)5 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/TP-LINK_81DF7E]] (600 root)
[connection] id=TP-LINK_81DF7E | type=wifi
[wifi] ssid=TP-LINK_81DF7E | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/tatinet-428(6)3]] (600 root)
[connection] id=tatinet-428(6)3 | type=802-11-wireless
[802-11-wireless] ssid=tatinet-428(6)3 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Vitalik]] (600 root)
[connection] id=Vitalik | type=wifi
[wifi] ssid=Vitalik | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/temp_net]] (600 root)
[connection] id=temp_net | type=wifi
[wifi] ssid=temp_net | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DIR-320NRU]] (600 root)
[connection] id=DIR-320NRU | type=802-11-wireless
[802-11-wireless] ssid=DIR-320NRU | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/355]] (600 root)
[connection] id=355 | type=802-11-wireless
[802-11-wireless] ssid=355 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/KFU-NET]] (600 root)
[connection] id=KFU-NET | type=wifi
[wifi] ssid=KFU-NET | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/crow72]] (600 root)
[connection] id=crow72 | type=802-11-wireless
[802-11-wireless] ssid=crow72 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TP1111]] (600 root)
[connection] id=TP1111 | type=wifi
[wifi] ssid=TP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=manual
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Moscow (based on set time zone)


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


eth1      no frequency information.


lo        no frequency information.


wlan0     13 channels in total; available frequencies :
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


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TP' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"TP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004240749180
                    Extra: Last beacon: 288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '409' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"409"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb892d0d2a
                    Extra: Last beacon: 316ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     E3CBEE01463DF37AB9C5AB1
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:73:06:0A:C5:F5:47:55:7E:1D:F7:A4:C8:C2:DF:B5:9D:E2:27:F8
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6AE775D26377F997426A49D
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:73:06:0A:C5:F5:47:55:7E:1D:F7:A4:C8:C2:DF:B5:9D:E2:27:F8
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.19.0-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:73:06:0A:C5:F5:47:55:7E:1D:F7:A4:C8:C2:DF:B5:9D:E2:27:F8
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.19.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:73:06:0A:C5:F5:47:55:7E:1D:F7:A4:C8:C2:DF:B5:9D:E2:27:F8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


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
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


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


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0896 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"
# PCI device 0x8086:0x0896 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[14295.605656] wlan0: direct probe to <MAC 'wifi.tattele.com' [AN3]> (try 3/3)
[14295.809699] wlan0: authentication with <MAC 'wifi.tattele.com' [AN3]> timed out
[14322.081381] r8169 0000:03:00.0 eth0: link down
[14322.085069] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[14322.091755] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[14322.168189] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled
[14322.174983] iwlwifi 0000:02:00.0: Radio type=0x2-0x2-0x1
[15877.509318] wlan0: authenticate with <MAC 'TP' [AC1]>
[15877.514147] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15877.715879] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15877.919973] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15878.124157] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15878.656934] wlan0: authenticate with <MAC 'TP' [AC1]>
[15878.658866] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15878.860571] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15879.064771] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15879.268761] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15880.205931] wlan0: authenticate with <MAC 'TP' [AC1]>
[15880.208208] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15880.409426] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15880.613579] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15880.817670] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15882.229956] wlan0: authenticate with <MAC 'TP' [AC1]>
[15882.233060] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15882.434575] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15882.638676] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15882.842817] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15893.720858] wlan0: authenticate with <MAC 'TP' [AC1]>
[15893.723640] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15893.925069] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15894.129240] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15894.333371] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15922.401342] rndis_host 2-1.1:1.0 eth1: unregister 'rndis_host' usb-0000:00:1d.0-1.1, RNDIS device
[15944.812013] wlan0: authenticate with <MAC 'TP' [AC1]>
[15944.814637] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15945.018096] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15945.222194] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15945.426270] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15955.869846] wlan0: authenticate with <MAC 'TP' [AC1]>
[15955.872235] wlan0: direct probe to <MAC 'TP' [AC1]> (try 1/3)
[15956.076345] wlan0: direct probe to <MAC 'TP' [AC1]> (try 2/3)
[15956.280459] wlan0: direct probe to <MAC 'TP' [AC1]> (try 3/3)
[15956.484563] wlan0: authentication with <MAC 'TP' [AC1]> timed out
[15963.825003] wlan0: authenticate with <MAC '409' [AC2]>
[15963.829867] wlan0: direct probe to <MAC '409' [AC2]> (try 1/3)
[15964.032859] wlan0: direct probe to <MAC '409' [AC2]> (try 2/3)
[15964.236934] wlan0: direct probe to <MAC '409' [AC2]> (try 3/3)
[15964.441084] wlan0: authentication with <MAC '409' [AC2]> timed out
[15999.802898] wlan0: authenticate with <MAC 'wifi.tattele.com' [AN4]>
[15999.805844] wlan0: direct probe to <MAC 'wifi.tattele.com' [AN4]> (try 1/3)
[16000.009106] wlan0: direct probe to <MAC 'wifi.tattele.com' [AN4]> (try 2/3)
[16000.213216] wlan0: direct probe to <MAC 'wifi.tattele.com' [AN4]> (try 3/3)
[16000.417325] wlan0: authentication with <MAC 'wifi.tattele.com' [AN4]> timed out
[16015.195759] r8169 0000:03:00.0 eth0: link down
[16016.364360] wlan0: authenticate with <MAC address>
[16016.366810] wlan0: direct probe to <MAC address> (try 1/3)
[16016.570415] wlan0: direct probe to <MAC address> (try 2/3)
[16016.774506] wlan0: direct probe to <MAC address> (try 3/3)
[16016.978642] wlan0: authentication with <MAC address> timed out
[16027.344014] rndis_host 2-1.5:1.0 eth1: register 'rndis_host' at usb-0000:00:1d.0-1.5, RNDIS device, <MAC 'eth1' [IF]>


########## wireless info END ############



```

---

### Post by chili555 on 2015-11-08
We see, in your wireless script, attempts to connect to every wireless access point in your range! I suggest that you detach any ethernet and/or tether and concentrate on just one access point. Check the password carefully. For example.ChiliPepper is not the same as chilipepper.

Check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot. Any improvement?

---

