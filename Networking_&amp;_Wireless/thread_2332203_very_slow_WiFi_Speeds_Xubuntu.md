---
title: "very slow WiFi Speeds Xubuntu"
date: 2016-07-29
forum: Networking &amp; Wireless
---

### Post by teprac on 2016-07-29
I installed Xubuntu 16.04 amd64bit about a week ago. So far i really like it. 

When Ethernet is connected i get about 17mbps download speed. 

However the speeds are VERY SLOW when i connect my J-LINK LJ-6106 Ralink 3070 , Chipset: Ralink 3070 (this same usb wifi adapter gets good speeds on my other pc running Windows 7 64bit)

I have been doing alot of searching and reading, but i cannot seem to resolve this poor wifi performance problem.

I set IPv6 settings to IGNORE and this solved the random disconnect problem.

Does anyone have suggestions on how to fix this or can you recommend a good usb wireless adapter that has good speeds out of the box?

Thank you for any help

---

### Post by praseodym on 2016-07-29
Please run the wireless script from the sticky thread and show the outputs

---

### Post by teprac on 2016-07-29
I ran the scripts. I hope this is the correct output. wireless-info.txt

```


########## wireless info START ##########


Report from: 29 Jul 2016 16:36 CDT -0500


Booted last: 29 Jul 2016 00:00 CDT -0500


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Xubuntu


##### lspci #############################




00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Subsystem: ASUSTeK Computer Inc. M4N68T series motherboard [1043:83a4]
    Kernel driver in use: forcedeth


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1d8e:8100  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


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


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp0s7    Link encap:Ethernet  HWaddr f4:6d:04:60:13:e5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:189 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114811 (114.8 KB)  TX bytes:18208 (18.2 KB)


wlx983f9f2240b0 Link encap:Ethernet  HWaddr 98:3f:9f:22:40:b0  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9a3f:9fff:fe22:40b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7408 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10337250 (10.3 MB)  TX bytes:1055597 (1.0 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s7    no wireless extensions.


wlx983f9f2240b0  IEEE 802.11bgn  ESSID:"backtrackWR841N"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: C0:4A:00:BE:9F:D8   
          Bit Rate:58.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-11 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:99  Invalid misc:309   Missed beacon:0




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlx983f9f2240b0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlx983f9f2240b0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2084     1  0 16:27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlx983f9f2240b0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         rt2800usb
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         98:3F:9F:22:40:B0
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.1/usb1/1-2/1-2:1.0/net/wlx983f9f2240b0
GENERAL.IP-IFACE:                       wlx983f9f2240b0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     backtrackWR841N
GENERAL.CON-UUID:                       4da225f6-a25e-42c5-b4cb-321f83e27eb7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4da225f6-a25e-42c5-b4cb-321f83e27eb7 | backtrackWR841N
IP4.ADDRESS[1]:                         192.168.1.102/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             208.67.222.222
IP4.DNS[2]:                             208.67.220.220
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1469834837
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.102
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.1.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 208.67.222.222 208.67.220.220
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.1.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::9a3f:9fff:fe22:40b0/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp0s7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP61 Ethernet (M4N68T series motherboard)
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         F4:6D:04:60:13:E5
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:07.0/net/enp0s7
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 




SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
TC8715D02            FC:52:8D:CA:39:08  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
DEE                  C0:F8:DA:88:C3:91  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
backtrackWR841N      C0:4A:00:BE:9F:D8  Infra  10    2457 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
Exiner Home          A8:A7:95:E9:70:6E  Infra  1     2412 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
FiOS-KUVPK           48:5D:36:4E:24:A8  Infra  6     2437 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
W5Z79                18:1B:EB:4D:C4:7F  Infra  6     2437 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       no        
MacMiller            E8:ED:05:78:A1:A0  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
Willis2              38:4C:90:82:98:70  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
Cambridge Residents  88:DC:96:25:48:37  Infra  11    2462 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
Criss                08:95:2A:06:88:8C  Infra  8     2447 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
blackbriar841n       C0:4A:00:BE:B2:E0  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2  no        
SBG6700AC-FEC76      F8:35:DD:7A:C7:D4  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
--                   B0:A7:37:0A:FE:BB  Infra  1     2412 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
QQ3Y6                00:26:62:B2:0D:77  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WEP        no        
BIGK                 14:AB:F0:D4:D5:60  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
TREVINOWIFI          00:1D:D5:38:EB:F0  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
MZ4T0                00:26:B8:14:BE:87  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WEP        no        
8X46L                18:1B:EB:AE:33:B1  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        
BJPK2                18:1B:EB:05:D5:17  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2       no        


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



```

---

### Post by praseodym on 2016-07-30
Lets check
```

sudo iwconfig wlx983f9f2240b0 power off
```
Try also changing the channel to "1" in your router, there is a lot of traffic between 6 and 11.

---

### Post by teprac on 2016-07-30
I changed the Channel in the router from 10 to Channel 1 and i changed Channel Width from 20MHz to Auto, Mode is set to 11bgn mixed.
I then rebooted the router and i have fast speeds now. not sure what was the difference. 

[COLOR=#000000]*btw i ran the "*[/COLOR][COLOR=#000000][COLOR=#000000][I]sudo iwconfig wlx983f9f2240b0 power off" and it did not return anything.

[/I][/COLOR][/COLOR][COLOR=#000000]*Thank you for all your help.*[/COLOR]

[COLOR=#000000]*Cheers and Beers*[/COLOR]

> **praseodym said:**
> Lets check
```

sudo iwconfig wlx983f9f2240b0 power off
```
Try also changing the channel to "1" in your router, there is a lot of traffic between 6 and 11.

---

