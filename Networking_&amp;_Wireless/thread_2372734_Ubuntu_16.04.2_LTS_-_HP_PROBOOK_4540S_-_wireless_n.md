---
title: "Ubuntu 16.04.2 LTS - HP PROBOOK 4540S - wireless network does not work"
date: 2017-09-28
forum: Networking &amp; Wireless
---

### Post by balajimit on 2017-09-28
With Ubuntu 16.04.2 LTS, wireless network does not work on HP PROBOOK 4540S.
It is able to connect to the router and get IP and ping the gateway. But internet does not work.
Attaching the output of wireless info script wireless-info.tar.gz (Script [https://github.com/UbuntuForums/wireless-info](https://github.com/UbuntuForums/wireless-info)).

Thanks in advance

---

### Post by praseodym on 2017-09-28
Here, I cannot open that file. Can you please c/p the content here in CODE-tags?

---

### Post by jeremy31 on 2017-09-28
For praseodym, as it did open for me
```

########## wireless info START ##########

Report from: 28 Sep 2017 16:49 IST +0530

Booted last: 28 Sep 2017 00:00 IST +0530

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-96-generic #119-Ubuntu SMP Tue Sep 12 14:59:54 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	DeviceName: WLAN
	Subsystem: Hewlett-Packard Company AR9485 Wireless Network Adapter [103c:1785]

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
	Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:17f6]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0cf3:311d Atheros Communications, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b370 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0781:5530 SanDisk Corp. Cruzer
Bus 001 Device 003: ID 138a:003d Validity Sensors, Inc. VFS491
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 04b3:3025 IBM Corp. NetVista Full Width Keyboard
Bus 003 Device 003: ID 0461:4e22 Primax Electronics, Ltd 
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ath3k                  20480  0
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF1]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF2]>  
          inet addr:10.161.104.189  Bcast:10.161.255.255  Mask:255.255.0.0
          inet6 addr: fe80::<IP6 'enp4s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15492059 (15.4 MB)  TX bytes:2527417 (2.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:74833 (74.8 KB)  TX bytes:74833 (74.8 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF3]>  
          inet addr:10.169.1.149  Bcast:10.169.1.255  Mask:255.255.254.0
          inet6 addr: fe80::<IP6 'wlo1' [IF3]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13 errors:0 dropped:0 overruns:0 frame:0
          TX packets:468 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1904 (1.9 KB)  TX bytes:70603 (70.6 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp4s0    no wireless extensions.

docker0   no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"CAV-GUEST"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'CAV-GUEST' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.161.0.1      0.0.0.0         UG    100    0        0 enp4s0
0.0.0.0         10.169.0.1      0.0.0.0         UG    600    0        0 wlo1
1.1.1.1         10.169.0.1      255.255.255.255 UGH   600    0        0 wlo1
10.161.0.0      0.0.0.0         255.255.0.0     U     100    0        0 enp4s0
10.169.0.0      0.0.0.0         255.255.254.0   U     600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 docker0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0

##### resolv.conf #######################

domain caveonetworks.com
search caveonetworks.com
nameserver 10.167.4.10
nameserver 10.17.5.10

##### network managers ##################

Installed:

	NetworkManager

Running:

root      3343     1  0 16:05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         docker0
GENERAL.TYPE:                           bridge
GENERAL.NM-TYPE:                        NMDeviceBridge
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bridge
GENERAL.DRIVER-VERSION:                 2.3
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'docker0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       docker0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     docker0
GENERAL.CON-UUID:                       764377a8-2d15-4b00-abff-3e12378a6fc8
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               yes
BRIDGE.SLAVES:                          
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   764377a8-2d15-4b00-abff-3e12378a6fc8 | docker0
IP4.ADDRESS[1]:                         172.17.0.1/16
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168e-3_0.0.4 03/27/12
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       enp4s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       b76a8ba8-9a3c-321b-ab5b-eae71b9a6310
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b76a8ba8-9a3c-321b-ab5b-eae71b9a6310 | Wired connection 1
IP4.ADDRESS[1]:                         10.161.104.189/16
IP4.GATEWAY:                            10.161.0.1
IP4.DNS[1]:                             10.167.4.10
IP4.DNS[2]:                             10.17.5.10
IP4.DOMAIN[1]:                          caveonetworks.com
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1506682740
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.161.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.161.104.189
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = caveonetworks.com
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.161.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 10.167.4.10 10.17.5.10
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.0.0
DHCP4.OPTION[26]:                       network_number = 10.161.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.161.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'enp4s0' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-96-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     CAV-GUEST
GENERAL.CON-UUID:                       02f78ad9-bd3a-4b00-9968-bbe4b67a1935
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     6 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   02f78ad9-bd3a-4b00-9968-bbe4b67a1935 | CAV-GUEST
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   c05d2974-c28d-4054-a065-6d052a3867c4 | CAV-Guest5
IP4.ADDRESS[1]:                         10.169.1.149/23
IP4.GATEWAY:                            10.169.0.1
IP4.ROUTE[1]:                           dst = 1.1.1.1/32, nh = 10.169.0.1, mt = 600
IP4.DNS[1]:                             103.8.46.5
IP4.DNS[2]:                             180.151.151.151
IP4.DNS[3]:                             103.8.44.5
IP4.DOMAIN[1]:                          caveonetworks.com
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1506682127
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.169.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.169.1.149
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = caveonetworks.com
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.169.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 103.8.46.5 180.151.151.151 103.8.44.5
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.254.0
DHCP4.OPTION[26]:                       network_number = 10.169.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 1.1.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlo1' [IF3]>/64
IP6.GATEWAY:                            

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
CAV-Guest5            <MAC 'CAV-Guest5' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
CAV-GUEST             <MAC 'CAV-GUEST' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       yes     * 
--                    <MAC '\00\00\00\00\00\00\00' [AC6]>  Infra  10    2457 MHz  54 Mbit/s  40      &#9602;&#9604;__  --         no        
CAVM_Akshat_24        <MAC 'CAVM_Akshat_24' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
NCG_DSP_LAB           <MAC 'NCG_DSP_LAB' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
TeleCentro Wifi Zone  <MAC 'TeleCentro Wifi Zone' [AC7]>  Infra  8     2447 MHz  54 Mbit/s  17      &#9602;___  --         no        
island-365240         <MAC 'island-365240' [AC2]>  Infra  7     2442 MHz  54 Mbit/s  12      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/CAV-GUEST]] (600 root)
[connection] id=CAV-GUEST | type=wifi | permissions=user:balaji:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=CAV-GUEST
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/CAV-Guest5]] (600 root)
[connection] id=CAV-Guest5 | type=wifi | permissions=user:balaji:;
[wifi] mac-address=<MAC 'wlo1' [IF3]> | mac-address-blacklist= | ssid=CAV-Guest5
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country IN: DFS-JP
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A)
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 20), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp4s0    no frequency information.

docker0   no frequency information.

wlo1      13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp4s0    Interface doesn't support scanning.

docker0   Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'CAV-GUEST' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"CAV-GUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000240aedd9b1f
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'island-365240' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"island-365240"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000035d3b20d
                    Extra: Last beacon: 20280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'CAV-Guest5' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"CAV-Guest5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000336372be84
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'CAVM_Akshat_24' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"CAVM_Akshat_24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014444be817e
                    Extra: Last beacon: 748ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NCG_DSP_LAB' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"NCG_DSP_LAB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b9ee6b11f9
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC '\00\00\00\00\00\00\00' [AC6]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ca7a6e1190
                    Extra: Last beacon: 1020ms ago
          Cell 07 - Address: <MAC 'TeleCentro Wifi Zone' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"TeleCentro Wifi Zone"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000066f7625e
                    Extra: Last beacon: 14048ms ago

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D578DE67B7E1EB3760B717B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5E13CACC8C4252BB4B57367
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     19C5721EB199C107B73269F
depends:        ath
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 

[ath]
filename:       /lib/modules/4.4.0-96-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-96-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     066D9B501A63401DBFCBF56
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-96-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     074D104BC98456ECCF3395E
depends:        
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/4.4.0-96-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     AC2C693C639F7A0981097A7
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-96-generic SMP mod_unload modversions 

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
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

[  935.206420] ath9k 0000:03:00.0 wlo1: renamed from wlan0
[  935.236583] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)
[  937.213500] wlo1: authenticate with <MAC 'CAV-GUEST' [AC1]>
[  937.234943] wlo1: send auth to <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[  937.237046] wlo1: authenticated
[  937.240492] wlo1: associate with <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[  937.251142] wlo1: RX AssocResp from <MAC 'CAV-GUEST' [AC1]> (capab=0x431 status=0 aid=40)
[  937.251256] wlo1: associated
[  937.251310] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[  937.256028] ath: EEPROM regdomain: 0x8164
[  937.256033] ath: EEPROM indicates we should expect a country code
[  937.256036] ath: doing EEPROM country->regdmn map search
[  937.256038] ath: country maps to regdmn code: 0x5b
[  937.256041] ath: Country alpha2 being used: IN
[  937.256043] ath: Regpair used: 0x5b
[  937.256045] ath: regdomain 0x8164 dynamically updated by country IE
[  937.316112] wlo1: Limiting TX power to 19 dBm as advertised by <MAC 'CAV-GUEST' [AC1]>
[ 1085.462129] wlo1: deauthenticating from <MAC 'CAV-GUEST' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1086.436225] wlo1: authenticate with <MAC 'CAV-GUEST' [AC1]>
[ 1086.457690] wlo1: send auth to <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[ 1086.463657] wlo1: authenticated
[ 1086.467429] wlo1: associate with <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[ 1086.473274] wlo1: RX AssocResp from <MAC 'CAV-GUEST' [AC1]> (capab=0x431 status=0 aid=40)
[ 1086.473389] wlo1: associated
[ 1086.477057] ath: EEPROM regdomain: 0x8164
[ 1086.477061] ath: EEPROM indicates we should expect a country code
[ 1086.477064] ath: doing EEPROM country->regdmn map search
[ 1086.477066] ath: country maps to regdmn code: 0x5b
[ 1086.477069] ath: Country alpha2 being used: IN
[ 1086.477071] ath: Regpair used: 0x5b
[ 1086.477074] ath: regdomain 0x8164 dynamically updated by country IE
[ 1086.576506] wlo1: Limiting TX power to 19 dBm as advertised by <MAC 'CAV-GUEST' [AC1]>
[ 1697.847036] r8169 0000:04:00.0 enp4s0: link down
[ 1699.400505] r8169 0000:04:00.0 enp4s0: link up
[ 2896.583848] wlo1: deauthenticated from <MAC 'CAV-GUEST' [AC1]> (Reason: 2=PREV_AUTH_NOT_VALID)
[ 2897.703524] wlo1: authenticate with <MAC 'CAV-GUEST' [AC1]>
[ 2897.725189] wlo1: send auth to <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[ 2897.729728] wlo1: authenticated
[ 2897.730794] wlo1: associate with <MAC 'CAV-GUEST' [AC1]> (try 1/3)
[ 2897.738211] wlo1: RX AssocResp from <MAC 'CAV-GUEST' [AC1]> (capab=0x431 status=0 aid=40)
[ 2897.738325] wlo1: associated
[ 2897.741290] ath: EEPROM regdomain: 0x8164
[ 2897.741293] ath: EEPROM indicates we should expect a country code
[ 2897.741295] ath: doing EEPROM country->regdmn map search
[ 2897.741296] ath: country maps to regdmn code: 0x5b
[ 2897.741297] ath: Country alpha2 being used: IN
[ 2897.741298] ath: Regpair used: 0x5b
[ 2897.741300] ath: regdomain 0x8164 dynamically updated by country IE
[ 2897.861056] wlo1: Limiting TX power to 19 dBm as advertised by <MAC 'CAV-GUEST' [AC1]>

########## wireless info END ############

```
I think the likely cause is the nameserver entries in resolv.conf

---

### Post by praseodym on 2017-09-29
Sure the PW is correct? No "strange" characters? Should be at least 8 characters there.

Edit: MAC address filter is turned off? Check the router interface.

---

