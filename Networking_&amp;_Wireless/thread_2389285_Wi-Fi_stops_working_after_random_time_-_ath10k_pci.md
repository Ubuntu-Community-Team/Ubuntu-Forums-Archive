---
title: "Wi-Fi stops working after random time - ath10k_pci Qualcomm Atheros Device"
date: 2018-04-14
forum: Networking &amp; Wireless
---

### Post by Briga on 2018-04-14
Hi, I hope someone can help me with this issue. I start with the problem description and then get into more technical description. 

My wireless works well and then after a while it goes off and the only way is to restart the PC. By going off I mean it looks connected on the network manager, but the adapter is not responding any more, and won't connect to any AP. Wired connection keeps working. The problem is strictly with the wireless adapter. When that happens this is what fills my log:

```
failed to start hw scan: -11 ath10k_pci failed to wake target for write32 of ...
```

One after the other, plenty of lines like that. 

This can happen after few minutes after boot, or hours, there's no evident cause. With a specific AP in an office it happens always in minutes though. 
It happens always then there is some power issues (switching to battery) or closing the lid. I therefore disabled suspend on lid closing, and tried disabling power management on the adapter with no luck. This is the configuration when everything is fine:

```

########## wireless info START ##########

Report from: 14 Apr 2018 17:22 CEST +0200

Booted last: 14 Apr 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, pci=noaer, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:205f]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
	Subsystem: AzureWave Device [1a3b:2231]
	Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 002: ID 0bc2:61b6 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3491 IMC Networks 
Bus 001 Device 003: ID 04d9:fc07 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 04f2:b52b Chicony Electronics Co., Ltd 
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

ath10k_pci             45056  0
ath10k_core           352256  1 ath10k_pci
ath                    28672  1 ath10k_core
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
mac80211              782336  1 ath10k_core
sparse_keymap          16384  1 asus_wmi
cfg80211              614400  3 mac80211,ath,ath10k_core
wmi                    24576  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:309144 (309.1 KB)  TX bytes:309144 (309.1 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7cd2:28f7:c6ca:8b29/64 Scope:Link
          inet6 addr: ::194:e640:dd94:90e0/64 Scope:Global
          inet6 addr: ::ce5c:5a20:146:b73/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:361901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132391 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:479801845 (479.8 MB)  TX bytes:14439646 (14.4 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"pdb_elcancelda_5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'pdb_elcancelda_5G' [AC1]>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:150  Invalid misc:2189   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       952     1  0 16:18 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Sunrise Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.13.0-38-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     pdb_elcancelda_5G
GENERAL.CON-UUID:                       d4bbf62b-4f3c-4cfd-8907-bad269434e53
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,6,7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   886a76b2-a633-4687-b6c0-42a499e2368a | MYA-L11
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   4f5b31eb-eb32-467a-b555-9270ebb32412 | pdb_elcancelda_2.4G
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   d4bbf62b-4f3c-4cfd-8907-bad269434e53 | pdb_elcancelda_5G
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.220.220
IP4.DNS[2]:                             208.67.222.222
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1523715512
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.3
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 208.67.220.220 208.67.222.222
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ::194:e640:dd94:90e0/64
IP6.ADDRESS[2]:                         ::ce5c:5a20:146:b73/64
IP6.ADDRESS[3]:                         fe80::7cd2:28f7:c6ca:8b29/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             ::777f:d050:0:0
IP6.DNS[2]:                             0:0:50d0:7f77::
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = ::777f:d050:0:0 0:0:50d0:7f77::
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:70:4f:57:3c:2:ba
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:68:d8:76:6c:56:fc:55:c1:41:72:5d:20:87:19:c5:f

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_B0_55_08_60_7B_1A
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{16}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   38bfda4b-2f0b-404f-addf-9217b03b783a | MatyRocks Network

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_EC_10_7B_E1_E8_32
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   340cb6ae-dfae-47b9-869d-fba6e18a5413 | Briga3 Network

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
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

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
elacandela_guest                 <MAC 'elacandela_guest' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2      no        
pdb_elcancelda_2.4G              <MAC 'pdb_elcancelda_2.4G' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2      no        
pdb_elcancelda_5G                <MAC 'pdb_elcancelda_5G' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2      yes     * 
MYA-L11                          <MAC 'MYA-L11' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2      no        
Vodafone-WiFi                    <MAC 'Vodafone-WiFi' [AC5]>  Infra  5     2432 MHz  54 Mbit/s  17      &#9602;___  --        no        
NETGEAR SSID                     <MAC 'NETGEAR SSID' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  17      &#9602;___  WPA1      no        
HP-Print-44-Deskjet 3520 series  <MAC 'HP-Print-44-Deskjet 3520 series' [AN7]>  Infra  10    2457 MHz  54 Mbit/s  14      &#9602;___  WPA2      no        
Vodafone-SAIMIR-BOSSI            <MAC 'Vodafone-SAIMIR-BOSSI' [AN8]>  Infra  5     2432 MHz  54 Mbit/s  9       &#9602;___  WPA2      no        

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

[[/etc/NetworkManager/system-connections/pdb_elcancelda_5G]] (600 root)
[connection] id=pdb_elcancelda_5G | type=wifi | permissions=user:briga:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=pdb_elcancelda_5G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pdb_elcancelda_2.4G]] (600 root)
[connection] id=pdb_elcancelda_2.4G | type=wifi | autoconnect=false | permissions=user:briga:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=pdb_elcancelda_2.4G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

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

enp2s0    no frequency information.

wlp3s0    32 channels in total; available frequencies :
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

enp2s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'pdb_elcancelda_5G' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"pdb_elcancelda_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c4fb068d1c
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'pdb_elcancelda_2.4G' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"pdb_elcancelda_2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c51b5200ec
                    Extra: Last beacon: 6932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'elacandela_guest' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"elacandela_guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c51b52d6c8
                    Extra: Last beacon: 6932ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'dlink-2AB1' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"dlink-2AB1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007cba4616d
                    Extra: Last beacon: 6904ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 05 - Address: <MAC 'Vodafone-WiFi' [AC5]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"Vodafone-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000012cb3385
                    Extra: Last beacon: 6608ms ago
          Cell 06 - Address: <MAC 'MYA-L11' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"MYA-L11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000068d38ef4a
                    Extra: Last beacon: 6424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     8D7A52EE462CD73D0445DB2
depends:        ath10k_core
intree:         Y
name:           ath10k_pci
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     7F06478F5745B064BF3BC89
depends:        mac80211,cfg80211,ath
intree:         Y
name:           ath10k_core
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-38-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     125925493BE4168AD62F1ED
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

mount /mnt/exthdd 
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.318036] ath10k_pci 0000:03:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    3.669197] ath10k_pci 0000:03:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2231
[    3.669201] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.669765] ath10k_pci 0000:03:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7
[    3.749155] ath10k_pci 0000:03:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[    4.244375] ath10k_pci 0000:03:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    4.251032] ath: EEPROM regdomain: 0x6a
[    4.251033] ath: EEPROM indicates we should expect a direct regpair map
[    4.251035] ath: Country alpha2 being used: 00
[    4.251035] ath: Regpair used: 0x6a
[    4.259722] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.060862] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[    5.740263] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.758688] r8169 0000:02:00.0 enp2s0: link down
[    5.758746] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    5.838259] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.942898] ath10k_pci 0000:03:00.0: no channel configured; ignoring frame(s)!
[   18.056775] wlp3s0: authenticate with <MAC 'pdb_elcancelda_5G' [AC1]>
[   18.085289] wlp3s0: send auth to <MAC 'pdb_elcancelda_5G' [AC1]> (try 1/3)
[   18.085966] wlp3s0: authenticated
[   18.088016] wlp3s0: associate with <MAC 'pdb_elcancelda_5G' [AC1]> (try 1/3)
[   18.089298] wlp3s0: RX AssocResp from <MAC 'pdb_elcancelda_5G' [AC1]> (capab=0x411 status=0 aid=1)
[   18.091685] wlp3s0: associated
[   18.091808] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready

########## wireless info END ############

```

