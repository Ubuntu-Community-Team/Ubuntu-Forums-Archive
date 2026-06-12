---
title: "Airplane Mode issue"
date: 2018-10-05
forum: Networking &amp; Wireless
---

### Post by husamfarra on 2018-10-05
Hi All 

I do have a serious issue about Airplane mode its always disconnect the WiFi.

 Thanks

---

### Post by jeremy31 on 2018-10-05
Moved to Networking & Wireless
Please see the wireless script link in my signature and post results

---

### Post by praseodym on 2018-10-05
Of course, airplane mode deactivates wifi?! What is the issue? Doesn't it reconnect afterwards?

---

### Post by husamfarra on 2018-10-07
Thank you, I installed the Script, what you want me to do?

---

### Post by husamfarra on 2018-10-07
the problem is i cant disable the air plan mode,it still working on the background, and  it keep disconnect the wifi

---

### Post by husamfarra on 2018-10-07
O i have Thinkpad laptob, and am using wifi stick since no driver are available 



########## wireless info START ##########


Report from: 07 Oct 2018 08:03 +03 +0300


Booted last: 07 Oct 2018 00:00 +03 +0300


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:505b]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter [10ec:c821]
    Subsystem: Lenovo RTL8821CE 802.11ac PCIe Wireless Network Adapter [17aa:c024]


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 005: ID 0bda:58db Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0458:6001 KYE Systems Corp. (Mouse Systems) GF3000F Ethernet Adapter
Bus 001 Device 002: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no


##### lsmod #############################


