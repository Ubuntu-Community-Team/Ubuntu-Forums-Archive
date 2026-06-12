---
title: "QCA6164 in Ubuntu 16.04, 5GHz issue"
date: 2016-05-21
forum: Networking &amp; Wireless
---

### Post by Emmoth on 2016-05-21
Hi
I have some issues too, my 2,4GHz works just fine, and I can see both my 5GHz bands but they won't accept the password. So I can't connect to them. 

Not sure if it has anything to do with the diffrence in 5GHz bands between Sweden and Kvalos firmware.
Anyway here is my wireless scrip

```


########## wireless info START ##########

Report from: 21 May 2016 22:01 CEST +0200

Booted last: 21 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.6.0-040600rc7-generic #201605120803 SMP Thu May 12 12:04:59 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:382e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 004: ID 174f:14ee Syntek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           323584  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              745472  1 ath10k_core
cfg80211              581632  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.0.179  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5cd5:ae7d:d77:c32f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2949 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1458000 (1.4 MB)  TX bytes:455312 (455.3 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"Airfilter G/N 2.4GHz"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Airfilter G/N 2.4GHz' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:72   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search bahnhof.se

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2327     1  0 21:45 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.6.0-040600rc7-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Airfilter G/N 2.4GHz
GENERAL.CON-UUID:                       036877a5-0c6c-416f-afd8-b11669386054
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3,1,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3f5aa970-d4bf-42cd-9015-8072d096e2d8 | Airfilter AC/N 5GHz
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   3673d872-0e05-4413-9452-d7323cc4ca95 | Airfilter AC/N
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   036877a5-0c6c-416f-afd8-b11669386054 | Airfilter G/N 2.4GHz
IP4.ADDRESS[1]:                         192.168.0.179/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          bahnhof.se
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464464800
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.179
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = bahnhof.se
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 604800
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::5cd5:ae7d:d77:c32f/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168h-2_0.0.2 02/26/15
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
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

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                    <MAC '' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
Airfilter AC/N        <MAC 'Airfilter AC/N' [AC5]>  Infra  100   5500 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Airfilter AC/N 5GHz   <MAC 'Airfilter AC/N 5GHz' [AC4]>  Infra  52    5260 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Airfilter G/N 2.4GHz  <MAC 'Airfilter G/N 2.4GHz' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
TN_24GHz_EDAA43       <MAC 'TN_24GHz_EDAA43' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Airfilter AC*N 5GHz]] (600 root)

[[/etc/NetworkManager/system-connections/EmmothS6Edge]] (600 root)
[connection] id=EmmothS6Edge | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=EmmothS6Edge
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter G*N 2.4GHz]] (600 root)

[[/etc/NetworkManager/system-connections/Airfilter AC*N]] (600 root)

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.26 GHz (Channel 52)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Airfilter G/N 2.4GHz' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Airfilter G/N 2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000032a172f28
                    Extra: Last beacon: 1728ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000032a16d142
                    Extra: Last beacon: 4460ms ago
          Cell 03 - Address: <MAC 'TN_24GHz_EDAA43' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TN_24GHz_EDAA43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000059fa9cd79e
                    Extra: Last beacon: 4660ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Airfilter AC/N 5GHz' [AC4]>
                    Channel:52
                    Frequency:5.26 GHz (Channel 52)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Airfilter AC/N 5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000032a24e3ae
                    Extra: Last beacon: 3152ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Airfilter AC/N' [AC5]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Airfilter AC/N"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000032a32f3d8
                    Extra: Last beacon: 2208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
srcversion:     BD2C668795CFC4DA8EE58E0
depends:        ath10k_core
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     0B2570EA10985724B7B6B5F
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0F85316D3D74DC638291862
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     64D16DD2A026E169A36027A
depends:        
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[  192.443843] ath10k_pci 0000:02:00.0: [48]: 0x800B49E9 0x0041A930 0x00422484 0x00005008
[  192.443845] ath10k_pci 0000:02:00.0: [52]: 0x809A6C5C 0x0041A9C0 0x0042942C 0x0042CB4C
[  192.443847] ath10k_pci 0000:02:00.0: [56]: 0x809A62B0 0x0041AA00 0x0041AA28 0x00427230
[  192.444104] ath10k_pci 0000:02:00.0: failed to poke peer <MAC 'Airfilter AC/N 5GHz' [AC4]> param for ps workaround on vdev 0: -108
[  192.444123] ath10k_pci 0000:02:00.0: failed to set 2g txpower 0: -108
[  192.444128] ath10k_pci 0000:02:00.0: failed to setup tx power 0: -108
[  192.444132] ath10k_pci 0000:02:00.0: failed to recalc tx power: -108
[  192.444140] ath10k_pci 0000:02:00.0: failed to set PS Mode 0 for vdev 0: -108
[  192.444144] ath10k_pci 0000:02:00.0: failed to setup powersave: -108
[  192.444149] ath10k_pci 0000:02:00.0: failed to setup ps on vdev 0: -108
[  192.444163] ath10k_pci 0000:02:00.0: device is wedged, will not restart
[  192.444178] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 1: -108
[  200.937578] wlp2s0: deauthenticating from <MAC 'Airfilter AC/N 5GHz' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  200.937718] ath10k_warn: 3 callbacks suppressed
[  200.937733] ath10k_pci 0000:02:00.0: failed to delete peer <MAC 'Airfilter AC/N 5GHz' [AC4]> for vdev 0: -108
[  200.938423] ath10k_pci 0000:02:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[  200.938429] ath10k_pci 0000:02:00.0: failed to set protection mode 0 on vdev 0: -108
[  200.938434] ath10k_pci 0000:02:00.0: failed to set erp slot for vdev 0: -108
[  200.938439] ath10k_pci 0000:02:00.0: failed to set preamble for vdev 0: -108
[  200.938444] ath10k_pci 0000:02:00.0: faield to down vdev 0: -108
[  200.938449] ath10k_pci 0000:02:00.0: failed to submit vdev param txbf 0x0: -108
[  200.938453] ath10k_pci 0000:02:00.0: failed to recalc txbf for vdev 0: -108
[  200.938459] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -108 (repeated 2 times)
[  206.041582] ath10k_warn: 9 callbacks suppressed
[  206.041601] ath10k_pci 0000:02:00.0: failed to start hw scan: -108 (repeated 24 times)
[  229.123494] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 1: -108
[  229.124854] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 0: -108
[  229.124864] ath10k_pci 0000:02:00.0: removing stale peer <MAC 'Airfilter AC/N 5GHz' [AC4]> from vdev_id 0
[  229.124945] ath10k_pci 0000:02:00.0: could not suspend target (-108)
[  234.722208] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  238.636775] wlp2s0: authenticate with <MAC 'Airfilter G/N 2.4GHz' [AC1]>
[  238.675499] wlp2s0: send auth to <MAC 'Airfilter G/N 2.4GHz' [AC1]> (try 1/3)
[  238.695361] wlp2s0: authenticated
[  238.697908] wlp2s0: associate with <MAC 'Airfilter G/N 2.4GHz' [AC1]> (try 1/3)
[  238.732147] wlp2s0: RX AssocResp from <MAC 'Airfilter G/N 2.4GHz' [AC1]> (capab=0x411 status=0 aid=3)
[  238.735251] wlp2s0: associated
[  238.735379] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############

```

