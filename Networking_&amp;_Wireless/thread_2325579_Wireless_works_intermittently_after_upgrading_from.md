---
title: "Wireless works intermittently after upgrading from 14.04 SP1 to 16.04 LTS"
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by aleddilwynfisher on 2016-05-23
Hi, 

After some problems upgrading to 16.04 LTS, I completely reinstalled Ubuntu using a USB stick. 

Previously, I was on 14.04 SP1 and wireless worked perfectly. I'm using a brand new laptop that came with Ubuntu pre-installed, so can't see why this would be a hardware issue (and, as I've said, the problems began after installing 16.04 LTS). 

Now, wireless works fine most of the time, but suddenly cuts out every now and again, at which point I need to disconnect and reconnect; furthermore, my wireless networks often disappear when coming out of suspend (although I understand that this is not uncommon, it is not a problem I had before installing 16.04 and, again, only happens intermittently). 

As you can probably tell, I am very inexperienced/ignorant when it comes to all things Ubuntu. I followed the instructions on the sticky thread and the wireless-info.txt file is attached to this, and inserted below. I have absolutely no idea how to decipher the information in the file itself, despite searching the forum, so appreciate any help that people can give. There is nothing about Broadcom in the file, if that helps!

```

########## wireless info START ##########

Report from: 23 May 2016 21:15 CEST +0200

Booted last: 23 May 2016 00:00 CEST +0200

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

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:8739]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:5683 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 0bda:b739 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 013: ID 05ac:1297 Apple, Inc. iPhone 4
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
13: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
rtl8723be              86016  0
dell_laptop            20480  0
dcdbas                 16384  1 dell_laptop
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              565248  2 mac80211,rtlwifi
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20u1c4i2 Link encap:Ethernet  HWaddr <MAC 'enp0s20u1c4i2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF]>  
          inet addr:10.0.1.38  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d13:e51:df15:3628/64 Scope:Link
          inet6 addr: 2a02:fe0:c020:410:d5a7:9446:1108:637d/64 Scope:Global
          inet6 addr: 2a02:fe0:c020:410:777d:7776:9220:c9d9/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1903351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1043577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2557994706 (2.5 GB)  TX bytes:100602846 (100.6 MB)

##### iwconfig ##########################

enp0s20u1c4i2  no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11bgn  ESSID:"Narnia"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC 'Narnia' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:124   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.1.1        0.0.0.0         UG    600    0        0 wlp1s0
10.0.1.0        0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search getinternet.no

##### network managers ##################

Installed:

    NetworkManager

Running:

root       882     1  0 May21 ?        00:00:42 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.4.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Narnia
GENERAL.CON-UUID:                       ccc01d0e-07ee-483e-9933-c36ddac79a83
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/22
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{10,16,14,0,11,5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f7d759c9-355a-4371-bda1-1837c8e609ed | Romantika
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   a1c9c5d2-e1f6-47c2-b98b-75ab241f04c8 | The Kasbah 2
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   d5b36e01-2325-4116-9dc6-a05525d4620a | Romantika 1
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   1db761b9-479e-4087-9ef9-96eeb772221d | Elion-362CD8 1
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   a305402c-8212-4bc2-b8bc-fd77035e3100 | SJ 1
CONNECTIONS.AVAILABLE-CONNECTIONS[6]:   ccc01d0e-07ee-483e-9933-c36ddac79a83 | Narnia
IP4.ADDRESS[1]:                         10.0.1.38/24
IP4.GATEWAY:                            10.0.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.0.1.1
IP4.DOMAIN[1]:                          getinternet.no
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1464117158
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 10.0.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.0.1.38
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = getinternet.no
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
IP6.ADDRESS[1]:                         2a02:fe0:c020:410:d5a7:9446:1108:637d/64
IP6.ADDRESS[2]:                         2a02:fe0:c020:410:777d:7776:9220:c9d9/64
IP6.ADDRESS[3]:                         fe80::d13:e51:df15:3628/64
IP6.GATEWAY:                            fe80::8a1f:a1ff:fe2b:a5c
IP6.ROUTE[1]:                           dst = 2a02:fe0:c020:410::/60, nh = fe80::8a1f:a1ff:fe2b:a5c, mt = 600
IP6.DNS[1]:                             2a02:fe0:c020:410:8a1f:a1ff:fe2b:a5c
IP6.DOMAIN[1]:                          getinternet.no
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:b9:ba:9:ec:46:6f:bd:d:e:9f:fd:e:c7:a6:9c:21
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:fe0:c020:410:8a1f:a1ff:fe2b:a5c
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = getinternet.no.
DHCP6.OPTION[7]:                        dhcp6_preference = 255
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:0:1:1e:c6:eb:9c:8a:21:22:35:a1:10

GENERAL.DEVICE:                         enp0s20u1c4i2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Apple Inc.
GENERAL.PRODUCT:                        iPhone
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s20u1c4i2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:4.2/net/enp0s20u1c4i2
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

SSID                         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Klesskapet                   <MAC 'Klesskapet' [AC3]>  Infra  13    2472 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Mr. WiFi                     <MAC 'Mr. WiFi' [AC14]>  Infra  6     2437 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Styrets nettverk             <MAC 'Styrets nettverk' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Søndre Åsens gjestenettverk  <MAC 'Søndre Åsens gjestenettverk' [AC17]>  Infra  6     2437 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
Narnia                       <MAC 'Narnia' [AC4]>  Infra  13    2472 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
l337n37                      <MAC 'l337n37' [AC16]>  Infra  6     2437 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2       no        
Getbox-9DA5C0                <MAC 'Getbox-9DA5C0' [AC15]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Small Wireless               <MAC 'Small Wireless' [AC11]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       no        
Narnia                       <MAC 'Narnia' [AC1]>  Infra  13    2472 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2       yes     * 
Hjemme-Nett                  <MAC 'Hjemme-Nett' [AC9]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Penthouse5G                  <MAC 'Penthouse5G' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
ilovesnouti                  <MAC 'ilovesnouti' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2       no        
AirLink224810                <MAC 'AirLink224810' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1       no        
LegoLove                     <MAC 'LegoLove' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no        
Getbox-9E1EB0                <MAC 'Getbox-9E1EB0' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Getbox-25018C                <MAC 'Getbox-25018C' [AC2]>  Infra  13    2472 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Get-360490Superbredband      <MAC 'Get-360490Superbredband' [AC10]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Getbox-7CBF23                <MAC 'Getbox-7CBF23' [AN18]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
impaw                        <MAC 'impaw' [AC18]>  Infra  10    2457 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2       no        
Getbox-EF4833                <MAC 'Getbox-EF4833' [AN20]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Penthouse                    <MAC 'Penthouse' [AC5]>  Infra  12    2467 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/JOSEPHINE]] (600 root)
[connection] id=JOSEPHINE | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=JOSEPHINE
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=eduroam
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/mycloud]] (600 root)
[connection] id=mycloud | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=mycloud
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Romantika]] (600 root)
[connection] id=Romantika | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Romantika
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/The Kasbah 2]] (600 root)
[connection] id=The Kasbah 2 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=The Kasbah 2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Romantika 1]] (600 root)
[connection] id=Romantika 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Romantika
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Victoria Premium]] (600 root)
[connection] id=Victoria Premium | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Victoria Premium
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Zocalo WiFi]] (600 root)
[connection] id=Zocalo WiFi | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Zocalo WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Victoria]] (600 root)
[connection] id=Victoria | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Victoria
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/The Kasbah]] (600 root)
[connection] id=The Kasbah | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=The Kasbah
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SJ 1]] (600 root)
[connection] id=SJ 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=SJ
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Gjestenett Holmen Fjordhotell]] (600 root)
[connection] id=Gjestenett Holmen Fjordhotell | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Gjestenett Holmen Fjordhotell
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Elion-362CD8 1]] (600 root)
[connection] id=Elion-362CD8 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Elion-362CD8
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SJ]] (600 root)
[connection] id=SJ | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=SJ
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Elion-362CD8]] (600 root)
[connection] id=Elion-362CD8 | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Elion-362CD8
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/uio]] (600 root)
[connection] id=uio | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=uio
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Narnia]] (600 root)
[connection] id=Narnia | type=wifi | permissions=user:aled:;
[wifi] mac-address=<MAC 'wlp1s0' [IF]> | mac-address-blacklist= | ssid=Narnia
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Stockholm (based on set time zone)

country NO: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 23), (N/A)
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), DFS
    (5470 - 5795 @ 160), (N/A, 26), (0 ms), DFS
    (5815 - 5850 @ 35), (N/A, 33), (0 ms), DFS
    (17100 - 17300 @ 200), (N/A, 20), (N/A)
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp0s20u1c4i2  no frequency information.

lo        no frequency information.

wlp1s0    13 channels in total; available frequencies :
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
          Current Frequency:2.472 GHz (Channel 13)

##### iwlist scan #######################

enp0s20u1c4i2  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)
      4   APs on   Frequency:2.472 GHz (Channel 13)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'Narnia' [AC1]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Narnia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e7776514ff
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Getbox-25018C' [AC2]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Getbox-25018C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009222ebc76
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Klesskapet' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Klesskapet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e777652ed1
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Narnia' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Narnia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000dd24b08a95
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Penthouse' [AC5]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Penthouse"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000021fb6a16f
                    Extra: Last beacon: 188ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Getbox-9E1EB0' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Getbox-9E1EB0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d1bf5af13a
                    Extra: Last beacon: 264ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Get-525615' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Get-525615"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002488e3e482
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'Penthouse5G' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Penthouse5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000004640a2
                    Extra: Last beacon: 68ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Hjemme-Nett' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Hjemme-Nett"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000037b77593c
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Get-360490Superbredband' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Get-360490Superbredband"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000038a1f34b219
                    Extra: Last beacon: 4256ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'Small Wireless' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Small Wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000047e44c7dd76
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'Styrets nettverk' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Styrets nettverk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001499bf849ea7
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'AirLink224810' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"AirLink224810"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025121eb4183
                    Extra: Last beacon: 2908ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Mr. WiFi' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Mr. WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000092629170eb4
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'Getbox-9DA5C0' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Getbox-9DA5C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000047e41168162
                    Extra: Last beacon: 2584ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'l337n37' [AC16]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"l337n37"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002aac9c49d
                    Extra: Last beacon: 2576ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 17 - Address: <MAC 'Søndre Åsens gjestenettverk' [AC17]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"S\xC3\xB8ndre \xC3\x85sens gjestenettverk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001499bf83ebf3
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'impaw' [AC18]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"impaw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000e6258dd19a
                    Extra: Last beacon: 1136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     935DB8E91ADCC9A3C200D60
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     AC6426E73F4CB059EE7332C
depends:        
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[rtl_pci]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CCAF123FC0D21AE93AD5A6F
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-22-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-22-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
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

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[38098.261902] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[38098.261909] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[38098.261942] WARNING: CPU: 0 PID: 14144 at /build/linux-FvcHlK/linux-4.4.0/drivers/base/firmware_class.c:1147 _request_firmware+0x7cf/0xb00()
[38098.262526]  [<ffffffff815604df>] _request_firmware+0x7cf/0xb00
[38098.262552]  [<ffffffff81560841>] request_firmware+0x31/0x50
[38098.262566]  [<ffffffffc038e275>] btrtl_setup_rtl8723b+0x55/0x500 [btrtl]
[38098.262933] bluetooth hci0: firmware: rtl_bt/rtl8723b_fw.bin will not be loaded
[38098.262942] Bluetooth: hci0: Failed to load rtl_bt/rtl8723b_fw.bin
[38103.812185] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[38103.812198] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[38103.849827] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 3 times)
[38107.006869] wlp1s0: authenticate with <MAC 'Narnia' [AC1]>
[38107.620946] wlp1s0: send auth to <MAC 'Narnia' [AC1]> (try 1/3)
[38107.626293] wlp1s0: authenticated
[38107.634577] wlp1s0: associate with <MAC 'Narnia' [AC1]> (try 1/3)
[38107.639541] wlp1s0: RX AssocResp from <MAC 'Narnia' [AC1]> (capab=0x1411 status=0 aid=3)
[38107.640493] wlp1s0: associated
[38107.640578] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[38107.733316] wlp1s0: Limiting TX power to 20 (20 - 0) dBm as advertised by <MAC 'Narnia' [AC1]>
[38170.555336] ipheth 1-1:4.2 enp0s20u1c4i2: renamed from eth0
[38170.615024] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1c4i2: link is not ready (repeated 2 times)

########## wireless info END ############


```

Best wishes,
Aled

---

### Post by aleddilwynfisher on 2016-06-05
Is there anyone who can help with this? I'm still having the same problems, despite installing a Realtek firmware package that I've seen recommended at other Ubuntu resources. 

Any help is massively appreciated!

Aled

---

### Post by jeremy31 on 2016-06-05
We can try the usuall fix for rtl8723be chips
```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

reboot

---

