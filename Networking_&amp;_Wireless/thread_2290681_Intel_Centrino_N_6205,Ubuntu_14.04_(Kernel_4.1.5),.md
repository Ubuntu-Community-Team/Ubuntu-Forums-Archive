---
title: "Intel Centrino N 6205,Ubuntu 14.04 (Kernel 4.1.5), rly slow"
date: 2015-08-14
forum: Networking &amp; Wireless
---

### Post by peterpan6 on 2015-08-14
Hey Guys,
when i use my Ubuntu i only have 81Mbits Downlink to my FritzBox.
With windows i have always 300Mbits
Tried to update to the newest Kernel (4.1.5) allthough i am using Ubuntu 15.04 but still slow.

Tried also to update my iwlwifi manually but seems i allready have the newest driver?!

Here is the the output of the script:
```

########## wireless info START ##########

Report from: 14 Aug 2015 14:06 CEST +0200

Booted last: 14 Aug 2015 16:04 CEST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 4.1.5-040105-generic #201508101730 SMP Mon Aug 10 21:31:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 04f2:b2da Chicony Electronics Co., Ltd 
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0bdb:1926 Ericsson Business Mobile Networks BV 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_wwan_sw: Wireless WAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                237568  0 
mac80211              745472  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              552960  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f1500000-f1520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.178.23  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1975 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1905 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1199964 (1.1 MB)  TX bytes:448480 (448.4 KB)

wwan0     Link encap:Ethernet  HWaddr <MAC 'wwan0' [IF]>  
          BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

wwan0     no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Fritz 5"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: <MAC 'Fritz 5' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:55   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.2   0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root       679     1  0 14:04 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6205 [Taylor Peak] (Centrino Advanced-N 6205 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.1.5-040105-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Fritz 5
GENERAL.CON-UUID:                       2656ce3f-ca13-4ceb-af52-709f9f412788
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2656ce3f-ca13-4ceb-af52-709f9f412788 | Fritz 5
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   54060fc3-98d6-4e9b-a575-b5dc768567ad | Fritz
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.178.23/24, gw = 192.168.178.2
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.2
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.2
DHCP4.OPTION[5]:                        ip_address = 192.168.178.23
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.2
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.2
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1440417889
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.2
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.2
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579LM Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 2.3.2-k
GENERAL.FIRMWARE-VERSION:               0.13-3
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

GENERAL.DEVICE:                         ttyACM1
GENERAL.TYPE:                           gsm
GENERAL.VENDOR:                         Lenovo
GENERAL.PRODUCT:                        H5321 gw
GENERAL.DRIVER:                         cdc_acm, cdc_mbim, cdc_wdm
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                     BSSID              MODE    CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Fritz                    <MAC 'Fritz' [AC12]>  Infra   13    2472 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
FRITZ!Box Fon WLAN 7112  <MAC 'FRITZ!Box Fon WLAN 7112' [AC6]>  Infra   6     2437 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Fritz 2                  <MAC 'Fritz 2' [AC3]>  Infra   1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2       no        
WLAN-607171              <MAC 'WLAN-607171' [AC13]>  Infra   100   5500 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        
WLAN-607171              <MAC 'WLAN-607171' [AC2]>  Infra   1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
ALICE-WLAN63             <MAC 'ALICE-WLAN63' [AC5]>  Infra   4     2427 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
o2-WLAN30                <MAC 'o2-WLAN30' [AN7]>  Infra   2     2417 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
FRITZ!Box 7362 SL        <MAC 'FRITZ!Box 7362 SL' [AC4]>  Infra   1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
o2-WLAN77                <MAC 'o2-WLAN77' [AC10]>  Infra   9     2452 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
ALICE-WLAN45             <MAC 'ALICE-WLAN45' [AC9]>  Infra   8     2447 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
WLAN-809226              <MAC 'WLAN-809226' [AN11]>  Infra   1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
Telekom_FON              <MAC 'Telekom_FON' [AN12]>  Infra   1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --         no        
HP100-13601d             <MAC 'HP100-13601d' [AC7]>  Ad-Hoc  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  --         no        
Fritz 5                  <MAC 'Fritz 5' [AC1]>  Infra   36    5180 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2       yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:home:;
[wifi] ssid=eduroam
[ipv4] method=auto
[ipv6] method=ignore
[802-1x] ca-cert=/home/home/.eduroam/ca.pem

[[/etc/NetworkManager/system-connections/AV]] (600 root)
[connection] id=AV | type=wifi
[wifi] ssid=AV | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/burg]] (600 root)
[connection] id=burg | type=wifi
[wifi] ssid=burg | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fritz 5]] (600 root)
[connection] id=Fritz 5 | type=wifi
[wifi] ssid=Fritz 5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC2595729]] (600 root)
[connection] id=UPC2595729 | type=wifi
[wifi] ssid=UPC2595729 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fritz]] (600 root)
[connection] id=Fritz | type=wifi
[wifi] ssid=Fritz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Toiletten-HotSpot]] (600 root)
[connection] id=Toiletten-HotSpot | type=wifi
[wifi] ssid=Toiletten-HotSpot | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 40), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), (0 ms), DFS
    (57240 - 65880 @ 2160), (N/A, 40), (N/A), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

wwan0     no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.472 GHz (Channel 13)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Fritz 5' [AC1]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Fritz 5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000cbc7357d
                    Extra: Last beacon: 128ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WLAN-607171' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"WLAN-607171"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037b25d6ed3
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Fritz 2' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Fritz 2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000d191a3c9
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'FRITZ!Box 7362 SL' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box 7362 SL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000853761a4c48
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ALICE-WLAN63' [AC5]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000085371317e84
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FRITZ!Box Fon WLAN 7112' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7112"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000014a5ff0e9
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HP100-13601d' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"HP100-13601d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000143207b3b5
                    Extra: Last beacon: 36ms ago
          Cell 08 - Address: <MAC 'WLAN-713D53' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"WLAN-713D53"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c16090191
                    Extra: Last beacon: 4524ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'ALICE-WLAN45' [AC9]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a3611bf5c8
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'o2-WLAN77' [AC10]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN77"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000043e9ebf4df6
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 11 - Address: <MAC 'FRITZ!Box o2 DSL' [AC11]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box o2 DSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000011841fee
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Fritz' [AC12]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Fritz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f16ff71f9c
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'WLAN-607171' [AC13]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"WLAN-607171"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000037b25ca316
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     4F1B8CE3D3FB07439A2911D
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.1.5-040105-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     74E30AABABDE7CAEA5C2EFE
depends:        cfg80211
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.1.5-040105-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     1D3A82817350FFD5F07F830
depends:        cfg80211
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
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
filename:       /lib/modules/4.1.5-040105-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A34537645016AD6A2B4091
depends:        
intree:         Y
vermagic:       4.1.5-040105-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        46:FD:0F:30:F3:BD:8F:14:68:03:E9:82:17:7A:AC:2D:07:7A:89:9C
sig_hashalgo:   sha512
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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    3.534259] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.555822] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.595625] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.595628] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.595630] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.595631] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    3.595744] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    3.625878] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.665827] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    7.305987] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    7.313029] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[    7.584607] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    7.591655] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   10.819926] wlan0: authenticate with <MAC 'Fritz 5' [AC1]>
[   10.822944] wlan0: send auth to <MAC 'Fritz 5' [AC1]> (try 1/3)
[   10.890464] wlan0: authenticated
[   10.893640] wlan0: associate with <MAC 'Fritz 5' [AC1]> (try 1/3)
[   10.897470] wlan0: RX AssocResp from <MAC 'Fritz 5' [AC1]> (capab=0x411 status=0 aid=1)
[   10.900657] wlan0: associated
[   10.991187] wlan0: Limiting TX power to 23 (23 - 0) dBm as advertised by <MAC 'Fritz 5' [AC1]>

########## wireless info END ############


```