I also tried disabling IPv6 without solving the issue which seems very HW to me. 

The PC is an Asus P2530UA-XO1246D Notebook running Ubuntu 16.04 fully updated. 

Thanks to any one who could try to help me!

---

### Post by jeremy31 on 2018-04-14
How did you disable power management?

---

### Post by Briga on 2018-04-14
> **jeremy31 said:**
> How did you disable power management?

I tried putting this lines:
```
[connection]
wifi.powersave = 2
```
in 
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf 

but nothing changed.....

---

### Post by jeremy31 on 2018-04-14
Did you reboot or restart Network Manager after that?

---

### Post by Briga on 2018-04-15
> **jeremy31 said:**
> Did you reboot or restart Network Manager after that?

I rebooted but I believe you can restart NM as well. 
The proof should come from iwconfig that's stating power management

---

### Post by jeremy31 on 2018-04-15
Can you run the script again after you have a problem with it.  Since you have already downloaded it, just do ```
./wireless-info
```
What AP does it always have problems with?

---

### Post by praseodym on 2018-04-15
Lets check
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=IT/g" /etc/default/crda 
```
Reboot

---

### Post by Briga on 2018-04-15
> **jeremy31 said:**
> Can you run the script again after you have a problem with it.  Since you have already downloaded it, just do ```
./wireless-info
```
What AP does it always have problems with?

Here is the script:
```

