---
title: "Intermittent/Slow wifi on Gigabyte GC-WB867D-I PCIe card on 16.04"
date: 2017-01-30
forum: Networking &amp; Wireless
---

### Post by komali2 on 2017-01-30
I've been plagued by intermittent and slow wifi speeds on 16.04 with this card, although it performs flawlessly in Windows 10 on the same machine. 


It's strange behavior - I'll be cruising along no problem, and then speeds will plummet to 0, or I'll get up to 50% package loss, until I turn off and on wifi, which fixes the problem about 80% of the time. Info below, any thoughts or debugging tips greatly appreciated. I can't see anything that catches my relatively untrained eye, and googling hasn't turned up anything that seems in line with my build. 


ubuntu 16.04 LTS
Memory: 15.6 GiB
Processor: Intel® Core™ i5-6500 CPU @ 3.20GHz × 4
Graphics: GeForce GTX 1060 6GB/PCIe/SSE2
OS type 64-bit
Disk: 14.1 GB


Wifi Card: Gigabyte GC-WB867D-I Rev 4.2 Bluetooth 4.2/Wireless AC/B/G/N Band Dual frequency.... etc. Plugged in a PCI-E port. Totally functional on windows 10. 


Dual-booted with Windows 10. 


During a slowdown, a ping:


```

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=56 time=30.2 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=56 time=26.5 ms
64 bytes from 8.8.8.8: icmp_seq=9 ttl=56 time=29.3 ms
64 bytes from 8.8.8.8: icmp_seq=10 ttl=56 time=25.2 ms
64 bytes from 8.8.8.8: icmp_seq=11 ttl=56 time=25.6 ms
64 bytes from 8.8.8.8: icmp_seq=12 ttl=56 time=25.6 ms
64 bytes from 8.8.8.8: icmp_seq=13 ttl=56 time=26.5 ms
64 bytes from 8.8.8.8: icmp_seq=14 ttl=56 time=25.1 ms
64 bytes from 8.8.8.8: icmp_seq=15 ttl=56 time=27.7 ms
64 bytes from 8.8.8.8: icmp_seq=31 ttl=56 time=24.6 ms
64 bytes from 8.8.8.8: icmp_seq=32 ttl=56 time=27.2 ms
64 bytes from 8.8.8.8: icmp_seq=33 ttl=56 time=28.2 ms
64 bytes from 8.8.8.8: icmp_seq=34 ttl=56 time=26.2 ms
64 bytes from 8.8.8.8: icmp_seq=35 ttl=56 time=25.4 ms
64 bytes from 8.8.8.8: icmp_seq=36 ttl=56 time=26.0 ms
64 bytes from 8.8.8.8: icmp_seq=37 ttl=56 time=26.8 ms
64 bytes from 8.8.8.8: icmp_seq=38 ttl=56 time=25.9 ms
64 bytes from 8.8.8.8: icmp_seq=39 ttl=56 time=25.3 ms
64 bytes from 8.8.8.8: icmp_seq=40 ttl=56 time=26.6 ms
64 bytes from 8.8.8.8: icmp_seq=41 ttl=56 time=25.0 ms
64 bytes from 8.8.8.8: icmp_seq=42 ttl=56 time=28.8 ms
64 bytes from 8.8.8.8: icmp_seq=43 ttl=56 time=25.1 ms
64 bytes from 8.8.8.8: icmp_seq=44 ttl=56 time=26.5 ms
64 bytes from 8.8.8.8: icmp_seq=45 ttl=56 time=26.3 ms
^C
--- 8.8.8.8 ping statistics ---
48 packets transmitted, 24 received, 50% packet loss, time 47097ms
rtt min/avg/max/mdev = 24.637/26.529/30.211/1.407 ms



```


Results of your very handy wifi tool:

---

### Post by wildmanne39 on 2017-01-30
That is actually the wireless script, we need to see the results the script created, it is in your home folder.
Thanks

---

### Post by komali2 on 2017-01-31
Haha wow I'm dumb, pasted below: 