I'm hoping that you guys have more ideas for me :D

---

### Post by jeremy31 on 2016-05-21
Post moved to it's own thread

I would change the wifi encryption settings on the router to WPA2 only, now it appears that TKIP is enabled on the Airfilter network

And you might want to eliminate the spaces in the wifi SSID, instead of Airfilter G/N 2.4GHz use Airfilter-G/N-2.4GHz

---

### Post by Emmoth on 2016-05-22
I've tried what you suggested as far as changing the names and removed the spaces. But I can't figure out how to use only WPA2 on my D-Link DIR-890L, so it looks like that I have to change my router to a different one :/ 

When I changed the name and removed the spaces I couldn't see the 5GHz bands at all, but they popped up after a short while, stil couldn't connect to them.

So it seems that I can't disable TKIP encryption either. So If it comes to change the router, and suggest to which ? A Tri-band router is what I want tho, one that I could install DD WRT on would be nice :)

---

### Post by jeremy31 on 2016-05-22
[http://setuprouter.com/router/dlink/dir-890l/wifi.htm](http://setuprouter.com/router/dlink/dir-890l/wifi.htm)

This says if the WPA2-Personal option by itself is not available,you need to update the firmware on the router

---

### Post by Emmoth on 2016-05-22
I've checked the router and I have the latest firmware and I only have the option WPA/WPA2 as security.

If I boot up the windows part of the computer the network card works as it should. 

I think that the main problem is that there aint any "real" FW for the QCA6164, and that we have to use workarounds. One thing that I have been wondering about too is that to get my 2,4GHz band to work I had to remove the all the upper letters in the password which I don't like :/ Sadly that didn't fix the 5GHZ bands. So I think my problem could be the damn router in this care

But if you have any more ideas I'll gladly try them :)

---

### Post by Emmoth on 2016-05-24
Tried a new router, didn't help at all.

On this one I can choose WPA2 only and AES, but now I can't connect at all :/

here's the script again.

```


########## wireless info START ##########

Report from: 24 May 2016 18:27 CEST +0200

Booted last: 24 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.6.0-040600rc7-generic #201605120803 SMP Thu May 12 12:04:59 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:382e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 003: ID 174f:14ee Syntek 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           323584  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              745472  1 ath10k_core
cfg80211              581632  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::494f:eb53:b29f:d473/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1240939 (1.2 MB)  TX bytes:95714 (95.7 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       672     1  0 17:52 ?        00:00:11 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6be81c77-4a1f-446b-a0b7-f41e2c438d75
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/10
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{6}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6be81c77-4a1f-446b-a0b7-f41e2c438d75 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.146/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.146
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1464193502
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = etecsdev
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::494f:eb53:b29f:d473/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.6.0-040600rc7-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{7,8}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   803a943c-44a6-4184-933d-45ffe641436d | Airfilter5GHz
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   837e64d5-4a11-47fa-aa69-3d3f8ab3d26d | Airfilter2.4GHz

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
AirCast          <MAC 'AirCast' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
Airfilter2.4GHz  <MAC 'Airfilter2.4GHz' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter-guest  <MAC 'Airfilter-guest' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter5GHz-2  <MAC 'Airfilter5GHz-2' [AC6]>  Infra  116   5580 MHz  54 Mbit/s  85      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter5GHz    <MAC 'Airfilter5GHz' [AC5]>  Infra  36    5180 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2       no        
TN_24GHz_EDAA43  <MAC 'TN_24GHz_EDAA43' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/Airfilter5GHz]] (600 root)
[connection] id=Airfilter5GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter5GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/EmmothS6Edge]] (600 root)
[connection] id=EmmothS6Edge | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=EmmothS6Edge
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter2.4GHz]] (600 root)
[connection] id=Airfilter2.4GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter2.4GHz
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.58 GHz (Channel 116)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'AirCast' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"AirCast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ddb57c708
                    Extra: Last beacon: 3420ms ago
          Cell 02 - Address: <MAC 'Airfilter2.4GHz' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Airfilter2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000008302293b
                    Extra: Last beacon: 3424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Airfilter-guest' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Airfilter-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000830238b1
                    Extra: Last beacon: 3480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TN_24GHz_EDAA43' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TN_24GHz_EDAA43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009357bbac99
                    Extra: Last beacon: 3256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Airfilter5GHz' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000083073ed4
                    Extra: Last beacon: 2784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Airfilter5GHz-2' [AC6]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz-2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000008322534a
                    Extra: Last beacon: 1016ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'LAFDAC' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"LAFDAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000082f617af848
                    Extra: Last beacon: 3776ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'LAFDAC-guest' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"LAFDAC-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000082f617b1ddd
                    Extra: Last beacon: 3776ms ago

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
srcversion:     BD2C668795CFC4DA8EE58E0
depends:        ath10k_core
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     0B2570EA10985724B7B6B5F
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0F85316D3D74DC638291862
depends:        cfg80211
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.6.0-040600rc7-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     64D16DD2A026E169A36027A
depends:        
intree:         Y
vermagic:       4.6.0-040600rc7-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath10k_core.conf]
options ath10k_core skip_otp=Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 1936.636643] ath10k_pci 0000:02:00.0: failed to start hw scan: -108 (repeated 48 times)
[ 1983.763621] r8169 0000:01:00.0 enp1s0: link up
[ 1983.763656] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[ 1984.724351] ath10k_pci 0000:02:00.0: failed to start hw scan: -108 (repeated 41 times)
[ 2024.602557] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 1: -108
[ 2024.604555] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 0: -108
[ 2024.604565] ath10k_pci 0000:02:00.0: removing stale peer <MAC 'Airfilter5GHz' [AC5]> from vdev_id 0
[ 2024.604619] ath10k_pci 0000:02:00.0: could not suspend target (-108)
[ 2031.689419] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 2032.176293] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)! (repeated 3 times)

########## wireless info END ############



```

---

### Post by jeremy31 on 2016-05-24
Can you restart the computer and post the results for ```
dmesg | grep ath10k
```

---

### Post by Emmoth on 2016-05-24
Here you go :)