r8188eu               421888  0
cfg80211              622592  1 r8188eu
wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 4307803  bytes 386802439 (386.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 4307803  bytes 386802439 (386.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlxc025e90fa378: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.8.101  netmask 255.255.255.0  broadcast 192.168.8.255
        inet6 fe80::2a53:e09c:2f58:6dbd  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 37814  bytes 44083950 (44.0 MB)
        RX errors 0  dropped 370  overruns 0  frame 0
        TX packets 21825  bytes 4952072 (4.9 MB)
        TX errors 0  dropped 18 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlxc025e90fa378  IEEE 802.11bgn  ESSID:"HUAWEI-D42A"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.452 GHz  Access Point:   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=70/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.1     0.0.0.0         UG    600    0        0 wlxc025e90fa378
  255.255.0.0     U     1000   0        0 wlxc025e90fa378
192.168.8.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxc025e90fa378


##### resolv.conf #######################


nameserver 127.0.0.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      6018     1  0 07:40 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlxc025e90fa378
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlxc025e90fa378
GENERAL.IP-IFACE:                       wlxc025e90fa378
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:  
GENERAL.CON-UUID:  
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.8.101/24
IP4.GATEWAY:                            192.168.8.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.8.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.8.0/24, nh = 0.0.0.0, mt = 600
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.8.1
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        network_number = 192.168.8.0
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        expiry = 1538973992
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.8.101
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.8.255
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       routers = 192.168.8.1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.8.1
DHCP4.OPTION[29]:                       domain_name_servers = 192.168.8.1 192.168.8.1
IP6.ADDRESS[1]:                         fe80::2a53:e09c:2f58:6dbd/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 600
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   69639d1e-d968-46a4-b4da-52b9f7c274b6 | HUAWEI-D42A


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:04:00.0/net/enp4s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
HUAWEI-D42A  <MAC 'HUAWEI-D42A' [AC1]>  Infra  9     2452 MHz  16 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     *      
DIR-615      <MAC 'DIR-615' [AN2]>  Infra  6     2437 MHz  44 Mbit/s  44      &#9602;&#9604;__  --         no             


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


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/HAMZA]] (600 root)
[connection] id=HAMZA | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HAMZA
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HBKGuest]] (600 root)
[connection] id=HBKGuest | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HBKGuest
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Shahid]] (600 root)
[connection] id=Shahid | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Shahid
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/METROPOLITAN-PUBLIC]] (600 root)
[connection] id=METROPOLITAN-PUBLIC | type=wifi |  
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=METROPOLITAN-PUBLIC
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI-CA00]] (600 root)
[connection] id=HUAWEI-CA00 | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI-CA00
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/FJT-ACCO]] (600 root)
[connection] id=FJT-ACCO | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FJT-ACCO
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/KAEFER]] (600 root)
[connection] id=KAEFER | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=KAEFER
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/METROPOLITAN-CONFERENCE]] (600 root)
[connection] id=METROPOLITAN-CONFERENCE | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=METROPOLITAN-CONFERENCE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HW-4G-MobileWiFi-1B07]] (600 root)
[connection] id=HW-4G-MobileWiFi-1B07 | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HW-4G-MobileWiFi-1B07
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HTC Portable Hotspot 8D0C]] (600 root)
[connection] id=HTC Portable Hotspot 8D0C | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HTC Portable Hotspot 8D0C
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MUEHLHAN-5]] (600 root)
[connection] id=MUEHLHAN-5 | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MUEHLHAN-5
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI-D42A]] (600 root)
[connection] id=HUAWEI-D42A | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI-D42A
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HP-Print-41-Deskjet 2540 series]] (600 root)
[connection] id=HP-Print-41-Deskjet 2540 series | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HP-Print-41-Deskjet 2540 series
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HUAWEI-CA00 1]] (600 root)
[connection] id=HUAWEI-CA00 1 | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=HUAWEI-CA00
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/**** you ]] (600 root)
[connection] id=**** you  | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=**** you 
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DERE]] (600 root)
[connection] id=DERE | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DERE
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Rumman]] (600 root)
[connection] id=Rumman | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Rumman
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/DIRECT-75-HP DeskJet 4530 series]] (600 root)
[connection] id=DIRECT-75-HP DeskJet 4530 series | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DIRECT-75-HP DeskJet 4530 series
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/kaefer_office]] (600 root)
[connection] id=kaefer_office | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=kaefer_office
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/chi]] (600 root)
[connection] id=chi | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=chi
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/METROPOLITAN-GUEST]] (600 root)
[connection] id=METROPOLITAN-GUEST | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=METROPOLITAN-GUEST
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/City Centre Rotana]] (600 root)
[connection] id=City Centre Rotana | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=City Centre Rotana
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/husam_nomap]] (600 root)
[connection] id=husam_nomap | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=husam_nomap
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Roots-Energy]] (600 root)
[connection] id=Roots-Energy | type=wifi | permissions=user:husam:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Roots-Energy
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: Asia/Qatar (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp4s0    no frequency information.


wlxc025e90fa378  13 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)


wlxc025e90fa378  Scan completed :
          Cell 01 - Address: <MAC 'HUAWEI-D42A' [AC1]>
                    ESSID:"HUAWEI-D42A"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.452 GHz (Channel 9)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=100/100  Signal level=67/100  
          Cell 02 - Address: <MAC '' [AC2]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=23/100  


##### module infos ######################


[r8188eu]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     F8246795A04531CE815E5AD
depends:        cfg80211
staging:        Y
retpoline:      Y
intree:         Y
name:           r8188eu
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)
parm:           monitor_enable:Enable monitor inferface (default: false) (bool)


[cfg80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
monitor_enable: N
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1


[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode


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


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   25.691813] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[   25.880456] r8188eu 1-2:1.0 wlxc025e90fa378: renamed from wlan0
[   33.258123] IPv6: ADDRCONF(NETDEV_UP): wlxc025e90fa378: link is not ready (repeated 3 times)
[  418.455952] IPv6: ADDRCONF(NETDEV_CHANGE): wlxc025e90fa378: link becomes ready
[ 1245.460920] R8188EU: linked_status_chk(wlxc025e90fa378) disconnect or roaming


########## wireless info END ############

---

### Post by praseodym on 2018-10-07
Driver for the internal card:

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Reboot and deactivate SecureBoot

---

