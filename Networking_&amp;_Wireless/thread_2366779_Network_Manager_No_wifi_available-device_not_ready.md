---
title: "Network Manager No wifi available-device not ready"
date: 2017-07-21
forum: Networking &amp; Wireless
---

### Post by brewski-59 on 2017-07-21
Normally I will search the forums and find a solution but this time I'm not so lucky.
After I updated I notice that network manager will be connected to a wireless AP on start up then moments later it will disconnect and NM will show device not ready.
wireless info.txt below
```

########## wireless info START ##########

Report from: 21 Jul 2017 11:28 AKDT -0800

Booted last: 21 Jul 2017 00:00 AKDT -0800

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:31:03 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Limited BCM4321 802.11a/b/g/n [14e4:4328] (rev 01)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-Card [1028:0009]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 003: ID 1058:0810 Western Digital Technologies, Inc. My Passport Ultra (WDBZFP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dell_smbios            16384  2 dell_wmi,dell_laptop
ssb                    57344  1 b44
wl                   6209536  0
cfg80211              532480  1 wl
wmi                    16384  1 dell_wmi
video                  40960  2 dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.102  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::71e0:f5b7:3f7d:d2d3  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 77783  bytes 108419998 (108.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 76432  bytes 6622082 (6.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 432  bytes 30820 (30.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 432  bytes 30820 (30.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 45  bytes 15343 (15.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 265832
        TX packets 127  bytes 17483 (17.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  base 0xc000  

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       772     1  0 09:36 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6400)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       9621cc0a-0408-3a87-8ed5-88fb1e04770a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9621cc0a-0408-3a87-8ed5-88fb1e04770a | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.102/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1500671874
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.102
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::71e0:f5b7:3f7d:d2d3/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-Card)
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         10 (802.1X supplicant failed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/net/wlan0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Armadillo]] (600 root)
[connection] id=Armadillo | type=802-11-wireless
[802-11-wireless] ssid=Armadillo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Aardvark]] (600 root)
[connection] id=Aardvark | type=802-11-wireless
[802-11-wireless] ssid=Aardvark | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vanilla]] (600 root)
[connection] id=Vanilla | type=802-11-wireless
[802-11-wireless] ssid=Vanilla | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Anchorage (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      7   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:5.765 GHz
      2   APs on   Frequency:5.785 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR01' [AC1]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Armadillo' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Armadillo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'NETGEAR36-5G' [AC3]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR36-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'NETGEAR65-5G' [AC4]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR65-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'belkin.5b4.media' [AC5]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"belkin.5b4.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FBI surveillance van #1.media' [AC6]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"FBI surveillance van #1.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Virus Infected Wi-Fi' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Virus Infected Wi-Fi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Cisco37705' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Cisco37705"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'belkin.f4a' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"belkin.f4a"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'belkin.5b4' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"belkin.5b4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'belkin.5b4.guests' [AC11]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"belkin.5b4.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
          Cell 12 - Address: <MAC 'belkin.b00' [AC12]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"belkin.b00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Vanilla' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Vanilla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 25344ms ago
          Cell 14 - Address: <MAC 'NETGEAR36' [AC14]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR36"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'NETGEAR65' [AC15]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR65"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'Borincano' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Borincano"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'FBI surveillance van #1' [AC17]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"FBI surveillance van #1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'Mainframe' [AC18]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Mainframe"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'belkin.3cd' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"belkin.3cd"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'belkin.b00.5GHz' [AC20]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"belkin.b00.5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'SigSauer' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"SigSauer"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'belkin.e3a.guests' [AC22]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"belkin.e3a.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
          Cell 23 - Address: <MAC 'NETGEAR24' [AC23]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'Buckwild' [AC24]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Buckwild"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'Johns Room.b' [AC25]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"Johns Room.b"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12136ms ago
          Cell 26 - Address: <MAC 'Vanilla' [AC26]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Vanilla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 25344ms ago
          Cell 27 - Address: <MAC 'Vanilla' [AC27]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Vanilla"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 25344ms ago
          Cell 28 - Address: <MAC '' [AC28]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12136ms ago

##### module infos ######################

[ssb]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[wl]
filename:       /lib/modules/4.10.0-28-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     23E3E484987ACB03940A990
depends:        cfg80211
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma
blacklist b44
install wl modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install wl ; modprobe --ignore-install b44

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
# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4328 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 6735.450203] ERROR @wl_dev_intvar_get : 

########## wireless info END ############


```

