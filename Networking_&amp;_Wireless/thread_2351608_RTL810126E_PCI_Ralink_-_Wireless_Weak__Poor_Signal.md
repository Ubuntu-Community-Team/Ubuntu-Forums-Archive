---
title: "RTL8101/2/6E PCI Ralink - Wireless Weak / Poor Signal"
date: 2017-02-05
forum: Networking &amp; Wireless
---

### Post by usrandrd3 on 2017-02-05
I have installed Ubuntu 16 and i have poor wireless signal (1-2 lines out of 5). I am new to Linux.
Other devices in house work ok: tablet, phone, another laptop with windows. probably is the driver for network card, but i dont know what to do next.
I have followed the instructions from here to generate a report  [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

```



########## wireless info START ##########


Report from: 05 Feb 2017 12:14 EET +0200


Booted last: 05 Feb 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
    DeviceName: Ralink WLAN Ralink Ripple3 RT5390F_802.11 b/g/n 1x1 PCIe HMC
    Subsystem: Hewlett-Packard Company Device [103c:1839]


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:183e]


##### lsusb #############################


Bus 002 Device 003: ID 05c8:0223 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 03f0:002a Hewlett-Packard LaserJet P1102
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:078c Microsoft Corp. 
Bus 003 Device 002: ID 0e8f:00a7 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              57344  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              757760  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              581632  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 511605  bytes 307956752 (307.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 511605  bytes 307956752 (307.9 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.7  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e9a4:eb5a:8326:5de8  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 360870  bytes 229509304 (229.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 272586  bytes 35419353 (35.4 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


eno1      no wireless extensions.


lo        no wireless extensions.


wlo1      IEEE 802.11  ESSID:"Clicknet-ECCF"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Clicknet-ECCF' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2106  Invalid misc:2581   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1124     1  0 08:30 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        7 Series/C210 Series Chipset Family PCI Express Root Port 1
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Clicknet-ECCF
GENERAL.CON-UUID:                       923a33a4-e555-4612-8091-91ec294fc517
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     52 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   75a07422-8f64-4edd-a4f2-ca358f1be77f | RomTelecom-WEP-D09B
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   923a33a4-e555-4612-8091-91ec294fc517 | Clicknet-ECCF
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486362643
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.7
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e9a4:eb5a:8326:5de8/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/net/eno1
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


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DIRECT-C7-BRAVIA     <MAC 'DIRECT-C7-BRAVIA' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
Clicknet-4547        <MAC 'Clicknet-4547' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
RomTelecom-WPA-D09B  <MAC 'RomTelecom-WPA-D09B' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
RomTelecom-WEP-D09B  <MAC 'RomTelecom-WEP-D09B' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WEP        no        
Clicknet-ECCF        <MAC 'Clicknet-ECCF' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       yes     * 
DIGI-49A6            <MAC 'DIGI-49A6' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
HUAWEI-8hbv          <MAC 'HUAWEI-8hbv' [AC8]>  Infra  9     2452 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
HUAWEI-AmF2          <MAC 'HUAWEI-AmF2' [AC3]>  Infra  3     2422 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
Clicknet-2875        <MAC 'Clicknet-2875' [AC4]>  Infra  4     2427 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
WestMeck             <MAC 'WestMeck' [AC7]>  Infra  8     2447 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
Clicknet-6C55        <MAC 'Clicknet-6C55' [AN11]>  Infra  3     2422 MHz  54 Mbit/s  12      &#9602;___  WPA2       no        
HUAWEI-Hx83          <MAC 'HUAWEI-Hx83' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/RomTelecom-WEP-D09B]] (600 root)
[connection] id=RomTelecom-WEP-D09B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=RomTelecom-WEP-D09B
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Clicknet-ECCF]] (600 root)
[connection] id=Clicknet-ECCF | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Clicknet-ECCF
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bucharest (based on set time zone)


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


eno1      no frequency information.


lo        no frequency information.


wlo1      14 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


eno1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlo1      Scan completed :
          Cell 01 - Address: <MAC 'Clicknet-ECCF' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Clicknet-ECCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d7de80212a
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIGI-49A6' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"DIGI-49A6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e10b5ba435
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HUAWEI-AmF2' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-AmF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000018809a22b24
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Clicknet-2875' [AC4]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Clicknet-2875"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00002d3b85adb810
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'RomTelecom-WEP-D09B' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WEP-D09B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008ed10e0ca91
                    Extra: Last beacon: 64ms ago
          Cell 06 - Address: <MAC 'RomTelecom-WPA-D09B' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-D09B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008ed10e0ddad
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'WestMeck' [AC7]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WestMeck"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b667257d457
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'HUAWEI-8hbv' [AC8]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-8hbv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000ece109d767
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Clicknet-4547' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Clicknet-4547"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00001a3e2b30450b
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'DIRECT-C7-BRAVIA' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-C7-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002c16f4322
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: Y
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


[/etc/modprobe.d/cfg80211.conf]
options cfg80211 cfg80211_disable_40mhz_24ghz=Y


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


[11285.918942] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 26 times)
[12129.033167] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=fe80:0000:0000:0000:e9a4:eb5a:8326:5de8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=25344 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[12129.033183] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=fe80:0000:0000:0000:e9a4:eb5a:8326:5de8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=954865 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[12129.043317] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=fe80:0000:0000:0000:e9a4:eb5a:8326:5de8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=25344 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[12129.043349] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=fe80:0000:0000:0000:e9a4:eb5a:8326:5de8 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=954865 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[12410.068796] [UFW BLOCK] IN=wlo1 OUT= MAC=33:33:00:01:00:03:b4:82:fe:5e:9d:5c:86:dd SRC=fe80:0000:0000:0000:4cd1:245f:02e2:4a2d DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=73 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=51536 DPT=5355 LEN=33 
[12410.069979] [UFW BLOCK] IN=wlo1 OUT= MAC=01:00:5e:00:00:fc:b4:82:fe:5e:9d:5c:08:00 SRC=192.168.1.8 DST=224.0.0.252 LEN=53 TOS=0x00 PREC=0x00 TTL=1 ID=2286 PROTO=UDP SPT=50263 DPT=5355 LEN=33 
[12410.168585] [UFW BLOCK] IN=wlo1 OUT= MAC=33:33:00:01:00:03:b4:82:fe:5e:9d:5c:86:dd SRC=fe80:0000:0000:0000:4cd1:245f:02e2:4a2d DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=73 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=51536 DPT=5355 LEN=33 
[12410.169727] [UFW BLOCK] IN=wlo1 OUT= MAC=01:00:5e:00:00:fc:b4:82:fe:5e:9d:5c:08:00 SRC=192.168.1.8 DST=224.0.0.252 LEN=53 TOS=0x00 PREC=0x00 TTL=1 ID=2290 PROTO=UDP SPT=50263 DPT=5355 LEN=33 
[12479.600279] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 13 times)


########## wireless info END ############




```

---

### Post by praseodym on 2017-02-05
Lets try
```

sudo iwconfig wlo1 power off
```

---

### Post by usrandrd3 on 2017-02-05
I have runned this command and restarted the laptop, but the signal is the same.

```

sudo iwconfig wlo1 power off

```

I have runned again the  commands from [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and below is the report.

```



########## wireless info START ##########


Report from: 05 Feb 2017 17:26 EET +0200


Booted last: 05 Feb 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
    DeviceName: Ralink WLAN Ralink Ripple3 RT5390F_802.11 b/g/n 1x1 PCIe HMC
    Subsystem: Hewlett-Packard Company Device [103c:1839]


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:183e]


##### lsusb #############################


Bus 002 Device 003: ID 05c8:0223 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:078c Microsoft Corp. 
Bus 003 Device 002: ID 0e8f:00a7 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              57344  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              757760  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              581632  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6317  bytes 388481 (388.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6317  bytes 388481 (388.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.7  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e9a4:eb5a:8326:5de8  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 2907  bytes 2863744 (2.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2562  bytes 342715 (342.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11  ESSID:"Clicknet-ECCF"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Clicknet-ECCF' [AN6]>   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9  Invalid misc:107   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1122     1  0 17:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        7 Series/C210 Series Chipset Family PCI Express Root Port 1
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Clicknet-ECCF
GENERAL.CON-UUID:                       923a33a4-e555-4612-8091-91ec294fc517
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   923a33a4-e555-4612-8091-91ec294fc517 | Clicknet-ECCF
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   75a07422-8f64-4edd-a4f2-ca358f1be77f | RomTelecom-WEP-D09B
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486394553
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.7
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e9a4:eb5a:8326:5de8/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/net/eno1
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


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DIRECT-C7-BRAVIA     <MAC 'DIRECT-C7-BRAVIA' [AN1]>  Infra  10    2457 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       no        
RomTelecom-WPA-D09B  <MAC 'RomTelecom-WPA-D09B' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
DIGI-49A6            <MAC 'DIGI-49A6' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
RomTelecom-WEP-D09B  <MAC 'RomTelecom-WEP-D09B' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WEP        no        
HUAWEI-8hbv          <MAC 'HUAWEI-8hbv' [AN5]>  Infra  10    2457 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA1 WPA2  no        
Clicknet-ECCF        <MAC 'Clicknet-ECCF' [AN6]>  Infra  2     2417 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA2       yes     * 
Clicknet-4547        <MAC 'Clicknet-4547' [AN7]>  Infra  10    2457 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
WestMeck             <MAC 'WestMeck' [AN8]>  Infra  8     2447 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
HUAWEI-AmF2          <MAC 'HUAWEI-AmF2' [AN9]>  Infra  3     2422 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
Clicknet-2875        <MAC 'Clicknet-2875' [AN10]>  Infra  4     2427 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        
HUAWEI-Hx83          <MAC 'HUAWEI-Hx83' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/RomTelecom-WEP-D09B]] (600 root)
[connection] id=RomTelecom-WEP-D09B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=RomTelecom-WEP-D09B
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Clicknet-ECCF]] (600 root)
[connection] id=Clicknet-ECCF | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Clicknet-ECCF
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bucharest (based on set time zone)


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


eno1      no frequency information.


wlo1      14 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


wlo1      Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: Y
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


[/etc/modprobe.d/cfg80211.conf]
options cfg80211 cfg80211_disable_40mhz_24ghz=Y


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


[   21.434983] rt2800pci 0000:07:00.0 wlo1: renamed from wlan0
[   40.949783] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   40.949823] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   41.198193] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.40
[   41.353817] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   45.270315] wlo1: authenticate with <MAC 'Clicknet-ECCF' [AN6]>
[   45.293901] wlo1: send auth to <MAC 'Clicknet-ECCF' [AN6]> (try 1/3)
[   45.295423] wlo1: authenticated
[   45.297093] wlo1: associate with <MAC 'Clicknet-ECCF' [AN6]> (try 1/3)
[   45.300507] wlo1: RX AssocResp from <MAC 'Clicknet-ECCF' [AN6]> (capab=0x411 status=0 aid=5)
[   45.300590] wlo1: associated
[   45.300602] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   46.356637] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=48 TOS=0x00 PREC=0x00 TTL=255 ID=17230 PROTO=UDP SPT=5355 DPT=5355 LEN=28 
[   46.568988] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=48 TOS=0x00 PREC=0x00 TTL=255 ID=17280 PROTO=UDP SPT=5355 DPT=5355 LEN=28 
[   46.818996] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=48 TOS=0x00 PREC=0x00 TTL=255 ID=17319 PROTO=UDP SPT=5355 DPT=5355 LEN=28 
[   47.069144] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=fe80:0000:0000:0000:e9a4:eb5a:8326:5de8 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=68 TC=0 HOPLIMIT=255 FLOWLBL=898447 PROTO=UDP SPT=5355 DPT=5355 LEN=28  (repeated 3 times)
[  110.472848] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush
[  138.476251] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32769 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  138.476316] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32770 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  138.476351] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=56 TOS=0x00 PREC=0x00 TTL=255 ID=32771 PROTO=UDP SPT=5355 DPT=5355 LEN=36 
[  138.763109] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32809 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  138.763211] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=56 TOS=0x00 PREC=0x00 TTL=255 ID=32810 PROTO=UDP SPT=5355 DPT=5355 LEN=36 
[  138.763252] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32811 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  139.013084] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32840 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  139.013144] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=59 TOS=0x00 PREC=0x00 TTL=255 ID=32841 PROTO=UDP SPT=5355 DPT=5355 LEN=39 
[  139.013167] [UFW BLOCK] IN=wlo1 OUT= MAC= SRC=192.168.1.7 DST=224.0.0.252 LEN=56 TOS=0x00 PREC=0x00 TTL=255 ID=32842 PROTO=UDP SPT=5355 DPT=5355 LEN=36 
[  173.772514] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 3 times)


########## wireless info END ############




```

---

### Post by praseodym on 2017-02-05
So, try
```

echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
```
Do you need the firewall?

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```
Reboot

---

### Post by usrandrd3 on 2017-02-06
I disabled the firewall. I have runned those commands and restarted.
Things are better now: it does not disconnect anymore, i can upload files via ftp, but still slowly.

The signal indicator is still poor, also the speed is still lower than on Windows.
[IMG]https://s27.postimg.org/4m5rq86o3/ubunt_wifi_sig.jpg[/IMG]

When i upload php files via Filezilla or when i keep opened the Teamviewer, is also slower than slow. On Windows the connection was ok when connected to skype or teamviewer.

This is the report runned again.
```



########## wireless info START ##########


Report from: 06 Feb 2017 13:05 EET +0200


Booted last: 06 Feb 2017 00:00 EET +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-37-generic #39-Ubuntu SMP Thu Jan 26 02:27:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


07:00.0 Network controller [0280]: Ralink corp. Device [1814:539a]
    DeviceName: Ralink WLAN Ralink Ripple3 RT5390F_802.11 b/g/n 1x1 PCIe HMC
    Subsystem: Hewlett-Packard Company Device [103c:1839]


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:183e]


##### lsusb #############################


Bus 002 Device 003: ID 05c8:0223 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 045e:078c Microsoft Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 03f0:002a Hewlett-Packard LaserJet P1102
Bus 003 Device 002: ID 0e8f:00a7 GreenAsia Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              57344  5 rt2800lib,rt2x00pci,rt2800mmio,rt2x00mmio,rt2800pci
mac80211              757760  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              581632  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
wmi                    16384  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 161390  bytes 9824285 (9.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 161390  bytes 9824285 (9.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlo1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.7  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::e9a4:eb5a:8326:5de8  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 291208  bytes 239569272 (239.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 273307  bytes 104828121 (104.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11  ESSID:"Clicknet-ECCF"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Clicknet-ECCF' [AC1]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:13  Invalid misc:49   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1064     1  0 09:24 ?        00:00:04 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        7 Series/C210 Series Chipset Family PCI Express Root Port 1
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.8.0-37-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Clicknet-ECCF
GENERAL.CON-UUID:                       923a33a4-e555-4612-8091-91ec294fc517
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   75a07422-8f64-4edd-a4f2-ca358f1be77f | RomTelecom-WEP-D09B
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   923a33a4-e555-4612-8091-91ec294fc517 | Clicknet-ECCF
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486452369
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.7
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       domain_name_servers = 192.168.1.1 0.0.0.0
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::e9a4:eb5a:8326:5de8/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:08:00.0/net/eno1
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


SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
DIRECT-C7-BRAVIA     <MAC 'DIRECT-C7-BRAVIA' [AC9]>  Infra  10    2457 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       no        
DIGI-49A6            <MAC 'DIGI-49A6' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
RomTelecom-WEP-D09B  <MAC 'RomTelecom-WEP-D09B' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WEP        no        
RomTelecom-WPA-D09B  <MAC 'RomTelecom-WPA-D09B' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
Clicknet-4547        <MAC 'Clicknet-4547' [AN5]>  Infra  10    2457 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2       no        
Clicknet-ECCF        <MAC 'Clicknet-ECCF' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA2       yes     * 
HUAWEI-AmF2          <MAC 'HUAWEI-AmF2' [AC5]>  Infra  3     2422 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
HUAWEI-8hbv          <MAC 'HUAWEI-8hbv' [AC8]>  Infra  8     2447 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
RomTelecom-WEP-17A9  <MAC 'RomTelecom-WEP-17A9' [AC3]>  Infra  2     2417 MHz  54 Mbit/s  35      &#9602;&#9604;__  WEP        no        
WestMeck             <MAC 'WestMeck' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
RomTelecom-WPA-17A9  <MAC 'RomTelecom-WPA-17A9' [AC4]>  Infra  2     2417 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
Clicknet-2875        <MAC 'Clicknet-2875' [AN12]>  Infra  4     2427 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
HUAWEI-Hx83          <MAC 'HUAWEI-Hx83' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  12      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/RomTelecom-WEP-D09B]] (600 root)
[connection] id=RomTelecom-WEP-D09B | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=RomTelecom-WEP-D09B
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Clicknet-ECCF]] (600 root)
[connection] id=Clicknet-ECCF | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Clicknet-ECCF
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Bucharest (based on set time zone)


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


eno1      no frequency information.


wlo1      14 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlo1      Scan completed :
          Cell 01 - Address: <MAC 'Clicknet-ECCF' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Clicknet-ECCF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ecab7e6a31
                    Extra: Last beacon: 30956ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'DIGI-49A6' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"DIGI-49A6"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f5dcdf3920
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'RomTelecom-WEP-17A9' [AC3]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WEP-17A9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2725c827
                    Extra: Last beacon: 4ms ago
          Cell 04 - Address: <MAC 'RomTelecom-WPA-17A9' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-17A9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f2725eb2d
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'HUAWEI-AmF2' [AC5]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-AmF2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019cdb2bd06d
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'RomTelecom-WPA-D09B' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WPA-D09B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000901e26abb2c
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'RomTelecom-WEP-D09B' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"RomTelecom-WEP-D09B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000901e26ab286
                    Extra: Last beacon: 4ms ago
          Cell 08 - Address: <MAC 'HUAWEI-8hbv' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-8hbv"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000101b28e9a9b
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'DIRECT-C7-BRAVIA' [AC9]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-C7-BRAVIA"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000325664599
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'WestMeck' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"WestMeck"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b7b43f77c54
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'HUAWEI-Hx83' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"HUAWEI-Hx83"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010b91df7196
                    Extra: Last beacon: 2720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     4D2CAAE95D28B3DF4F72A52
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     DBE617B0243C0FEB62786D4
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7092408A4EF1A70FC0C7538
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D84965563CC7530CFFD2269
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     02CA9DA77FC2C7FCCC58176
depends:        rt2x00lib
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.8.0-37-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CF930122B7900096FC259FA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5F9AB87008B83E8D5117A0B
depends:        
intree:         Y
vermagic:       4.8.0-37-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: Y
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


[/etc/modprobe.d/cfg80211.conf]
options cfg80211 cfg80211_disable_40mhz_24ghz=Y


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 9004.654292] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 3 times)
[ 9076.970198] wlo1: authenticate with <MAC 'Clicknet-ECCF' [AC1]>
[ 9076.997448] wlo1: send auth to <MAC 'Clicknet-ECCF' [AC1]> (try 1/3)
[ 9076.998972] wlo1: authenticated
[ 9077.000896] wlo1: associate with <MAC 'Clicknet-ECCF' [AC1]> (try 1/3)
[ 9077.004404] wlo1: RX AssocResp from <MAC 'Clicknet-ECCF' [AC1]> (capab=0x411 status=0 aid=1)
[ 9077.004494] wlo1: associated
[ 9124.133433] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 19 times)
[10083.770265] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 50 times)
[12915.743499] wlo1: authenticate with <MAC 'Clicknet-ECCF' [AC1]>
[12915.770655] wlo1: send auth to <MAC 'Clicknet-ECCF' [AC1]> (try 1/3)
[12915.772484] wlo1: authenticated
[12915.773997] wlo1: associate with <MAC 'Clicknet-ECCF' [AC1]> (try 1/3)
[12915.777474] wlo1: RX AssocResp from <MAC 'Clicknet-ECCF' [AC1]> (capab=0x411 status=0 aid=1)
[12915.777571] wlo1: associated
[12964.811512] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 15 times)


########## wireless info END ############



```
Thanks

---

### Post by praseodym on 2017-02-06
Lets try

```
sudo iwconfig wlo1 power off
```

---

### Post by usrandrd3 on 2017-02-21
The internet speed is ok, is a problem with Filezilla that is slower on Ubuntu. I will open a different topic. Thanks.

---