```

[   15.603774] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   15.916909] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   16.511915] ath10k_pci 0000:02:00.0: qca6164 hw2.1 target 0x05010000 chip_id 0x003405ff sub 17aa:3545
[   16.511921] ath10k_pci 0000:02:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   16.512434] ath10k_pci 0000:02:00.0: firmware ver atheros-12.0.0.102-fw api 5 features  crc32 fe72c381
[   16.573692] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-2.bin failed with error -2
[   16.600413] ath10k_pci 0000:02:00.0: board_file api 1 bmi_id N/A crc32 b75e3a4f
[   17.768049] ath10k_pci 0000:02:00.0: htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   17.899246] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   61.432333] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[   94.713822] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!


```

---

### Post by jeremy31 on 2016-05-24
I wonder if this firmware is different from what Kalle Valo has?
```
cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo mv board.bin board.bin.bak
sudo mv firmware-5.bin firmware-5.bin.bak
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw2.1/board-2.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw2.1/board.bin
sudo wget https://github.com/kvalo/ath10k-firmware/blob/master/QCA6174/hw2.1/firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1
sudo mv firmware-5.bin_SW_RM.1.1.1-00157-QCARMSWPZ-1 firmware-5.bin
```

Reboot

---

### Post by Emmoth on 2016-05-24
Yeah that was diffrent, now nothing works, can't even find the wireless now :P So I'm doing this.

```

cd /lib/firmware/ath10k/QCA6174/hw2.1
sudo mv board.bin.bak board.bin
sudo mv firmware-5.bin.bak firmware-5.bin

```

and I'm going to hit the sack for tonight, I'll run the wireless scrip again and the dmesg before bed tho.

OK rebooted now

Here's dmesg.
```

[   13.142685] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   13.518421] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.916072] ath10k_pci 0000:02:00.0: found invalid board magic
[   15.143223] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   15.143229] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   15.522346] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0

```

and here's the wireless script

