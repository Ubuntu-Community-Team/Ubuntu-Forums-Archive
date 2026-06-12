---
title: "WIFI Doesnt work"
date: 2018-07-30
forum: Networking &amp; Wireless
---

### Post by clicky on 2018-07-30
Greetings , i used the wifi script from sticky post . And here are the results [http://paste.ubuntu.com/p/SYVtNJJZN7/](http://paste.ubuntu.com/p/SYVtNJJZN7/)

[HTML]
########## wireless info START ##########

Report from: 30 Jul 2018 11:51 EEST +0300

Booted last: 30 Jul 2018 00:00 EEST +0300

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic

##### kernel ############################

Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, acpi=off, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 06)
	Subsystem: ASUSTeK Computer Inc. RTL810xE PCI Express Fast Ethernet controller [1043:200f]
	Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Lite-On Communications Inc RTL8723BE PCIe Wireless Network Adapter [11ad:1723]
	Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b721 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 13d3:5a01 IMC Networks 
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be              98304  0
btcoexist             131072  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                32768  1 rtl8723be
rtlwifi                77824  4 rtl_pci,btcoexist,rtl8723_common,rtl8723be
mac80211              778240  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              622592  2 mac80211,rtlwifi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0f2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0f2' [IF1]> brd <MAC address>
    inet 192.168.10.5/24 brd 192.168.10.255 scope global dynamic noprefixroute enp2s0f2
       valid_lft 86268sec preferred_lft 86268sec
    inet6 fe80::106f:b9e4:11b:656f/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF2]> brd <MAC address>
    inet6 fe80::889d:c0d:5000:653d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0f2  no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"Centro Home Limassol"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Centro Home Limassol' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

default via 192.168.10.254 dev enp2s0f2 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0f2 scope link metric 1000 
192.168.10.0/24 dev enp2s0f2 proto kernel scope link src 192.168.10.5 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root      3131     1  0 11:44 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0f2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8402-1_0.0.1 10/26/11
GENERAL.HWADDR:                         <MAC 'enp2s0f2' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.2/net/enp2s0f2
GENERAL.IP-IFACE:                       enp2s0f2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       edafcacc-c6f0-3b68-8fcb-5cf2e0faaec5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.10.5/24
IP4.GATEWAY:                            192.168.10.254
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.10.254, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.10.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.10.254
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1533026961
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.10.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       ip_address = 192.168.10.5
DHCP4.OPTION[15]:                       requested_netbios_scope = 1
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       vendor_unknown_17 = 5422F8,ZXDSL 931VII,ZTEE40NDAH00769
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.10.254
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       routers = 192.168.10.254
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       dhcp_message_type = 5
DHCP4.OPTION[26]:                       network_number = 192.168.10.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.10.254
IP6.ADDRESS[1]:                         fe80::106f:b9e4:11b:656f/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = ::/0, nh = fe80::1, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   edafcacc-c6f0-3b68-8fcb-5cf2e0faaec5 | Wired connection 1

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.15.0-29-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
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
GENERAL.CONNECTION:                     Centro Home Limassol
GENERAL.CON-UUID:                       d8d46bc5-1e24-405f-ba8b-a65b1f54739c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP6.ADDRESS[1]:                         fe80::889d:c0d:5000:653d/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = ::/0, nh = fe80::1, mt = 20600
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.DNS[1]:                             fe80::1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d8d46bc5-1e24-405f-ba8b-a65b1f54739c | Centro Home Limassol

SSID                  BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
Centro Home Limassol  <MAC 'Centro Home Limassol' [AC1]>  Infra  6     2437 MHz  117 Mbit/s  94      â–‚â–„â–†â–ˆ  WPA1 WPA2  yes     *      

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Centro Home Limassol]] (600 root)
[connection] id=Centro Home Limassol | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=Centro Home Limassol
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ARRIS-9872]] (600 root)
[connection] id=ARRIS-9872 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=ARRIS-9872
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Asia/Nicosia (based on set time zone)