########## wireless info START ##########

Report from: 14 Apr 2018 19:00 CEST +0200

Booted last: 14 Apr 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.4 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, pci=noaer, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:205f]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 31)
	Subsystem: AzureWave Device [1a3b:2231]
	Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 002: ID 0bc2:61b6 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 13d3:3491 IMC Networks 
Bus 001 Device 003: ID 04d9:fc07 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 04f2:b52b Chicony Electronics Co., Ltd 
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

ath10k_pci             45056  0
ath10k_core           352256  1 ath10k_pci
ath                    28672  1 ath10k_core
asus_nb_wmi            28672  0
asus_wmi               28672  1 asus_nb_wmi
mac80211              782336  1 ath10k_core
sparse_keymap          16384  1 asus_wmi
cfg80211              614400  3 mac80211,ath,ath10k_core
wmi                    24576  1 asus_wmi
video                  40960  3 asus_wmi,int3406_thermal,i915

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:7912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:729134 (729.1 KB)  TX bytes:729134 (729.1 KB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7cd2:28f7:c6ca:8b29/64 Scope:Link
          inet6 addr: ::194:e640:dd94:90e0/64 Scope:Global
          inet6 addr: ::ce5c:5a20:146:b73/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:574356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:233897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:753866313 (753.8 MB)  TX bytes:27350785 (27.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"pdb_elcancelda_5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'pdb_elcancelda_5G' [AN3]>   
          Bit Rate=6 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:194  Invalid misc:4177   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       952     1  0 16:18 ?        00:00:10 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Sunrise Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.13.0-38-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     pdb_elcancelda_5G
GENERAL.CON-UUID:                       d4bbf62b-4f3c-4cfd-8907-bad269434e53
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,6,7}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   886a76b2-a633-4687-b6c0-42a499e2368a | MYA-L11
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   4f5b31eb-eb32-467a-b555-9270ebb32412 | pdb_elcancelda_2.4G
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   d4bbf62b-4f3c-4cfd-8907-bad269434e53 | pdb_elcancelda_5G
IP4.ADDRESS[1]:                         192.168.1.3/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             208.67.220.220
IP4.DNS[2]:                             208.67.222.222
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1523715512
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.3
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 208.67.220.220 208.67.222.222
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ::194:e640:dd94:90e0/64
IP6.ADDRESS[2]:                         ::ce5c:5a20:146:b73/64
IP6.ADDRESS[3]:                         fe80::7cd2:28f7:c6ca:8b29/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             ::777f:d050:0:0
IP6.DNS[2]:                             0:0:50d0:7f77::
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = ::777f:d050:0:0 0:0:50d0:7f77::
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:70:4f:57:3c:2:ba
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:68:d8:76:6c:56:fc:55:c1:41:72:5d:20:87:19:c5:f

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_B0_55_08_60_7B_1A
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{16}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   38bfda4b-2f0b-404f-addf-9217b03b783a | MatyRocks Network

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_EC_10_7B_E1_E8_32
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{15}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   340cb6ae-dfae-47b9-869d-fba6e18a5413 | Briga3 Network

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
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

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
elacandela_guest       <MAC 'elacandela_guest' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2      no        
pdb_elcancelda_2.4G    <MAC 'pdb_elcancelda_2.4G' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2      no        
pdb_elcancelda_5G      <MAC 'pdb_elcancelda_5G' [AN3]>  Infra  36    5180 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      yes     * 
MYA-L11                <MAC 'MYA-L11' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2      no        
Vodafone-SAIMIR-BOSSI  <MAC 'Vodafone-SAIMIR-BOSSI' [AN5]>  Infra  5     2432 MHz  54 Mbit/s  19      &#9602;___  WPA2      no        
Vodafone-WiFi          <MAC 'Vodafone-WiFi' [AN6]>  Infra  5     2432 MHz  54 Mbit/s  17      &#9602;___  --        no        

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
[[/etc/NetworkManager/system-connections/pdb_elcancelda_5G]] (600 root)
[connection] id=pdb_elcancelda_5G | type=wifi | permissions=user:briga:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=pdb_elcancelda_5G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pdb_elcancelda_2.4G]] (600 root)
[connection] id=pdb_elcancelda_2.4G | type=wifi | autoconnect=false | permissions=user:briga:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=pdb_elcancelda_2.4G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

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

