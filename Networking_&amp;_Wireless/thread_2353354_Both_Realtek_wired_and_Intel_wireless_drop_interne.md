---
title: "Both Realtek wired and Intel wireless drop internet every few minutes, Ubuntu 16.04"
date: 2017-02-21
forum: Networking &amp; Wireless
---

### Post by linuxguiri on 2017-02-21
Internet drops every few minutes on both Realtek wired and Intel wireless connections even though connection icon indicates the computer is still connected. 

Dropped internet is discovered with "The site can't be reached" screens in Chromium, or error messages when downloading/updating in Terminal, or stalled syncing in Insync application (but it occurs even when Insync is stopped).

Disconnecting and reconnecting via the connection icon resets internet temporarily.

Internet drops more frequently on wireless than on wired.

It seems to disconnect more frequently with heavier internet use (e.g., downloading multiple files, opening several webpages in quick succession).

This is a fresh install (yesterday) of Ubuntu 16.04 on a Dell Inspiron 15 5567 (dual boot). 

Ethernet and WiFi both work without disconnecting in Windows 10 on the same machine, and ethernet and wifi work on other machines running Ubuntu and Windows with the same router, so it is not a hardware or router issue.

Any suggestions for where to start?

```

########## wireless info START ##########

Report from: 21 Feb 2017 15:18 JST +0900

Booted last: 21 Feb 2017 00:00 JST +0900

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-62-generic #83-Ubuntu SMP Wed Jan 18 14:10:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 3165 [8086:3165] (rev 79)
	Subsystem: Intel Corporation Wireless 3165 [8086:4410]
	Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Dell RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1028:0767]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0c45:6a06 Microdia 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915_bpo,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::754d:a82c:8771:dc62/64 Scope:Link
          inet6 addr: 2408:210:2907:2000:a36a:a837:b619:61c1/64 Scope:Global
          inet6 addr: 2408:210:2907:2000:8c66:cb05:3f75:9b69/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:111056 (111.0 KB)  TX bytes:119318 (119.3 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5451 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3562435 (3.5 MB)  TX bytes:1118389 (1.1 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search flets-east.jp iptvf.jp

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1045     1  0 15:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

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
GENERAL.CON-UUID:                       af17b354-47be-3d43-a6f7-ba675463a9d1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   af17b354-47be-3d43-a6f7-ba675463a9d1 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.13/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 192.168.1.1
DHCP4.OPTION[10]:                       expiry = 1487672304
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 14400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.13
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 7200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 12600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         2408:210:2907:2000:8c66:cb05:3f75:9b69/64
IP6.ADDRESS[2]:                         2408:210:2907:2000:a36a:a837:b619:61c1/64
IP6.ADDRESS[3]:                         fe80::754d:a82c:8771:dc62/64
IP6.GATEWAY:                            fe80::c67d:4fff:feb3:2bc6
IP6.DNS[1]:                             2404:1a8:7f01:b::3
IP6.DNS[2]:                             2404:1a8:7f01:a::3
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:89:7:79:fc:ae:f4:24:c0:69:30:25:76:f6:d5:f0:f1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2404:1a8:7f01:b::3 2404:1a8:7f01:a::3
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_sntp_servers = 2404:1a8:1102::b 2404:1a8:1102::a
DHCP6.OPTION[7]:                        dhcp6_domain_search = flets-east.jp. iptvf.jp.
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:3:0:1:0:19:e7:13:6c:1b

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3165
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-62-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   36301ded-0ac5-4a86-9621-87290ef159af | pr500k-9912ec-1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   94420ec4-67d5-4e8b-a9bc-68665c8c0e8a | 106F3F3BCCEF

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
pr500k-9912ec-1  <MAC 'pr500k-9912ec-1' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
pr500k-9912ec-3  <MAC 'pr500k-9912ec-3' [AC15]>  Infra  116   5580 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
pr500k-35caaf-1  <MAC 'pr500k-35caaf-1' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
IhM6hT-lqOzi     <MAC 'IhM6hT-lqOzi' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
pr500k-35caaf-2  <MAC 'pr500k-35caaf-2' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
pr500m-a80d93-2  <MAC 'pr500m-a80d93-2' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
106F3F3BCCEF-1   <MAC '106F3F3BCCEF-1' [AC16]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1       no        
pr500m-a80d93-1  <MAC 'pr500m-a80d93-1' [AC18]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
106F3F3BCCEF     <MAC '106F3F3BCCEF' [AC17]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
pwr-q8aea43-1    <MAC 'pwr-q8aea43-1' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
aterm-e8fd2e-gw  <MAC 'aterm-e8fd2e-gw' [AC6]>  Infra  8     2447 MHz  54 Mbit/s  34      &#9602;&#9604;__  WEP        no        
aterm-e8fd2e-g   <MAC 'aterm-e8fd2e-g' [AC5]>  Infra  8     2447 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
pr500k-35caaf-3  <MAC 'pr500k-35caaf-3' [AC13]>  Infra  52    5260 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        
aterm-e8fd2e-a   <MAC 'aterm-e8fd2e-a' [AC11]>  Infra  36    5180 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        
aterm-e8fd2e-aw  <MAC 'aterm-e8fd2e-aw' [AC12]>  Infra  36    5180 MHz  54 Mbit/s  30      &#9602;___  WEP        no        
pr500k-9912ec-2  <MAC 'pr500k-9912ec-2' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
pr500m-a80d93-3  <MAC 'pr500m-a80d93-3' [AC14]>  Infra  100   5500 MHz  54 Mbit/s  14      &#9602;___  WPA2       no        
IhM6hT-lqOzi     <MAC 'IhM6hT-lqOzi' [AC10]>  Infra  36    5180 MHz  54 Mbit/s  12      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/pr500k-9912ec-1]] (600 root)
[connection] id=pr500k-9912ec-1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=pr500k-9912ec-1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/106F3F3BCCEF]] (600 root)
[connection] id=106F3F3BCCEF | type=wifi | permissions=user:tyler:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=106F3F3BCCEF
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Tokyo (based on set time zone)

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

enp3s0    no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.26 GHz (Channel 52)
      1   APs on   Frequency:5.58 GHz (Channel 116)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'pr500k-9912ec-1' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"pr500k-9912ec-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef8490494f
                    Extra: Last beacon: 600ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'pr500k-9912ec-2' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"pr500k-9912ec-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef84912aec
                    Extra: Last beacon: 592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'IhM6hT-lqOzi' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"IhM6hT-lqOzi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e9b91f0ad
                    Extra: Last beacon: 528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'pwr-q8aea43-1' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"pwr-q8aea43-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000016e5249c0ce
                    Extra: Last beacon: 19928ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'aterm-e8fd2e-g' [AC5]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"aterm-e8fd2e-g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dcc299c552
                    Extra: Last beacon: 452ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'aterm-e8fd2e-gw' [AC6]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"aterm-e8fd2e-gw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dcc29b2501
                    Extra: Last beacon: 416ms ago
          Cell 07 - Address: <MAC 'pr500k-35caaf-1' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"pr500k-35caaf-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c0845d8fd
                    Extra: Last beacon: 364ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'pr500k-35caaf-2' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"pr500k-35caaf-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c0846aa2b
                    Extra: Last beacon: 360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'pr500m-a80d93-2' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"pr500m-a80d93-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000090fdbe8b4
                    Extra: Last beacon: 340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'IhM6hT-lqOzi' [AC10]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"IhM6hT-lqOzi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015e9bb50371
                    Extra: Last beacon: 312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'aterm-e8fd2e-a' [AC11]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"aterm-e8fd2e-a"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dc7eb8eb03
                    Extra: Last beacon: 312ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'aterm-e8fd2e-aw' [AC12]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"aterm-e8fd2e-aw"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001dc7eb826fd
                    Extra: Last beacon: 308ms ago
          Cell 13 - Address: <MAC 'pr500k-35caaf-3' [AC13]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"pr500k-35caaf-3"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f1dd1eff82
                    Extra: Last beacon: 296ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'pr500m-a80d93-3' [AC14]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"pr500m-a80d93-3"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000644fe69c259
                    Extra: Last beacon: 280ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'pr500k-9912ec-3' [AC15]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"pr500k-9912ec-3"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ef84826b54
                    Extra: Last beacon: 152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC '106F3F3BCCEF-1' [AC16]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"106F3F3BCCEF-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000efe357e6a06
                    Extra: Last beacon: 624ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC '106F3F3BCCEF' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"106F3F3BCCEF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000efe357eeeeb
                    Extra: Last beacon: 592ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'pr500m-a80d93-1' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"pr500m-a80d93-1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000090fdb16ea
                    Extra: Last beacon: 376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'aterm-829a66-g' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"aterm-829a66-g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000449bc3cdae1
                    Extra: Last beacon: 496ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000449bc3d1183
                    Extra: Last beacon: 484ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     60ED6558F1225672289299A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-62-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-62-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-62-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     902BDA34A9B6BB2AE64F135
depends:        
intree:         Y
vermagic:       4.4.0-62-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
blacklist psmouse

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

[   26.760597] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.760974] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   26.851381] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.858459] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.038812] r8169 0000:03:00.0 enp3s0: link down
[   27.038870] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.588169] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   30.854960] wlp2s0: authenticate with <MAC 'pr500k-9912ec-1' [AC1]>
[   30.860701] wlp2s0: send auth to <MAC 'pr500k-9912ec-1' [AC1]> (try 1/3)
[   30.863092] wlp2s0: authenticated
[   30.865817] wlp2s0: associate with <MAC 'pr500k-9912ec-1' [AC1]> (try 1/3)
[   30.869770] wlp2s0: RX AssocResp from <MAC 'pr500k-9912ec-1' [AC1]> (capab=0x431 status=0 aid=2)
[   30.881224] wlp2s0: associated
[   30.881259] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  532.438062] r8169 0000:03:00.0 enp3s0: link up
[  532.438078] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  536.347261] wlp2s0: deauthenticating from <MAC 'pr500k-9912ec-1' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by linuxguiri on 2017-02-22
Bump

---

### Post by jeremy31 on 2017-02-22
It might be power management for wifi causing some issues
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Reboot

---

### Post by linuxguiri on 2017-02-22
Thanks for the suggestion, but it didn't work.
How do I undo the change?

Since wired connections drop too, I'm thinking it won't just be a wireless fix.

---

### Post by jeremy31 on 2017-02-22
```
sudo sed -i 's/wifi.powersave = 2/wifi.powersave = 3/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