global
country CY: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
	(5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0f2  no frequency information.

wlp3s0    13 channels in total; available frequencies :
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
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0f2  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'Centro Home Limassol' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"Centro Home Limassol"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008d9175d7e4
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'CYTA16E1D3' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"CYTA16E1D3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004db8211cb86
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MAIN-PC_Network' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"MAIN-PC_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000002cef92e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ARRIS-25C2' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ARRIS-25C2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010e764cb139
                    Extra: Last beacon: 236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'naxtme' [AC5]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"naxtme"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003fe01da3a
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'magazzino' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"magazzino"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000498b311e96
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '9662f4' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"9662f4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014b05e5635
                    Extra: Last beacon: 696ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw_36.bin
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     6A56582B1FEECB841E329C4
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
retpoline:      Y
intree:         Y
name:           rtl8723be
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     90DB9C652E26F4135F339B8
depends:        rtlwifi
retpoline:      Y
intree:         Y
name:           rtl8723_common
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtl_pci]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9F5FA8A771710F4CA500C6E
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_pci
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[rtlwifi]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8AB8B2AAF3BCFFB93D91956
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-29-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 0
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.627549] rtl8723be 0000:03:00.0 wlp3s0: renamed from wlan0
[    4.199585] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
[    4.286154] r8169 0000:02:00.2 enp2s0f2: link down (repeated 2 times)
[    4.286277] IPv6: ADDRCONF(NETDEV_UP): enp2s0f2: link is not ready
[    4.289313] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[    5.911134] r8169 0000:02:00.2 enp2s0f2: link up
[    5.911140] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0f2: link becomes ready
[    6.623557] wlp3s0: authenticate with <MAC 'Centro Home Limassol' [AC1]>
[    6.633829] wlp3s0: send auth to <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[    6.635703] wlp3s0: authenticated
[    6.636138] wlp3s0: associate with <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[    6.639663] wlp3s0: RX AssocResp from <MAC 'Centro Home Limassol' [AC1]> (capab=0x431 status=0 aid=4)
[    6.639893] wlp3s0: associated
[    6.668056] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  180.160664] wlp3s0: deauthenticating from <MAC 'Centro Home Limassol' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  180.533718] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[  181.233245] rtl8723be: error H2C cmd because of Fw download fail!!!
[  181.233264] WARNING: CPU: 0 PID: 91 at /build/linux-60XibS/linux-4.15.0/drivers/net/wireless/realtek/rtlwifi/rtl8723be/fw.c:227 rtl8723be_fill_h2c_cmd+0x109/0x440 [rtl8723be]
[  181.233310] Workqueue: rtl8723be_pci rtl_c2hcmd_wq_callback [rtlwifi]
[  181.233312] RIP: 0010:rtl8723be_fill_h2c_cmd+0x109/0x440 [rtl8723be]
[  181.233334]  rtl_btc_btinfo_notify+0x18/0x20 [btcoexist]
[  181.233335]  rtl8723be_c2h_content_parsing+0xb5/0xc0 [rtl8723be]
[  181.233337]  rtl_c2hcmd_launcher+0x9a/0xf0 [rtlwifi]
[  181.233339]  rtl_c2hcmd_wq_callback+0x1a/0x20 [rtlwifi]
[  182.689093] wlp3s0: authenticate with <MAC 'Centro Home Limassol' [AC1]>
[  182.699285] wlp3s0: send auth to <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[  182.700909] wlp3s0: authenticated
[  182.701219] wlp3s0: associate with <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[  182.705079] wlp3s0: RX AssocResp from <MAC 'Centro Home Limassol' [AC1]> (capab=0x431 status=0 aid=4)
[  182.705332] wlp3s0: associated
[  182.719403] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  589.858233] wlp3s0: deauthenticating from <MAC 'Centro Home Limassol' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  590.181491] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 3 times)
[  592.343136] wlp3s0: authenticate with <MAC 'Centro Home Limassol' [AC1]>
[  592.355069] wlp3s0: send auth to <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[  592.356584] wlp3s0: authenticated
[  592.360026] wlp3s0: associate with <MAC 'Centro Home Limassol' [AC1]> (try 1/3)
[  592.363605] wlp3s0: RX AssocResp from <MAC 'Centro Home Limassol' [AC1]> (capab=0x431 status=0 aid=4)
[  592.363891] wlp3s0: associated
[  592.386171] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  842.669680] r8169 0000:02:00.2 enp2s0f2: link down
[  887.854651] r8169 0000:02:00.2 enp2s0f2: link up

########## wireless info END ############


[/HTML]

---

