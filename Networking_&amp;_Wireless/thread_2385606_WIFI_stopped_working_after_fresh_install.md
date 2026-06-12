---
title: "WIFI stopped working after fresh install"
date: 2018-02-22
forum: Networking &amp; Wireless
---

### Post by alex184 on 2018-02-22
I just did a fresh install of Ubuntu Studios 16.04 64-bit. During installation and afterwards WIFI was working fine, then a few restarts later it began to no longer connect to any network. I can't figure out what I must have done, I basically only upgraded Firefox, did a apt-get update and dist-upgrade. If I run the live USB I can connect just fine. Any suggestions?

```
########## wireless info START ##########

Report from: 22 Feb 2018 18:00 CET +0100

Booted last: 22 Feb 2018 00:00 CET +0100

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-36-lowlatency #40~16.04.1-Ubuntu SMP PREEMPT Sat Feb 17 00:18:34 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

1b:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a38]
    Kernel driver in use: r8169

1d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:818b]
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8192EE PCIe Wireless Network Adapter [10ec:8196]
    Kernel driver in use: rtl8192ee

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046a:b090 Cherry GmbH 
Bus 003 Device 002: ID 046d:c332 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wmi_bmof               16384  0
rtl8192ee             114688  0
btcoexist             131072  1 rtl8192ee
rtl_pci                32768  1 rtl8192ee
rtlwifi                77824  3 rtl8192ee,rtl_pci,btcoexist
mac80211              794624  3 rtl8192ee,rtl_pci,rtlwifi
cfg80211              626688  2 mac80211,rtlwifi
wmi                    24576  1 wmi_bmof

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp27s0   Link encap:Ethernet  HWaddr <MAC 'enp27s0' [IF1]>  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:8109:9a40:1add:4046:2959:d6d1:4224/64 Scope:Global
          inet6 addr: 2a02:8109:9a40:1add:913:ccc8:2afc:da08/64 Scope:Global
          inet6 addr: fe80::a67e:80e5:ba1e:8d29/64 Scope:Link
          inet6 addr: 2a02:8109:9a40:1add:eade:c8c7:aee0:46b/64 Scope:Global
          inet6 addr: 2a02:8109:9a40:1add:e1be:979b:5f49:5dcd/64 Scope:Global
          inet6 addr: 2a02:8109:9a40:1add:8b31:2241:bacd:717c/64 Scope:Global
          inet6 addr: 2a02:8109:9a40:1add:992:1062:f100:2ab1/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23654 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18586364 (18.5 MB)  TX bytes:1720524 (1.7 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256973 (256.9 KB)  TX bytes:256973 (256.9 KB)

wlp29s0   Link encap:Ethernet  HWaddr <MAC 'wlp29s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp27s0   no wireless extensions.

lo        no wireless extensions.

wlp29s0   IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp27s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp27s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp27s0

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root      3741     1  0 17:15 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp27s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168h-2_0.0.2 02/26/15
GENERAL.HWADDR:                         <MAC 'enp27s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/1
GENERAL.IP-IFACE:                       enp27s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     enp27s0
GENERAL.CON-UUID:                       0b6cd462-1629-45a2-a1f3-e075f2cab166
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c28784b7-54b2-3d1d-8b10-e52597e33a26 | Wired connection 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   0b6cd462-1629-45a2-a1f3-e075f2cab166 | enp27s0
IP4.ADDRESS[1]:                         192.168.0.8/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        default_ip_ttl = 64
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        host_name = Ginkgo-PC
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_netbios_scope = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       expiry = 1519321506
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_message_type = 5
DHCP4.OPTION[17]:                       ip_address = 192.168.0.8
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 3600
DHCP4.OPTION[25]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         2a02:8109:9a40:1add:992:1062:f100:2ab1/64
IP6.ADDRESS[2]:                         2a02:8109:9a40:1add:4046:2959:d6d1:4224/64
IP6.ADDRESS[3]:                         2a02:8109:9a40:1add:e1be:979b:5f49:5dcd/64
IP6.ADDRESS[4]:                         2a02:8109:9a40:1add:913:ccc8:2afc:da08/64
IP6.ADDRESS[5]:                         2a02:8109:9a40:1add:8b31:2241:bacd:717c/64
IP6.ADDRESS[6]:                         2a02:8109:9a40:1add:eade:c8c7:aee0:46b/64
IP6.ADDRESS[7]:                         fe80::a67e:80e5:ba1e:8d29/64
IP6.GATEWAY:                            fe80::ae22:5ff:fe61:18bb
IP6.ROUTE[1]:                           dst = 2a02:8109:9a40:1add::/64, nh = fe80::ae22:5ff:fe61:18bb, mt = 100
IP6.DNS[1]:                             2a02:8109:9a40:1add:ae22:5ff:fe61:18bb
IP6.DOMAIN[1]:                          home
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:ad:7a:82:89:69:8c:5a:ee:67:0:e:b6:1c:25:81:dc
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2a02:8109:9a40:1add:ae22:5ff:fe61:18bb
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[5]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[6]:                        dhcp6_domain_search = home.
DHCP6.OPTION[7]:                        dhcp6_preference = 0
DHCP6.OPTION[8]:                        dhcp6_server_id = 0:1:3:1:22:21:88:62:2a:2:81:9:80:0:0:34:d1:9e:7b:9c:f2:5a:b8:29

GENERAL.DEVICE:                         wlp29s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8192EE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8192ee
GENERAL.DRIVER-VERSION:                 4.13.0-36-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp29s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.3/0000:03:00.2/0000:16:06.0/0000:1d:00.0/net/wlp29s0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   f561626c-9e28-49e5-8841-0ceec2e509f1 | KabelBox-421C

SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Vodafone Homespot  <MAC 'Vodafone Homespot' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  --         no        
KabelBox-421C      <MAC 'KabelBox-421C' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
KDG-51CDA          <MAC 'KDG-51CDA' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  --         no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --         no        
koGast             <MAC 'koGast' [AC6]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        

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

[[/etc/NetworkManager/system-connections/KabelBox-421C]] (600 root)
[connection] id=KabelBox-421C | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp29s0' [IF2]> | mac-address-blacklist= | ssid=KabelBox-421C
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

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

enp27s0   no frequency information.

lo        no frequency information.

wlp29s0   13 channels in total; available frequencies :
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

##### iwlist scan #######################

enp27s0   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      6   APs on   Frequency:2.412 GHz (Channel 1)

wlp29s0   Scan completed :
          Cell 01 - Address: <MAC 'Vodafone Homespot' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Homespot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000002979955ee
                    Extra: Last beacon: 807ms ago
          Cell 02 - Address: <MAC 'Vodafone Hotspot' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000297994ccd
                    Extra: Last beacon: 904ms ago
          Cell 03 - Address: <MAC 'KabelBox-421C' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"KabelBox-421C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000029799421b
                    Extra: Last beacon: 907ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'KDG-51CDA' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"KDG-51CDA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7d0247173
                    Extra: Last beacon: 909ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Vodafone Hotspot' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Vodafone Hotspot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c7d022e173
                    Extra: Last beacon: 1012ms ago
          Cell 06 - Address: <MAC 'koGast' [AC6]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"koGast"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f47e89180
                    Extra: Last beacon: 1039ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ee]
filename:       /lib/modules/4.13.0-36-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192ee/rtl8192ee.ko
firmware:       rtlwifi/rtl8192eefw.bin
description:    Realtek 8192EE 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     020E653CD1653FB5C691637
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
name:           rtl8192ee
vermagic:       4.13.0-36-lowlatency SMP preempt mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.13.0-36-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     5420D01192151E61E4996F0
depends:        mac80211,rtlwifi
intree:         Y
name:           rtl_pci
vermagic:       4.13.0-36-lowlatency SMP preempt mod_unload 

[rtlwifi]
filename:       /lib/modules/4.13.0-36-lowlatency/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     13660D4EA770EA7108332E6
depends:        mac80211,cfg80211
intree:         Y
name:           rtlwifi
vermagic:       4.13.0-36-lowlatency SMP preempt mod_unload 

[mac80211]
filename:       /lib/modules/4.13.0-36-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8F500F2EE3AF9C7436BAEE
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-36-lowlatency SMP preempt mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-36-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-36-lowlatency SMP preempt mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192ee]
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: Y
swenc: Y
swlps: N

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[ 2890.950077] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 2891.966633] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 2891.999171] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 2892.652252] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 2893.676282] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 2894.628954] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 2905.684857] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 2905.717462] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 2906.641910] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 2907.636761] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 2908.638216] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 2915.951316] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3216.984933] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3217.017537] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3217.649444] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3218.656912] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3219.652975] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3230.694592] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3230.727373] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3231.630451] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3232.654462] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3233.649262] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3240.956551] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3241.971609] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3242.004423] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3242.668962] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3243.633401] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3244.657978] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3255.707912] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3255.740620] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3256.625537] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3257.640511] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3258.643869] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3265.956614] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3266.973157] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3267.005801] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3267.654720] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3268.657700] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3269.669252] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3280.710176] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3280.742932] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3281.649830] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3282.656945] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3283.629242] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3290.956872] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3291.971472] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3292.004198] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3292.640575] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3293.665069] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3294.642403] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3305.688870] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3305.721393] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3306.670644] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3307.643143] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3308.641554] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3315.957089] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3616.992194] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3617.024860] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3617.653574] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3618.655805] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3619.633018] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3630.675226] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3630.707793] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3631.669709] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3632.629695] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3633.635283] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3640.961111] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3643.989298] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3644.022157] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3644.643866] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3645.643009] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3646.645840] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3657.690158] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3657.722788] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3658.645705] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3659.669710] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3660.640895] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3665.960479] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3666.975591] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3667.008234] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3667.657070] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3668.656519] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3669.651869] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3680.706233] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3680.738917] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3681.654119] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3682.638333] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3683.634031] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3690.961069] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready
[ 3691.977775] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3692.010286] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3692.662208] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3693.667072] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3694.637982] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3705.685846] wlp29s0: authenticate with <MAC 'KabelBox-421C' [AC3]>
[ 3705.718386] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 1/3)
[ 3706.647855] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 2/3)
[ 3707.638320] wlp29s0: send auth to <MAC 'KabelBox-421C' [AC3]> (try 3/3)
[ 3708.662325] wlp29s0: authentication with <MAC 'KabelBox-421C' [AC3]> timed out
[ 3715.961242] IPv6: ADDRCONF(NETDEV_UP): wlp29s0: link is not ready

########## wireless info END ############
```

EDIT: It's a desktop PC with a TP Link TL-WN881ND

---

