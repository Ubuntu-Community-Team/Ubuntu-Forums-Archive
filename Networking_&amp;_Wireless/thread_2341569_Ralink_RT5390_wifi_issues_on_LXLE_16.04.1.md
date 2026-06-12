---
title: "Ralink RT5390 wifi issues on LXLE 16.04.1"
date: 2016-10-29
forum: Networking &amp; Wireless
---

### Post by pemartins on 2016-10-29
Hi, 

I'm having issues connecting to the wifi networks on LXLE 16.04.1, my card is:

Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
    Kernel driver in use: rt2800pci

So basically I can see all the networks available but I have trouble connecting. I have two routers which I can see on the network list but most of the time I can only connect to one, the other usually I'm not able to connect to; and when I do connect the speed is low on either of them.
The network that I'm able to connect to is ZON-7FB0, the other one is ZON-7FB0_2.

My laptop is an Asus X55U-SX038H.

Here is the report generated with the superb script you provide:

```

########## wireless info START ##########

Report from: 29 Oct 2016 12:30 WEST +0100

Booted last: 29 Oct 2016 00:00 WEST +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    LXLE Eclectica 16.04.1 64bit
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, acpi_osi=Linux, quiet, splash, acpi_backlight=vendor, vt.handoff=7

##### desktop ###########################

LXDE

##### lspci #############################

01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
    Kernel driver in use: rt2800pci

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. AR8161 Gigabit Ethernet [1043:14e7]
    Kernel driver in use: alx

##### lsusb #############################

Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 15d9:0a4f Trust International B.V. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ca4e:c6a3:6f8f:3f5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24060 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27492978 (27.4 MB)  TX bytes:15641221 (15.6 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11bgn  ESSID:"ZON-7FB0"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'ZON-7FB0' [AC1]>   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       927     1  0 12:21 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ZON-7FB0 1
GENERAL.CON-UUID:                       378d37f1-a9aa-48f4-b970-8993490ec31c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   378d37f1-a9aa-48f4-b970-8993490ec31c | ZON-7FB0 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   3171f8c0-ad81-4a83-9b0f-90773214f7d6 | ZON-7FB0_2
IP4.ADDRESS[1]:                         192.168.1.5/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        time_offset = 0
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = pemartins-X55U
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.1.1
DHCP4.OPTION[12]:                       expiry = 1477743684
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.1.5
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 3600
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.1.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::ca4e:c6a3:6f8f:3f5b/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8161 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0
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

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ZON-7FB0_2             <MAC 'ZON-7FB0_2' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  62      â–‚â–„â–†_  WPA1 WPA2  no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AC5]>  Infra  10    2457 MHz  54 Mbit/s  55      â–‚â–„__  --         no        
ZON-7FB0               <MAC 'ZON-7FB0' [AC1]>  Infra  10    2457 MHz  54 Mbit/s  55      â–‚â–„__  WPA1 WPA2  yes     * 
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  52      â–‚â–„__  --         no        
ZON-00B0               <MAC 'ZON-00B0' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  52      â–‚â–„__  WPA1 WPA2  no        
ZON-1DF0               <MAC 'ZON-1DF0' [AN6]>  Infra  2     2417 MHz  54 Mbit/s  29      â–‚___  WPA1 WPA2  no        
ZON-BAA0               <MAC 'ZON-BAA0' [AC6]>  Infra  13    2472 MHz  54 Mbit/s  25      â–‚___  WPA1 WPA2  no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AN8]>  Infra  2     2417 MHz  54 Mbit/s  22      â–‚___  --         no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AC7]>  Infra  13    2472 MHz  54 Mbit/s  22      â–‚___  --         no        
ZON-3A14               <MAC 'ZON-3A14' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  19      â–‚___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/ZON-7FB0]] (600 root)
[connection] id=ZON-7FB0 | type=wifi | permissions=user:qwerty:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7FB0_2]] (600 root)
[connection] id=ZON-7FB0_2 | type=wifi | permissions=user:pemartins:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0_2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7FB0 1]] (600 root)
[connection] id=ZON-7FB0 1 | type=wifi | permissions=user:pemartins:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    14 channels in total; available frequencies :
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
          Current Frequency:2.457 GHz (Channel 10)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.472 GHz (Channel 13)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'ZON-7FB0' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"ZON-7FB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000125f9a70326
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000063eb1f7633
                    Extra: Last beacon: 24ms ago
          Cell 03 - Address: <MAC 'ZON-3A14' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"ZON-3A14"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002e58c63a007
                    Extra: Last beacon: 2136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ZON-7FB0_2' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ZON-7FB0_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002e58c755848
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC5]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000125f9a72e45
                    Extra: Last beacon: 24ms ago
          Cell 06 - Address: <MAC 'ZON-BAA0' [AC6]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ZON-BAA0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038d2a3acae
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038d2a3b3a7
                    Extra: Last beacon: 24ms ago

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

##### udev rules ########################

##### dmesg #############################

[   17.713313] rt2800pci 0000:01:00.0: enabling device (0000 -> 0002)
[   17.713839] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   17.718954] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   19.326625] rt2800pci 0000:01:00.0 wlp1s0: renamed from wlan0
[   37.185555] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[   37.234185] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   37.234301] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   37.456386] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   37.593828] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[   50.555455] wlp1s0: authenticate with <MAC 'ZON-7FB0' [AC1]>
[   50.571111] wlp1s0: send auth to <MAC 'ZON-7FB0' [AC1]> (try 1/3)
[   50.574749] wlp1s0: authenticated
[   50.576793] wlp1s0: associate with <MAC 'ZON-7FB0' [AC1]> (try 1/3)
[   50.594488] wlp1s0: RX AssocResp from <MAC 'ZON-7FB0' [AC1]> (capab=0x431 status=0 aid=2)
[   50.594630] wlp1s0: associated
[   50.594720] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   66.828116] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 6 times)
[  109.854018] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush
[  110.013997] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 1 failed to flush
[  110.174043] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 22 times)
[  587.600969] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 1 failed to flush (repeated 2 times)

########## wireless info END ############


```