---

### Post by Hadaka on 2017-07-21
Hi, you have a few things that are causing you "issues"
The most glaring is your wifi driver ,it is not correct for the type
of card you have.
```
* Ethernet Broadcom pci-id [14e4:170c] b44 <- correct 
* Wireless Broadcom pci-id [14e4:4328] wl **[COLOR=#ff0000]<- [/COLOR]**'ERROR'
```
*To correct, With a working wired connection or you can use this..
*USB device 0x:0x (r8712u)-Your usb wireless,--wired is prefered
please open a terminal then COPY and paste one line at a time .
*Ignore any file not found response..do every line.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe b43
```
##### iw reg get ########################
Region: America/Anchorage (based on set time zone)
country 00: DFS-UNSET **[COLOR=#ff0000]<-[/COLOR]** "UNSET,causes drops"
*To correct..
```
sudo iw reg set US
sudo sed -i 's/=.*/=US/' /etc/default/crda
```
*To clear "wl" from udev rules..it rewrites on boot
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
*Lastly you can have one or the other not both...CHOOSE
##### network managers ##################
Installed:
    NetworkManager
    Wicd

Remove wired connection,and any usb,boot and test wireless
Thanks

---

### Post by brewski-59 on 2017-07-22
I've implemented the changes you outlined.  As of now I'm connected on wireless only but if I attempt to use wireless and wired together it will drop and revert to device not ready.  This is the longest its held so I assume it may have issues with being connected to wire and drop wireless.
  also although I have uninstalled WICD using the instructions here [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD).  it still shows as installed on the report.
```

########## wireless info START ##########

Report from: 21 Jul 2017 20:25 AKDT -0800

Booted last: 21 Jul 2017 00:00 AKDT -0800

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-28-generic #32-Ubuntu SMP Fri Jun 30 05:31:03 UTC 2017 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Ethernet controller [0200]: Broadcom Limited BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Inspiron 6400 [1028:01af]
    Kernel driver in use: b44