```



########## wireless info START ##########


Report from: 30 Jan 2017 18:23 PST -0800


Booted last: 30 Jan 2017 00:00 PST -0800


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


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
	Kernel driver in use: r8169


05:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
	Subsystem: Intel Corporation Wireless 8260 [8086:1010]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 0bc2:2322 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1b80:b4f9 Afatech 
Bus 001 Device 002: ID 046d:c332 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915_bpo,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF2]>  
          inet addr:10.0.0.37  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::32b2:410d:d6b7:d797/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11933912 (11.9 MB)  TX bytes:1985576 (1.9 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp3s0    no wireless extensions.


wlp5s0    IEEE 802.11abgn  ESSID:"Speedy Remember Harambe"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: <MAC 'Speedy Remember Harambe' [AC1]>   
          Bit Rate=195 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:84   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    600    0        0 wlp5s0
10.0.0.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp5s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp5s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       939     1  0 18:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-59-generic
GENERAL.FIRMWARE-VERSION:               16.242414.0
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.1/0000:05:00.0/net/wlp5s0
GENERAL.IP-IFACE:                       wlp5s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Speedy Remember Harambe
GENERAL.CON-UUID:                       f148a27f-92ed-43e5-8191-d85ed7fe8da4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     585 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f148a27f-92ed-43e5-8191-d85ed7fe8da4 | Speedy Remember Harambe
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0c3b4792-34b6-466e-bc8f-ec3bcd5e6429 | Remember Harambe
IP4.ADDRESS[1]:                         10.0.0.37/24
IP4.GATEWAY:                            10.0.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1485915692
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.0.37
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 10.0.0.1
DHCP4.OPTION[19]:                       broadcast_address = 10.0.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 10.0.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 10.0.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.0.0.1
IP6.ADDRESS[1]:                         fe80::32b2:410d:d6b7:d797/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.7/0000:03:00.0/net/enp3s0
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


SSID                     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Remember Harambe         <MAC 'Remember Harambe' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no        
ATT467                   <MAC 'ATT467' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
NETGEAR25                <MAC 'NETGEAR25' [AC3]>  Infra  2     2417 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
Speedy Remember Harambe  <MAC 'Speedy Remember Harambe' [AC1]>  Infra  153   5765 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       yes     * 
TP-LINK_F4C4_5G          <MAC 'TP-LINK_F4C4_5G' [AC16]>  Infra  153   5765 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
PALS_Network             <MAC 'PALS_Network' [AN6]>  Infra  2     2417 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
TP-LINK_F4C5             <MAC 'TP-LINK_F4C5' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
ATT9JTW5cy               <MAC 'ATT9JTW5cy' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2  no        
Quantenna                <MAC 'Quantenna' [AC15]>  Infra  104   5520 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
MimiFifi1                <MAC 'MimiFifi1' [AN10]>  Infra  36    5180 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
NETGEAR25-5G             <MAC 'NETGEAR25-5G' [AN11]>  Infra  153   5765 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
ATT2C598f4               <MAC 'ATT2C598f4' [AC8]>  Infra  8     2447 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
ATT270                   <MAC 'ATT270' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        
--                       <MAC '--' [AN14]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
Skoof_Linksys            <MAC 'Skoof_Linksys' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
HOME-54D0                <MAC 'HOME-54D0' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
lpaccess                 <MAC 'lpaccess' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
medialink082115          <MAC 'medialink082115' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
MimiFifi2                <MAC 'MimiFifi2' [AC7]>  Infra  8     2447 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
CellSpotForMe            <MAC 'CellSpotForMe' [AC9]>  Infra  10    2457 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
--                       <MAC '' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
NETGEAR10                <MAC 'NETGEAR10' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2       no        
UnderCoverCop            <MAC 'UnderCoverCop' [AN23]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/Speedy Remember Harambe]] (600 root)
[connection] id=Speedy Remember Harambe | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=Speedy Remember Harambe
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Remember Harambe]] (600 root)
[connection] id=Remember Harambe | type=wifi | permissions=user:caleb:;
[wifi] mac-address=<MAC 'wlp5s0' [IF2]> | mac-address-blacklist= | ssid=Remember Harambe
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


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


wlp5s0    32 channels in total; available frequencies :
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
          Current Frequency:5.765 GHz


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp3s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.52 GHz (Channel 104)
      2   APs on   Frequency:5.765 GHz


wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'Speedy Remember Harambe' [AC1]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Speedy Remember Harambe"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b99c08ca03
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TP-LINK_F4C5' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_F4C5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010b491a0de
                    Extra: Last beacon: 488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


          Cell 04 - Address: <MAC 'Remember Harambe' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Remember Harambe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b99ed33eba
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK






##### module infos ######################


[iwlmvm]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     60ED6558F1225672289299A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)


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


[iwlwifi]
filename:       /lib/modules/4.4.0-59-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       4.4.0-59-generic SMP mod_unload modversions 
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


[    2.147060] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.430381] iwlwifi 0000:05:00.0 wlp5s0: renamed from wlan0
[    2.751575] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[    2.755096] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    3.000213] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[    3.003183] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    3.018559] r8169 0000:03:00.0 enp3s0: link down
[    3.018638] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    3.100834] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready
[    6.239230] wlp5s0: authenticate with <MAC 'Speedy Remember Harambe' [AC1]>
[    6.247986] wlp5s0: send auth to <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[    6.257856] wlp5s0: authenticated
[    6.259761] wlp5s0: associate with <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[    6.289468] wlp5s0: RX AssocResp from <MAC 'Speedy Remember Harambe' [AC1]> (capab=0x411 status=0 aid=5)
[    6.291017] wlp5s0: associated
[    6.291059] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready
[   52.011763] wlp5s0: deauthenticating from <MAC 'Speedy Remember Harambe' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   52.594056] wlp5s0: authenticate with <MAC 'Speedy Remember Harambe' [AC1]>
[   52.599481] wlp5s0: send auth to <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[   52.606072] wlp5s0: authenticated
[   52.608587] wlp5s0: associate with <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[   52.641742] wlp5s0: RX AssocResp from <MAC 'Speedy Remember Harambe' [AC1]> (capab=0x411 status=0 aid=5)
[   52.644018] wlp5s0: associated
[  528.989209] wlp5s0: deauthenticated from <MAC 'Speedy Remember Harambe' [AC1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  529.069790] wlp5s0: authenticate with <MAC 'Speedy Remember Harambe' [AC1]>
[  529.076843] wlp5s0: send auth to <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[  529.082742] wlp5s0: authenticated
[  529.083129] wlp5s0: associate with <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[  529.110475] wlp5s0: RX AssocResp from <MAC 'Speedy Remember Harambe' [AC1]> (capab=0x411 status=0 aid=5)
[  529.112206] wlp5s0: associated
[  545.550689] wlp5s0: deauthenticating from <MAC 'Speedy Remember Harambe' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  548.104100] iwlwifi 0000:05:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[  548.328341] IPv6: ADDRCONF(NETDEV_UP): wlp5s0: link is not ready (repeated 2 times)
[  551.437879] wlp5s0: authenticate with <MAC 'Speedy Remember Harambe' [AC1]>
[  551.440982] wlp5s0: send auth to <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[  551.450629] wlp5s0: authenticated
[  551.451671] wlp5s0: associate with <MAC 'Speedy Remember Harambe' [AC1]> (try 1/3)
[  551.479023] wlp5s0: RX AssocResp from <MAC 'Speedy Remember Harambe' [AC1]> (capab=0x411 status=0 aid=5)
[  551.480794] wlp5s0: associated
[  551.480826] IPv6: ADDRCONF(NETDEV_CHANGE): wlp5s0: link becomes ready


########## wireless info END ############



```