```


########## wireless info START ##########

Report from: 24 May 2016 23:32 CEST +0200

Booted last: 24 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:382e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 004: ID 174f:14ee Syntek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          inet addr:192.168.1.146  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::195b:58de:e58c:c2e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10467 (10.4 KB)  TX bytes:9840 (9.8 KB)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae42:51b0:b2e4:5622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7587 (7.5 KB)  TX bytes:6824 (6.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"Airfilter2.4GHz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Airfilter2.4GHz' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:41   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       679     1  1 23:30 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5f8c33e3-22fd-440d-ad89-3e7f6385a8f5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5f8c33e3-22fd-440d-ad89-3e7f6385a8f5 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.146/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.146
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1464211829
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = etecsdev
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::195b:58de:e58c:c2e0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Airfilter2.4GHz
GENERAL.CON-UUID:                       d19eb036-9520-450b-82ba-fdcf2c3e363e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
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
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5ec5e5dc-967e-49df-9990-e9352e08c29f | Airfilter5GHz-2
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0082f2a6-ec0a-454c-addd-6e620138ba7d | Airfilter5GHz
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   d19eb036-9520-450b-82ba-fdcf2c3e363e | Airfilter2.4GHz
IP4.ADDRESS[1]:                         192.168.1.55/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.55
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1464211932
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = etecsdev
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::ae42:51b0:b2e4:5622/64
IP6.GATEWAY:                            

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
AirCast          <MAC 'AirCast' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
Airfilter-guest  <MAC 'Airfilter-guest' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter5GHz    <MAC 'Airfilter5GHz' [AC5]>  Infra  36    5180 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter5GHz-2  <MAC 'Airfilter5GHz-2' [AC6]>  Infra  116   5580 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter2.4GHz  <MAC 'Airfilter2.4GHz' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  76      &#9602;&#9604;&#9606;_  WPA2       yes     * 
TN_24GHz_EDAA43  <MAC 'TN_24GHz_EDAA43' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
comhem_4C0517    <MAC 'comhem_4C0517' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/Airfilter5GHz]] (600 root)
[connection] id=Airfilter5GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter5GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter5GHz-2]] (600 root)
[connection] id=Airfilter5GHz-2 | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter5GHz-2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter2.4GHz]] (600 root)
[connection] id=Airfilter2.4GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter2.4GHz
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.58 GHz (Channel 116)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Airfilter2.4GHz' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Airfilter2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c6d4808e
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'AirCast' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:"AirCast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000321f2a73c0
                    Extra: Last beacon: 4944ms ago
          Cell 03 - Address: <MAC 'Airfilter-guest' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Airfilter-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c6d49028
                    Extra: Last beacon: 4948ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'TN_24GHz_EDAA43' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TN_24GHz_EDAA43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000979b8f474f
                    Extra: Last beacon: 4528ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Airfilter5GHz' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c6e1d338
                    Extra: Last beacon: 3876ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Airfilter5GHz-2' [AC6]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz-2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004c704334e
                    Extra: Last beacon: 1428ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
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
options ath10k_core skip_otp=Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   13.142685] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   13.518421] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   13.916072] ath10k_pci 0000:02:00.0: found invalid board magic
[   15.143223] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   15.143229] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   15.227917] ath: EEPROM regdomain: 0x6c
[   15.227924] ath: EEPROM indicates we should expect a direct regpair map
[   15.227928] ath: Country alpha2 being used: 00
[   15.227930] ath: Regpair used: 0x6c
[   15.522346] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   26.926409] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   28.237225] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   28.297919] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   28.298032] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   29.103497] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   31.124030] r8169 0000:01:00.0 enp1s0: link up
[   31.124055] IPv6: ADDRCONF(NETDEV_CHANGE): enp1s0: link becomes ready
[  134.826097] wlp2s0: authenticate with <MAC 'Airfilter2.4GHz' [AC1]>
[  134.863355] wlp2s0: send auth to <MAC 'Airfilter2.4GHz' [AC1]> (try 1/3)
[  134.865694] wlp2s0: authenticated
[  134.866677] wlp2s0: associate with <MAC 'Airfilter2.4GHz' [AC1]> (try 1/3)
[  134.870405] wlp2s0: RX AssocResp from <MAC 'Airfilter2.4GHz' [AC1]> (capab=0x411 status=0 aid=1)
[  134.874119] wlp2s0: associated
[  134.874264] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-05-24
Actually you might just have to delete the board-2.bin with ```
sudo rm /lib/firmware/ath10k/QCA6174/hw2.1/board-2.bin
```

I know this firmware has worked for others with the same QCA6164 in Ubuntu 16.04

I will wait for the new script and dmesg results as it might be a network manager bug and not a firmware issue

---

### Post by Emmoth on 2016-05-25
I had the time to try this before going work.

Didn't change anything connect wise anyway.

Here's a new dmesg, but this is after I tried to connect to 5GHz if that might help.
```