I can't be sure what might be happening with the wired connection as I just use wireless.  After either wifi or ethernet fails, do
```
dmesg | tail -20
```
Post the info as it might reveal the issue

---

### Post by linuxguiri on 2017-02-22
Thank you so much for your help on this.

> **jeremy31 said:**
> After either wifi or ethernet fails, do ```
dmesg | tail -20
```
Post the info as it might reveal the issue

Here's the output of ```
dmesg | tail -20
``` after wireless and then wired internet failure.

Hope it means something to you because I don't know where to even begin interpreting it.

After wireless fail:

```
[ 4524.245320] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=1)
[ 4524.246767] wlp2s0: associated
[ 4524.313623] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[ 4531.666273] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4534.507596] wlp2s0: authenticate with 00:25:36:99:12:9c
[ 4534.513549] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[ 4534.514422] wlp2s0: authenticated
[ 4534.516072] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[ 4534.517543] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=1)
[ 4534.519061] wlp2s0: associated
[ 4534.553779] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[ 4585.034829] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4587.041645] wlp2s0: authenticate with 00:25:36:99:12:9c
[ 4587.047268] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[ 4587.048007] wlp2s0: authenticated
[ 4587.048750] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[ 4587.050180] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=1)
[ 4587.051360] wlp2s0: associated
[ 4587.087334] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[ 4813.328276] usb 1-2: USB disconnect, device number 2

