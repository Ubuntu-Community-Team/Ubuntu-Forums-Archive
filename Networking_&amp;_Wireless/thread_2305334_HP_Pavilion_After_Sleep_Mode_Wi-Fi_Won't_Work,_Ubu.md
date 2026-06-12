---
title: "HP Pavilion After Sleep Mode Wi-Fi Won't Work, Ubuntu 15.04"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by apalm112 on 2015-12-04
Hi,

I have an HP Pavilion Intel Core i3-5010U, partitioned with Windows 10 & Ubuntu 15.04.  The WiFi works, until awakened from sleep mode, then it will not connect to WiFi.  It's been this way since Ubuntu was installed, originally installed Ubuntu 14 but upgraded to 15.04 recently.  I've followed the advice given on a few similar posts of this type of problem and have had no success in fixing it.  Such as sudo killall wpa_supplicant, sudo service network-manager restart, sudo chmod +x /etc/pm/config.d/config, etc..

The drop down menu for the wifi icon in the browser toolbar says 'Wi-Fi is disabled by hardware switch' after awakening from sleep mode.

I've only been using Ubuntu for a few months & any help is greatly appreciated!


```




########## wireless info START ##########


Report from: 04 Dec 2015 16:05 PST -0800


Booted last: 04 Dec 2015 07:56 PST -0800


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.16.0-51-generic #69~14.04.1-Ubuntu SMP Wed Oct 7 15:32:41 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


08:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi


09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:8093]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0eef:c04d D-WAV Scientific Co., Ltd 
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 064e:930a Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                217725  0 
mac80211              652777  1 iwlmvm
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
iwlwifi               179412  1 iwlmvm
cfg80211              498458  3 iwlwifi,mac80211,iwlmvm
wmi                    19193  1 hp_wmi


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


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 2601:601:300:e700:ac42:de59:2a45:e4fb/64 Scope:Global
          inet6 addr: 2601:601:300:e700:<IP6 'wlan0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2342 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:829447 (829.4 KB)  TX bytes:373306 (373.3 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Freedom_Slap"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Freedom_Slap' [AC1]>   
          Bit Rate=58.5 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:76   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    400    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     400    0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search hsd1.wa.comcast.net


##### network managers ##################


Installed:


    NetworkManager


Running:


root       750     1  0 15:58 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.16.0-51-generic
GENERAL.FIRMWARE-VERSION:               25.228.9.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Freedom_Slap
GENERAL.CON-UUID:                       15bb5860-672b-42bd-9f69-71d081af3b39
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     58 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   15bb5860-672b-42bd-9f69-71d081af3b39 | Freedom_Slap
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.15/24, gw = 192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.wa.comcast.net.
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 192.168.0.15
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = hsd1.wa.comcast.net.
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1449359873
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       next_server = 192.168.0.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
DHCP4.OPTION[32]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         ip = 2601:601:300:e700:ac42:de59:2a45:e4fb/64, gw = fe80::a62b:8cff:feb8:b33a
IP6.ADDRESS[2]:                         ip = 2601:601:300:e700:<IP6 'wlan0' [IF]>/64, gw = fe80::a62b:8cff:feb8:b33a
IP6.ADDRESS[3]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = fe80::a62b:8cff:feb8:b33a
IP6.ROUTE[1]:                           dst = 2601:601:300:e700::/60, nh = fe80::a62b:8cff:feb8:b33a, mt = 400
IP6.ROUTE[2]:                           dst = 2601:601:300:e700::/64, nh = ::, mt = 400
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_server_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[7]:                        dhcp6_client_id = 0:4:8c:d8:86:6b:12:1d:a6:de:ca:b:31:3:9a:14:4d:a2


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eth0
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


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR73-5G   <MAC 'NETGEAR73-5G' [AC28]>  Infra  153   5765 MHz  54 Mbit/s  95      â–‚â–„â–†â–ˆ  WPA2       no        
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC26]>  Infra  11    2462 MHz  54 Mbit/s  44      â–‚â–„__  WPA2       no        
HOME-A92D      <MAC 'HOME-A92D' [AC24]>  Infra  11    2462 MHz  54 Mbit/s  40      â–‚â–„__  WPA2       no        
--             <MAC '' [AC22]>  Infra  11    2462 MHz  54 Mbit/s  32      â–‚â–„__  WPA2       no        
--             <MAC '' [AC23]>  Infra  11    2462 MHz  54 Mbit/s  32      â–‚â–„__  WPA1 WPA2  no        
--             <MAC '--' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  32      â–‚â–„__  WPA1 WPA2  no        
HOME-2922      <MAC 'HOME-2922' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  30      â–‚___  WPA1 WPA2  no        
--             <MAC '--' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  30      â–‚___  WPA2       no        
DeadZone       <MAC 'DeadZone' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  29      â–‚___  WPA1 WPA2  no        
HOME-04E2      <MAC 'HOME-04E2' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  27      â–‚___  WPA1 WPA2  no        
HOME-00B4      <MAC 'HOME-00B4' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  25      â–‚___  WPA1 WPA2  no        
Boone123       <MAC 'Boone123' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  25      â–‚___  WPA2       no        
Tran           <MAC 'Tran' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  24      â–‚___  WPA1 WPA2  no        
HOME-37C4-2.4  <MAC 'HOME-37C4-2.4' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  20      â–‚___  WPA1 WPA2  no        
PewPewPew      <MAC 'PewPewPew' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  17      â–‚___  WPA2       no        
--             <MAC '--' [AN16]>  Infra  6     2437 MHz  54 Mbit/s  17      â–‚___  WPA2       no        
ASUS           <MAC 'ASUS' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  44      â–‚â–„__  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AC25]>  Infra  11    2462 MHz  54 Mbit/s  40      â–‚â–„__  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AC21]>  Infra  11    2462 MHz  54 Mbit/s  30      â–‚___  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  27      â–‚___  --         no        
xfinitywifi    <MAC 'xfinitywifi' [AN21]>  Infra  1     2412 MHz  54 Mbit/s  25      â–‚___  --         no        
Freedom_Slap   <MAC 'Freedom_Slap' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  69      â–‚â–„â–†_  WPA2       yes     * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/bing]] (600 root)
[connection] id=bing | type=802-11-wireless
[802-11-wireless] ssid=bing | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Code Fellows Guest]] (600 root)
[connection] id=Code Fellows Guest | type=802-11-wireless
[802-11-wireless] ssid=Code Fellows Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Freedom_Slap]] (600 root)
[connection] id=Freedom_Slap | type=wifi
[wifi] ssid=Freedom_Slap | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Code Fellows]] (600 root)
[connection] id=Code Fellows | type=802-11-wireless
[802-11-wireless] ssid=Code Fellows | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      10   APs on   Frequency:2.412 GHz (Channel 1)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      12   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.745 GHz
      1   APs on   Frequency:5.765 GHz


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Freedom_Slap' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Freedom_Slap"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004124479ae
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'xfinitywifi' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004e953b0142
                    Extra: Last beacon: 5616ms ago
          Cell 03 - Address: <MAC 'HOME-04E2' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-04E2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000091eaf9716a
                    Extra: Last beacon: 5616ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000091eaf97bc4
                    Extra: Last beacon: 5616ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000091eaf9833e
                    Extra: Last beacon: 5616ms ago
          Cell 06 - Address: <MAC 'HOME-6302' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOME-6302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005123b4415d
                    Extra: Last beacon: 5616ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005123b44bb7
                    Extra: Last beacon: 5616ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'xfinitywifi' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000005123b45331
                    Extra: Last beacon: 5616ms ago
          Cell 09 - Address: <MAC '' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fd586c3e2
                    Extra: Last beacon: 5616ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC '' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fd586cce4
                    Extra: Last beacon: 5616ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'ASUS' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076c3be30b7
                    Extra: Last beacon: 84ms ago
          Cell 12 - Address: <MAC 'Boone123' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Boone123"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f6b84a019d
                    Extra: Last beacon: 5236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'xfinitywifi' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001250e152180
                    Extra: Last beacon: 5236ms ago
          Cell 14 - Address: <MAC 'NETGEAR79' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR79"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024dc0db180
                    Extra: Last beacon: 5236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC15]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=16/70  Signal level=-94 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001db1742ba74
                    Extra: Last beacon: 5236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'DeadZone' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"DeadZone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006103c7f95d
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'HOME-37C4-2.4' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"HOME-37C4-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001db2a45e180
                    Extra: Last beacon: 5184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'CenturyLink5219' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink5219"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000079e34134148
                    Extra: Last beacon: 5184ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'valhalla2.4' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=15/70  Signal level=-95 dBm  
                    Encryption key:on
                    ESSID:"valhalla2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000025fbf62e180
                    Extra: Last beacon: 5184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC '' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001db2a477180
                    Extra: Last beacon: 5184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'xfinitywifi' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000106fe4ce323
                    Extra: Last beacon: 5052ms ago
          Cell 22 - Address: <MAC '' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006103ca8b4b
                    Extra: Last beacon: 5052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC '' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000006103ca92ad
                    Extra: Last beacon: 5052ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC 'HOME-A92D' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"HOME-A92D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001db3465fdfe
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC 'xfinitywifi' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001db34660afa
                    Extra: Last beacon: 84ms ago
          Cell 26 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001db3466205a
                    Extra: Last beacon: 4988ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'ASUS_5G' [AC27]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:off
                    ESSID:"ASUS_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000076c3bc403a
                    Extra: Last beacon: 580ms ago
          Cell 28 - Address: <MAC 'NETGEAR73-5G' [AC28]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR73-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b579440af
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     C3CE81DD94553577D83E97E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F027B13105AEA0ECF6ABE3F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-51-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)


[cfg80211]
filename:       /lib/modules/3.16.0-51-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-51-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        94:4E:CB:AA:DC:B4:B4:ED:A1:DF:3F:DB:49:C1:EB:05:E5:12:65:68
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1


[cfg80211]
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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (755 root)
SUSPEND_MODULES="iwlwifi"


[/etc/pm/config.d/config~] (755 root)
SUSPEND_MODULES="iwlmvm iwlwifi"


[/etc/pm/sleep.d/wakenet.sh] (755 root)
case "$1" in
thaw|resume)
nmcli nm sleep false
;;
*)
;;
esac
exit $?


[/etc/pm/sleep.d/wakenet.sh~] (755 root)
case "$1" in
thaw|resume)
nmcli nm sleep false
;;
*)
;;
esac
exit $?


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b3 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   11.125427] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   11.294827] iwlwifi 0000:08:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[   11.723682] iwlwifi 0000:08:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   11.724005] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   11.875315] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   27.427120] r8169 0000:09:00.0 eth0: link down
[   27.427182] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.429625] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   27.447761] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.217510] wlan0: authenticate with <MAC 'Freedom_Slap' [AC1]>
[   31.225460] wlan0: send auth to <MAC 'Freedom_Slap' [AC1]> (try 1/3)
[   31.227379] wlan0: authenticated
[   31.228398] wlan0: associate with <MAC 'Freedom_Slap' [AC1]> (try 1/3)
[   31.232263] wlan0: RX AssocResp from <MAC 'Freedom_Slap' [AC1]> (capab=0x1411 status=0 aid=4)
[   31.232710] wlan0: associated
[   31.232731] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.581863] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlan0' [IF]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24  (repeated 2 times)
[   78.734797] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   78.735701] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[   78.736840] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:a4:2b:8c:b8:b3:3a:86:dd SRC=fe80:0000:0000:0000:a62b:8cff:feb8:b33a DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[   94.212886] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:a4:2b:8c:b8:b3:3a:08:00 SRC=216.58.216.162 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x20 TTL=55 ID=4252 PROTO=TCP SPT=443 DPT=37774 WINDOW=358 RES=0x00 ACK PSH URGP=0 
[   94.449353] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:a4:2b:8c:b8:b3:3a:08:00 SRC=216.58.216.162 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x20 TTL=55 ID=4365 PROTO=TCP SPT=443 DPT=37774 WINDOW=358 RES=0x00 ACK PSH URGP=0 
[   94.872606] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:a4:2b:8c:b8:b3:3a:08:00 SRC=216.58.216.162 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x20 TTL=55 ID=4595 PROTO=TCP SPT=443 DPT=37774 WINDOW=358 RES=0x00 ACK PSH URGP=0 
[   95.721128] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:a4:2b:8c:b8:b3:3a:08:00 SRC=216.58.216.162 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x20 TTL=55 ID=5555 PROTO=TCP SPT=443 DPT=37774 WINDOW=358 RES=0x00 ACK PSH URGP=0 
[   97.588256] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:a4:2b:8c:b8:b3:3a:08:00 SRC=216.58.216.162 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x20 TTL=55 ID=6539 PROTO=TCP SPT=443 DPT=37774 WINDOW=358 RES=0x00 ACK PSH URGP=0 
[  204.959207] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  204.960122] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  204.961346] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:a4:2b:8c:b8:b3:3a:86:dd SRC=fe80:0000:0000:0000:a62b:8cff:feb8:b33a DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[  330.978776] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  330.979689] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  330.980921] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:a4:2b:8c:b8:b3:3a:86:dd SRC=fe80:0000:0000:0000:a62b:8cff:feb8:b33a DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 
[  456.998353] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  456.999004] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:a4:2b:8c:b8:b3:3a:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 PROTO=2 
[  457.000207] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:a4:2b:8c:b8:b3:3a:86:dd SRC=fe80:0000:0000:0000:a62b:8cff:feb8:b33a DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=76 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=ICMPv6 TYPE=130 CODE=0 


########## wireless info END ############

```

