---
title: "Ubuntu 16.04 Wifi not working RTL8192E/RTL8192SE"
date: 2017-08-31
forum: Networking &amp; Wireless
---

### Post by nydaelith on 2017-08-31
Hey everyone,


Having some issues with a new instal of Ubuntu 16.4 on an old laptop.


Wired connection is working fine, but Wifi is not.


I can see all different routers around, but I'm prompted for my password over and over.


Tried reseting the password of the router, and followed the steps of this link : [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)


That gave me the following results.




```
########## wireless info START ##########


Report from: 31 Aug 2017 09:09 CEST +0200


Booted last: 31 Aug 2017 00:00 CEST +0200


Script from: 25 Mar 2017 07:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.10.0-33-generic #37~16.04.1-Ubuntu SMP Fri Aug 11 14:07:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E/RTL8192SE Wireless LAN Controller [10ec:8192] (rev 01)
    Subsystem: Askey Computer Corp. RTL8192E/RTL8192SE Wireless LAN Controller [144f:7160]
    Kernel driver in use: rtl819xE


07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [11ab:4381] (rev 11)
    Subsystem: Samsung Electronics Co Ltd Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB] [144d:c06a]
    Kernel driver in use: sky2


##### lsusb #############################


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0ac8:c342 Z-Star Microelectronics Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


r8192e_pci            135168  0
rtllib                151552  1 r8192e_pci
lib80211               16384  1 rtllib
rtl8192se              65536  0
rtl_pci                28672  1 rtl8192se
rtlwifi                73728  2 rtl8192se,rtl_pci
mac80211              782336  3 rtl8192se,rtl_pci,rtlwifi
cfg80211              602112  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:ffffb3b0c0d18000-ffffb3b0c0d18100 


enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF2]>  
          inet addr:192.168.1.236  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fd94:52ce:e35c:0:b96d:b666:837b:50be/64 Scope:Global
          inet6 addr: fd94:52ce:e35c::7c4/128 Scope:Global
          inet6 addr: fd94:52ce:e35c:0:d90b:468f:c6f1:62aa/64 Scope:Global
          inet6 addr: fe80::dfb5:7b28:4140:1a19/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5888520 (5.8 MB)  TX bytes:397988 (397.9 KB)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:160613 (160.6 KB)  TX bytes:160613 (160.6 KB)


##### iwconfig ##########################


enp7s0    no wireless extensions.


lo        no wireless extensions.


enp3s0    802.11bgn  ESSID:"Alexandre"  Nickname:"rtl8192E"
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp7s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp7s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp7s0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


    NetworkManager


Running:


root       791     1  0 08:57 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        Yukon Optima 88E8059 [PCIe Gigabit Ethernet Controller with AVB]
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       enp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       e4376eb6-1020-4cd5-93cb-d6c59d835482
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e4376eb6-1020-4cd5-93cb-d6c59d835482 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.1.236/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.236
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1504206088
DHCP4.OPTION[21]:                       host_name = alexandre-R580-R590
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fd94:52ce:e35c::7c4/128
IP6.ADDRESS[2]:                         fd94:52ce:e35c:0:b96d:b666:837b:50be/64
IP6.ADDRESS[3]:                         fd94:52ce:e35c:0:d90b:468f:c6f1:62aa/64
IP6.ADDRESS[4]:                         fe80::dfb5:7b28:4140:1a19/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fd94:52ce:e35c::/48, nh = fe80::c6e9:84ff:fe7a:99a7, mt = 100
IP6.DNS[1]:                             fd94:52ce:e35c::1
IP6.DOMAIN[1]:                          lan
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:5:91:80:7:23:99:fb:ec:65:9b:bd:40:8e:c0:ec:7d
DHCP6.OPTION[2]:                        dhcp6_unknown_11 = 3:1:0:59:a7:b4:4c:0:0:0:7c:1:45:f0:51:bd:81:25:48:e4:93:27:20:18:26:d6:25:87
DHCP6.OPTION[3]:                        dhcp6_name_servers = fd94:52ce:e35c::1
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        rebind = 34560
DHCP6.OPTION[6]:                        max_life = 4294967295
DHCP6.OPTION[7]:                        preferred_life = 4294967295
DHCP6.OPTION[8]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[9]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[10]:                       life_starts = 1504162892
DHCP6.OPTION[11]:                       ip6_address = fd94:52ce:e35c::7c4
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       dhcp6_domain_search = lan.
DHCP6.OPTION[14]:                       dhcp6_solmax_rt = 60
DHCP6.OPTION[15]:                       renew = 21600
DHCP6.OPTION[16]:                       starts = 1504162892
DHCP6.OPTION[17]:                       iaid = 54:b1:81:50
DHCP6.OPTION[18]:                       dhcp6_server_id = 0:3:0:1:<MAC address>


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8192E/RTL8192SE Wireless LAN Controller
GENERAL.DRIVER:                         rtl819xE
GENERAL.DRIVER-VERSION:                 0014.0401.2010
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:03:00.0/net/enp3s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ffa7ba4a-ae5b-4393-9a90-c884ddcf398a | Alexandre


SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Svetli                 <MAC 'Svetli' [AC8]>  Infra  9     2452 MHz  22 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
MTEL-5DE8              <MAC 'MTEL-5DE8' [AN2]>  Infra  1     2412 MHz  16 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
chipev                 <MAC 'chipev' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
AngellL1               <MAC 'AngellL1' [AC2]>  Infra  3     2422 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
Marian                 <MAC 'Marian' [AN5]>  Infra  3     2422 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Chudomira              <MAC 'Chudomira' [AC4]>  Infra  5     2432 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
stoian                 <MAC 'stoian' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WEP        no        
Kemi Wiki              <MAC 'Kemi Wiki' [AC3]>  Infra  6     2437 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
202zmk                 <MAC '202zmk' [AN9]>  Infra  6     2437 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
NET1 WiFi              <MAC 'NET1 WiFi' [AN10]>  Infra  6     2437 MHz  22 Mbit/s  55      &#9602;&#9604;__  --         no        
c17h21no4              <MAC 'c17h21no4' [AN11]>  Infra  6     2437 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Kiflichka              <MAC 'Kiflichka' [AC6]>  Infra  6     2437 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Daria                  <MAC 'Daria' [AN13]>  Infra  7     2442 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
e.klinkova             <MAC 'e.klinkova' [AN14]>  Infra  7     2442 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Niky Home Network      <MAC 'Niky Home Network' [AN15]>  Infra  8     2447 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
M-Tel_B875             <MAC 'M-Tel_B875' [AC9]>  Infra  9     2452 MHz  16 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
Tenda_594B98           <MAC 'Tenda_594B98' [AC13]>  Infra  10    2457 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1       no        
Mitevi                 <MAC 'Mitevi' [AC10]>  Infra  11    2462 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
HELENE                 <MAC 'HELENE' [AC16]>  Infra  11    2462 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
Kozaliev               <MAC 'Kozaliev' [AC12]>  Infra  11    2462 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
kalinovd               <MAC 'kalinovd' [AC14]>  Infra  11    2462 MHz  22 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
OpenWrt                <MAC 'OpenWrt' [AC15]>  Infra  11    2462 MHz  16 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Alexandre              <MAC 'Alexandre' [AC7]>  Infra  11    2462 MHz  8 Mbit/s   55      &#9602;&#9604;__  WPA1       no        
Pretty fly for a WiFi  <MAC 'Pretty fly for a WiFi' [AC11]>  Infra  13    2472 MHz  44 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
&#1042;&#1080;&#1088;&#1091;&#1089;                  <MAC '&#1042;&#1080;&#1088;&#1091;&#1089;' [AN25]>  Infra  11    2462 MHz  22 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
Nicol                  <MAC 'Nicol' [AN26]>  Infra  11    2462 MHz  22 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/Alexandre]] (600 root)
[connection] id=Alexandre | type=wifi | permissions=
[wifi] mac-address=<MAC 'enp3s0' [IF1]> | mac-address-blacklist= | ssid=Alexandre
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Paris (based on set time zone)


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


enp7s0    no frequency information.


lo        no frequency information.


enp3s0    13 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


enp7s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


enp3s0    Scan completed :
          Cell 01 - Address: <MAC 'chipev' [AC1]>
                    ESSID:"chipev"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 80ms ago
          Cell 02 - Address: <MAC 'AngellL1' [AC2]>
                    ESSID:"AngellL1"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 49ms ago
          Cell 03 - Address: <MAC 'Kemi Wiki' [AC3]>
                    ESSID:"Kemi Wiki"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=74/100  Signal level=-67 dBm  Noise level=-107 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 37ms ago
          Cell 04 - Address: <MAC 'Chudomira' [AC4]>
                    ESSID:"Chudomira"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=76/100  Signal level=-67 dBm  Noise level=-108 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 32ms ago
          Cell 05 - Address: <MAC 'stoian' [AC5]>
                    ESSID:"stoian"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 9 11 6 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    Extra: Last beacon: 53ms ago
          Cell 06 - Address: <MAC 'Kiflichka' [AC6]>
                    ESSID:"Kiflichka"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 38ms ago
          Cell 07 - Address: <MAC 'Alexandre' [AC7]>
                    ESSID:"Alexandre"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:72 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 12ms ago
          Cell 08 - Address: <MAC 'Svetli' [AC8]>
                    ESSID:"Svetli"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 9ms ago
          Cell 09 - Address: <MAC 'M-Tel_B875' [AC9]>
                    ESSID:"M-Tel_B875"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-67 dBm  Noise level=-101 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6ms ago
          Cell 10 - Address: <MAC 'Mitevi' [AC10]>
                    ESSID:"Mitevi"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-67 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7ms ago
          Cell 11 - Address: <MAC 'Pretty fly for a WiFi' [AC11]>
                    ESSID:"Pretty fly for a WiFi"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-67 dBm  Noise level=-101 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7ms ago
          Cell 12 - Address: <MAC 'Kozaliev' [AC12]>
                    ESSID:"Kozaliev"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=63/100  Signal level=-67 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1ms ago
          Cell 13 - Address: <MAC 'Tenda_594B98' [AC13]>
                    ESSID:"Tenda_594B98"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:10
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=68/100  Signal level=-67 dBm  Noise level=-104 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3ms ago
          Cell 14 - Address: <MAC 'kalinovd' [AC14]>
                    ESSID:"kalinovd"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:150 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-67 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1377ms ago
          Cell 15 - Address: <MAC 'OpenWrt' [AC15]>
                    ESSID:"OpenWrt"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:144.5 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality=65/100  Signal level=-67 dBm  Noise level=-102 dBm
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 17ms ago
          Cell 16 - Address: <MAC 'HELENE' [AC16]>
                    ESSID:"HELENE"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality=60/100  Signal level=-67 dBm  Noise level=-100 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 150ms ago


##### module infos ######################


[r8192e_pci]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/staging/rtl8192e/rtl8192e/r8192e_pci.ko
firmware:       RTL8192E/data.img
firmware:       RTL8192E/main.img
firmware:       RTL8192E/boot.img
license:        GPL
version:        0014.0401.2010
author:         Copyright(c) 2008 - 2010 Realsil Semiconductor Corporation <wlanfae@realtek.com>
description:    Linux driver for Realtek RTL819x WiFi cards
srcversion:     E201B82E770DB45D6952678
depends:        rtllib
staging:        Y
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware WEP support(default use hw. set 0 to use software security) (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)


[rtllib]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/staging/rtl8192e/rtllib.ko
license:        GPL
srcversion:     E68311DC8054206E5E9719D
depends:        lib80211
staging:        Y
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 


[rtl8192se]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     6B0D839AC40BB4CA9AD1487
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 1)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_pci]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B93F82B28F7945C22514E4D
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.10.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     884DE3F31278351A45DA409
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.10.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-33-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[r8192e_pci]
channels: 16383
hwwep: 1
ifname: wlan%d


[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y


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


##### dmesg #############################


[  693.909836] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  696.449025] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  696.469670] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  699.008798] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  699.029551] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  701.568761] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  701.593418] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6! (repeated 21 times)
[  704.128592] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  704.160641] rtl819xE 0000:03:00.0 enp3s0: ============>sync_scan_hurryup out
[  704.181290] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  706.720553] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  706.745232] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  709.280336] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  709.301013] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  711.840243] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  711.860901] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  714.404014] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  714.424704] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  716.959986] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  716.980647] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  719.519866] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  719.540533] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  722.079727] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  722.100415] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  724.639557] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  724.660264] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  727.199460] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  727.220105] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  729.759339] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  729.779949] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  732.319197] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  732.339854] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  734.878969] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  734.899744] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  737.438939] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  737.459591] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  739.998734] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  740.019490] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  742.558640] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  742.579360] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  745.118465] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  745.139151] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!
[  747.678411] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  747.699055] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6! (repeated 11 times)
[  750.238237] rtl819xE 0000:03:00.0 enp3s0: Linking with Alexandre,channel:11, qos:1, myHT:1, networkHT:1, mode:10 cur_net.flags:0x40e
[  750.286223] rtl819xE 0000:03:00.0 enp3s0: ============>sync_scan_hurryup out
[  750.306927] rtl819xE 0000:03:00.0 enp3s0: softmac_mgmt_xmit():insert to waitqueue, queue_index:6!



```




