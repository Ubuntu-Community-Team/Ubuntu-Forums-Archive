---
title: "Ubuntu 16.04 sees 5GHz wifi, but cannot connect"
date: 2016-08-27
forum: Networking &amp; Wireless
---

### Post by sonicking on 2016-08-27
Hi,

I am new to Ubuntu so please forgive my ignorance.

The WIFI is able to see the 5GHz connection, but it cannot connect.

Outputs from **iwconfig**:

[HTML]enp3s0f1  no wireless extensions.
lo        no wireless extensions.
wlp2s0    IEEE 802.11abgn  ESSID:"FiOS-P0HBK"            
Mode:Managed  Frequency:2.412 GHz  Access Point: 48:5D:36:2D:9A:8A             
Bit Rate=1 Mb/s   Tx-Power=20 dBm             Retry short limit:7   RTS thr:off   Fragment thr:off          
Power Management:on          Link Quality=34/70  Signal level=-76 dBm            
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0         
Tx excessive retries:9  Invalid misc:133   Missed beacon:0[/HTML]

I have updated to this firmware by running: 
[HTML]wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.160_all.deb
sudo dpkg -i linux-firmware_1.160_all.deb[/HTML]

Please let me know what else I need to provide in order to get the help.  Thanks~

---

### Post by wildmanne39 on 2016-08-27
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by sonicking on 2016-08-27
Here you go.  Thanks for looking into it.



```
########## wireless info START ##########


Report from: 27 Aug 2016 22:38 EDT -0400


Booted last: 27 Aug 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 005: ID 0461:4e22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
5: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1  Link encap:Ethernet  HWaddr <MAC 'enp3s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::307a:32db:165c:db96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58036945 (58.0 MB)  TX bytes:17698599 (17.6 MB)


##### iwconfig ##########################


enp3s0f1  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"FiOS-P0HBK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FiOS-P0HBK' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:103   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fios-router.home


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2601     1  0 19:30 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FiOS-P0HBK
GENERAL.CON-UUID:                       66249d45-0f9d-4730-aab3-ec140f62365c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   66249d45-0f9d-4730-aab3-ec140f62365c | FiOS-P0HBK
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   a272fccc-b41d-4dc5-8dbe-0d3a58c5c43a | FiOS-P0HBK-5G
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   28b3783f-14df-4903-84c0-51b2297736b4 | ZKSS6
IP4.ADDRESS[1]:                         192.168.1.159/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.159
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1472438049
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::307a:32db:165c:db96/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:03:00.1/net/enp3s0f1
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


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
FiOS-YAYFU     <MAC 'FiOS-YAYFU' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>  Infra  149   5745 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2      no        
FiOS-P0HBK-5G  <MAC 'FiOS-P0HBK-5G' [AC6]>  Infra  149   5745 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2      no        
FiOS-P0HBK     <MAC 'FiOS-P0HBK' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA2      yes     * 
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC3]>  Infra  132   5660 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2      no        
FiOS-YAYFU-5G  <MAC 'FiOS-YAYFU-5G' [AC2]>  Infra  132   5660 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2      no        
ZKSS6          <MAC 'ZKSS6' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        


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


[[/etc/NetworkManager/system-connections/FiOS-P0HBK]] (600 root)
[connection] id=FiOS-P0HBK | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G]] (600 root)
[connection] id=FiOS-P0HBK-5G | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
[ipv4] method=shared
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/ZKSS6]] (600 root)
[connection] id=ZKSS6 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ZKSS6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G 1]] (600 root)
[connection] id=FiOS-P0HBK-5G 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
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


enp3s0f1  no frequency information.


lo        no frequency information.


wlp2s0    32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


enp3s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      2   APs on   Frequency:5.66 GHz (Channel 132)
      2   APs on   Frequency:5.745 GHz (Channel 149)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'FiOS-P0HBK' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae41a842c
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FiOS-YAYFU-5G' [AC2]>
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"FiOS-YAYFU-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae2e98052
                    Extra: Last beacon: 1768ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC3]>
                    Channel:132
                    Frequency:5.66 GHz (Channel 132)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae2e98269
                    Extra: Last beacon: 1768ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003fab6d2180
                    Extra: Last beacon: 5772ms ago
          Cell 05 - Address: <MAC 'FiOS-YAYFU' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"FiOS-YAYFU"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae3ebb1b6
                    Extra: Last beacon: 5292ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'FiOS-P0HBK-5G' [AC6]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae3749053
                    Extra: Last beacon: 972ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC7]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dae3749233
                    Extra: Last beacon: 968ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
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


##### udev rules ########################


##### dmesg #############################


[ 4989.572933] r8169 0000:03:00.1 enp3s0f1: link down
[ 4992.075929] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 4993.986027] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[ 4994.000784] r8169 0000:03:00.1 enp3s0f1: link down
[ 4994.000842] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[ 4994.042119] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[ 4998.734332] wlp2s0: authenticate with <MAC 'FiOS-P0HBK' [AC1]>
[ 4998.778498] wlp2s0: send auth to <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[ 4998.780131] wlp2s0: authenticated
[ 4998.782767] wlp2s0: associate with <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[ 4998.786208] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK' [AC1]> (capab=0x431 status=0 aid=4)
[ 4998.788718] wlp2s0: associated
[ 4998.788850] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 4998.830778] ath: EEPROM regdomain: 0x8348
[ 4998.830780] ath: EEPROM indicates we should expect a country code
[ 4998.830782] ath: doing EEPROM country->regdmn map search
[ 4998.830783] ath: country maps to regdmn code: 0x3a
[ 4998.830784] ath: Country alpha2 being used: US
[ 4998.830785] ath: Regpair used: 0x3a
[ 4998.830787] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############
```