[   15.847679] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   16.550003] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   16.706577] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-2.bin failed with error -2
[   17.912064] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   17.912070] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   18.752954] ath10k_pci 0000:02:00.0 wlp2s0: renamed from wlan0
[   25.562558] ath10k_pci 0000:02:00.0: no channel configured; ignoring frame(s)!
[   58.243456] ath10k_pci 0000:02:00.0: firmware crashed! (uuid bfaf2c2d-3ece-4e60-8246-282ce1f11d69)
[   58.243500] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   58.243506] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   58.245535] ath10k_pci 0000:02:00.0: firmware register dump:
[   58.245540] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x00939797 0x00955B31
[   58.245545] ath10k_pci 0000:02:00.0: [04]: 0x00939797 0x00060330 0x00000000 0x0041A92C
[   58.245550] ath10k_pci 0000:02:00.0: [08]: 0x00413A18 0x0000FFFF 0x00000000 0x00000000
[   58.245553] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0xFFFFFFFF 0x0096C09C 0x0096C0A7
[   58.245594] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009287BD 0x00000000 0x009287BD
[   58.245601] ath10k_pci 0000:02:00.0: [20]: 0x40939797 0x0041A7D0 0x00407124 0x00000000
[   58.245606] ath10k_pci 0000:02:00.0: [24]: 0x8093D6C4 0x0041A830 0x00400000 0xC0939797
[   58.245623] ath10k_pci 0000:02:00.0: [28]: 0x8094777F 0x0041A850 0x0046D5D8 0x00000001
[   58.245628] ath10k_pci 0000:02:00.0: [32]: 0x800AA334 0x0041A880 0x0046D5D8 0x00000001
[   58.245634] ath10k_pci 0000:02:00.0: [36]: 0x800AA49E 0x0041A8A0 0x00424944 0x00000001
[   58.245641] ath10k_pci 0000:02:00.0: [40]: 0x80994E3A 0x0041A8C0 0x00424944 0x0041A908
[   58.245646] ath10k_pci 0000:02:00.0: [44]: 0x80996E7A 0x0041A8F0 0x0046F888 0x00412984
[   58.245653] ath10k_pci 0000:02:00.0: [48]: 0x800B49E9 0x0041A930 0x00422484 0x00005008
[   58.245658] ath10k_pci 0000:02:00.0: [52]: 0x809A6C5C 0x0041A9C0 0x0042942C 0x0042CB4C
[   58.245662] ath10k_pci 0000:02:00.0: [56]: 0x809A62B0 0x0041AA00 0x0041AA28 0x00427230
[   58.270283] ath10k_pci 0000:02:00.0: failed to poke peer 2c:56:dc:5e:18:84 param for ps workaround on vdev 0: -108
[   59.795657] ath10k_pci 0000:02:00.0: firmware crashed! (uuid edc4af83-daac-4a53-9e46-f19a58166013)
[   59.795784] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw atheros-12.0.0.102-fw fwapi 5 bdapi 1 htt-ver 3.25 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features 
[   59.795789] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   59.797830] ath10k_pci 0000:02:00.0: firmware register dump:
[   59.797840] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x00939797 0x00955B31
[   59.797845] ath10k_pci 0000:02:00.0: [04]: 0x00939797 0x00060330 0x00000000 0x0041A92C
[   59.797849] ath10k_pci 0000:02:00.0: [08]: 0x00413A18 0x0000FFFF 0x00000000 0x00000000
[   59.797854] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0xFFFFFFFF 0x0096C09C 0x0096C0A7
[   59.797858] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x0097F8DB 0x00000000 0x00000000
[   59.797862] ath10k_pci 0000:02:00.0: [20]: 0x40939797 0x0041A7D0 0x00407124 0x00000000
[   59.797867] ath10k_pci 0000:02:00.0: [24]: 0x8093D6C4 0x0041A830 0x00400000 0xC0939797
[   59.797871] ath10k_pci 0000:02:00.0: [28]: 0x8094777F 0x0041A850 0x0046D5D8 0x00000001
[   59.797875] ath10k_pci 0000:02:00.0: [32]: 0x800AA334 0x0041A880 0x0046D5D8 0x00000001
[   59.797879] ath10k_pci 0000:02:00.0: [36]: 0x800AA49E 0x0041A8A0 0x00424944 0x00000001
[   59.797882] ath10k_pci 0000:02:00.0: [40]: 0x80994E3A 0x0041A8C0 0x00424944 0x0041A908
[   59.797886] ath10k_pci 0000:02:00.0: [44]: 0x80996E7A 0x0041A8F0 0x0046F888 0x00412984
[   59.797890] ath10k_pci 0000:02:00.0: [48]: 0x800B49E9 0x0041A930 0x00422484 0x00005008
[   59.797900] ath10k_pci 0000:02:00.0: [52]: 0x809A6C5C 0x0041A9C0 0x0042942C 0x0042CB4C
[   59.797904] ath10k_pci 0000:02:00.0: [56]: 0x809A62B0 0x0041AA00 0x0041AA28 0x00427230
[   59.798008] ath10k_pci 0000:02:00.0: failed to poke peer 2c:56:dc:5e:18:84 param for ps workaround on vdev 0: -108
[   59.798021] ath10k_pci 0000:02:00.0: failed to set 2g txpower 0: -108
[   59.798026] ath10k_pci 0000:02:00.0: failed to setup tx power 0: -108
[   59.798028] ath10k_pci 0000:02:00.0: failed to recalc tx power: -108
[   59.798033] ath10k_pci 0000:02:00.0: failed to set PS Mode 0 for vdev 0: -108
[   59.798036] ath10k_pci 0000:02:00.0: failed to setup powersave: -108
[   59.798039] ath10k_pci 0000:02:00.0: failed to setup ps on vdev 0: -108
[   59.798051] ath10k_pci 0000:02:00.0: device is wedged, will not restart
[   59.798062] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 1: -108
[   68.185558] ath10k_warn: 3 callbacks suppressed
[   68.185567] ath10k_pci 0000:02:00.0: failed to delete peer 2c:56:dc:5e:18:84 for vdev 0: -108
[   68.185654] Modules linked in: drbg ansi_cprng ctr ccm rfcomm bnep nls_iso8859_1 arc4 rtsx_usb_ms memstick ath10k_pci ath10k_core btusb kvm_amd ath btrtl btbcm kvm btintel bluetooth mac80211 uvcvideo snd_hda_codec_realtek irqbypass crct10dif_pclmul crc32_pclmul snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_codec aesni_intel videobuf2_vmalloc videobuf2_memops videobuf2_v4l2 videobuf2_core v4l2_common videodev aes_x86_64 lrw fam15h_power gf128mul glue_helper ablk_helper media cryptd input_leds snd_hda_core snd_hwdep joydev serio_raw cfg80211 snd_pcm k10temp snd_seq_midi snd_seq_midi_event snd_rawmidi edac_mce_amd snd_seq edac_core snd_seq_device i2c_piix4 snd_timer snd ideapad_laptop sparse_keymap soundcore shpchp 8250_fintek i2c_designware_platform 8250_dw i2c_designware_core mac_hid
[   68.186182] ath10k_pci 0000:02:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[   68.186185] ath10k_pci 0000:02:00.0: failed to set protection mode 0 on vdev 0: -108
[   68.186188] ath10k_pci 0000:02:00.0: failed to set erp slot for vdev 0: -108
[   68.186190] ath10k_pci 0000:02:00.0: failed to set preamble for vdev 0: -108
[   68.186193] ath10k_pci 0000:02:00.0: faield to down vdev 0: -108
[   68.186196] ath10k_pci 0000:02:00.0: failed to submit vdev param txbf 0x0: -108
[   68.186197] ath10k_pci 0000:02:00.0: failed to recalc txbf for vdev 0: -108
[   68.186202] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -108
[   68.186204] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -108
[   73.277893] ath10k_warn: 9 callbacks suppressed
[   73.277908] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   74.277178] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   75.276722] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   76.276409] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   77.276148] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   78.276030] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   79.275777] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   80.276044] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   81.276479] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   82.277115] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   96.672045] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   97.674401] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   98.676008] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[   99.677628] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  100.679254] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  101.680930] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  102.682572] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  103.684285] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  104.685298] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  105.686795] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  106.688181] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  107.689585] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  108.691208] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  109.692115] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  110.693752] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  111.695339] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  112.697065] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  113.698755] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  114.699815] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  115.701516] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  116.703190] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  117.704954] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  118.706644] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  119.707718] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  120.709266] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  121.710918] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  121.849066] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  121.883012] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  122.884898] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  123.886545] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  124.887644] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  125.889384] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  126.891055] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  127.892542] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  128.894228] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  129.895794] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  130.897469] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  131.899135] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  132.900803] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  133.902160] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  134.903228] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  135.904941] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  136.906732] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  137.908397] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  138.910094] ath10k_pci 0000:02:00.0: failed to start hw scan: -108
[  139.837201] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 1: -108
[  139.837351] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 0: -108
[  139.837359] ath10k_pci 0000:02:00.0: removing stale peer 2c:56:dc:5e:18:84 from vdev_id 0
[  139.837440] ath10k_pci 0000:02:00.0: could not suspend target (-108)


