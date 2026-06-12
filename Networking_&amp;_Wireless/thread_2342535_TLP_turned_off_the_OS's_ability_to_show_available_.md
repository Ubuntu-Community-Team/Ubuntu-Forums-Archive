---
title: "TLP turned off the OS's ability to show available wireless connections"
date: 2016-11-07
forum: Networking &amp; Wireless
---

### Post by vikram91 on 2016-11-07
Hello I just installed tlp and when the battery got low, wifi was stopped. 
So I connected the power adapter. And I got the wifi back. 
Immediately I have changed the value of WIFI_PWR_ON_BAT to off in the tlp config. 
But I am no more able to see the list of available wifi connections. :(

I have attached the screenshot.

I faced this same issue on a different computer in older version of ubuntu. 

Any help would be appreciated. 

Thank you.

[SIZE=4][FONT=arial black]Edit[/FONT][/SIZE]: 

Wireless script output as requested:
```

########## wireless info START ##########

Report from: 08 Nov 2016 09:02 IST +0530

Booted last: 08 Nov 2016 00:00 IST +0530

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-45-generic #66-Ubuntu SMP Wed Oct 19 14:12:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller [1969:e0a1] (rev 10)
    Subsystem: Device [0707:2400]
    Kernel driver in use: alx

3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
mxm_wmi                16384  0
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
wmi                    20480  2 dell_wmi,mxm_wmi
video                  40960  2 i915_bpo,dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp59s0   Link encap:Ethernet  HWaddr <MAC 'enp59s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlp60s0   Link encap:Ethernet  HWaddr <MAC 'wlp60s0' [IF2]>  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::26f9:6ea3:164c:5baa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61941070 (61.9 MB)  TX bytes:2197836 (2.1 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp59s0   no wireless extensions.

wlp60s0   IEEE 802.11abgn  ESSID:"DIGISOL"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'DIGISOL' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    600    0        0 wlp60s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp60s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp60s0

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2965     1  0 08:58 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp60s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-45-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.2.0-00180-QCARMSWPZ-1
GENERAL.HWADDR:                         <MAC 'wlp60s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:3c:00.0/net/wlp60s0
GENERAL.IP-IFACE:                       wlp60s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     DIGISOL 1
GENERAL.CON-UUID:                       05c94bc0-c262-4839-992e-977ecdb25a1b
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   05c94bc0-c262-4839-992e-977ecdb25a1b | DIGISOL 1
IP4.ADDRESS[1]:                         192.168.2.6/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             223.196.100.100
IP4.DNS[2]:                             223.196.50.50
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1478599032
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.2.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.6
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = domain.name
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 7200
DHCP4.OPTION[23]:                       domain_name_servers = 223.196.100.100 223.196.50.50
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::26f9:6ea3:164c:5baa/64
IP6.GATEWAY:                            fe80::217:7cff:fe30:203
IP6.ROUTE[1]:                           dst = fe80::217:7cff:fe30:203/128, nh = ::, mt = 600

GENERAL.DEVICE:                         enp59s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Killer E2400 Gigabit Ethernet Controller
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp59s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3b:00.0/net/enp59s0
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
dlink-E67E                        <MAC 'dlink-E67E' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
Himalaya                          <MAC 'Himalaya' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
DIGISOL                           <MAC 'DIGISOL' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  73      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 
ForBroadband_SMS_Idea_9505450000  <MAC 'ForBroadband_SMS_Idea_9505450000' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  --           no        
--                                <MAC '--' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X  no        
TP-LINK_ACD2                      <MAC 'TP-LINK_ACD2' [AN6]>  Infra  6     2437 MHz  48 Mbit/s  34      &#9602;&#9604;__  WPA2         no        
vijay kalyan                      <MAC 'vijay kalyan' [AC4]>  Infra  3     2422 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
rohit                             <MAC 'rohit' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2    no        
Tenda_2C6A50                      <MAC 'Tenda_2C6A50' [AN9]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1         no        
DIRECT-J5-BRAVIA                  <MAC 'DIRECT-J5-BRAVIA' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
nln raju                          <MAC 'nln raju' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  WPA2         no        

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

[[/etc/NetworkManager/system-connections/DIGISOL]] (600 root)
[connection] id=DIGISOL | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp60s0' [IF2]> | mac-address-blacklist= | ssid=DIGISOL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIGISOL 1]] (600 root)
[connection] id=DIGISOL 1 | type=wifi | permissions=user:code_brah:;
[wifi] mac-address=<MAC 'wlp60s0' [IF2]> | mac-address-blacklist= | ssid=DIGISOL
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

enp59s0   no frequency information.

wlp60s0   32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp59s0   Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp60s0   Scan completed :
          Cell 01 - Address: <MAC 'DIGISOL' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"DIGISOL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000de44216d74
                    Extra: Last beacon: 40ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'dlink-E67E' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"dlink-E67E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b69cb38b46
                    Extra: Last beacon: 6360ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Himalaya' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Himalaya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001e9365488e
                    Extra: Last beacon: 5496ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'vijay kalyan' [AC4]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"vijay kalyan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005238e6c18e
                    Extra: Last beacon: 6116ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'rohit' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"rohit"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000369d5db518
                    Extra: Last beacon: 5920ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'KHAN' [AC6]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"KHAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000070d303917e
                    Extra: Last beacon: 6240ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'nln raju' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"nln raju"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ee5b83176
                    Extra: Last beacon: 5924ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Navya' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Navya"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000219be4e176
                    Extra: Last beacon: 5420ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
srcversion:     8CBDAC7980FC042032AE6A6
depends:        ath10k_core
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
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

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

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

[    2.546556] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[    2.548090] ath10k_pci 0000:3c:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[    2.786598] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[    2.786737] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[    2.786739] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[    4.364372] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready (repeated 2 times)
[    4.976474] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 (0x05030000, 0x00340aff sub 1a56:1535) fw WLAN.RM.2.0-00180-QCARMSWPZ-1 fwapi 4 bdapi 2 htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features wowlan,ignore-otp,no-4addr-pad
[    4.976494] ath10k_pci 0000:3c:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    5.044336] ath: EEPROM regdomain: 0x69
[    5.044338] ath: EEPROM indicates we should expect a direct regpair map
[    5.044340] ath: Country alpha2 being used: 00
[    5.044340] ath: Regpair used: 0x69
[    5.049603] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[    5.072477] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready (repeated 3 times)
[   11.825854] wlp60s0: authenticate with <MAC 'DIGISOL' [AC1]>
[   11.883671] wlp60s0: send auth to <MAC 'DIGISOL' [AC1]> (try 1/3)
[   11.885244] wlp60s0: authenticated
[   11.888879] wlp60s0: associate with <MAC 'DIGISOL' [AC1]> (try 1/3)
[   11.892872] wlp60s0: RX AssocResp from <MAC 'DIGISOL' [AC1]> (capab=0x411 status=0 aid=3)
[   11.896221] wlp60s0: associated
[   11.896261] IPv6: ADDRCONF(NETDEV_CHANGE): wlp60s0: link becomes ready

########## wireless info END ############


```

[SIZE=4]**Edit2**[/SIZE]: 
Problem unrelated to TLP.
Solved by disabling the automatic login in /etc/lightdm/lightdm.conf by commenting out autologin-user=blankand autologin-user-timeout=0

---

### Post by jeremy31 on 2016-11-07
See the wireless script link in my signature and post results.  I would suspect another power management issue is also occurring

---

### Post by vikram91 on 2016-11-08
> **jeremy31 said:**
> See the wireless script link in my signature and post results.  I would suspect another power management issue is also occurring

Hello, I have included the wireless script output in the first post and also here: [http://pastebin.com/xcm7YA8w](http://pastebin.com/xcm7YA8w)

I have tried using this command:  ```
sudo systemctl restart NetworkManager.service
``` 

It works. But after restarting pc, the problem appears again.

---

### Post by jeremy31 on 2016-11-08
Results are what I expected, iwconfig shows power management on
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

Then restart the network manager service

---

### Post by vikram91 on 2016-11-08
Did that and restarted the PC. Still have the issue.

---

### Post by jeremy31 on 2016-11-08
Might have to disable TLP for wireless
[http://linrunner.de/en/tlp/docs/tlp-configuration.html#networking](http://linrunner.de/en/tlp/docs/tlp-configuration.html#networking)

Says power save can cause unstable wifi link

---

### Post by vikram91 on 2016-11-08
That is the first thing I did. I set WIFI_PWR_ON_BAT to off after facing the issue.

Edit: Removed the tlp and still have the issue. Guess I would have to reinstall Ubuntu

---

### Post by jeremy31 on 2016-11-08
I wonder if "off" is still correct as linrunner posted [http://askubuntu.com/a/546469/300665](http://askubuntu.com/a/546469/300665)
It may need to be ```
WIFI_PWR_ON_BAT=1 
```

EDIT: didn't see your edit about removing TLP

---

### Post by vikram91 on 2016-11-08
Still have the issue after freshly installing Ubuntu. Not sure what's going on.

Just checked this after a reboot:

```
sudo service network-manager status
&#9679; NetworkManager.service - Network Manager
   Loaded: loaded (/lib/systemd/system/NetworkManager.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-11-08 19:35:28 IST; 8min ago
 Main PID: 3061 (NetworkManager)
   CGroup: /system.slice/NetworkManager.service
           &#9500;&#9472;3061 /usr/sbin/NetworkManager --no-daemon
           &#9500;&#9472;3972 /sbin/dhclient -d -q -sf /usr/lib/NetworkManager/nm-dhcp-helper -pf /var/run/dhclient-wlp60s0.pid -lf /var/lib/NetworkManager/dhclient-26af9d6b-7a28-4114-b6a2-16fcb8c30403-wlp60s0.lease 
           &#9500;&#9472;3983 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --proxy-dnssec --
           &#9500;&#9472;5266 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --proxy-dnssec --
           &#9492;&#9472;5277 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --proxy-dnssec --

Nov 08 19:35:40 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 1030ms.
Nov 08 19:35:41 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 2030ms.
Nov 08 19:35:43 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 4110ms.
Nov 08 19:35:47 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 8180ms.
Nov 08 19:35:55 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 16300ms.
Nov 08 19:36:11 Alienware dhclient[4131]: XMT: Info-Request on wlp60s0, interval 33670ms.
Nov 08 19:36:24 Alienware NetworkManager[3061]: <warn>  [1478613984.6599] dhcp6 (wlp60s0): request timed out
Nov 08 19:36:24 Alienware NetworkManager[3061]: <info>  [1478613984.6600] dhcp6 (wlp60s0): state changed unknown -> timeout
Nov 08 19:36:24 Alienware NetworkManager[3061]: <info>  [1478613984.6607] dhcp6 (wlp60s0): canceled DHCP transaction, DHCP client pid 4131
Nov 08 19:36:24 Alienware NetworkManager[3061]: <info>  [1478613984.6607] dhcp6 (wlp60s0): state changed timeout -> done
lines 1-21/21 (END)



```

So why does restarting the service fixes the issue if it is already running? Is there a way to check? or is this an issue caused by using generic driver instead of vendor specific driver for my Killer 1535 which is notoriously known for causing wifi issues in many other laptops?

Or instead can I just set a script or something to run this command to restart network-manager at every boot without me having to type it every boot?

---

### Post by jeremy31 on 2016-11-08
Try the command from post 4 again then restart the networking service.

The drivers in the kernel are maintained by Qualcomm employees so only time can make them better.

Did you install updates when you reinstalled Ubuntu?

---

### Post by vikram91 on 2016-11-08
I noticed when I tried to logout and login using password for switching the intel card to Nvidia card, the issue fixed itself. Then I remembered that I set it to login automatically during installation and I wasn't logging in at every boot. So I just disabled the automatic login by commenting out the last two lines of /etc/lightdm/lightdm.conf and the issue fixed itself. What a weird fix!

```

[Seat:*]autologin-guest=false
#autologin-user=code_brah
#autologin-user-timeout=0
```

---