---

### Post by wildmanne39 on 2016-08-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2016-08-27
Hello and welcome to the forum! Please unplug your wired connection and then see if you can connect to your wifi, and it looks like it is trying to connect to a 2.4 and and 5ghz at the same time.

---

### Post by sonicking on 2016-08-27
I am confused.  The wired connection is not plugged at all.  

My Verizon Fios router is a dual-band kind, so it is sending out both 2.4Ghz and 5Ghz signals on the Wifi.  

I can see both.  But when I try to connect the 5Ghz (the network name is FiOS-P0HBK-5G), I cannot connect.  Then it resumes back to the 2.4Ghz connection (the network name is FiOS-P0HBK).  

But both networks are visible.

Does this help?  Thanks again~

---

### Post by wildmanne39 on 2016-08-27
I am real tired right now but I see that MTU is 0 and it should be set to automatic or 1500 in network manger. I will look again after I get some sleep but maybe some one will pop in to help since they have the information needed to check out your issue.

---

### Post by sonicking on 2016-08-27
I don't know what MTU is.  But it is set to 1500 in many other places, EXCEPT in Network Manager.  I don't know what it means.

Thanks again for looking into it.  The fact that you are trying to help makes me feel good about joining this wonderful community. :) Have a good night~

---

### Post by sonicking on 2016-08-28
Does anyone have any idea???  Thanks!

---

### Post by Keith_Helms on 2016-08-29
Looks like you have two wireless connections set up for FiOS-P0HBK-5G.  Click on the network manager icon and select edit connections.  Under wifi you should see both "FiOS-P0HBK-5G" and "FiOS-P0HBK-5G 1".  The one that doesn't end with a 1 looks like you may have been trying to share a network connection or something.  Highlight that entry and select delete.  Then try to connect to that 5ghz network.

---