Please let me know if there's something I can do to improve this. My knowledge skills are very basic.

Thank you very much in advance.

---

### Post by jeremy31 on 2016-10-29
If you can change wifi router settings, move them to channel 9 and change encryption to WPA2-AES with no WEP or TKIP.  I see the fail to flush error at the end of your results, so
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
This will disable wifi power management that usually causes this issue and we will set your country code with
```

sudo iw reg set PT
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda

```

Reboot

---

### Post by pemartins on 2016-10-29
Thank you very much for your help! And thank you for such a quick reply.

So you must be the Harry Potter of networks, you really made a huge change for the better! I did all the changes you mentioned and I can now say that I can connect to either of my routers in a couple of seconds and the speeds really went up! But very significantly! 

Here is the new report:

```

########## wireless info START ##########

Report from: 29 Oct 2016 14:46 WEST +0100

Booted last: 29 Oct 2016 00:00 WEST +0100

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    LXLE Eclectica 16.04.1 64bit
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, acpi_osi=Linux, quiet, splash, acpi_backlight=vendor, vt.handoff=7

##### desktop ###########################

LXDE

##### lspci #############################

01:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Foxconn International, Inc. RT5390 Wireless 802.11n 1T/1R PCIe [105b:e054]
    Kernel driver in use: rt2800pci

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. AR8161 Gigabit Ethernet [1043:14e7]
    Kernel driver in use: alx

##### lsusb #############################

Bus 001 Device 003: ID 1bcf:2883 Sunplus Innovation Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 15d9:0a4f Trust International B.V. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 asus_wmi
video                  40960  1 asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::685c:8e84:910e:c604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89032715 (89.0 MB)  TX bytes:30045961 (30.0 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11bgn  ESSID:"ZON-7FB0_2"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'ZON-7FB0_2' [AC1]>   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    600    0        0 wlp1s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       962     1  0 14:35 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     ZON-7FB0_2
GENERAL.CON-UUID:                       3171f8c0-ad81-4a83-9b0f-90773214f7d6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     57 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3171f8c0-ad81-4a83-9b0f-90773214f7d6 | ZON-7FB0_2
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   378d37f1-a9aa-48f4-b970-8993490ec31c | ZON-7FB0 1
IP4.ADDRESS[1]:                         192.168.2.105/24
IP4.GATEWAY:                            192.168.2.1
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.2.1
DHCP4.OPTION[10]:                       expiry = 1477748593
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.2.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.105
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = smc
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 4294967295
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::685c:8e84:910e:c604/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8161 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0
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

SSID                   BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
ZON-7FB0               <MAC 'ZON-7FB0' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  75      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;_  WPA2       no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AC5]>  Infra  9     2452 MHz  54 Mbit/s  72      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;_  --         no        
ZON-7FB0_2             <MAC 'ZON-7FB0_2' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  61      â&#8211;&#8218;â&#8211;&#8222;â&#8211;&#8224;_  WPA2       yes     * 
ZON-00B0               <MAC 'ZON-00B0' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  55      â&#8211;&#8218;â&#8211;&#8222;__  WPA1 WPA2  no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  55      â&#8211;&#8218;â&#8211;&#8222;__  --         no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AN6]>  Infra  13    2472 MHz  54 Mbit/s  42      â&#8211;&#8218;â&#8211;&#8222;__  --         no        
ZON-BAA0               <MAC 'ZON-BAA0' [AN7]>  Infra  13    2472 MHz  54 Mbit/s  42      â&#8211;&#8218;â&#8211;&#8222;__  WPA1 WPA2  no        
FON_ZON_FREE_INTERNET  <MAC 'FON_ZON_FREE_INTERNET' [AN8]>  Infra  2     2417 MHz  54 Mbit/s  29      â&#8211;&#8218;___  --         no        
ZON-1DF0               <MAC 'ZON-1DF0' [AN9]>  Infra  2     2417 MHz  54 Mbit/s  29      â&#8211;&#8218;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/ZON-7FB0]] (600 root)
[connection] id=ZON-7FB0 | type=wifi | permissions=user:qwerty:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7FB0_2]] (600 root)
[connection] id=ZON-7FB0_2 | type=wifi | permissions=user:pemartins:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0_2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZON-7FB0 1]] (600 root)
[connection] id=ZON-7FB0 1 | type=wifi | permissions=user:pemartins:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=ZON-7FB0
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    11 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'ZON-7FB0_2' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ZON-7FB0_2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076d949cf
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ZON-00B0' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ZON-00B0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000065d434f162
                    Extra: Last beacon: 1828ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000065d434faa4
                    Extra: Last beacon: 1828ms ago
          Cell 04 - Address: <MAC 'ZON-7FB0' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"ZON-7FB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c1f04437
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c1f06203
                    Extra: Last beacon: 20ms ago
          Cell 06 - Address: <MAC 'FON_ZON_FREE_INTERNET' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"FON_ZON_FREE_INTERNET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a7667959ec
                    Extra: Last beacon: 80ms ago

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2800lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00mmio]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[rt2x00lib]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
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

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

##### udev rules ########################

##### dmesg #############################

[   37.758056] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   37.758171] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   37.854482] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   37.988713] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   38.002368] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[   38.746871] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  346.296849] wlp1s0: authenticate with <MAC 'ZON-7FB0_2' [AC1]>
[  346.310165] wlp1s0: send auth to <MAC 'ZON-7FB0_2' [AC1]> (try 1/3)
[  346.311893] wlp1s0: authenticated
[  346.314369] wlp1s0: associate with <MAC 'ZON-7FB0_2' [AC1]> (try 1/3)
[  346.318210] wlp1s0: RX AssocResp from <MAC 'ZON-7FB0_2' [AC1]> (capab=0x411 status=0 aid=1)
[  346.318349] wlp1s0: associated
[  346.318442] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  347.041068] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=148 PROTO=2 
[  360.144967] wlp1s0: deauthenticating from <MAC 'ZON-7FB0_2' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  361.047661] wlp1s0: authenticate with <MAC 'ZON-7FB0' [AC4]>
[  361.065204] wlp1s0: send auth to <MAC 'ZON-7FB0' [AC4]> (try 1/3)
[  361.069515] wlp1s0: authenticated
[  361.072850] wlp1s0: associate with <MAC 'ZON-7FB0' [AC4]> (try 1/3)
[  361.090940] wlp1s0: RX AssocResp from <MAC 'ZON-7FB0' [AC4]> (capab=0x431 status=0 aid=3)
[  361.091091] wlp1s0: associated
[  498.389016] wlp1s0: deauthenticating from <MAC 'ZON-7FB0' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  499.309757] wlp1s0: authenticate with <MAC 'ZON-7FB0_2' [AC1]>
[  499.328148] wlp1s0: send auth to <MAC 'ZON-7FB0_2' [AC1]> (try 1/3)
[  499.329804] wlp1s0: authenticated
[  499.332136] wlp1s0: associate with <MAC 'ZON-7FB0_2' [AC1]> (try 1/3)
[  499.335805] wlp1s0: RX AssocResp from <MAC 'ZON-7FB0_2' [AC1]> (capab=0x411 status=0 aid=1)
[  499.335998] wlp1s0: associated
[  547.226582] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=159 PROTO=2 
[  547.227420] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=160 PROTO=2 
[  547.228405] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=161 PROTO=2 
[  547.229399] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=162 PROTO=2 
[  547.230443] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=163 PROTO=2 
[  596.737545] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=165 PROTO=2 
[  672.078446] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=166 PROTO=2 
[  672.079215] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=167 PROTO=2 
[  672.080328] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=168 PROTO=2 
[  672.080961] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=169 PROTO=2 
[  672.081922] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=170 PROTO=2 
[  721.587253] [UFW BLOCK] IN=wlp1s0 OUT= MAC=01:00:5e:00:00:01:<MAC 'ZON-7FB0_2' [AC1]>:08:00 SRC=192.168.2.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=172 PROTO=2 

########## wireless info END ############


```

If you see something else that should be done please let me know, but I can now say that I am very pleased with the wifi connections.

Once again I thank you very much for your help, for your time, for your knowledge but above all I thank you very much for your kindness of helping me!


ps- the issue is solved, I tried to edit the main post to put a solved tag on in but I wasn't able to.

---

### Post by jeremy31 on 2016-10-29
Use thread tools near the top right of the page to Mark as Solved
Your welcome, enjoy

---

### Post by pemartins on 2016-10-29
Done!

Thank you very much for everything!

---