---

### Post by SlidingHorn on 2015-12-04
If this is what I'm thinking it is, it's a common issue and known bug.

```
service network-manager restart
```

In order to not have to do this every time, you can place the following in a script in your /etc/pm/sleep.d/ directory & make it executable:

```
#!/bin/bash

# This script gets NetworkManager out of suspend.
case $1 in
     suspend|suspend_hybrid|hibernate)
    # No need to do anything here.
        ;;
     resume|thaw)
    nmcli nm sleep false
        ;;
esac
```

Source: [http://askubuntu.com/questions/362933/network-disabled-on-some-wake-ups-on-saucy-laptop](http://askubuntu.com/questions/362933/network-disabled-on-some-wake-ups-on-saucy-laptop)

---

### Post by Bucky Ball on 2015-12-04
> **SlidingHorn said:**
> If this is what I'm thinking it is, it's a common issue and known bug.

```
service network-manager restart
```



> **apalm112 said:**
> I've followed the advice given on a few similar posts of this type of problem and have had no success in fixing it.  Such as sudo killall wpa_supplicant, sudo **service network-manager restart**, sudo chmod +x /etc/pm/config.d/config, etc.
              


Looks like your guess, 'service network-manager restart', has been tried and failed.

---

### Post by apalm112 on 2015-12-05
I've tried both of those & they have not solved the problem.

---