### Post by sonicking on 2016-08-29
Hi, I deleted [COLOR=#000000]"FiOS-P0HBK-5G" and tried to connect to "FiOS-P0HBK-5G 1".  But I still cannot connect.  :(
[/COLOR]

---

### Post by sonicking on 2016-08-29
I re-ran the wireless script.  I see near the bottom it says: **wlp2s0: authentication with <MAC 'FiOS-P0HBK-5G' [AC2]> timed out**

I wonder what it means and why....

```



########## wireless info START ##########


Report from: 29 Aug 2016 11:04 EDT -0400


Booted last: 29 Aug 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
	Subsystem: Lite-On Communications Inc Device [11ad:0806]
	Kernel driver in use: ath10k_pci


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 004: ID 0461:4e22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
wmi                    20480  1 acer_wmi
video                  40960  2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1  Link encap:Ethernet  HWaddr <MAC 'enp3s0f1' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.159  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::307a:32db:165c:db96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:134459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150959045 (150.9 MB)  TX bytes:15198961 (15.1 MB)


##### iwconfig ##########################


enp3s0f1  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11abgn  ESSID:"FiOS-P0HBK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FiOS-P0HBK' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1377   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1
search fios-router.home


##### network managers ##################


Installed:


	NetworkManager


Running:


root      2581     1  0 08:59 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-34-generic
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FiOS-P0HBK
GENERAL.CON-UUID:                       66249d45-0f9d-4730-aab3-ec140f62365c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,3,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   28b3783f-14df-4903-84c0-51b2297736b4 | ZKSS6
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   756e566e-1741-4233-8d82-264c3edb04c6 | FiOS-P0HBK-5G 1
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   66249d45-0f9d-4730-aab3-ec140f62365c | FiOS-P0HBK
IP4.ADDRESS[1]:                         192.168.1.159/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          fios-router.home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.159
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       expiry = 1472562724
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       domain_name = fios-router.home
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       domain_search = fios-router.home.
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       routers = 192.168.1.1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::307a:32db:165c:db96/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp3s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.3/0000:03:00.1/net/enp3s0f1
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


SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
FiOS-P0HBK     <MAC 'FiOS-P0HBK' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  48      &#9602;&#9604;__  WPA2      yes     * 
ZKSS6          <MAC 'ZKSS6' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2      no        
--             <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC3]>  Infra  149   5745 MHz  54 Mbit/s  25      &#9602;___  WPA2      no        
FiOS-P0HBK-5G  <MAC 'FiOS-P0HBK-5G' [AC2]>  Infra  149   5745 MHz  54 Mbit/s  25      &#9602;___  WPA2      no        
FiOS-3HCE1     <MAC 'FiOS-3HCE1' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2      no        


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


[[/etc/NetworkManager/system-connections/FiOS-P0HBK]] (600 root)
[connection] id=FiOS-P0HBK | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ZKSS6]] (600 root)
[connection] id=ZKSS6 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ZKSS6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G 1]] (600 root)
[connection] id=FiOS-P0HBK-5G 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
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


enp3s0f1  no frequency information.


lo        no frequency information.


wlp2s0    32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


enp3s0f1  Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:5.745 GHz (Channel 149)


wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'FiOS-P0HBK' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f96f995f14
                    Extra: Last beacon: 96ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'FiOS-P0HBK-5G' [AC2]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"FiOS-P0HBK-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f96ed5803c
                    Extra: Last beacon: 960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '\00\00\00\00\00\00\00\00\00\00\00\00\00' [AC3]>
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f96ed3f21f
                    Extra: Last beacon: 1060ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     F5C0E3964FCD86D0F5FE986
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.4.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-34-generic SMP mod_unload modversions 
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
skip_otp: Y
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


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


[  767.348070] wlp2s0: deauthenticating from <MAC 'FiOS-P0HBK' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  770.347148] ath10k_pci 0000:02:00.0: failed to install key for vdev 0 peer <MAC 'FiOS-P0HBK' [AC1]>: -110
[  770.347166] wlp2s0: failed to remove key (0, <MAC 'FiOS-P0HBK' [AC1]>) from hardware (-110)
[  774.246276] wlp2s0: authenticate with <MAC 'FiOS-P0HBK-5G' [AC2]>
[  774.276936] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 1/3)
[  774.279528] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 2/3)
[  774.280722] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 3/3)
[  774.281838] wlp2s0: authentication with <MAC 'FiOS-P0HBK-5G' [AC2]> timed out
[  774.329523] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 9 times)
[  779.464956] wlp2s0: authenticate with <MAC 'FiOS-P0HBK-5G' [AC2]>
[  779.495514] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 1/3)
[  779.496727] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 2/3)
[  779.497936] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 3/3)
[  779.499115] wlp2s0: authentication with <MAC 'FiOS-P0HBK-5G' [AC2]> timed out
[  779.552094] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  785.182278] wlp2s0: authenticate with <MAC 'FiOS-P0HBK-5G' [AC2]>
[  785.212707] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 1/3)
[  785.213926] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 2/3)
[  785.215186] wlp2s0: send auth to <MAC 'FiOS-P0HBK-5G' [AC2]> (try 3/3)
[  785.216807] wlp2s0: authentication with <MAC 'FiOS-P0HBK-5G' [AC2]> timed out
[  785.286719] ath10k_warn: 10 callbacks suppressed
[  785.286758] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 10 times)
[  796.014955] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  796.120303] ath10k_warn: 88 callbacks suppressed
[  796.120313] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  800.674241] wlp2s0: authenticate with <MAC 'FiOS-P0HBK' [AC1]>
[  800.717487] wlp2s0: send auth to <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[  800.719728] wlp2s0: authenticated
[  800.723263] wlp2s0: associate with <MAC 'FiOS-P0HBK' [AC1]> (try 1/3)
[  800.726732] wlp2s0: RX AssocResp from <MAC 'FiOS-P0HBK' [AC1]> (capab=0x431 status=0 aid=3)
[  800.728510] wlp2s0: associated
[  800.728587] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  800.749883] ath: EEPROM regdomain: 0x8348
[  800.749885] ath: EEPROM indicates we should expect a country code
[  800.749886] ath: doing EEPROM country->regdmn map search
[  800.749887] ath: country maps to regdmn code: 0x3a
[  800.749888] ath: Country alpha2 being used: US
[  800.749889] ath: Regpair used: 0x3a
[  800.749890] ath: regdomain 0x8348 dynamically updated by country IE


########## wireless info END ############

```

---

### Post by Keith_Helms on 2016-08-29
I'd be curious if you could connect by temporarily changing the 5ghz network to have no security.

Unfortunately, I think a full solution may involve a drawn-out cycle of compiling new driver or firmware versions and playing with driver settings.  This may be one of those problems where you just live with using only the 2.4ghz band and then try it again on some future release and see if the underlying bug has been fixed.

---

### Post by wildmanne39 on 2016-08-29
Please post the output of:
```
dmesg | grep ath10k
```
Sorry I am not on much right now as far as being able to help.
Thanks

---

### Post by sonicking on 2016-08-29
> **Keith_Helms said:**
> I'd be curious if you could connect by temporarily changing the 5ghz network to have no security.


Hi, could you provide the instructions on how to do this?  I'd like to give it a shot.

> **Keith_Helms said:**
> Unfortunately, I think a full solution may involve a drawn-out cycle of compiling new driver or firmware versions and playing with driver settings.  This may be one of those problems where you just live with using only the 2.4ghz band and then try it again on some future release and see if the underlying bug has been fixed.

Is there a way to check future releases regularly?  Also, may I report this as a bug report?  If so, where to do that?

---

### Post by jeremy31 on 2016-08-29
I know Wild Man is a bit busy so I recommend that we disable power management for wifi
```
sudo -H gedit /lib/systemd/system/wifi-power-management-off.service
```

Paste the following in
```
[Unit]
Description=Disable power management for wlp2s0
Requires=sys-subsystem-net-devices-wlp2s0.device
After=network.target


[Service]
Type=oneshot
ExecStartPre= /bin/sleep 25
ExecStart=/sbin/iwconfig wlp2s0 power off



[Install]
WantedBy=multi-user.target
```

Then activate with
```
systemctl enable wifi-power-management-off.service
```

You will likely be asked for your password twice, enter it both times and reboot

Your 5GHz signal is pretty weak and I think you may have better luck being closer to the router

---

### Post by sonicking on 2016-08-29
> **Wild Man said:**
> Please post the output of:
```
dmesg | grep ath10k
```


This is what I got:
```

[   10.130109] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   10.472360] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.127783] ath10k_pci 0000:02:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 2 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   13.127786] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   13.188160] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[  322.082335] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  322.084459] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  326.827706] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  326.828123] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.640632] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.641021] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.743164] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.743460] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.845663] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.845927] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.948069] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  331.948303] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  332.050437] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  332.050802] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  336.863351] ath10k_warn: 1 callbacks suppressed
[  336.863371] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  336.863627] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  336.965827] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  336.966060] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.068222] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.068452] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.170615] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.170899] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.273073] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  337.273236] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.597791] ath10k_warn: 10 callbacks suppressed
[  342.597820] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.598211] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.700299] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.700607] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.802744] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.803052] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.905216] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  342.905452] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  343.007434] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  343.007818] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  379.872755] ath10k_warn: 77 callbacks suppressed
[  379.872795] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  379.872993] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  379.975195] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  379.975361] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.077551] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.077761] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.179945] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.180196] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.282263] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  380.282621] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  387.859995] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  387.860409] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  387.962449] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  387.962783] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.064906] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.065337] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.167316] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.167632] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.269666] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  388.270031] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.564314] ath10k_warn: 10 callbacks suppressed
[  396.564334] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.564753] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.666727] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.667107] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.769565] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.871566] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.871920] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.973947] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  396.974335] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  397.076396] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  401.832903] ath10k_warn: 86 callbacks suppressed
[  401.832924] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  401.884333] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  770.347148] ath10k_pci 0000:02:00.0: failed to install key for vdev 0 peer 48:5d:36:2d:9a:8a: -110
[  774.329523] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.432143] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.432358] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.534531] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.534742] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.636990] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.637142] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.739376] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  774.739542] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.552094] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.552500] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.654540] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.654876] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.757010] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.757310] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.859444] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.859719] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.961758] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  779.962084] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.286719] ath10k_warn: 10 callbacks suppressed
[  785.286758] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.287080] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.389142] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.389483] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.491547] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.491943] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.593937] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.594292] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.696504] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  785.696715] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[  796.120303] ath10k_warn: 88 callbacks suppressed
[  796.120313] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[13334.271262] ath10k_pci 0000:02:00.0: failed to install key for vdev 0 peer 48:5d:36:2d:9a:8a: -110
[13334.322365] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[13341.128518] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[15750.948356] ath10k_pci 0000:02:00.0: failed to install key for vdev 0 peer 48:5d:36:2d:9a:8a: -110
[15751.036029] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[15767.925619] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!

```

---

### Post by sonicking on 2016-08-29
> **jeremy31 said:**
> I know Wild Man is a bit busy so I recommend that we disable power management for wifi 

Hi, I did what you suggested.  But after rebooting, the power management is still ON.  Furthermore, I still cannot connect to the 5Ghz.  

> **jeremy31 said:**
> Your 5GHz signal is pretty weak and I think you may have better luck being closer to the router

I am sitting in my home office.  This is the same spot I always sit, back then when I was using Win 10.  In theory if everything works, this should not be a factor.  I cannot move my home office since my house is small.  :(

---

### Post by jeremy31 on 2016-08-29
I am not sure what to tell you about 5GHz as I am not one of the people working on this module but I know 2 of the people working on it are Qualcomm Atheros employees.

We can increase the sleep timer to see if it helps in disabling power management with
```
sudo sed -i 's/sleep 25/sleep 40/' /lib/systemd/system/wifi-power-management-off.service
```

The kernel developers for the module have a mailing list at [http://ath10k.infradead.narkive.com/](http://ath10k.infradead.narkive.com/)

---

### Post by sonicking on 2016-08-29
> **jeremy31 said:**
> I am not sure what to tell you about 5GHz as I am not one of the people working on this module but I know 2 of the people working on it are Qualcomm Atheros employees.
We can increase the sleep timer to see if it helps in disabling power management with
```
sudo sed -i 's/sleep 25/sleep 40/' /lib/systemd/system/wifi-power-management-off.service
```


Hi, thanks again.  I followed your suggestion.  After I rebooted the computer, **iwconfig** showed the power management was OFF. but it was still connected to the 2.4Ghz network. Then I tried to connect to the 5Ghz network. Once again, it failed and resumed back to the 2.4 Ghz network.  At this point, I checked **iwconfig **again and power management is now ON. I guess I am not able to keep power management OFF permanently.  I also don't know if this somehow affects the connection to the 5Gh network...

---

### Post by wildmanne39 on 2016-08-29
It still looks like a firmware issue I would install the git version from post 28 at the following link.
[https://ubuntuforums.org/showthread.php?t=2304250&page=3](https://ubuntuforums.org/showthread.php?t=2304250&page=3)

---

### Post by sonicking on 2016-08-29
> **Wild Man said:**
> It still looks like a firmware issue I would install the git version from post 28 at the following link.
[https://ubuntuforums.org/showthread.php?t=2304250&page=3](https://ubuntuforums.org/showthread.php?t=2304250&page=3)

Hi, this is super weird. Because as a result of following that, I lost the wireless connection AND sound!  I am now on wired connection.  What is going on????

---

### Post by wildmanne39 on 2016-08-29
I do not know why you would lose sound is your speakers blue tooth perhaps? even then you should not.

Did you do this set of  commands like I said and only this set:
```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```

---

### Post by sonicking on 2016-08-29
> **Wild Man said:**
> I do not know why you would lose sound is your speakers blue tooth perhaps? even then you should not.

Did you do this set of  commands like I said and only this set:
```
sudo apt-get install git
git clone https://github.com/kvalo/ath10k-firmware.git
cd ath10k-firmware/QCA9377/hw1.0
sudo cp board.bin  /lib/firmware/ath10k/QCA9377/hw1.0
sudo cp firmware-5.bin_WLAN.TF.1.0-00267-1 /lib/firmware/ath10k/QCA9377/hw1.0/firmware5.bin
sudo modprobe -r ath10k_pci
sudo modprobe ath10k_pci
```

The sound comes and goes as I reboot.  So weird.  But I will worry about it later.

No, I did all 3 sets.  Should I only do this one set????  Ahh...I am an idiot!

But I did notice one thing:

```

sudo modprobe ath10k_pci

```

The output for this step is:
```

modprobe: ERROR: could not insert 'ath10k_pci': Required key not available

```

Is this right?  This does not look right.

One more thing, now when I run iwconfig, I only see:
[CODE]
enp3s0f1  no wireless extensions.
lo        no wireless extensions.
[\CODE]

My wifi card is not being seen altogether.  OK, this is really bad.

If I reinstall Ubuntu from the disk, would that at least bring everything back???  [I mean, I don't have any new data on this computer.  I did have wifi before, albeit at only 2.4 GhZ.]

---

### Post by wildmanne39 on 2016-08-29
Reboot your computer and go into grub then choose the previous kernel and you hopefully will have wifi and sound.

This > modprobe: ERROR: could not insert 'ath10k_pci': Required key not availablemeans the driver loading failed because the key is not signed so secure boot will not let it load.

Secure boot has to be turned off or temporarily turned off to enable the key to be signed.

---

### Post by sonicking on 2016-08-29
> **Wild Man said:**
> Reboot your computer and go into grub then choose the previous kernel and you hopefully will have wifi and sound.

Hi, the advanced option, I saw two kernel's: 4.6 and 4.4.  I chose kernel 4.4.  However, I still do NOT have Wifi!  The sound is back though...so weird.  

> **Wild Man said:**
> Secure boot has to be turned off or temporarily turned off to enable the key to be signed.

Another stupid question.  How do I turn secure boot off?  I feel like I need to reinstall the driver and/or firmware successfully in order to get the Wifi back (and maybe it can even resolve the 5Ghz connection problem)...

Thanks again for your patience.

---

### Post by sonicking on 2016-08-29
I ran the wireless script again. I am hoping someone can at least quickly diagnose why the Wifi is off altogether. Thanks.

```

########## wireless info START ##########


Report from: 29 Aug 2016 23:13 EDT -0400


Booted last: 29 Aug 2016 00:00 EDT -0400


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID: Ubuntu
Description: Ubuntu 16.04.1 LTS
Release: 16.04
Codename: xenial


##### kernel ############################


Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
Subsystem: Lite-On Communications Inc Device [11ad:0806]
Kernel modules: ath10k_pci


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:1094]
Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f2:b573 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 04ca:3015 Lite-On Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
Soft blocked: no
Hard blocked: no
1: acer-bluetooth: Bluetooth
Soft blocked: yes
Hard blocked: no
2: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no


##### lsmod #############################


acer_wmi 20480 0
sparse_keymap 16384 1 acer_wmi
wmi 20480 1 acer_wmi
video 40960 2 i915_bpo,acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0f1 Link encap:Ethernet HWaddr <MAC 'enp3s0f1' [IF1]> 
inet addr:192.168.1.161 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::949e:f066:de13:9970/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1074 errors:0 dropped:0 overruns:0 frame:0
TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:646504 (646.5 KB) TX bytes:216055 (216.0 KB)


##### iwconfig ##########################


enp3s0f1 no wireless extensions.


lo no wireless extensions.


##### route #############################


Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 100 0 0 enp3s0f1
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 enp3s0f1
192.168.1.0 0.0.0.0 255.255.255.0 U 100 0 0 enp3s0f1


##### resolv.conf #######################


nameserver 127.0.1.1
search fios-router.home


##### network managers ##################


Installed:


NetworkManager


Running:


root 2514 1 0 23:05 ? 00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE: enp3s0f1
GENERAL.TYPE: ethernet
GENERAL.NM-TYPE: NMDeviceEthernet
GENERAL.VENDOR: Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER: r8169
GENERAL.DRIVER-VERSION: 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION: 
GENERAL.HWADDR: <MAC 'enp3s0f1' [IF1]>
GENERAL.MTU: 1500
GENERAL.STATE: 100 (connected)
GENERAL.REASON: 0 (No reason given)
GENERAL.UDI: /sys/devices/pci0000:00/0000:00:1d.3/0000:03:00.1/net/enp3s0f1
GENERAL.IP-IFACE: enp3s0f1
GENERAL.IS-SOFTWARE: no
GENERAL.NM-MANAGED: yes
GENERAL.AUTOCONNECT: yes
GENERAL.FIRMWARE-MISSING: no
GENERAL.NM-PLUGIN-MISSING: no
GENERAL.PHYS-PORT-ID: --
GENERAL.CONNECTION: Wired connection 1
GENERAL.CON-UUID: 9ccb8ff7-2839-4535-9d3a-ec69d16f2a8c
GENERAL.CON-PATH: /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED: no (guessed)
CAPABILITIES.CARRIER-DETECT: yes
CAPABILITIES.SPEED: 1000 Mb/s
CAPABILITIES.IS-SOFTWARE: no
WIRED-PROPERTIES.CARRIER: on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]: 9ccb8ff7-2839-4535-9d3a-ec69d16f2a8c | Wired connection 1
IP4.ADDRESS[1]: 192.168.1.161/24
IP4.GATEWAY: 192.168.1.1
IP4.ROUTE[1]: dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]: 192.168.1.1
IP4.DOMAIN[1]: fios-router.home
DHCP4.OPTION[1]: requested_routers = 1
DHCP4.OPTION[2]: requested_domain_search = 1
DHCP4.OPTION[3]: requested_host_name = 1
DHCP4.OPTION[4]: requested_time_offset = 1
DHCP4.OPTION[5]: requested_domain_name = 1
DHCP4.OPTION[6]: requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]: requested_broadcast_address = 1
DHCP4.OPTION[8]: requested_wpad = 1
DHCP4.OPTION[9]: requested_netbios_scope = 1
DHCP4.OPTION[10]: next_server = 0.0.0.0
DHCP4.OPTION[11]: broadcast_address = 192.168.1.255
DHCP4.OPTION[12]: requested_interface_mtu = 1
DHCP4.OPTION[13]: requested_subnet_mask = 1
DHCP4.OPTION[14]: dhcp_lease_time = 86400
DHCP4.OPTION[15]: dhcp_message_type = 5
DHCP4.OPTION[16]: ip_address = 192.168.1.161
DHCP4.OPTION[17]: requested_static_routes = 1
DHCP4.OPTION[18]: expiry = 1472613188
DHCP4.OPTION[19]: requested_domain_name_servers = 1
DHCP4.OPTION[20]: subnet_mask = 255.255.255.0
DHCP4.OPTION[21]: requested_ntp_servers = 1
DHCP4.OPTION[22]: domain_name = fios-router.home
DHCP4.OPTION[23]: requested_netbios_name_servers = 1
DHCP4.OPTION[24]: domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]: requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]: domain_search = fios-router.home.
DHCP4.OPTION[27]: network_number = 192.168.1.0
DHCP4.OPTION[28]: routers = 192.168.1.1
DHCP4.OPTION[29]: dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]: fe80::949e:f066:de13:9970/64
IP6.GATEWAY: 


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


[[/etc/NetworkManager/system-connections/FiOS-P0HBK]] (600 root)
[connection] id=FiOS-P0HBK | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-P0HBK
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ZKSS6]] (600 root)
[connection] id=ZKSS6 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ZKSS6
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FiOS-P0HBK-5G 1]] (600 root)
[connection] id=FiOS-P0HBK-5G 1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FiOS-P0HBK-5G
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


nl80211 not found.


##### iwlist channels ###################


enp3s0f1 no frequency information.


lo no frequency information.


##### iwlist scan #######################


enp3s0f1 Interface doesn't support scanning.


lo Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=y


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


[ 26.219515] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[ 26.669075] r8169 0000:03:00.1 enp3s0f1: link down (repeated 2 times)
[ 26.669128] IPv6: ADDRCONF(NETDEV_UP): enp3s0f1: link is not ready
[ 29.624226] r8169 0000:03:00.1 enp3s0f1: link up
[ 29.624233] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0f1: link becomes ready
[ 368.013074] r8169 0000:03:00.1 enp3s0f1: link down
[ 383.605287] r8169 0000:03:00.1 enp3s0f1: link up
[ 458.529566] r8169 0000:03:00.1 enp3s0f1: link down
[ 476.126213] r8169 0000:03:00.1 enp3s0f1: link up


########## wireless info END ############

```

---

### Post by wildmanne39 on 2016-08-29
This driver is still new and very experimental, I do not have the experience with it like I do other drivers, I hope someone with experience with it will step in and help out.

---

### Post by sonicking on 2016-08-29
> **Wild Man said:**
> This driver is still new and very experimental, I do not have the experience with it like I do other drivers, I hope someone with experience with it will step in and help out.

At the meantime, if I reinstall Ubuntu 16.04 from the disk, would that at least bring everything back to what it was 2 days ago???  I tried going to the Grub and even that still cannot turn on the wifi.  Thanks!

---

### Post by sonicking on 2016-08-30
> **Wild Man said:**
> It still looks like a firmware issue I would install the git version from post 28 at the following link.
[https://ubuntuforums.org/showthread.php?t=2304250&page=3](https://ubuntuforums.org/showthread.php?t=2304250&page=3)

Hi. I just want to say that I *disabled* secure boot and then installed the git successfully.  Now I have regained the Wifi capability.  I can even connect to the 5Ghz network I put my laptop next to the router.  So this is still not as good as Win 10.  When I was sitting in my home office upstairs using Win 10, I could easily connect to the 5Ghz network.  Now with Ubuntu 16.04, I cannot connect to the 5Ghz network sitting in the same spot.  

Anyway, thanks for the people in the community looking into my problem!

Finally, since I disabled the secure boot in order to install the git, my laptop is now in insecure boot model.  Do I need to re-enable secure boot?  If so, how do I do that????  Thanks!

---

### Post by wildmanne39 on 2016-08-31
I am running with secure boot off on my computer right now and it is not an issue as far as I am concerned, since I mainly install applications from the repositories and I do my research before I install applications outside of the repositories so I know that I can trust the source before I install there apps. 

I have created a signed key for a driver before which requires turning off secure boot then creating the key then turning it back on but with secure boot on you have to go through the process every time you try to add a application from an outside source.

Since you did not create a key for the new driver you installed if you turn secure boot back on it will not allow that driver to load.

---

### Post by sonicking on 2016-08-31
> **Wild Man said:**
> I am running with secure boot off on my computer right now and it is not an issue as far as I am concerned, since I mainly install applications from the repositories and I do my research before I install applications outside of the repositories so I know that I can trust the source before I install there apps. 

I have created a signed key for a driver before which requires turning off secure boot then creating the key then turning it back on but with secure boot on you have to go through the process every time you try to add a application from an outside source.

Since you did not create a key for the new driver you installed if you turn secure boot back on it will not allow that driver to load.

I see.  I am ok to continue to run the computer without secure boot.  It just feels weird to see the word "insecure" every time I start the computer. :P

Please consider this issue resolved.  Thanks again for all the help I got.

---

### Post by sonicking on 2016-09-03
> **jeremy31 said:**
> I know Wild Man is a bit busy so I recommend that we disable power management for wifi
```
sudo -H gedit /lib/systemd/system/wifi-power-management-off.service
```

Paste the following in
```
[Unit]
Description=Disable power management for wlp2s0
Requires=sys-subsystem-net-devices-wlp2s0.device
After=network.target


[Service]
Type=oneshot
ExecStartPre= /bin/sleep 25
ExecStart=/sbin/iwconfig wlp2s0 power off



[Install]
WantedBy=multi-user.target
```

Then activate with
```
systemctl enable wifi-power-management-off.service
```

You will likely be asked for your password twice, enter it both times and reboot

Hi, sorry for more follow-up question on this topic.  This is just for my own knowledge.  

So I know I have done this step and have the file wifi-power-management-off.service in the /lib/systemd/system/ folder.

Suppose I want to undo this action, how may I do so???

---

### Post by jeremy31 on 2016-09-03
```
systemctl disable wifi-power-management-off.service
```
Should do what you want and if you want to go one more step you can remove the file itself with
```
sudo rm /lib/systemd/system/wifi-power-management-off.service
```
But only execute the second command after using the first as I don't know what problems it may cause if run by itself

---

### Post by sonicking on 2016-09-04
> **jeremy31 said:**
> 

Paste the following in
```
[Unit]
Description=Disable power management for wlp2s0
Requires=sys-subsystem-net-devices-wlp2s0.device
After=network.target


[Service]
Type=oneshot
ExecStartPre= /bin/sleep 25
ExecStart=/sbin/iwconfig wlp2s0 power off



[Install]
WantedBy=multi-user.target
```


Hi, is there anything special about the timer (25)?  I am experimenting with different numbers.  With 25, I cannot to my 5Ghz connection at all.  With 40, I can connect to it, but the download speed (according to a Speed Test) is capped.  With 60, it is having the fastest download speed.  [Of course, there could have been some variances on the speed that I experienced intermittently.]  I am even wondering if I should try an even greater number than 60...Do you have any thought about this???  Thanks.

---

### Post by jeremy31 on 2016-09-04
Test as much as you like with the sleep time, sometimes it works with as little as 10, it all depends on how fast things load in the kernel and when the power management gets enabled.  Your wifi gets 3 firmware files loaded which might take a little time and then with the rename from wlan0
If setting it to over 60 works better, please post back as I am sure others will have this issue.

---