enp2s0    no frequency information.

wlp3s0    32 channels in total; available frequencies :
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

wlp3s0    Interface doesn't support scanning : Resource temporarily unavailable

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     8D7A52EE462CD73D0445DB2
depends:        ath10k_core
intree:         Y
name:           ath10k_pci
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     7F06478F5745B064BF3BC89
depends:        mac80211,cfg80211,ath
intree:         Y
name:           ath10k_core
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-38-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     125925493BE4168AD62F1ED
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

mount /mnt/exthdd 
exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 9723.907359] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002d9 at 0x0003543c: -110
[ 9724.290992] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002db at 0x0003543c: -110
[ 9724.611934] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9724.930877] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002dd at 0x0003543c: -110
[ 9725.314961] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002df at 0x0003543c: -110
[ 9725.954936] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002e1 at 0x0003543c: -110
[ 9726.979668] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002e3 at 0x0003543c: -110
[ 9728.002978] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002e5 at 0x0003543c: -110
[ 9728.707573] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9728.739916] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002e7 at 0x0003543c: -110
[ 9729.027478] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002e9 at 0x0003543c: -110
[ 9729.762947] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002eb at 0x0003543c: -110
[ 9730.051218] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002ed at 0x0003543c: -110
[ 9730.194318] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002ef at 0x0003543c: -110
[ 9730.787261] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002f1 at 0x0003543c: -110
[ 9731.075477] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002f3 at 0x0003543c: -110
[ 9732.099158] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002f5 at 0x0003543c: -110
[ 9732.803639] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9732.836202] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002f7 at 0x0003543c: -110
[ 9733.123782] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002f9 at 0x0003543c: -110
[ 9733.740618] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002fb at 0x0003543c: -110
[ 9734.147092] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002fd at 0x0003543c: -110
[ 9734.754869] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000002ff at 0x0003543c: -110
[ 9735.171082] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000301 at 0x0003543c: -110
[ 9735.783419] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000303 at 0x0003543c: -110
[ 9736.195586] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000305 at 0x0003543c: -110
[ 9737.219649] ath10k_warn: 1 callbacks suppressed
[ 9737.219679] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000307 at 0x0003543c: -110
[ 9738.243656] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000309 at 0x0003543c: -110
[ 9739.267584] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000030b at 0x0003543c: -110
[ 9740.291509] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000030d at 0x0003543c: -110
[ 9740.995935] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9741.028222] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000030f at 0x0003543c: -110
[ 9741.315090] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000311 at 0x0003543c: -110
[ 9742.051264] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000313 at 0x0003543c: -110
[ 9742.339183] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000315 at 0x0003543c: -110
[ 9743.075716] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000317 at 0x0003543c: -110
[ 9743.363557] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000319 at 0x0003543c: -110
[ 9744.387792] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000031b at 0x0003543c: -110
[ 9745.091857] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9745.411912] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000031d at 0x0003543c: -110
[ 9746.028966] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000031f at 0x0003543c: -110
[ 9746.435081] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000321 at 0x0003543c: -110
[ 9747.043206] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000323 at 0x0003543c: -110
[ 9747.459638] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000325 at 0x0003543c: -110
[ 9748.067449] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000327 at 0x0003543c: -110
[ 9748.484018] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000329 at 0x0003543c: -110
[ 9749.188228] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9749.507643] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000032b at 0x0003543c: -110
[ 9750.531678] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000032d at 0x0003543c: -110
[ 9751.034762] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000032f at 0x0003543c: -110
[ 9751.556032] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000331 at 0x0003543c: -110
[ 9752.035880] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000333 at 0x0003543c: -110
[ 9752.579709] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000335 at 0x0003543c: -110
[ 9753.059837] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000337 at 0x0003543c: -110
[ 9753.284431] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9753.603873] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000339 at 0x0003543c: -110
[ 9754.627784] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000033b at 0x0003543c: -110
[ 9755.651360] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000033d at 0x0003543c: -110
[ 9756.035555] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000033f at 0x0003543c: -110
[ 9756.675404] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000341 at 0x0003543c: -110
[ 9757.059575] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000343 at 0x0003543c: -110
[ 9757.380475] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9757.703613] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000345 at 0x0003543c: -110
[ 9758.083490] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000347 at 0x0003543c: -110
[ 9758.723993] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000349 at 0x0003543c: -110
[ 9759.747844] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000034b at 0x0003543c: -110
[ 9760.772015] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000034d at 0x0003543c: -110
[ 9760.945207] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000034f at 0x0003543c: -110
[ 9761.476457] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9761.508827] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000351 at 0x0003543c: -110
[ 9761.540141] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000353 at 0x0003543c: -110
[ 9761.795779] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000355 at 0x0003543c: -110
[ 9762.819885] ath10k_warn: 1 callbacks suppressed
[ 9762.819906] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000359 at 0x0003543c: -110
[ 9763.556026] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000035b at 0x0003543c: -110
[ 9763.844199] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000035d at 0x0003543c: -110
[ 9764.868082] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000035f at 0x0003543c: -110
[ 9765.572648] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9765.891396] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000361 at 0x0003543c: -110
[ 9766.516849] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000363 at 0x0003543c: -110
[ 9766.916361] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000365 at 0x0003543c: -110
[ 9767.523974] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000367 at 0x0003543c: -110
[ 9767.940193] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000369 at 0x0003543c: -110
[ 9768.551473] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000036b at 0x0003543c: -110
[ 9768.963991] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000036d at 0x0003543c: -110
[ 9769.668292] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9769.988373] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000036f at 0x0003543c: -110
[ 9771.012030] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000371 at 0x0003543c: -110
[ 9771.522659] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000373 at 0x0003543c: -110
[ 9772.036236] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000375 at 0x0003543c: -110
[ 9772.548251] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000377 at 0x0003543c: -110
[ 9772.740778] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9773.060334] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000379 at 0x0003543c: -110
[ 9773.572303] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000037b at 0x0003543c: -110
[ 9774.084244] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000037d at 0x0003543c: -110
[ 9775.108018] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x0000037f at 0x0003543c: -110
[ 9775.812277] ath10k_pci 0000:03:00.0: failed to start hw scan: -11
[ 9775.844638] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000381 at 0x0003543c: -110