```

and the wireless info
```


########## wireless info START ##########

Report from: 25 May 2016 06:30 CEST +0200

Booted last: 25 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:382e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 004: ID 174f:14ee Syntek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF]>  
          inet addr:192.168.1.55  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae42:51b0:b2e4:5622/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81550 (81.5 KB)  TX bytes:45292 (45.2 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"Airfilter2.4GHz"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Airfilter2.4GHz' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:48   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       715     1  2 06:27 ?        00:00:03 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6164 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               atheros-12.0.0.102-fw
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Airfilter2.4GHz
GENERAL.CON-UUID:                       d19eb036-9520-450b-82ba-fdcf2c3e363e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,1,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0082f2a6-ec0a-454c-addd-6e620138ba7d | Airfilter5GHz
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   d19eb036-9520-450b-82ba-fdcf2c3e363e | Airfilter2.4GHz
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   5ec5e5dc-967e-49df-9990-e9352e08c29f | Airfilter5GHz-2
IP4.ADDRESS[1]:                         192.168.1.55/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.55
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       wpad = a
DHCP4.OPTION[17]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1464237001
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = etecsdev
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::ae42:51b0:b2e4:5622/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
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

SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
AirCast          <MAC 'AirCast' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
Airfilter5GHz-2  <MAC 'Airfilter5GHz-2' [AC6]>  Infra  116   5580 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter-guest  <MAC 'Airfilter-guest' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter5GHz    <MAC 'Airfilter5GHz' [AC5]>  Infra  36    5180 MHz  54 Mbit/s  82      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Airfilter2.4GHz  <MAC 'Airfilter2.4GHz' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2       yes     * 
TN_24GHz_EDAA43  <MAC 'TN_24GHz_EDAA43' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2  no        
comhem_4C0517    <MAC 'comhem_4C0517' [AC7]>  Infra  1     2412 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/Airfilter5GHz]] (600 root)
[connection] id=Airfilter5GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter5GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter5GHz-2]] (600 root)
[connection] id=Airfilter5GHz-2 | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter5GHz-2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter2.4GHz]] (600 root)
[connection] id=Airfilter2.4GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC 'wlp2s0' [IF]> | mac-address-blacklist= | ssid=Airfilter2.4GHz
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country SE: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.58 GHz (Channel 116)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'Airfilter2.4GHz' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"Airfilter2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9ddf85be
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Airfilter-guest' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Airfilter-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9ddf9f73
                    Extra: Last beacon: 5048ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'AirCast' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:off
                    ESSID:"AirCast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001f8bdb211
                    Extra: Last beacon: 4928ms ago
          Cell 04 - Address: <MAC 'TN_24GHz_EDAA43' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"TN_24GHz_EDAA43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009d72982ec6
                    Extra: Last beacon: 4480ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Airfilter5GHz' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9ded13b9
                    Extra: Last beacon: 4016ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Airfilter5GHz-2' [AC6]>
                    Channel:116
                    Frequency:5.58 GHz (Channel 116)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:on
                    ESSID:"Airfilter5GHz-2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000a9e110344
                    Extra: Last beacon: 1368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'comhem_4C0517' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"comhem_4C0517"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000010d1ced8120
                    Extra: Last beacon: 5640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
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
options ath10k_core skip_otp=Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   68.186182] ath10k_pci 0000:02:00.0: failed to recalculate rts/cts prot for vdev 0: -108
[   68.186185] ath10k_pci 0000:02:00.0: failed to set protection mode 0 on vdev 0: -108
[   68.186188] ath10k_pci 0000:02:00.0: failed to set erp slot for vdev 0: -108
[   68.186190] ath10k_pci 0000:02:00.0: failed to set preamble for vdev 0: -108
[   68.186193] ath10k_pci 0000:02:00.0: faield to down vdev 0: -108
[   68.186196] ath10k_pci 0000:02:00.0: failed to submit vdev param txbf 0x0: -108
[   68.186197] ath10k_pci 0000:02:00.0: failed to recalc txbf for vdev 0: -108
[   68.186202] ath10k_pci 0000:02:00.0: failed to set vdev wmm params on vdev 0: -108 (repeated 2 times)
[   73.277893] ath10k_warn: 9 callbacks suppressed
[   73.277908] ath10k_pci 0000:02:00.0: failed to start hw scan: -108 (repeated 36 times)
[  121.842966] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  121.849066] ath10k_pci 0000:02:00.0: failed to start hw scan: -108 (repeated 19 times)
[  139.837201] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 1: -108
[  139.837351] ath10k_pci 0000:02:00.0: failed to delete WMI vdev 0: -108
[  139.837359] ath10k_pci 0000:02:00.0: removing stale peer <MAC 'Airfilter5GHz' [AC5]> from vdev_id 0
[  139.837440] ath10k_pci 0000:02:00.0: could not suspend target (-108)
[  146.100943] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  150.028483] wlp2s0: authenticate with <MAC 'Airfilter2.4GHz' [AC1]>
[  150.069151] wlp2s0: send auth to <MAC 'Airfilter2.4GHz' [AC1]> (try 1/3)
[  150.070844] wlp2s0: authenticated
[  150.074377] wlp2s0: associate with <MAC 'Airfilter2.4GHz' [AC1]> (try 1/3)
[  150.078259] wlp2s0: RX AssocResp from <MAC 'Airfilter2.4GHz' [AC1]> (capab=0x411 status=0 aid=2)
[  150.081044] wlp2s0: associated
[  150.081148] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############