Hope you can help me guys ;-)
Really frustrating when i want to work with my  NAS.

---

### Post by jeremy31 on 2015-08-14
You might just need to set the parameter to get better 11n performance
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
Reboot

---

### Post by peterpan6 on 2015-08-14
No sry, didn't help. Still only 81 Mbits

---

### Post by weatherman2 on 2015-08-14
Where are you seeing 300Mbps and 81Mbps?  Is that coming from your router?

---

### Post by jeremy31 on 2015-08-15
See if turning off power management for the wifi card helps```
sudo iwconfig wlan0 power off
```

---

### Post by peterpan6 on 2015-08-15
> **weatherman2 said:**
> Where are you seeing 300Mbps and 81Mbps?  Is that coming from your router?

I see that it is very slowly when i copy something to my NAS and i also look it up in my FritzBox.

> **jeremy31 said:**
> See if turning off power management for the wifi card helps 

actually it helped for like 10 minutes. i had 240 Mbits for a short time. then i checked it again and it changed back to 81 Mbits.

---

### Post by weatherman2 on 2015-08-15
Well, you aren't going to get sustained 300Mbps when copying files to your NAS, anyway.  300Mbps is a theoretical maximum which few people get with any OS.  And just because the connection rate is briefly reported as 300Mbps or 240Mbps doesn't mean it's going to stay that way for long.  Because WiFi is radio, it's not immune to interference and other atmospheric disturbances.

You need to compare apples to apples.  First, look at your router status, if possible, and see what connection speed it shows - over several minutes with both Windows and with Ubuntu.

Next, try copying a large file over to your NAS with Windows, several times, and find a reliable way to measure the real transfer rate.  Do it several times, then average the times.

Do the same thing with Ubuntu.  Try to ignore the "immediate status" showing connection speeds at that second - you need an average for the entire time the file is being transferred.

And make sure you perform the tests in the same conditions.  If you are 20 feet from your router when doing the Windows tests, make sure you are also 20 feet from your router when doing the Ubuntu tests.

---

