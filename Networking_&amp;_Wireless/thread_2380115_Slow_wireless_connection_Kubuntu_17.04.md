---
title: "Slow wireless connection Kubuntu 17.04"
date: 2017-12-13
forum: Networking &amp; Wireless
---

### Post by nerethos on 2017-12-13
Hi all.

I dual boot W10 and Kubuntu, my wireless connection speed in Kubuntu is about 1/3 of the speed I get in Windows. I tested this using [testmy.net]("http://testmy.net") with 10 consecutive tests on each OS. The result is always the same with Kubuntu at around 54Mbps and Windows at around 150Mbps. Here is the the text dump after running the wireless script.


```
########## wireless info START ##########

Report from: 13 Dec 2017 13:07 GMT +0000

Booted last: 13 Dec 2017 00:00 GMT +0000

Script from: 05 Dec 2017 03:13 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-42-generic #46-Ubuntu SMP Mon Dec 4 14:38:01 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

/usr/share/xsessions/plasma

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller [1969:e091] (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller [1462:10d2]
    Kernel driver in use: alx

03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1770:ff00  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

msi_wmi                16384  0
mxm_wmi                16384  0
sparse_keymap          16384  1 msi_wmi
iwldvm                233472  0
mac80211              782336  1 iwldvm
iwlwifi               229376  1 iwldvm
cfg80211              602112  3 iwlwifi,mac80211,iwldvm
wmi                    16384  2 msi_wmi,mxm_wmi
video                  40960  2 msi_wmi,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1230  bytes 613402 (613.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1226  bytes 272795 (272.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 423  bytes 29611 (29.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 423  bytes 29611 (29.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.6  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::5809:d2d9:6db:17c0  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 88714  bytes 129447110 (129.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 49529  bytes 12683371 (12.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"VM615853-5G"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'VM615853-5G' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:325   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1022     1  0 13:02 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        WiFi Link 5100 (AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.10.0-42-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     VM615853-5G
GENERAL.CON-UUID:                       ebfc254e-f04e-4575-a48c-abb8838e7aa1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ebfc254e-f04e-4575-a48c-abb8838e7aa1 | VM615853-5G
IP4.ADDRESS[1]:                         192.168.0.6/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = james-X6823
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1513256558
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::5809:d2d9:6db:17c0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Killer E220x Gigabit Ethernet Controller
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
VM615853-2G         <MAC 'VM615853-2G' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
VM615853-5G         <MAC 'VM615853-5G' [AC1]>  Infra  36    5180 MHz  54 Mbit/s  76      &#9602;&#9604;&#9606;_  WPA2         yes     * 
--                  <MAC '--' [AN3]>  Infra  36    5180 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2         no        
virginmedia6758251  <MAC 'virginmedia6758251' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Virgin Media        <MAC 'Virgin Media' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2 802.1X  no        
VM7801096           <MAC 'VM7801096' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2    no        
Virgin Media        <MAC 'Virgin Media' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X  no        
VM322865-2G         <MAC 'VM322865-2G' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
Sentinel            <MAC 'Sentinel' [AC7]>  Infra  13    2472 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
VM5272264           <MAC 'VM5272264' [AN10]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2    no        
VM6822622           <MAC 'VM6822622' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2    no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/VM615853-5G-ebfc254e-f04e-4575-a48c-abb8838e7aa1]] (600 root)
[connection] id=VM615853-5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM615853-5G
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/SKYE8B4D]] (600 root)
[connection] id=SKYE8B4D | type=wifi | permissions=user:james:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=SKYE8B4D
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM615853-5G]] (600 root)
[connection] id=VM615853-5G | type=wifi | permissions=user:kubuntu:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM615853-5G
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VM615853-5G-8c3c70d0-7df4-47f3-945a-867f1b4c1dca]] (600 root)
[connection] id=VM615853-5G | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VM615853-5G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country GB: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

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

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.18 GHz (Channel 36)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'VM615853-5G' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"VM615853-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000851e75f8e1
                    Extra: Last beacon: 176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'VM615853-2G' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"VM615853-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001774c012
                    Extra: Last beacon: 5156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'virginmedia6758251' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"virginmedia6758251"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007c37e26322
                    Extra: Last beacon: 4740ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'VM322865-2G' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VM322865-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000002c286ee9
                    Extra: Last beacon: 4524ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'VM7801096' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"VM7801096"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e1e07ba155
                    Extra: Last beacon: 4104ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Virgin Media' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Virgin Media"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002e1e07bb072
                    Extra: Last beacon: 4308ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'Sentinel' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Sentinel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000030734e965cd
                    Extra: Last beacon: 3948ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VM6822622' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"VM6822622"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d9462b5019
                    Extra: Last beacon: 4764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Virgin Media' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Virgin Media"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d9462b5f23
                    Extra: Last beacon: 4764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.10.0-42-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     62AB06F76928D08BDC96CD5
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.10.0-42-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-26.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-26.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-26.ucode
firmware:       iwlwifi-8000C-26.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--26.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--26.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--26.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--26.ucode
srcversion:     F8F4E503BE16838CB3C1ADC
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.10.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-42-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    4.444977] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    5.534211] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.536045] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    5.539268] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.649674] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    5.652840] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.685192] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[    5.692049] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    5.695212] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.805976] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    5.809129] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    5.843001] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[    9.061836] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    9.065014] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    9.174254] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    9.177410] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    9.209763] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[    9.221882] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    9.225059] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    9.333994] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    9.337153] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    9.369834] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   22.291820] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[   22.294985] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   22.403577] iwlwifi 0000:03:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[   22.406749] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   22.438246] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   25.631521] wlp3s0: authenticate with <MAC 'VM615853-5G' [AC1]>
[   25.634360] wlp3s0: send auth to <MAC 'VM615853-5G' [AC1]> (try 1/3)
[   25.649803] wlp3s0: authenticated
[   25.650138] wlp3s0: associate with <MAC 'VM615853-5G' [AC1]> (try 1/3)
[   25.654014] wlp3s0: RX AssocResp from <MAC 'VM615853-5G' [AC1]> (capab=0x411 status=0 aid=3)
[   25.656463] wlp3s0: associated
[   25.656506] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[   25.750212] wlp3s0: Limiting TX power to 19 (22 - 3) dBm as advertised by <MAC 'VM615853-5G' [AC1]>

########## wireless info END ############
```

---

### Post by praseodym on 2017-12-13
Lets check
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi-11n.conf
```
Reboot

---

### Post by nerethos on 2017-12-14
That seems to have made things worse, best speed is now 20Mbps

---

### Post by praseodym on 2017-12-15
Ok, revert it
```

sudo rm /etc/modprobe.d/iwlwifi-11n.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
There is a bug in the network manager starting with 17.04. Lets try

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by nerethos on 2017-12-15
Reverted the first step no problem, next step hasn't made any improvements.

---

### Post by nerethos on 2017-12-18
Is there anything else I can try?

---