```

---

### Post by Emmoth on 2016-05-25
Could it have something to do with diffrent 5GHZ channels ? I'm in Sweden for you info :)

---

### Post by jeremy31 on 2016-05-25
A bug report should be filed on this one against package linux, you can find a guide [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

I don't think it is related to different channels, Kalle Valo is from Finland and you do have the regulatory info set

I would like you to try the other firmware again without the board-2.bin

---

### Post by Emmoth on 2016-05-27
Ok I tried it without the board-2.bin now  without luck. Now the wireless is gone. can't see it.

Here is the dmesg and the wireless-info

```

[   15.574786] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   15.955714] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   16.010661] ath10k_pci 0000:02:00.0: invalid firmware magic
[   16.010735] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[   16.010739] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[   16.010748] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[   16.010751] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[   16.010760] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-2.bin failed with error -2
[   16.010762] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -2
[   16.010771] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware.bin failed with error -2
[   16.010774] ath10k_pci 0000:02:00.0: could not fetch firmware (-2)
[   16.010776] ath10k_pci 0000:02:00.0: could not fetch firmware files (-2)
[   16.010778] ath10k_pci 0000:02:00.0: could not probe fw (-2)

```

```


########## wireless info START ##########

Report from: 27 May 2016 19:25 CEST +0200

Booted last: 27 May 2016 00:00 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-22-generic #40-Ubuntu SMP Thu May 12 22:03:46 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:382e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros QCA6164 802.11ac Wireless Network Adapter [168c:0041] (rev 20)
    Subsystem: Lenovo QCA6164 802.11ac Wireless Network Adapter [17aa:3545]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 004: ID 174f:14ee Syntek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath10k_pci             45056  0
ath10k_core           311296  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              737280  1 ath10k_core
cfg80211              565248  3 ath,mac80211,ath10k_core
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0    Link encap:Ethernet  HWaddr <MAC 'enp1s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       654     1  0 19:24 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/enp1s0
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

[[/etc/NetworkManager/system-connections/Airfilter5GHz]] (600 root)
[connection] id=Airfilter5GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Airfilter5GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CaverionVentTelia2.4]] (600 root)
[connection] id=CaverionVentTelia2.4 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CaverionVentTelia2.4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter5GHz-2]] (600 root)
[connection] id=Airfilter5GHz-2 | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Airfilter5GHz-2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Airfilter2.4GHz]] (600 root)
[connection] id=Airfilter2.4GHz | type=wifi | permissions=user:etecs:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Airfilter2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CaverionVentTelia5]] (600 root)
[connection] id=CaverionVentTelia5 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=CaverionVentTelia5
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

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

enp1s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
srcversion:     275C24567932534F3B81E01
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     018D8EE375DD4919CA4D4B8
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
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
options ath10k_core skip_otp=Y

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   15.574786] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   15.955714] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   16.010661] ath10k_pci 0000:02:00.0: invalid firmware magic
[   16.010735] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-4.bin failed with error -2
[   16.010739] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-4.bin': -2
[   16.010748] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-3.bin failed with error -2
[   16.010751] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-3.bin': -2
[   16.010760] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware-2.bin failed with error -2
[   16.010762] ath10k_pci 0000:02:00.0: could not fetch firmware file 'ath10k/QCA6174/hw2.1/firmware-2.bin': -2
[   16.010771] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/firmware.bin failed with error -2
[   16.010774] ath10k_pci 0000:02:00.0: could not fetch firmware (-2)
[   16.010776] ath10k_pci 0000:02:00.0: could not fetch firmware files (-2)
[   16.010778] ath10k_pci 0000:02:00.0: could not probe fw (-2)
[   31.058149] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready
[   31.119344] r8169 0000:01:00.0 enp1s0: link down (repeated 2 times)
[   31.119510] IPv6: ADDRCONF(NETDEV_UP): enp1s0: link is not ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-05-27
We can try the firmware in the new linux-firmware from Ubuntu
```
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.157_all.deb
sudo dpkg -i linux-firmware_1.157_all.deb
```