########## wireless info END ############

```

All APs, with a Cisco Aironet even more

---

### Post by Briga on 2018-04-15
> **praseodym said:**
> Lets check
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=IT/g" /etc/default/crda 
```
Reboot

Well, that's something new. I edited the file and rebooted, let's see if it works! Finger crossed :)

---

### Post by jeremy31 on 2018-04-15
Lets try a new firmware file that was uploaded a couple months ago
```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA9377/hw1.0/firmware-5.bin
```
Reboot and see if that fixes it

---

### Post by Briga on 2018-04-18
> **praseodym said:**
> Lets check
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=IT/g" /etc/default/crda 
```
Reboot

For a day it worked, but I am afraid it was a coincidence, because today it crashed twice... .this time it seems when there was a burst of transfer to the network... with the usual 
ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00001bcd at 0x0003543c: -110

Thanks for the idea anyway!

---

### Post by Briga on 2018-04-18
> **jeremy31 said:**
> Lets try a new firmware file that was uploaded a couple months ago
```
cd /lib/firmware/ath10k/QCA9377/hw1.0
sudo wget https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/plain/ath10k/QCA9377/hw1.0/firmware-5.bin
```
Reboot and see if that fixes it

I tried this one too, but it also crashed few seconds after the reboot, as per the other message it seems when there was a burst of transfer to the network... with the usual 
ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00001bcd at 0x0003543c: -110

Since it was downloaded as .1 I renamed the existing one as .saved and the new one without the .1

Thanks for the help anyway!

---

### Post by Briga on 2018-04-27
few more lines I found in dmesg if they can help

```
[    3.894931] ath10k_pci 0000:03:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1a3b:2231
[    3.894935] ath10k_pci 0000:03:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    3.895501] ath10k_pci 0000:03:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7
[    3.968382] ath10k_pci 0000:03:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[    4.055407] Adding 1951740k swap on /dev/sda8.  Priority:-1 extents:1 across:1951740k SSFS
[    4.083111] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    4.085149] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    4.458799] ath10k_pci 0000:03:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    4.466156] ath: EEPROM regdomain: 0x6a
[    4.466157] ath: EEPROM indicates we should expect a direct regpair map
[    4.466158] ath: Country alpha2 being used: 00
[    4.466159] ath: Regpair used: 0x6a
[    4.474643] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
```

---

### Post by Briga on 2018-04-27
New update to the story. I upgraded to 18.04 but unfortunately no better luck. 
I did a fresh install by formatting / and a brand new /home

Now I get loads of these errors in dmesg even while working:

```