---

### Post by wildmanne39 on 2017-01-31
First let's turn power management off:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Add the google nameservers 8.8.8.8 and 8.8.4.4) in "IPv4-settings" in the network-manager applet.

Right-click->Edit connections->choose your network name->Edit->IPv4-setings

Change to "Automatic (DHCP), addresses only" and add the nameservers like this 8.8.8.8,8.8.4.4 in the field "DNS-servers".

Then go into the IPV6 setting and set it to ignore.

Save settings then restart the network after that by doing:
```
sudo  systemctl restart NetworkManager.service
```
Now let's set your Country code:
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
Change the settings in the router. WPA2-AES (CCMP) is best; do not use WPA and WPA2 mixed mode unless you absolutely have too and do not use TKIP. Second, if your router is capable of N speeds, You may have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. Set a fixed channel, either 1, 6 or 11, rather than automatic channel selection, also while in the routers configuration settings remove the spaces from the network name. After making these changes, reboot the router.

Your channel is shown to be on 153 but that channel is not available.
Do:
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Reboot for good measure.

---

### Post by komali2 on 2017-01-31
Hey thanks for the help! I've done every step (we were already on WAP2-AES) and will be watching results tonight and tomorrow. One thing, I got ```
modprobe: FATAL: Module iwlwifi is in use.
``` when I did ```
[COLOR=#000000][FONT=&quot]sudo modprobe -rfv iwlwifi
```[/FONT][/COLOR]

---

### Post by wildmanne39 on 2017-01-31
I think you missed running this one first:
```
sudo modprobe -rfv iwldvm
```
Please start all over again on that set of commands and copy and paste for accuracy.
Thanks

---

### Post by fargoth on 2017-07-13
Did that fix your issue? I also experience a lot of connection drops with this card on my 17.04

---

