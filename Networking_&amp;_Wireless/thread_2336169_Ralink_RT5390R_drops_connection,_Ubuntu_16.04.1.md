---
title: "Ralink RT5390R drops connection, Ubuntu 16.04.1"
date: 2016-09-05
forum: Networking &amp; Wireless
---

### Post by mrwalrus on 2016-09-05
My wireless connection drops once in a while. The only solution I have found is to switch back to 14.04, but I'd like to stick with 16.04.1.

```



########## wireless info START ##########


Report from: 05 Sep 2016 09:46 EDT -0400


Booted last: 05 Sep 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Ralink corp. RT5390R 802.11bgn PCIe Wireless Network Adapter [1814:539b]
	DeviceName: Ralink RT5390R 802.11bgn 1x1 Wi-Fi Adapter
	Subsystem: Hewlett-Packard Company RT5390R 802.11bgn PCIe Wireless Network Adapter [103c:18ed]


08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
	DeviceName: Hanksville 10/100 Lan Connection
	Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1854]


##### lsusb #############################


Bus 002 Device 004: ID 05c8:0348 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 093a:2521 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800pci              16384  0
rt2800mmio             20480  1 rt2800pci
rt2800lib              94208  2 rt2800pci,rt2800mmio
hp_wmi                 16384  0
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800pci,rt2800mmio
sparse_keymap          16384  1 hp_wmi
rt2x00lib              57344  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              737280  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
eeprom_93cx6           16384  1 rt2800pci
crc_ccitt              16384  1 rt2800lib
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback
allow-hotplug eth0
iface eth0 inet dhcp


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          inet addr:10.253.92.156  Bcast:10.253.95.255  Mask:255.255.248.0
          inet6 addr: fe80::de4:6835:559f:aa4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14249291 (14.2 MB)  TX bytes:2259783 (2.2 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlo1      IEEE 802.11bgn  ESSID:"WVU.Encrypted"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'WVU.Encrypted' [AC1]>   
          Bit Rate=43.3 Mb/s   Tx-Power=8 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:106  Invalid misc:145   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.253.88.1     0.0.0.0         UG    600    0        0 wlo1
1.1.1.100       10.253.88.1     255.255.255.255 UGH   600    0        0 wlo1
10.253.88.0     0.0.0.0         255.255.248.0   U     600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1


##### resolv.conf #######################


nameserver 127.0.1.1
search wvu.edu


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2457     1  0 08:51 ?        00:00:07 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390R 802.11bgn PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WVU.Encrypted
GENERAL.CON-UUID:                       7dc6797b-9cf4-4e86-aa9b-9543f872d27a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     43 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7dc6797b-9cf4-4e86-aa9b-9543f872d27a | WVU.Encrypted
IP4.ADDRESS[1]:                         10.253.92.156/21
IP4.GATEWAY:                            10.253.88.1
IP4.ROUTE[1]:                           dst = 1.1.1.100/32, nh = 10.253.88.1, mt = 600
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             157.182.203.110
IP4.DNS[2]:                             157.182.203.100
IP4.DNS[3]:                             157.182.232.200
IP4.DOMAIN[1]:                          wvu.edu
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1473090335
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.253.88.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.253.92.156
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = wvu.edu
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.253.95.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       domain_name_servers = 157.182.203.110 157.182.203.100 157.182.232.200
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.248.0
DHCP4.OPTION[26]:                       network_number = 10.253.88.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 1.1.1.100
IP6.ADDRESS[1]:                         fe80::de4:6835:559f:aa4a/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/eno1
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


SSID                              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
DIRECT-25-HP DeskJet 3630 series  <MAC 'DIRECT-25-HP DeskJet 3630 series' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
WVU.Play                          <MAC 'WVU.Play' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --           no        
WVU.Encrypted                     <MAC 'WVU.Encrypted' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2 802.1X  yes     * 
WVU.Play                          <MAC 'WVU.Play' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  55      &#9602;&#9604;__  --           no        
WVU.Encrypted                     <MAC 'WVU.Encrypted' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2 802.1X  no        
HP-Print-1B-Officejet 4630        <MAC 'HP-Print-1B-Officejet 4630' [AC14]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  --           no        
DIRECT-E4-HP DeskJet 3630 series  <MAC 'DIRECT-E4-HP DeskJet 3630 series' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2         no        
WVU.Play                          <MAC 'WVU.Play' [AC11]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  --           no        
WVU.Play                          <MAC 'WVU.Play' [AC12]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  --           no        
MT                                <MAC 'MT' [AN10]>  Infra  2     2417 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2    no        
--                                <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC13]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
WVU.Play                          <MAC 'WVU.Play' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  --           no        
WVU.Play                          <MAC 'WVU.Play' [AC21]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  --           no        
WVU.Play                          <MAC 'WVU.Play' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  --           no        
WVU.Encrypted                     <MAC 'WVU.Encrypted' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2 802.1X  no        
WVU.Encrypted                     <MAC 'WVU.Encrypted' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA2 802.1X  no        
--                                <MAC '' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2    no        
NETGEAR49                         <MAC 'NETGEAR49' [AN18]>  Infra  7     2442 MHz  54 Mbit/s  19      &#9602;___  WPA2         no        
DIRECT-34-HP ENVY 5540 series     <MAC 'DIRECT-34-HP ENVY 5540 series' [AN19]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  WPA2         no        
DIRECT-A6-HP DeskJet 3630 series  <MAC 'DIRECT-A6-HP DeskJet 3630 series' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  15      &#9602;___  WPA2         no        


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


[[/etc/NetworkManager/system-connections/WVU.Encrypted]] (600 root)
[connection] id=WVU.Encrypted | type=wifi | permissions=user:don:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=WVU.Encrypted
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eno1      no frequency information.


wlo1      11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      9   APs on   Frequency:2.412 GHz (Channel 1)
      8   APs on   Frequency:2.437 GHz (Channel 6)
      4   APs on   Frequency:2.462 GHz (Channel 11)


wlo1      Scan completed :
          Cell 01 - Address: <MAC 'WVU.Encrypted' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8025c9e6
                    Extra: Last beacon: 21160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC 'DIRECT-25-HP DeskJet 3630 series' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-25-HP DeskJet 3630 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000032d22f5561
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'DIRECT-E4-HP DeskJet 3630 series' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-E4-HP DeskJet 3630 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018aa147c381
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e463ba188
                    Extra: Last beacon: 1732ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'WVU.Encrypted' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8275fee3
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'WVU.Play' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8125e122
                    Extra: Last beacon: 21112ms ago
          Cell 07 - Address: <MAC 'DIRECT-A6-HP DeskJet 3630 series' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-A6-HP DeskJet 3630 series"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eb13443093
                    Extra: Last beacon: 22992ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WVU.Encrypted' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8037c263
                    Extra: Last beacon: 960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'WVU.Play' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8228b3d5
                    Extra: Last beacon: 960ms ago
          Cell 10 - Address: <MAC 'WVU.Play' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e57a6f830d
                    Extra: Last beacon: 44ms ago
          Cell 11 - Address: <MAC 'WVU.Play' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000151a6fbb47a
                    Extra: Last beacon: 1728ms ago
          Cell 12 - Address: <MAC 'WVU.Play' [AC12]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001065f9f7691
                    Extra: Last beacon: 21112ms ago
          Cell 13 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC13]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b14b91364e
                    Extra: Last beacon: 1704ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'HP-Print-1B-Officejet 4630' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-1B-Officejet 4630"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018aa1565e59
                    Extra: Last beacon: 4ms ago
          Cell 15 - Address: <MAC 'WVU.Play' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a80d41752
                    Extra: Last beacon: 21160ms ago
          Cell 16 - Address: <MAC 'WVU.Encrypted' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e57a6f8228
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC 'WVU.Encrypted' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000151a6fbb1fa
                    Extra: Last beacon: 1728ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 18 - Address: <MAC '' [AC18]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a8131d142
                    Extra: Last beacon: 1728ms ago
          Cell 19 - Address: <MAC '' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007e463d39c1
                    Extra: Last beacon: 1704ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'WVU.Encrypted' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"WVU.Encrypted"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a81a7045d
                    Extra: Last beacon: 996ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC 'WVU.Play' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"WVU.Play"
                    Bit Rates:9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000018a81a70542
                    Extra: Last beacon: 996ms ago


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     26CCED9E0CE5EFBFA9B8882
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     01C1A7641505065E52E0388
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00pci]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     543B84557258F153AC267F0
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00mmio]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     ADBE279820CFD0A1081C682
depends:        rt2x00lib
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


sleep 10
iwconfig wlo1 power off
exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="rt5390r"


[/etc/pm/power.d/wireless] (755 root)
/sbin/iwconfig wlo1 power off


##### udev rules ########################


##### dmesg #############################


[ 3189.339419] wlo1: authenticate with <MAC 'WVU.Encrypted' [AC16]>
[ 3189.346055] wlo1: send auth to <MAC 'WVU.Encrypted' [AC16]> (try 1/3)
[ 3189.350310] wlo1: authenticated
[ 3189.353637] wlo1: associate with <MAC 'WVU.Encrypted' [AC16]> (try 1/3)
[ 3189.357332] wlo1: RX AssocResp from <MAC 'WVU.Encrypted' [AC16]> (capab=0x431 status=0 aid=4)
[ 3189.357436] wlo1: associated
[ 3189.456707] wlo1: Limiting TX power to 8 dBm as advertised by <MAC 'WVU.Encrypted' [AC16]>
[ 3212.940902] wlo1: disassociated from <MAC 'WVU.Encrypted' [AC16]> (Reason: 1)
[ 3213.775637] wlo1: authenticate with <MAC 'WVU.Encrypted' [AC1]>
[ 3213.782747] wlo1: send auth to <MAC 'WVU.Encrypted' [AC1]> (try 1/3)
[ 3213.785076] wlo1: authenticated
[ 3213.786454] wlo1: associate with <MAC 'WVU.Encrypted' [AC1]> (try 1/3)
[ 3213.790445] wlo1: RX AssocResp from <MAC 'WVU.Encrypted' [AC1]> (capab=0x431 status=0 aid=47)
[ 3213.790534] wlo1: associated
[ 3213.804756] wlo1: Limiting TX power to 8 dBm as advertised by <MAC 'WVU.Encrypted' [AC1]>
[ 3238.553565] wlo1: deauthenticating from <MAC 'WVU.Encrypted' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 3239.288317] wlo1: authenticate with <MAC 'WVU.Encrypted' [AC1]>
[ 3239.295821] wlo1: send auth to <MAC 'WVU.Encrypted' [AC1]> (try 1/3)
[ 3239.298394] wlo1: authenticated
[ 3239.299355] wlo1: associate with <MAC 'WVU.Encrypted' [AC1]> (try 1/3)
[ 3239.301705] wlo1: RX AssocResp from <MAC 'WVU.Encrypted' [AC1]> (capab=0x431 status=0 aid=47)
[ 3239.301779] wlo1: associated
[ 3239.303014] wlo1: Limiting TX power to 8 dBm as advertised by <MAC 'WVU.Encrypted' [AC1]>
[ 3261.056097] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 2 failed to flush (repeated 6 times)
[ 3306.141642] ieee80211 phy0: rt2x00queue_flush_queue: Warning - Queue 0 failed to flush


########## wireless info END ############



```

---

### Post by autocrat on 2016-09-05
Is the firmware up to date?

---

### Post by jeremy31 on 2016-09-06
You may have to change your sleep value in /etc/rc.local to a higher value and the ```
iwconfig wlo1 power off
``` may need to be changed to ```
/sbin/iwconfig wlo1 power off
```

---

### Post by mrwalrus on 2016-09-06
Due to special circumstances, I cannot connect to ethernet and the 2.4GHz connection is congested. I just decided to run out and get a usb wifi adapter. Problem is solved. I'm putting this thread to sleep. Thanks for the replies. I really appreciate it guys.

---