[ 5286.846832] pcieport 0000:00:1c.5: AER: Corrected error received: id=00e5
[ 5286.846850] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e5(Transmitter ID)
[ 5286.846955] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00001000/00002000
[ 5286.846973] pcieport 0000:00:1c.5:    [12] Replay Timer Timeout 
```

1c.5 is
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)

And this is after a crash:

```

[  594.353526] pcieport 0000:00:1c.5: PCIe Bus Error: severity=Corrected, type=Data Link Layer, id=00e5(Transmitter ID)
[  594.353539] pcieport 0000:00:1c.5:   device [8086:9d15] error status/mask=00001000/00002000
[  594.353549] pcieport 0000:00:1c.5:    [12] Replay Timer Timeout  
[  594.375199] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x00000129 at 0x0003543c: -110
(tons of them)
[  636.170480] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001a9 at 0x0003543c: -110
[  636.683090] ath10k_pci 0000:03:00.0: failed to set 5g txpower 30: -11
[  636.683099] ath10k_pci 0000:03:00.0: failed to setup tx power 30: -11
[  636.683106] ath10k_pci 0000:03:00.0: failed to recalc tx power: -11
[  639.755786] wlp3s0: deauthenticating from 70:4f:57:3c:02:bc by local choice (Reason: 3=DEAUTH_LEAVING)
[  640.139147] ath10k_warn: 5 callbacks suppressed
[  640.139161] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001b7 at 0x0003543c: -110
[  640.266925] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001b9 at 0x0003543c: -110
[  641.162825] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001bb at 0x0003543c: -110
[  641.291365] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001bd at 0x0003543c: -110
[  642.315056] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001bf at 0x0003543c: -110
[  642.827983] ath10k_pci 0000:03:00.0: failed to set inactivity time for vdev 0: -11
[  642.827990] ath10k_pci 0000:03:00.0: failed to setup powersave: -11
[  643.366103] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001c1 at 0x0003543c: -110
[  644.365206] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001c3 at 0x0003543c: -110
[  644.399031] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001c5 at 0x0003543c: -110
[  645.387743] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001c7 at 0x0003543c: -110
[  645.419080] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001c9 at 0x0003543c: -110
[  645.899770] ath10k_pci 0000:03:00.0: failed to set PS Mode 0 for vdev 0: -11
[  645.899779] ath10k_pci 0000:03:00.0: failed to setup powersave: -11
[  645.899787] ath10k_pci 0000:03:00.0: failed to setup ps on vdev 0: -11
[  645.931419] ath10k_pci 0000:03:00.0: failed to wake target for write32 of 0x000001cb at 0x0003543c: -110
[  651.020133] ath10k_pci 0000:03:00.0: failed to flush transmit queue (skip 0 ar-state 1): 0
[  654.092463] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:4f:57:3c:02:bc: -11
[  654.092473] wlp3s0: failed to remove key (0, 70:4f:57:3c:02:bc) from hardware (-11)
[  657.164698] ath10k_pci 0000:03:00.0: failed to delete peer 70:4f:57:3c:02:bc for vdev 0: -11
[  657.164713] ath10k_pci 0000:03:00.0: found sta peer 70:4f:57:3c:02:bc (ptr 0000000000000000 id 125) entry on vdev 0 after it was supposedly removed
[  657.164850] WARNING: CPU: 2 PID: 692 at /build/linux-5s7Xkn/linux-4.15.0/net/mac80211/sta_info.c:1001 __sta_info_destroy_part2+0x169/0x170 [mac80211]
[  657.164854] Modules linked in: binfmt_misc rfcomm ccm arc4 cmac bnep snd_soc_skl snd_soc_skl_ipc snd_hda_ext_core snd_soc_sst_dsp snd_soc_sst_ipc snd_soc_acpi snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_codec_generic snd_hda_intel snd_hda_codec nls_iso8859_1 snd_hda_core snd_hwdep snd_pcm intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp snd_seq_midi kvm_intel snd_seq_midi_event kvm snd_rawmidi irqbypass crct10dif_pclmul crc32_pclmul ghash_clmulni_intel pcbc snd_seq ath10k_pci ath10k_core aesni_intel ath aes_x86_64 crypto_simd glue_helper cryptd snd_seq_device intel_cstate snd_timer intel_rapl_perf input_leds mac80211 uvcvideo asus_nb_wmi serio_raw asus_wmi videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 sparse_keymap joydev snd
[  657.164985]  btusb videobuf2_core cfg80211 btrtl soundcore btbcm videodev btintel media bluetooth processor_thermal_device ecdh_generic intel_soc_dts_iosf mei_me shpchp mei intel_pch_thermal int3403_thermal int340x_thermal_zone tpm_crb mac_hid acpi_pad int3400_thermal asus_wireless acpi_thermal_rel sch_fq_codel parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse drm r8169 ahci mii libahci wmi video
[  657.165099] CPU: 2 PID: 692 Comm: NetworkManager Not tainted 4.15.0-20-generic #21-Ubuntu
[  657.165103] Hardware name: ASUSTeK COMPUTER INC. P553UA/P553UA, BIOS P553UA.303 01/25/2017
[  657.165155] RIP: 0010:__sta_info_destroy_part2+0x169/0x170 [mac80211]
[  657.165160] RSP: 0018:ffff982c813f7978 EFLAGS: 00010286
[  657.165167] RAX: 00000000fffffff5 RBX: ffff88a7244de000 RCX: 0000000000000000
[  657.165171] RDX: ffff88a71fbdc680 RSI: 0000000000000000 RDI: 0000000000000000
[  657.165175] RBP: ffff982c813f7998 R08: ffff88a722b85e00 R09: 000000018010000f
[  657.165180] R10: ffff982c813f7880 R11: 0000000000000001 R12: ffff88a727780760
[  657.165183] R13: ffff88a7264ec8c0 R14: ffff88a7264ec8c0 R15: ffff88a727780cb0
[  657.165190] FS:  00007fd2f2b59fc0(0000) GS:ffff88a733d00000(0000) knlGS:0000000000000000
[  657.165195] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  657.165199] CR2: 00007fd825e6a000 CR3: 0000000267752002 CR4: 00000000003606e0
[  657.165203] Call Trace:
[  657.165257]  __sta_info_flush+0x12b/0x180 [mac80211]
[  657.165327]  ieee80211_set_disassoc+0xba/0x3d0 [mac80211]
[  657.165391]  ieee80211_mgd_deauth+0x287/0x440 [mac80211]
[  657.165450]  ieee80211_deauth+0x18/0x20 [mac80211]
[  657.165511]  cfg80211_mlme_deauth+0xaf/0x1c0 [cfg80211]
[  657.165561]  cfg80211_mlme_down+0x66/0x80 [cfg80211]
[  657.165611]  cfg80211_disconnect+0x12a/0x1e0 [cfg80211]
[  657.165649]  __cfg80211_leave+0x13c/0x170 [cfg80211]
[  657.165688]  cfg80211_leave+0x2b/0x40 [cfg80211]
[  657.165725]  cfg80211_netdev_notifier_call+0x340/0x610 [cfg80211]
[  657.165753]  ? ath10k_monitor_recalc+0x11c/0x570 [ath10k_core]
[  657.165766]  ? addrconf_notify+0x77/0xa40
[  657.165788]  ? ath10k_config_ps+0x52/0x70 [ath10k_core]
[  657.165796]  ? inetdev_event+0x76/0x4d0
[  657.165808]  ? skb_dequeue+0x59/0x70
[  657.165822]  notifier_call_chain+0x4c/0x70
[  657.165833]  raw_notifier_call_chain+0x16/0x20
[  657.165840]  call_netdevice_notifiers_info+0x2d/0x60
[  657.165848]  __dev_close_many+0x63/0x110
[  657.165855]  dev_close_many+0x8c/0x140
[  657.165863]  dev_close.part.90+0x4a/0x70
[  657.165870]  dev_close+0x19/0x20
[  657.165908]  cfg80211_shutdown_all_interfaces+0x77/0xc0 [cfg80211]
[  657.165946]  cfg80211_rfkill_set_block+0x26/0x30 [cfg80211]
[  657.165958]  rfkill_set_block+0x99/0x160
[  657.165969]  rfkill_fop_write+0xef/0x1d0
[  657.165981]  __vfs_write+0x1b/0x40
[  657.165990]  vfs_write+0xb1/0x1a0
[  657.166001]  SyS_write+0x55/0xc0
[  657.166010]  ? SyS_fcntl+0x5d/0xb0
[  657.166021]  do_syscall_64+0x73/0x130
[  657.166031]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
[  657.166037] RIP: 0033:0x7fd2f03342b7
[  657.166041] RSP: 002b:00007ffec04958b0 EFLAGS: 00000293 ORIG_RAX: 0000000000000001
[  657.166048] RAX: ffffffffffffffda RBX: 0000000000000014 RCX: 00007fd2f03342b7
[  657.166052] RDX: 0000000000000008 RSI: 00007ffec04958e8 RDI: 0000000000000014
[  657.166056] RBP: 00007ffec04958e8 R08: 0000000000000000 R09: 000000000000000c
[  657.166060] R10: 0000000000000000 R11: 0000000000000293 R12: 0000000000000008
[  657.166064] R13: 0000556fe9045060 R14: 0000556fe7048421 R15: 0000000000000000
[  657.166069] Code: 80 bb 0c 01 00 00 00 0f 84 33 ff ff ff 45 31 c0 b9 01 00 00 00 48 89 da 4c 89 ee 4c 89 e7 e8 5f aa ff ff 85 c0 0f 84 15 ff ff ff <0f> 0b e9 0e ff ff ff 0f 1f 44 00 00 55 48 89 e5 53 48 89 fb 48 
[  657.166207] ---[ end trace 5f33c448344e41d8 ]---
[  660.237346] ath10k_pci 0000:03:00.0: failed to recalculate rts/cts prot for vdev 0: -11