Any help would be awesome :)


Thank you in advance.

Edit : Also tried removing my router from the Network settings and add it again.

---

### Post by praseodym on 2017-08-31
```
r8192e_pci            135168  0
...
rtl8192se              65536  0
```
It shows 2 drivers loaded. Lets try one only
```

sudo modprobe -rfv rtl8192se r8192e_pci
sudo modprobe -v r8192e_pci
```

---

### Post by nydaelith on 2017-08-31
Ran the previous commands.

After reboot, still no luck.

---

### Post by praseodym on 2017-08-31
Please show "lsmod" again

---

### Post by nydaelith on 2017-09-01
There you go :

```


~$ lsmod
Module                  Size  Used by
cfg80211              602112  0
samsung_laptop         20480  0
snd_hda_codec_hdmi     49152  4
uvcvideo               90112  0
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_v4l2         24576  1 uvcvideo
videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2
videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2
media                  40960  2 uvcvideo,videodev
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             200704  0
kvm                   593920  1 kvm_intel
irqbypass              16384  1 kvm
intel_cstate           20480  0
snd_rawmidi            32768  1 snd_seq_midi
snd_hda_codec_realtek    90112  1
snd_hda_codec_generic    73728  1 snd_hda_codec_realtek
joydev                 20480  0
input_leds             16384  0
snd_hda_intel          36864  5
serio_raw              16384  0
snd_hda_codec         126976  4 snd_hda_intel,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
snd_hda_core           81920  5 snd_hda_intel,snd_hda_codec,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec_realtek
intel_ips              20480  0
snd_seq                65536  2 snd_seq_midi_event,snd_seq_midi
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               102400  4 snd_hda_intel,snd_hda_codec,snd_hda_core,snd_hda_codec_hdmi
r8192e_pci            135168  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
rtllib                151552  1 r8192e_pci
lib80211               16384  1 rtllib
snd_timer              32768  2 snd_seq,snd_pcm
snd                    77824  21 snd_hda_intel,snd_hwdep,snd_seq,snd_hda_codec,snd_timer,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_seq_device,snd_hda_codec_realtek,snd_pcm
lpc_ich                24576  0
shpchp                 36864  0
soundcore              16384  1 snd
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,parport_pc,ppdev
autofs4                40960  2
nouveau              1601536  8
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    98304  1 nouveau
drm_kms_helper        151552  1 nouveau
syscopyarea            16384  1 drm_kms_helper
sysfillrect            16384  1 drm_kms_helper
psmouse               139264  0
sysimgblt              16384  1 drm_kms_helper
fb_sys_fops            16384  1 drm_kms_helper
ahci                   36864  2
drm                   352256  11 nouveau,ttm,drm_kms_helper
libahci                32768  1 ahci
sky2                   61440  0
fjes                   77824  0
video                  40960  2 nouveau,samsung_laptop


```

---

### Post by nydaelith on 2017-09-01
After checking some threads about this, I saw there was an issue with my chipset on the 64bit version, so I started from scratch and installed the 32bit.

Same issues though, and after trying the same steps from before, no progress.

Ran the same script after everything :

[http://paste.ubuntu.com/25446647/](http://paste.ubuntu.com/25446647/)

Thanks again for help :)

---

### Post by praseodym on 2017-09-01
Still two drivers loaded. Check the commands again.

Is your network shown i the SSID list of the output? Or is it hidden?

---

### Post by nydaelith on 2017-09-02
Apologies, after trying the following commands, I rebooted my PC and saw there was no progress.

Today, I did the same and checked without rebooting, and the issue was solved. I can connect correctly to my network (Not hidden, name Alexandre).

However, the lsmod correctly displays only one driver now, however, after rebooting again, issue comes back, and lsmod displays again the 2 drivers loaded. 

Any way of making it permanent ?

EDIT : Never mind before. Now I get disconnected after a few minutes of use :/
It's not asking me for my password now, I just get the message "Disconnected".

Rebooting the PC and using again the commands solve the issue, again for a few minutes.

---

### Post by praseodym on 2017-09-02
Which one works?

---