0b:00.0 Network controller [0280]: Broadcom Limited BCM4321 802.11a/b/g/n [14e4:4328] (rev 01)
    Subsystem: Dell Wireless 1500 Draft 802.11n WLAN Mini-Card [1028:0009]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 001 Device 003: ID 1058:0810 Western Digital Technologies, Inc. My Passport Ultra (WDBZFP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_laptop            20480  0
dell_smbios            16384  2 dell_wmi,dell_laptop
b43                   397312  0
bcma                   53248  1 b43
mac80211              700416  1 b43
cfg80211              532480  2 b43,mac80211
ssb_hcd                16384  0
video                  40960  2 dell_wmi,dell_laptop
wmi                    16384  1 dell_wmi
ssb                    57344  3 b43,ssb_hcd,b44

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 569  bytes 353049 (353.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 577  bytes 100119 (100.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 394  bytes 28206 (28.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 394  bytes 28206 (28.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.100  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::216:cfff:feb5:ce6d  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 490  bytes 466941 (466.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 565  bytes 71485 (71.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11  ESSID:"Armadillo"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Armadillo' [AN1]>   
          Bit Rate=48 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:27  Invalid misc:84   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       775     1  0 20:23 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4321 802.11a/b/g/n (Wireless 1500 Draft 802.11n WLAN Mini-Card)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.10.0-28-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:0b:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Armadillo
GENERAL.CON-UUID:                       f4c43c52-7074-4700-aad5-c2ac8e706caf
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4c43c52-7074-4700-aad5-c2ac8e706caf | Armadillo
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   31f2ab66-71a1-4dcd-8436-f6dda9251092 | Vanilla
IP4.ADDRESS[1]:                         192.168.0.100/24
IP4.GATEWAY:                            192.168.0.1
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1500704632
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.100
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::216:cfff:feb5:ce6d/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Limited
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (Inspiron 6400)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0/net/eth0
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

SSID                           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Armadillo                      <MAC 'Armadillo' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
belkin.5b4                     <MAC 'belkin.5b4' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
belkin.b00                     <MAC 'belkin.b00' [AN3]>  Infra  5     2432 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
NETGEAR01                      <MAC 'NETGEAR01' [AN4]>  Infra  4     2427 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
Virus Infected Wi-Fi           <MAC 'Virus Infected Wi-Fi' [AN5]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
belkin.5b4.media               <MAC 'belkin.5b4.media' [AN6]>  Infra  157   5785 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
belkin.5b4.guests              <MAC 'belkin.5b4.guests' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  --         no        
NETGEAR65                      <MAC 'NETGEAR65' [AN8]>  Infra  9     2452 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2       no        
FBI surveillance van #1        <MAC 'FBI surveillance van #1' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
NETGEAR65-5G                   <MAC 'NETGEAR65-5G' [AN10]>  Infra  153   5765 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA2       no        
NETGEAR36                      <MAC 'NETGEAR36' [AN11]>  Infra  8     2447 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2       no        
belkin.3cd                     <MAC 'belkin.3cd' [AN12]>  Infra  11    2462 MHz  54 Mbit/s  55      &#9602;&#9604;__  WPA2       no        
FBI surveillance van #1.media  <MAC 'FBI surveillance van #1.media' [AN13]>  Infra  157   5785 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
belkin.e3a.guests              <MAC 'belkin.e3a.guests' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  --         no        
NETGEAR36-5G                   <MAC 'NETGEAR36-5G' [AN15]>  Infra  153   5765 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
Cisco37705                     <MAC 'Cisco37705' [AN16]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        
belkin.b00.5GHz                <MAC 'belkin.b00.5GHz' [AN17]>  Infra  153   5765 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2  no        
Vanilla                        <MAC 'Vanilla' [AN18]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WEP        no        
Monkey                         <MAC 'Monkey' [AN19]>  Infra  1     2412 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2       no        
belkin.f4a                     <MAC 'belkin.f4a' [AN20]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2       no        
Mainframe                      <MAC 'Mainframe' [AN21]>  Infra  7     2442 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
Buckwild                       <MAC 'Buckwild' [AN22]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
--                             <MAC '--' [AN23]>  Infra  1     2412 MHz  54 Mbit/s  32      &#9602;&#9604;__  --         no        
CIA SPY NETWORK-guest          <MAC 'CIA SPY NETWORK-guest' [AN24]>  Infra  9     2452 MHz  54 Mbit/s  32      &#9602;&#9604;__  --         no        
dlink-5C36                     <MAC 'dlink-5C36' [AN25]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
belkin.616                     <MAC 'belkin.616' [AN26]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        
CIA SPY NETWORK 2              <MAC 'CIA SPY NETWORK 2' [AN27]>  Infra  9     2452 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
belkin.1ca.guests              <MAC 'belkin.1ca.guests' [AN28]>  Infra  10    2457 MHz  54 Mbit/s  29      &#9602;___  --         no        
rustnbone                      <MAC 'rustnbone' [AN29]>  Infra  36    5180 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2  no        
belkin.60e                     <MAC 'belkin.60e' [AN30]>  Infra  2     2417 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
belkin.1ca                     <MAC 'belkin.1ca' [AN31]>  Infra  10    2457 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
Stormywalker                   <MAC 'Stormywalker' [AN32]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        

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

##### NetworkManager profiles ###########

sudo: unable to resolve host Avocado: Resource temporarily unavailable
[[/etc/NetworkManager/system-connections/Armadillo]] (600 root)
[connection] id=Armadillo | type=802-11-wireless
[802-11-wireless] ssid=Armadillo | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Aardvark]] (600 root)
[connection] id=Aardvark | type=802-11-wireless
[802-11-wireless] ssid=Aardvark | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vanilla]] (600 root)
[connection] id=Vanilla | type=802-11-wireless
[802-11-wireless] ssid=Vanilla | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Anchorage (based on set time zone)

global
country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
    (5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Current Frequency=2.462 GHz (Channel 11)

##### iwlist scan #######################

sudo: unable to resolve host Avocado: Resource temporarily unavailable
wlan0     Failed to read scan data : Resource temporarily unavailable

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/net/wireless/broadcom/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     5F955FFEA61C80144A2B433
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C645ADA4C8790A787B7C8E9
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[mac80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-28-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb_hcd]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/usb/host/ssb-hcd.ko
license:        GPL
description:    Common USB driver for SSB Bus
author:         Hauke Mehrtens
srcversion:     E000CFD45A5498EED47EBDD
depends:        ssb
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

[ssb]
filename:       /lib/modules/4.10.0-28-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     38B7A1BE5CF467C3CF164D5
depends:        
intree:         Y
vermagic:       4.10.0-28-generic SMP mod_unload 686 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

lp

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

[   32.342768] b43-phy0: Broadcom 4321 WLAN found (core revision 11)
[   32.390640] b43-phy0: Found PHY: Analog 5, Type 4 (N), Revision 1
[   32.390652] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2055, Revision 4, Version 0
[   39.457621] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   39.466598] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.644082] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   39.824509] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.064071] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   40.244102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   42.816194] b44 ssb1:0 eth0: Link is up at 100 Mbps, full duplex
[   42.816197] b44 ssb1:0 eth0: Flow control is off for TX and off for RX
[   42.816540] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   47.556474] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   47.744110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   47.836793] wlan0: authenticate with <MAC 'Armadillo' [AN1]>
[   47.864227] wlan0: send auth to <MAC 'Armadillo' [AN1]> (try 1/3)
[   47.866133] wlan0: authenticated
[   47.868032] wlan0: associate with <MAC 'Armadillo' [AN1]> (try 1/3)
[   47.870759] wlan0: RX AssocResp from <MAC 'Armadillo' [AN1]> (capab=0x431 status=0 aid=1)
[   47.871223] wlan0: associated
[   47.871273] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  102.816135] b44 ssb1:0 eth0: Link is down
[  105.639266] b44 ssb1:0 eth0: powering down PHY
[  105.649254] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