```

Of course any help would be much appreciated. In the meantime I am off to buy an external adapter :(

---

### Post by praseodym on 2018-04-28
Lets try a firmware update

```
git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
cd linux-firmware
sudo cp -r * /lib/firmware
```
Reboot

---

### Post by zerobytez on 2018-04-28
I believe this is actually something wrong with the card itself, as I've seen a fair bit of computers with that card do the exact same thing, no matter the OS or firmware.

---

### Post by zerobytez on 2018-04-30
Don't know if you're still watching this, but it seems the best fix to find a way to reboot the card/its drivers, and then script it so that when the internet stops you can run the script and hopefully reconnect.

---

### Post by Briga on 2018-05-18
You could be right. I don't have Windows installed (or any other OS) so I cannot test it, and I am not going to install it to do it. But it could be an hardware fault....

---

### Post by Briga on 2018-05-18
> **zerobytez said:**
> Don't know if you're still watching this, but it seems the best fix to find a way to reboot the card/its drivers, and then script it so that when the internet stops you can run the script and hopefully reconnect.

What I did is move the router close and wired it !

Indeed when I travel is an issue and I normally use my phone as an external modem. Don't know how to reboot a card (aside from rebooting the PC) but I will look it up because it could be a workaround. 

Thanks a lot.

---

### Post by eduardo-gaudino on 2018-10-10
I got the same exactly problem! 
This happens on my work computer which is installed Ubuntu 18.04, i did a lot of things to fix, but unfortunately with no good results.
Tried to reinstall Wifi firmware, install a fresh Ubuntu , update firmwares. 

It is totally random, i had work for entire day without a problem, but somedays i got like 3, 4 times this kind of error. 
The solution i took is to plug a connection cable and work on. 
If someone find some solution will be great :)

---

### Post by wildmanne39 on 2018-10-10
Hello and welcome to the forum eduardo-gaudino, please start your own thread to get the help you deserve instead of posting in someone else's old thread and click on the wireless script in my signature and post the results in your new thread and someone will most likely be able to help you.

---