Reboot and it gives the same issues, file a bug against package linux-firmware

---

### Post by Emmoth on 2016-05-27
well that didn't work either, the dmesg gives me this

```

[   16.415371] ath10k_pci 0000:02:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   16.975218] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/cal-pci-0000:02:00.0.bin failed with error -2
[   17.214155] ath10k_pci 0000:02:00.0: Direct firmware load for ath10k/QCA6174/hw2.1/board-2.bin failed with error -2
[   18.386407] ath10k_pci 0000:02:00.0: firmware crashed! (uuid 33b06c67-a11c-42a9-819a-92d885f675a4)
[   18.386433] ath10k_pci 0000:02:00.0: qca6164 hw2.1 (0x05010000, 0x003405ff sub 17aa:3545) fw WLAN.RM.1.1-00141 fwapi 5 bdapi 1 htt-ver 0.0 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp,no-4addr-pad
[   18.386437] ath10k_pci 0000:02:00.0: debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   18.388581] ath10k_pci 0000:02:00.0: firmware register dump:
[   18.388585] ath10k_pci 0000:02:00.0: [00]: 0x05010000 0x000015B3 0x000A012D 0x00955B31
[   18.388589] ath10k_pci 0000:02:00.0: [04]: 0x000A012D 0x00060330 0x00000016 0x83785006
[   18.388593] ath10k_pci 0000:02:00.0: [08]: 0x00000000 0x00400000 0x00400600 0x00000001
[   18.388596] ath10k_pci 0000:02:00.0: [12]: 0x00000009 0x00000000 0x00931C61 0x00931C7D
[   18.388600] ath10k_pci 0000:02:00.0: [16]: 0x0096BDBC 0x009287BD 0x00000000 0x00000000
[   18.388603] ath10k_pci 0000:02:00.0: [20]: 0x400A012D 0x0040E2B0 0x00955A00 0x00404590
[   18.388606] ath10k_pci 0000:02:00.0: [24]: 0x809287D9 0x0040E310 0x7A5087F8 0xC00A012D
[   18.388610] ath10k_pci 0000:02:00.0: [28]: 0x809288D7 0x0040E340 0x00000000 0xFFF08040
[   18.388613] ath10k_pci 0000:02:00.0: [32]: 0x809290FE 0x0040E360 0x00400000 0x00400600
[   18.388616] ath10k_pci 0000:02:00.0: [36]: 0x80929205 0x0040E380 0x00000000 0x00400600
[   18.388620] ath10k_pci 0000:02:00.0: [40]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   18.388623] ath10k_pci 0000:02:00.0: [44]: 0x00000000 0x0040E3D0 0x009BB001 0x00040020
[   18.388626] ath10k_pci 0000:02:00.0: [48]: 0x00401BF0 0x00000001 0x00404B9C 0x00400000
[   18.388629] ath10k_pci 0000:02:00.0: [52]: 0x40928024 0x0040E3B0 0x0040D3D0 0x0040D3D0
[   18.388633] ath10k_pci 0000:02:00.0: [56]: 0xA372B200 0x3D63B660 0x4F620356 0x08637F60
[   19.384342] ath10k_pci 0000:02:00.0: failed to receive control response completion, polling..
[   20.384326] ath10k_pci 0000:02:00.0: ctl_resp never came in (-110)
[   20.384337] ath10k_pci 0000:02:00.0: failed to connect to HTC: -110
[   20.460977] ath10k_pci 0000:02:00.0: could not init core (-110)
[   20.461040] ath10k_pci 0000:02:00.0: could not probe fw (-110)
[   20.476355] ath10k_pci 0000:02:00.0: cannot restart a device that hasn't been started


```

I tried 
```

systemctl restart NetworkManager.service

```

The WiFi icon flashed and the networkmanager crashed, so I had to restart it again to get the network up. Still no WiFi tho.

---

### Post by jeremy31 on 2016-05-27
It is time for a bug report then if the firmware from the repo causes issues

---

### Post by Emmoth on 2016-05-27
Yeah. I'll file a bug report first thing tomorrow.

---

### Post by Emmoth on 2016-05-28
Well i did what I said last night and filed a bug report this morning.

But now efter lunch and thought that I should have go at it again so I did check the site where I got the linux-firmware from and found another one, slightlly newer the the one before.

So I ran this command
```

wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.158_all.deb
sudo dpkg -i linux-firmware_1.158_all.deb

```

Rebooted andnow the 2.4GHz and the 5GHz works as they should, they connected me right away and when I check my internet speed I get around 160Mbps down and about 100Mbps up so yeah it works :)

Will mark this Solved now.

---

### Post by jeremy31 on 2016-05-28
That is strange.  The only thing that it could be is that the latest linux-firmware version uses the firmware-5.bin version SW_RM.1.1.1-00157-QCARMSWPZ-1 where your dmesg logs showed that we were trying to use fw WLAN.RM.1.1-00141  but that is what should have happened from my instructions in post 9

At least it finally works

---

### Post by Emmoth on 2016-05-28
Yea. But the weird thing is that I tried all this on my sons computer too, which is exactly the same as mine and the firmware in post 9 didn't work on his either but the one I tried worked. So now both of our computers works as the should.

---

