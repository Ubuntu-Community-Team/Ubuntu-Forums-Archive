---
title: "Panda PAU06 slow connection, Ubuntu 16.04"
date: 2017-02-01
forum: Networking &amp; Wireless
---

### Post by solidua on 2017-02-01
My wifi connection is significantly slower than expected. On my other wireless devices I'm downloading 90 mb/s while on my PAU06 im only getting 50 mb/s. Do i need to update a driver? If this is a limit due to the adapter, could you recommend an adapter? thanks. 

```


########## wireless info START ##########


Report from: 01 Feb 2017 14:24 PST -0800


Booted last: 01 Feb 2017 00:00 PST -0800


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-59-generic #80-Ubuntu SMP Fri Jan 6 17:47:47 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1] (rev 05)
	DeviceName:  Onboard LAN
	Subsystem: Gigabyte Technology Co., Ltd Ethernet Connection (2) I218-V [1458:e000]


##### lsusb #############################


Bus 002 Device 002: ID 8087:8002 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:800a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045b:0210 Hitachi, Ltd 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 007: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 003 Device 006: ID 045b:0209 Hitachi, Ltd 
Bus 003 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 003 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 003 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 002: ID 1b1c:1c02 Corsair 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800usb              28672  0
rt2x00usb              24576  1 rt2800usb
rt2800lib              94208  1 rt2800usb
rt2x00lib              57344  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              737280  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              565248  2 mac80211,rt2x00lib
crc_ccitt              16384  1 rt2800lib
mxm_wmi                16384  0
wmi                    20480  1 mxm_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fb100000-fb120000 


wlx<IF from MAC [IF2]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF2]>' [IF2]>  
          inet addr:10.0.1.37  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: 2601:600:9000:ceb4:61b3:81f5:7d41:95ae/64 Scope:Global
          inet6 addr: fe80::38a6:e199:2f06:99eb/64 Scope:Link
          inet6 addr: 2601:600:9000:ceb4:7039:94dd:4bd9:824c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:273453584 (273.4 MB)  TX bytes:41359042 (41.3 MB)


##### iwconfig ##########################


lo        no wireless extensions.


eno1      no wireless extensions.


wlx<IF from MAC [IF2]>  IEEE 802.11bgn  ESSID:"Hale Ohana"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Hale Ohana' [AC1]>   
          Bit Rate=144.4 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1673  Invalid misc:342   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    600    0        0 wlx<IF from MAC [IF2]>
10.0.1.0        0.0.0.0         255.255.255.0   U     600    0        0 wlx<IF from MAC [IF2]>
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlx<IF from MAC [IF2]>


##### resolv.conf #######################


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### network managers ##################


Installed:


	NetworkManager


Running:


root       780     1  0 14:18 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-59-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9.4/3-9.4:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Hale Ohana
GENERAL.CON-UUID:                       2a5aef04-e902-4fb2-a5b2-9111ba66343e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     144 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2a5aef04-e902-4fb2-a5b2-9111ba66343e | Hale Ohana
IP4.ADDRESS[1]:                         10.0.1.37/24
IP4.GATEWAY:                            10.0.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.1.1
IP4.DOMAIN[1]:                          hsd1.wa.comcast.net.
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486073935
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.0.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.1.37
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = hsd1.wa.comcast.net.
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 10.0.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 10.0.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 10.0.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.0.1.1
IP6.ADDRESS[1]:                         2601:600:9000:ceb4:7039:94dd:4bd9:824c/64
IP6.ADDRESS[2]:                         2601:600:9000:ceb4:61b3:81f5:7d41:95ae/64
IP6.ADDRESS[3]:                         fe80::38a6:e199:2f06:99eb/64
IP6.GATEWAY:                            fe80::9272:40ff:fe04:a7d1
IP6.ROUTE[1]:                           dst = 2601:600:9000:ceb4::/64, nh = fe80::9272:40ff:fe04:a7d1, mt = 600
IP6.DNS[1]:                             2601:600:9000:ceb4:9272:40ff:fe04:a7d1
IP6.DOMAIN[1]:                          hsd1.wa.comcast.net
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:ae:14:f0:c5:44:50:86:80:ef:60:ad:d2:bd:da:b2:67
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2601:600:9000:ceb4:9272:40ff:fe04:a7d1
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = hsd1.wa.comcast.net.
DHCP6.OPTION[7]:                        dhcp6_preference = 255
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:1f:ed:69:86:90:72:40:4:a7:d1


GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eno1
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


SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
Hale Ohana       <MAC 'Hale Ohana' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  91      &#9602;&#9604;&#9606;&#9608;  WPA2      yes     * 
MtRainier24_EXT  <MAC 'MtRainier24_EXT' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      no        
--               <MAC '' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2      no        
Hale Ohana       <MAC 'Hale Ohana' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2      no        
VRHOME           <MAC 'VRHOME' [AC7]>  Infra  7     2442 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2      no        
VRGUEST          <MAC 'VRGUEST' [AC6]>  Infra  7     2442 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2      no        
MtRainier24      <MAC 'MtRainier24' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2      no        


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


[[/etc/NetworkManager/system-connections/Hale Ohana]] (600 root)
[connection] id=Hale Ohana | type=wifi | permissions=user:tidyware:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=Hale Ohana
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


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


wlx<IF from MAC [IF2]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eno1      Interface doesn't support scanning.


Channel occupancy:


      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)


wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'Hale Ohana' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"Hale Ohana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000351dddf8f7b
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'MtRainier24_EXT' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"MtRainier24_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003774ace6114
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MtRainier24' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"MtRainier24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000795956013e
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cb394e2166
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Hale Ohana' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Hale Ohana"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000351e4e35967
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'VRGUEST' [AC6]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"VRGUEST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a6325176d
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VRHOME' [AC7]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"VRHOME"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a63251f9f
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR41' [AC8]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR41"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c78c2c537a
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     CD175F3067617C23A4A79F3
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     FADD78F4B0B6C8F4DDFA8E5
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2800lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     BB9F48B63A82C3FD3E73BAF
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[rt2x00lib]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     72E39180D883A5541F66494
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-59-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800usb]
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


##### udev rules ########################


##### dmesg #############################


[    6.278295] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready (repeated 2 times)
[    7.781716] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[    7.794370] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
[    7.802677] rt2800usb 3-9.4:1.0 wlx<IF from MAC [IF2]>: renamed from wlan0
[    7.819985] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready
[    7.820060] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[    7.821495] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[    8.004021] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF2]>: link is not ready (repeated 2 times)
[   16.147544] wlx<IF from MAC [IF2]>: authenticate with <MAC 'Hale Ohana' [AC1]>
[   16.163625] wlx<IF from MAC [IF2]>: send auth to <MAC 'Hale Ohana' [AC1]> (try 1/3)
[   16.165104] wlx<IF from MAC [IF2]>: authenticated
[   16.165211] wlx<IF from MAC [IF2]>: associating with AP with corrupt beacon
[   16.168038] wlx<IF from MAC [IF2]>: associate with <MAC 'Hale Ohana' [AC1]> (try 1/3)
[   16.171366] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'Hale Ohana' [AC1]> (capab=0x1431 status=0 aid=6)
[   16.175789] wlx<IF from MAC [IF2]>: associated
[   16.175815] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF2]>: link becomes ready
[   17.737767] wlx<IF from MAC [IF2]>: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'Hale Ohana' [AC1]>


########## wireless info END ############



```

---