```

After wired fail:

```
[ 4531.666273] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4534.507596] wlp2s0: authenticate with 00:25:36:99:12:9c
[ 4534.513549] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[ 4534.514422] wlp2s0: authenticated
[ 4534.516072] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[ 4534.517543] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=1)
[ 4534.519061] wlp2s0: associated
[ 4534.553779] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[ 4585.034829] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4587.041645] wlp2s0: authenticate with 00:25:36:99:12:9c
[ 4587.047268] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[ 4587.048007] wlp2s0: authenticated
[ 4587.048750] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[ 4587.050180] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=1)
[ 4587.051360] wlp2s0: associated
[ 4587.087334] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[ 4813.328276] usb 1-2: USB disconnect, device number 2
[ 6078.851149] r8169 0000:03:00.0 enp3s0: link up
[ 6078.851171] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 6116.307649] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)

```

---

### Post by linuxguiri on 2017-02-23
> **jeremy31 said:**
> After either wifi or ethernet fails, do
```
dmesg | tail -20
```
Post the info as it might reveal the issue

Would you mind pointing me towards some resources for interpreting the output above please?

---

### Post by QIII on 2017-02-23
Hello!

You needn't wait so long before bumping your thread.

If you have waited more than about 12 hours for a response, feel free to add a new post to your thread.  All it needs to contain is the word "bump".  That'll get your thread up to the top of the queue again.

Cheers!

---

### Post by linuxguiri on 2017-02-24
Bump

---

### Post by jeremy31 on 2017-02-24
Do you have TLP installed?  It might be some power management program making this happen.  Does your mouse also have issues?  I see
```
[ 4813.328276] usb 1-2: USB disconnect, device number 2
```
It seems that that is
```
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
```

---

### Post by linuxguiri on 2017-02-24
Thanks for the reply.

TLP is not installed.

As far as I know, there are no problems with my mouse. It's possible I disconnected my USB mouse or USB keyboard at some point (such as when I moved my laptop to connect to the ethernet to test that connection). The problem occurs with the USB mouse and keyboard disconnected as well though.

If you'd like to see other diagnostics, I filed a bug here (after a wireless internet failure): [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1666432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1666432)

---

### Post by linuxguiri on 2017-02-28
bump

---

### Post by jeremy31 on 2017-02-28
I would try a new download of the 16.04 ISO and see if the same issue occurs while using try without installing

---

### Post by linuxguiri on 2017-03-02
Thanks for the suggestion, jeremy31.

Internet fails on Ubuntu 16.04 Live CD (without installing).

In the dmesg log (ouput below), the common error for Live CD wired and installed wired and wireless internet failure seems to be:

```
[  299.865437] mce: [Hardware Error]: Machine check events logged
```

But, it didn't happen immediately prior to the wireless Live CD internet failure or in the dmesg logs I posted earlier in this thread for wired and wireless connections on installed 16.04, so it may be an error that always happens at 299.87 seconds(?) after booting and totally unrelated to the internet failure.

Not sure where to go from here.


Output of dmesg | tail -20 follows:

After wired connection internet failure on Live CD:

```
[  155.566037] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  155.889055] amdgpu 0000:01:00.0: couldn't schedule ib
[  155.889077] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  155.889093] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  155.988279] amdgpu 0000:01:00.0: couldn't schedule ib
[  155.988301] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  155.988317] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  157.877928] amdgpu 0000:01:00.0: couldn't schedule ib
[  157.877956] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  157.877978] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  157.878046] amdgpu 0000:01:00.0: couldn't schedule ib
[  157.878064] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  157.878082] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  157.878085] amdgpu 0000:01:00.0: couldn't schedule ib
[  157.878100] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  157.878116] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  227.302878] Bluetooth: RFCOMM TTY layer initialized
[  227.302884] Bluetooth: RFCOMM socket layer initialized
[  227.302887] Bluetooth: RFCOMM ver 1.11
[  299.865437] mce: [Hardware Error]: Machine check events logged
```

After wireless connection internet failure on Live CD:
```
[  157.878082] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  157.878085] amdgpu 0000:01:00.0: couldn't schedule ib
[  157.878100] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[  157.878116] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[  227.302878] Bluetooth: RFCOMM TTY layer initialized
[  227.302884] Bluetooth: RFCOMM socket layer initialized
[  227.302887] Bluetooth: RFCOMM ver 1.11
[  299.865437] mce: [Hardware Error]: Machine check events logged
[ 2609.721062] r8169 0000:03:00.0 enp3s0: link down
[ 2611.423007] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 2656.837814] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 2742.388750] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 2778.803810] wlp2s0: authenticate with 00:25:36:99:12:9c
[ 2778.810831] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[ 2778.811563] wlp2s0: authenticated
[ 2778.814565] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[ 2778.816003] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=3)
[ 2778.818174] wlp2s0: associated
[ 2778.818209] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 2781.555882] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
```

After wired connection internet failure on installed and updated 16.04
```
[   33.871252] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   33.871415] amdgpu 0000:01:00.0: couldn't schedule ib
[   33.871436] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   33.871455] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   33.871506] amdgpu 0000:01:00.0: couldn't schedule ib
[   33.871524] [drm:amdgpu_sched_run_job [amdgpu]] *ERROR* Error scheduling IBs (-22)
[   33.871541] [drm:amd_sched_main [amdgpu]] *ERROR* Failed to run job!
[   34.243313] wlp2s0: authenticate with 00:25:36:99:12:9c
[   34.250370] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[   34.251088] wlp2s0: authenticated
[   34.252725] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[   34.254225] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=3)
[   34.272530] wlp2s0: associated
[   34.272570] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   34.346001] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[   38.652878] Bluetooth: RFCOMM TTY layer initialized
[   38.652885] Bluetooth: RFCOMM socket layer initialized
[   38.652890] Bluetooth: RFCOMM ver 1.11
[   69.750753] wlp2s0: deauthenticating from 00:25:36:99:12:9c by local choice (Reason: 3=DEAUTH_LEAVING)
[  299.966544] mce: [Hardware Error]: Machine check events logged
```

After wireless connection internet failure on installed and updated 16.04
```
[   27.055583] [drm:sdma_v2_4_ring_test_ring [amdgpu]] *ERROR* amdgpu: dma failed to lock ring 10 (-2).
[   27.055589] [drm:amdgpu_resume [amdgpu]] *ERROR* resume 5 failed -2
[   27.055595] [drm:amdgpu_resume_kms [amdgpu]] *ERROR* amdgpu_resume failed (-2).
[   27.146798] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   30.331331] wlp2s0: authenticate with 00:25:36:99:12:9c
[   30.337277] wlp2s0: send auth to 00:25:36:99:12:9c (try 1/3)
[   30.338132] wlp2s0: authenticated
[   30.340069] wlp2s0: associate with 00:25:36:99:12:9c (try 1/3)
[   30.341506] wlp2s0: RX AssocResp from 00:25:36:99:12:9c (capab=0x411 status=0 aid=3)
[   30.342005] wlp2s0: associated
[   30.342027] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[   30.450989] wlp2s0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:99:12:9c
[   41.186536] Bluetooth: RFCOMM TTY layer initialized
[   41.186543] Bluetooth: RFCOMM socket layer initialized
[   41.186547] Bluetooth: RFCOMM ver 1.11
[  290.303016] pcieport 0000:00:1c.4: AER: Corrected error received: id=00e4
[  290.303024] pcieport 0000:00:1c.4: PCIe Bus Error: severity=Corrected, type=Physical Layer, id=00e4(Receiver ID)
[  290.303027] pcieport 0000:00:1c.4:   device [8086:9d14] error status/mask=00000001/00002000
[  290.303029] pcieport 0000:00:1c.4:    [ 0] Receiver Error         (First)
[  299.811807] mce: [Hardware Error]: Machine check events logged
```

---

### Post by douglas-blumeyer on 2017-03-10
I have almost exactly the same problem, linuxguiri! 

I noticed you're in Japan as well... I wonder if that has something to do with it?

I'm on a Lenovo Y50, dual boot like yours. The Windows 10 install works fine. My other computer (custom build tower, also Windows 10) works fine. It's just this Ubuntu 16.04 install that makes the internet a nightmare. Just like it is for you, my connection claims to remain active, but doesn't work until I reconnect it. And the problem is exacerbated by using wireless instead of wired, or by increased browsing activity.

I've tried fiddling with my mtu packets (due to Asahi's PPPoE), renewing my DHCP lease, changing my DNS servers, using different browsers and browser settings, power cycling, and I'm about out of ideas. I haven't totally re-installed Ubuntu yet so I guess there's always that. Here is the output of my `dmesg | tail -20` command:

```
[  578.199723] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[  578.199724] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[  581.192487] wlan0: authenticate with 00:25:36:ad:ba:5d
[  581.195182] wlan0: send auth to 00:25:36:ad:ba:5d (try 1/3)
[  581.195891] wlan0: authenticated
[  581.197959] wlan0: associate with 00:25:36:ad:ba:5d (try 1/3)
[  581.199287] wlan0: RX AssocResp from 00:25:36:ad:ba:5d (capab=0x411 status=0 aid=2)
[  581.200757] wlan0: associated
[  581.202554] cfg80211: Regulatory domain changed to country: JP
[  581.202556] cfg80211:  DFS Master region: JP
[  581.202558] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  581.202560] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  581.202561] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[  581.202562] cfg80211:   (4910000 KHz - 4990000 KHz @ 40000 KHz), (N/A, 2300 mBm), (N/A)
[  581.202564] cfg80211:   (5030000 KHz - 5090000 KHz @ 40000 KHz), (N/A, 2300 mBm), (N/A)
[  581.202565] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[  581.202567] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[  581.202569] cfg80211:   (5490000 KHz - 5710000 KHz @ 160000 KHz), (N/A, 2300 mBm), (0 s)
[  581.202570] cfg80211:   (59000000 KHz - 66000000 KHz @ 2160000 KHz), (N/A, 1000 mBm), (N/A)
[  581.208296] wlan0: Limiting TX power to 17 (20 - 3) dBm as advertised by 00:25:36:ad:ba:5d
```

---

### Post by linuxguiri on 2017-03-14
> **douglas-blumeyer said:**
> I have almost exactly the same problem, linuxguiri! 

I'm on a Lenovo Y50, dual boot like yours. The Windows 10 install works fine. My other computer (custom build tower, also Windows 10) works fine. It's just this Ubuntu 16.04 install that makes the internet a nightmare. Just like it is for you, my connection claims to remain active, but doesn't work until I reconnect it. And the problem is exacerbated by using wireless instead of wired, or by increased browsing activity. 

Thanks for your reply! It's good to know I'm not the only one with this issue. Did you file a bug?

Since we both have dual boot systems, I'm wondering if it's related to Windows not releasing the IP addresses before shutting down and booting into Ubuntu based on this page:
[https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer](https://sites.google.com/site/easylinuxtipsproject/internet#TOC-No-wired-or-wireless-internet-on-a-dual-boot-computer)

I haven't had time to investigate further though (checking IP addresses, lease times, etc. in Windows and Ubuntu). 

Have you looked into this at all?

---