########## wireless info END ############


```

---

### Post by brewski-59 on 2017-07-22
Strange
When I disconnected from Armadillo to attempted to connect to Vanilla It dropped wireless and went back to device not ready.

CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f4c43c52-7074-4700-aad5-c2ac8e706caf | Armadillo
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   31f2ab66-71a1-4dcd-8436-f6dda9251092 | Vanilla

---

### Post by Hadaka on 2017-07-22
Hi, if you do..
```
lsmod
```
The result printout are the loaded modules.
Please note that b44 and b43 share module ssb
This means you can use wired..or wireless not both.
*Shared ssb module...
```
   *  ssb    57344  3 b43,ssb_hcd,b44
```
Next is the configuration of the wireless Armadillo access point connection.

Armadillo  <MAC 'Armadillo' [AN1]> Infra 11 2462 MHz  54 Mbit/s 100  &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2 **[COLOR=#ff0000]<-[/COLOR]**   yes *

mixed mode of wpa1 and wpa2 is not correct for your broadcom wifi card and Ubuntu linux.
Please access your router settings and change to WPA2 AES CCMP....NO tkip.

The "Vanilla" connection is wep..and a signal strength of 47..so not that close to your computer..

'Vanilla' [AN18]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WEP        no

Please access your router settings and verify your settings are correct.
Your computer is doing excatly what is is suppose to do, and other than the mixed mode of wpa1 and wpa2
needing to be changed. and complete removal of WICD I have no further suggestions.\
thanks.

---

