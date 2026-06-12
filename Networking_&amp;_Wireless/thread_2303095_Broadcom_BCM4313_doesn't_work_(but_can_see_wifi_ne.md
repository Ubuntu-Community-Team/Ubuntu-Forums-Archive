---
title: "Broadcom BCM4313 doesn't work (but can see wifi networks), Ubuntu Studio 15.10"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by Hyenaz on 2015-11-16
Hi all,

Firstly, thanks in advance for taking the time to look into the problem. We are new to linux.

We have a Lenovo B580 with "Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)" and Ubuntu Studio 15.10

At the moment, we can see wifi networks and can connect to them, but websites, email etc fail to load. Oddly, the same model of laptop running the same Ubuntu version as well as our android phones can access the internet without a hitch.

Here is our wireless-info.txt:

```


########## wireless info START ##########

Report from: 16 Nov 2015 12:21 CET +0100

Booted last: 16 Nov 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-18-lowlatency #22-Ubuntu SMP PREEMPT Fri Nov 6 20:09:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   417792  0
mac80211              745472  2 b43,brcmsmac
cfg80211              557056  3 b43,brcmsmac,mac80211
ssb                    65536  1 b43
bcma                   53248  3 b43,brcmsmac
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx52d7fc419f14 Link encap:Ethernet  HWaddr <MAC 'enx52d7fc419f14' [IF]>  
          inet addr:192.168.42.191  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx52d7fc419f14' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:843317 (843.3 KB)  TX bytes:400911 (400.9 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp2s0b1' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0b1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:147430 (147.4 KB)  TX bytes:97256 (97.2 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

enx52d7fc419f14  no wireless extensions.

lo        no wireless extensions.

wlp2s0b1  IEEE 802.11bgn  ESSID:"UPC1929224"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'UPC1929224' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:485  Invalid misc:167   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx52d7fc419f14
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0b1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0b1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0b1
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx52d7fc419f14

##### resolv.conf #######################

nameserver 127.0.1.1
search chello.hu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       633     1  0 12:14 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx52d7fc419f14
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         asus
GENERAL.PRODUCT:                        Nexus 7
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx52d7fc419f14' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/net/enx52d7fc419f14
GENERAL.IP-IFACE:                       enx52d7fc419f14
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       a51be4c8-b585-45bf-b6c2-6be97445c811
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a51be4c8-b585-45bf-b6c2-6be97445c811 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.191/24
IP4.GATEWAY:                            192.168.42.129
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.191
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1447676465
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = Alfabus
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx52d7fc419f14' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-18-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlp2s0b1
GENERAL.IP-IFACE:                       wlp2s0b1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     UPC1929224
GENERAL.CON-UUID:                       90954600-7bd1-4e96-ae8d-b69c67ef6d4d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   90954600-7bd1-4e96-ae8d-b69c67ef6d4d | UPC1929224
IP4.ADDRESS[1]:                         192.168.0.20/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             213.46.246.53
IP4.DNS[2]:                             213.46.246.54
IP4.DOMAIN[1]:                          chello.hu
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1447762410
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       domain_name = chello.hu
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.20
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 213.46.246.53 213.46.246.54
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0b1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID           BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X       no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X       no        
tobias         <MAC 'tobias' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2         no        
UPC3350494     <MAC 'UPC3350494' [AC21]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2         no        
Erzsok         <MAC 'Erzsok' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2         no        
UPC1929224     <MAC 'UPC1929224' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA1 WPA2         yes     * 
MCIgazsagPoni  <MAC 'MCIgazsagPoni' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC5967383     <MAC 'UPC5967383' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X       no        
UPC6245610     <MAC 'UPC6245610' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2 802.1X  no        
UPC0091477     <MAC 'UPC0091477' [AC19]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC15]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC3986570     <MAC 'UPC3986570' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
balazs         <MAC 'balazs' [AN17]>  Infra  13    2472 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AN18]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2 802.1X       no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
T-7206F0       <MAC 'T-7206F0' [AC14]>  Infra  8     2447 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free    <MAC 'UPC Wi-Free' [AC18]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X       no        
DISZNO         <MAC 'DISZNO' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2         no        

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

[[/etc/NetworkManager/system-connections/HITRON-A9D0]] (600 root)
[connection] id=HITRON-A9D0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=HITRON-A9D0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC1929224]] (600 root)
[connection] id=UPC1929224 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=UPC1929224
[ipv4] method=auto
[ipv6] method=auto

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

enp3s0    no frequency information.

enx52d7fc419f14  no frequency information.

lo        no frequency information.

wlp2s0b1  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

enx52d7fc419f14  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      14   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      6   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'UPC1929224' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"UPC1929224"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011e61bd90
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'tobias' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"tobias"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ff94aea43
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'UPC Wi-Free' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ff94b1dc7
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'UPC Wi-Free' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fecffc180
                    Extra: Last beacon: 552ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'MCIgazsagPoni' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"MCIgazsagPoni"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000800386f1f1
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'UPC Wi-Free' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001367c1aa6a
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'UPC Wi-Free' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000011e6254b5
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'DISZNO' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"DISZNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001519218d1d2
                    Extra: Last beacon: 310ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'UPC5967383' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC5967383"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fed047180
                    Extra: Last beacon: 194ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'Erzsok' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Erzsok"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015161308b2b
                    Extra: Last beacon: 287ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'UPC3986570' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC3986570"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a8e2c19b
                    Extra: Last beacon: 868ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'UPC Wi-Free' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000080038a13d1
                    Extra: Last beacon: 182ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'UPC6245610' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UPC6245610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001367d41195
                    Extra: Last beacon: 219ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'T-7206F0' [AC14]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"T-7206F0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000015160209c0b
                    Extra: Last beacon: 4120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'UPC Wi-Free' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013a8edb180
                    Extra: Last beacon: 203ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 16 - Address: <MAC 'UPC Wi-Free' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3200007fef577521
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC 'UPC Wi-Free' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b5ca43d57
                    Extra: Last beacon: 5010ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 18 - Address: <MAC 'UPC Wi-Free' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000228c33b857
                    Extra: Last beacon: 4747ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'UPC0091477' [AC19]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"UPC0091477"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000411bcf61f0
                    Extra: Last beacon: 741ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'UPC7786961' [AC20]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC7786961"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b5ce44180
                    Extra: Last beacon: 763ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'UPC3350494' [AC21]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"UPC3350494"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fef57369d
                    Extra: Last beacon: 94ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[b43]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     EBCFBB62711AEC753D1C919
depends:        ssb,bcma,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
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

[mac80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     B9B638C64CE9AC05F1A1903
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[bcma]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

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

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[    9.118062] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[    9.118068] b43: probe of bcma0:1 failed with error -524
[    9.648683] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[    9.717942] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[    9.942320] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   41.444317] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   41.700427] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   41.700438] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   41.701094] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   41.702575] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   41.847881] r8169 0000:03:00.0 enp3s0: link down
[   41.847940] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   41.916400] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   42.859355] wlp2s0b1: authenticate with <MAC 'UPC1929224' [AC1]>
[   42.862984] wlp2s0b1: send auth to <MAC 'UPC1929224' [AC1]> (try 1/3)
[   42.890787] wlp2s0b1: authenticated
[   42.891199] wlp2s0b1: associate with <MAC 'UPC1929224' [AC1]> (try 1/3)
[   42.951889] wlp2s0b1: RX AssocResp from <MAC 'UPC1929224' [AC1]> (capab=0x1411 status=0 aid=2)
[   42.952488] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[   42.952492] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   42.952500] wlp2s0b1: associated
[   42.952547] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0b1: link becomes ready
[   44.334553] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  159.793909] rndis_host 1-4:1.0 enx52d7fc419f14: renamed from usb0
[  159.819034] IPv6: ADDRCONF(NETDEV_UP): enx52d7fc419f14: link is not ready

########## wireless info END ############

```

We tried a few solutions that people had posted who also had BCM4313 [14e4:4727] (rev 01) without any luck.

Any help you can offer would be wonderful.

Many thanks,

HYENAZ

Kate + Adrienne

---

### Post by Hadaka on 2015-11-16
Hi, open a terminal ctrl/alt/t then COPY and paste one line at a time..
```
sudo su
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
then do..
```
sudo iw reg set DE
sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
```

boot,test wireless

---

### Post by Hyenaz on 2015-11-16
Hi, thanks for replying. We completed the above, but still no luck. 
Is there anything else we can try?

---

### Post by Hadaka on 2015-11-16
Hi, yes, Please run again the wireless script and post the results.
meantime you can edit your network connection configuration and make it  look like the attaced
click the wifi signal icon and then Edit connections to change.
 [ATTACH=CONFIG]265611[/ATTACH][ATTACH=CONFIG]265612[/ATTACH]

---

### Post by Hyenaz on 2015-11-16
Thanks a lot.
Here is the wireless info script run a second time:

```


########## wireless info START ##########

Report from: 16 Nov 2015 19:43 CET +0100

Booted last: 16 Nov 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-18-lowlatency #22-Ubuntu SMP PREEMPT Fri Nov 6 20:09:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

03:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 18d1:4ee3 Google Inc. Nexus 4 (tether)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              745472  1 brcmsmac
cfg80211              557056  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx52d7fc419f14 Link encap:Ethernet  HWaddr <MAC 'enx52d7fc419f14' [IF]>  
          inet addr:192.168.42.191  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx52d7fc419f14' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45687 errors:7 dropped:0 overruns:0 frame:7
          TX packets:32629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62052386 (62.0 MB)  TX bytes:4545618 (4.5 MB)

wlp2s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp2s0b1' [IF]>  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp2s0b1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:498595 (498.5 KB)  TX bytes:201119 (201.1 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

enx52d7fc419f14  no wireless extensions.

lo        no wireless extensions.

wlp2s0b1  IEEE 802.11bgn  ESSID:"UPC1929224"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'UPC1929224' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:334  Invalid misc:23   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx52d7fc419f14
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp2s0b1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0b1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0b1
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx52d7fc419f14

##### resolv.conf #######################

nameserver 127.0.1.1
search chello.hu

##### network managers ##################

Installed:

    NetworkManager

Running:

root       634     1  0 14:47 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx52d7fc419f14
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         asus
GENERAL.PRODUCT:                        Nexus 7
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx52d7fc419f14' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/net/enx52d7fc419f14
GENERAL.IP-IFACE:                       enx52d7fc419f14
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       a51be4c8-b585-45bf-b6c2-6be97445c811
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/9
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a51be4c8-b585-45bf-b6c2-6be97445c811 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.191/24
IP4.GATEWAY:                            192.168.42.129
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.191
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1447702465
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = Alfabus
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx52d7fc419f14' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-18-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlp2s0b1
GENERAL.IP-IFACE:                       wlp2s0b1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     UPC1929224
GENERAL.CON-UUID:                       90954600-7bd1-4e96-ae8d-b69c67ef6d4d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/8
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   90954600-7bd1-4e96-ae8d-b69c67ef6d4d | UPC1929224
IP4.ADDRESS[1]:                         192.168.0.20/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             213.46.246.53
IP4.DNS[2]:                             213.46.246.54
IP4.DOMAIN[1]:                          chello.hu
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1447785027
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       domain_name = chello.hu
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.20
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 213.46.246.53 213.46.246.54
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp2s0b1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
UPC  Wi-Free          <MAC 'UPC Wi-Free' [AC10]>  Infra  6     2437  MHz  54 Mbit/s  89      &#9602;&#9604;&#9606;&#9608;  WPA2 802.1X       no        
tobias               <MAC 'tobias' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
UPC  Wi-Free          <MAC 'UPC Wi-Free' [AC5]>  Infra  6     2437  MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2 802.1X       no        
--                    <MAC '\00\00\00\00\00\00\00\00\00' [AC17]>  Infra  11    2462  MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
UPC2006233            <MAC 'UPC2006233' [AC29]>  Infra  11    2462 MHz  54 Mbit/s   59      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC18]>  Infra  11    2462 MHz  54 Mbit/s   55      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC24]>  Infra  11    2462 MHz  54 Mbit/s   54      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC16]>  Infra  11    2462 MHz  54 Mbit/s   49      &#9602;&#9604;__  WPA2 802.1X       no        
UPC1826327            <MAC 'UPC1826327' [AC22]>  Infra  11    2462 MHz  54 Mbit/s   47      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC8]>  Infra  6     2437 MHz  54 Mbit/s   34      &#9602;&#9604;__  WPA2 802.1X       no        
UPC6245610            <MAC 'UPC6245610' [AC2]>  Infra  6     2437 MHz  54 Mbit/s   39      &#9602;&#9604;__  WPA1 WPA2         no        
UPC1929224            <MAC 'UPC1929224' [AC1]>  Infra  6     2437 MHz  54 Mbit/s   74      &#9602;&#9604;&#9606;_  WPA1 WPA2         yes     * 
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC3]>  Infra  6     2437 MHz  54 Mbit/s   42      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC4]>  Infra  6     2437 MHz  54 Mbit/s   34      &#9602;&#9604;__  WPA2 802.1X       no        
UPC1275231            <MAC 'UPC1275231' [AC7]>  Infra  6     2437 MHz  54 Mbit/s   32      &#9602;&#9604;__  WPA1 WPA2         no        
DISZNO               <MAC 'DISZNO' [AC21]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
UPC  Wi-Free          <MAC 'UPC Wi-Free' [AC12]>  Infra  6     2437  MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2 802.1X  no        
UPC2559179            <MAC 'UPC2559179' [AC11]>  Infra  6     2437 MHz  54 Mbit/s   27      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AN19]>  Infra  6     2437 MHz  54 Mbit/s   29      &#9602;___  WPA1 WPA2 802.1X  no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC33]>  Infra  6     2437 MHz  54 Mbit/s   39      &#9602;&#9604;__  WPA2 802.1X       no        
UPC1824226            <MAC 'UPC1824226' [AC9]>  Infra  6     2437 MHz  54 Mbit/s   34      &#9602;&#9604;__  WPA1 WPA2         no        
GoddamnStonerRocker   <MAC 'GoddamnStonerRocker' [AC30]>  Infra  6     2437 MHz  54  Mbit/s  30      &#9602;___  WPA1 WPA2         no        
UPC2570983            <MAC 'UPC2570983' [AC20]>  Infra  6     2437 MHz  54 Mbit/s   22      &#9602;___  WPA1 WPA2         no        
UPC9225040            <MAC 'UPC9225040' [AC15]>  Infra  6     2437 MHz  54 Mbit/s   19      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC23]>  Infra  11    2462 MHz  54 Mbit/s   39      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC7786961            <MAC 'UPC7786961' [AC26]>  Infra  11    2462 MHz  54 Mbit/s   37      &#9602;&#9604;__  WPA1 WPA2         no        
UPC2562819            <MAC 'UPC2562819' [AC28]>  Infra  11    2462 MHz  54 Mbit/s   34      &#9602;&#9604;__  WPA1 WPA2         no        
shameonyou            <MAC 'shameonyou' [AC27]>  Infra  6     2437 MHz  54 Mbit/s   32      &#9602;&#9604;__  WPA1 WPA2         no        
UPC5927572            <MAC 'UPC5927572' [AC25]>  Infra  11    2462 MHz  54 Mbit/s   30      &#9602;___  WPA1 WPA2         no        
UPC0735987            <MAC 'UPC0735987' [AC19]>  Infra  6     2437 MHz  54 Mbit/s   27      &#9602;___  WPA1 WPA2         no        
UPC2339517            <MAC 'UPC2339517' [AC14]>  Infra  6     2437 MHz  54 Mbit/s   22      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free           <MAC 'UPC Wi-Free' [AC6]>  Infra  6     2437 MHz  54 Mbit/s   20      &#9602;___  WPA1 WPA2 802.1X  no        

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

Sorry, try again.
[[/etc/NetworkManager/system-connections/HITRON-A9D0]] (600 root)
[connection] id=HITRON-A9D0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=HITRON-A9D0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC1929224]] (600 root)
[connection] id=UPC1929224 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=UPC1929224
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

enx52d7fc419f14  no frequency information.

lo        no frequency information.

wlp2s0b1  13 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

enx52d7fc419f14  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      21   APs on   Frequency:2.437 GHz (Channel 6)
      12   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'UPC1929224' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"UPC1929224"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000074d24e26f
                    Extra: Last beacon: 35ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC6245610' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC6245610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001995131fea
                    Extra: Last beacon: 518ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'UPC Wi-Free' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001995135df6
                    Extra: Last beacon: 209ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC 'UPC Wi-Free' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000173a9632c
                    Extra: Last beacon: 484ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'UPC Wi-Free' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000862699151a
                    Extra: Last beacon: 158ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'UPC Wi-Free' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000038bd01b9
                    Extra: Last beacon: 24405ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'UPC1275231' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC1275231"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037ba4be186
                    Extra: Last beacon: 230ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'UPC Wi-Free' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000037ba4bea2a
                    Extra: Last beacon: 228ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'UPC1824226' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UPC1824226"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cd1a49763
                    Extra: Last beacon: 556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC Wi-Free' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000074d24ecc2
                    Extra: Last beacon: 35ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 11 - Address: <MAC 'UPC2559179' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC2559179"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000173a18194
                    Extra: Last beacon: 1000ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'UPC Wi-Free' [AC12]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000861d5ca180
                    Extra: Last beacon: 265ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'tobias' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"tobias"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008626990396
                    Extra: Last beacon: 160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'UPC2339517' [AC14]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"UPC2339517"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000757e07180
                    Extra: Last beacon: 26016ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'UPC9225040' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"UPC9225040"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000861db8d2d4
                    Extra: Last beacon: 25714ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'UPC Wi-Free' [AC16]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006cc44c021
                    Extra: Last beacon: 759ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 17 - Address: <MAC '\00\00\00\00\00\00\00\00\00' [AC17]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028bb3411a0
                    Extra: Last beacon: 443ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'UPC Wi-Free' [AC18]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006588dfad6
                    Extra: Last beacon: 736ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC 'UPC0735987' [AC19]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"UPC0735987"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008861ac180
                    Extra: Last beacon: 506ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'UPC2570983' [AC20]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"UPC2570983"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000038b08392
                    Extra: Last beacon: 25172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'DISZNO' [AC21]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"DISZNO"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000157c1bee900
                    Extra: Last beacon: 486ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'UPC1826327' [AC22]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"UPC1826327"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006cc44b5f9
                    Extra: Last beacon: 49ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC 'UPC Wi-Free' [AC23]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000618a2a8180
                    Extra: Last beacon: 24910ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC 'UPC Wi-Free' [AC24]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028bb2ffdd5
                    Extra: Last beacon: 35ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 25 - Address: <MAC 'UPC5927572' [AC25]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC5927572"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012eda65419c
                    Extra: Last beacon: 24864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC 'UPC7786961' [AC26]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC7786961"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000618b9b4316
                    Extra: Last beacon: 691ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC 'shameonyou' [AC27]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"shameonyou"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000527c4be235
                    Extra: Last beacon: 1481ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC 'UPC2562819' [AC28]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC2562819"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076d7e85197
                    Extra: Last beacon: 685ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC 'UPC2006233' [AC29]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UPC2006233"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000065726a04f
                    Extra: Last beacon: 24287ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC 'GoddamnStonerRocker' [AC30]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"GoddamnStonerRocker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000861d421180
                    Extra: Last beacon: 1954ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC 'Zebrazsiraf_1' [AC31]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Zebrazsiraf_1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000086202b61a9
                    Extra: Last beacon: 694ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC 'UPC Wi-Free' [AC32]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076d7e85a3a
                    Extra: Last beacon: 680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 33 - Address: <MAC 'UPC Wi-Free' [AC33]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cd1a94fc0
                    Extra: Last beacon: 246ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

##### module parameters #################

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
blacklist b43
blacklist ssb

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 1748.481537] r8169 0000:03:00.0 enp3s0: link down
[ 1748.851096] rndis_host 3-1.2:1.0 enx52d7fc419f14: unregister 'rndis_host' usb-0000:00:1a.0-1.2, RNDIS device
[ 1748.882449] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 1748.996959] r8169 0000:03:00.0 enp3s0: link down
[ 1748.996996] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[ 1748.997667] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[ 1749.097905] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1749.097914] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[ 1749.098528] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready (repeated 2 times)
[ 1750.091197] wlp2s0b1: authenticate with <MAC 'UPC1929224' [AC1]>
[ 1750.091296] wlp2s0b1: send auth to <MAC 'UPC1929224' [AC1]> (try 1/3)
[ 1750.093605] wlp2s0b1: authenticated
[ 1750.094082] wlp2s0b1: associate with <MAC 'UPC1929224' [AC1]> (try 1/3)
[ 1750.103712] wlp2s0b1: RX AssocResp from <MAC 'UPC1929224' [AC1]> (capab=0x1411 status=0 aid=5)
[ 1750.104414] brcmsmac bcma0:1: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1750.104419] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1750.104434] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0b1: link becomes ready
[ 1750.104895] wlp2s0b1: associated
[ 1751.208662] brcmsmac bcma0:1: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1989.457991] rndis_host 1-3:1.0 enx52d7fc419f14: renamed from usb0
[ 1989.473061] IPv6: ADDRCONF(NETDEV_UP): enx52d7fc419f14: link is not ready

########## wireless info END ############


```

Now  I'll change the settings for the connection as you suggested. I should  change these settings for the wireless router I am currently trying to  connect to, right?

Thanks again!

---

### Post by Hadaka on 2015-11-16
Hi, it looks like you have some conflict going on there.
you are trying to attach the internal wifi  and you have also plugged in a usb wifi
and the wired connection. so remove the wired connection, remove the usb wifi
boot...and report back.
thanks.

---

### Post by Hyenaz on 2015-11-16
Hi, 

We were tethering to an android device in order to communicate but when we untether we still cant connect to the network.  

Here are the new results from the script, run without being tethered to the android device.

```



########## wireless info START ##########


Report from: 16 Nov 2015 21:56 CET +0100


Booted last: 16 Nov 2015 00:00 CET +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily


##### kernel ############################


Linux 4.2.0-18-lowlatency #22-Ubuntu SMP PREEMPT Fri Nov 6 20:09:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu Studio


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 004 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              745472  1 brcmsmac
cfg80211              557056  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac
wmi                    20480  0


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlp2s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp2s0b1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


enp3s0    no wireless extensions.


lo        no wireless extensions.


wlp2s0b1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


##### network managers ##################


Installed:


    NetworkManager


Running:


root       634     1  0 21:51 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-18-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlp2s0b1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2 802.1X       no        
--           <MAC '\00\00\00\00\00\00\00\00\00' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2 802.1X       no        
tobias       <MAC 'tobias' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2         no        
T-E542C0     <MAC 'T-E542C0' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2         no        
UPC7786961   <MAC 'UPC7786961' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC1826327   <MAC 'UPC1826327' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2 802.1X       no        
UPC4039859   <MAC 'UPC4039859' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
UPC1824226   <MAC 'UPC1824226' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC13]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC12]>  Infra  8     2447 MHz  54 Mbit/s  24      &#9602;___  WPA2 802.1X       no        
UPC2010727   <MAC 'UPC2010727' [AC6]>  Infra  8     2447 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC14]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X       no        


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


[[/etc/NetworkManager/system-connections/HITRON-A9D0]] (600 root)
[connection] id=HITRON-A9D0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=HITRON-A9D0
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


enp3s0    no frequency information.


lo        no frequency information.


wlp2s0b1  13 channels in total; available frequencies :
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


enp3s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      6   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      7   APs on   Frequency:2.462 GHz (Channel 11)


wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'tobias' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"tobias"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000088039b9de1
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC Wi-Free' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000088039ba7bc
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC '\00\00\00\00\00\00\00\00\00' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a96bd9a1c
                    Extra: Last beacon: 120ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'T-E542C0' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"T-E542C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002992d345b9
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'UPC Wi-Free' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a96bb0db5
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'UPC2010727' [AC6]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"UPC2010727"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027f9359187
                    Extra: Last beacon: 474ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'UPC Wi-Free' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b721599ce
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 08 - Address: <MAC 'UPC Wi-Free' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=320000636723c407
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'UPC4039859' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC4039859"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000087f64c8180
                    Extra: Last beacon: 16415ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC1824226' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC1824226"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001eabfc1ebd
                    Extra: Last beacon: 19708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'UPC Wi-Free' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001eabfc4f4a
                    Extra: Last beacon: 19708ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC 'UPC Wi-Free' [AC12]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000027f8099a3c
                    Extra: Last beacon: 20133ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'UPC Wi-Free' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000833222ee2
                    Extra: Last beacon: 16475ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'UPC Wi-Free' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008a9413a45
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC 'UPC6245610' [AC15]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"UPC6245610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b7215866e
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[brcmsmac]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512


[brcmutil]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[bcma]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512


##### module parameters #################


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
blacklist b43
blacklist ssb


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


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[   10.870257] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   10.870284] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   10.870353] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   10.882451] bcma: bus0: Bus registered
[   12.989430] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   13.068951] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   14.248684] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   27.137438] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   27.445991] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   27.446001] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   27.446669] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   27.448214] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.638676] r8169 0000:03:00.0 enp3s0: link down
[   27.638729] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.710385] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   55.011996] wlp2s0b1: authenticate with <MAC address>
[   55.012098] wlp2s0b1: direct probe to <MAC address> (try 1/3)
[   55.212982] wlp2s0b1: direct probe to <MAC address> (try 2/3)
[   55.414229] wlp2s0b1: direct probe to <MAC address> (try 3/3)
[   55.615510] wlp2s0b1: authentication with <MAC address> timed out
[   74.446781] wlp2s0b1: authenticate with <MAC address>
[   74.449641] wlp2s0b1: send auth to <MAC address> (try 1/3)
[   74.456578] wlp2s0b1: authenticated
[   74.456980] wlp2s0b1: associate with <MAC address> (try 1/3)
[   74.604157] wlp2s0b1: associate with <MAC address> (try 2/3)
[   74.686623] wlp2s0b1: associate with <MAC address> (try 3/3)
[   74.913666] wlp2s0b1: association with <MAC address> timed out
[  105.138446] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready (repeated 4 times)
[  300.745454] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  300.745495] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[  300.746274] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready (repeated 2 times)


########## wireless info END ############

```

Thanks very much.

---

### Post by Hadaka on 2015-11-16
Hi, which wifi signal are you trying to attach to??
and is it your router that you can make changes??
also...i noted you didnt change the ipv4 or ipv6 settings.,,
so i will send them again along with the base set up configuration..
[ATTACH=CONFIG]265619[/ATTACH][ATTACH=CONFIG]265620[/ATTACH][ATTACH=CONFIG]265621[/ATTACH]

the SSID is the name of the connection
the BSSID is the mac address of the router/ssid you want to attatch to
the Device Mac address is the mac address of your computer

---

### Post by Hyenaz on 2015-11-17
> **Hadaka said:**
> Hi, which wifi signal are you trying to attach to??

We are attempting to connect to the network called UPC1929224, but in fact, it keeps disappearing on this one device, although it is visible to other laptops running Ubuntu or OSX, phones etc. Right now the laptop is about three feet away from the router.

> **Hadaka said:**
>  and is it your router that you can make changes??
Unfortunately not. We are staying at someone's apartment and they are not here.

> **Hadaka said:**
> also...i noted you didnt change the ipv4 or ipv6 settings.,,
Oops, that was a misunderstanding on our part. But now the network is actually no longer visible, but the connection is still there under "Edit Connections" so I will make the changes there. How can I determine the BSSID of the network I wish to connect to? I have left this field blank.

Thanks for all your help.

I'll post the output from wireless script in a few minutes.

---

### Post by Hyenaz on 2015-11-17
Hi Hadaka,

Here is the output from the script. Please see answers to your questions in previous post.

```


########## wireless info START ##########

Report from: 17 Nov 2015 15:59 CET +0100

Booted last: 17 Nov 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-18-lowlatency #22-Ubuntu SMP PREEMPT Fri Nov 6 20:09:48 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0608]
    Kernel driver in use: bcma-pci-bridge

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 07)
    Subsystem: Lenovo Device [17aa:5002]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:0295 Acer, Inc 
Bus 003 Device 003: ID 147e:1002 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              573440  0
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
mac80211              745472  1 brcmsmac
cfg80211              557056  2 brcmsmac,mac80211
bcma                   53248  2 brcmsmac
wmi                    20480  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0b1  Link encap:Ethernet  HWaddr <MAC 'wlp2s0b1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0b1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       659     1  0 15:47 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0b1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         brcmsmac
GENERAL.DRIVER-VERSION:                 4.2.0-18-lowlatency
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0b1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/bcma0:1/net/wlp2s0b1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY          ACTIVE  * 
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X       no        
--           <MAC '\00\00\00\00\00\00\00\00\00' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2         no        
tobias       <MAC 'tobias' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2         no        
T-E542C0     <MAC 'T-E542C0' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA1 WPA2         no        
UPC1826327   <MAC 'UPC1826327' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2         no        
UPC7786961   <MAC 'UPC7786961' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2         no        
UPC3350494   <MAC 'UPC3350494' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
Erzsok       <MAC 'Erzsok' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2         no        
T-7206F0     <MAC 'T-7206F0' [AN12]>  Infra  8     2447 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AN14]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2 802.1X  no        
UPC1275231   <MAC 'UPC1275231' [AC10]>  Infra  11    2462 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2         no        
UPC6245610   <MAC 'UPC6245610' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2         no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC12]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2 802.1X       no        
UPC Wi-Free  <MAC 'UPC Wi-Free' [AC13]>  Infra  6     2437 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2 802.1X       no        

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

[[/etc/NetworkManager/system-connections/HITRON-A9D0]] (600 root)
[connection] id=HITRON-A9D0 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=HITRON-A9D0
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPC1929224]] (600 root)
[connection] id=UPC1929224 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp2s0b1' [IF]> | mac-address-blacklist= | ssid=UPC1929224
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE: DFS-ETSI
    (2400 - 2483 @ 40), (N/A, 20), (N/A)
    (5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
    (5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
    (5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlp2s0b1  13 channels in total; available frequencies :
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

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.437 GHz (Channel 6)
      9   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0b1  Scan completed :
          Cell 01 - Address: <MAC 'UPC Wi-Free' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039b5a122b3
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 02 - Address: <MAC '\00\00\00\00\00\00\00\00\00' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000039b5a2018a
                    Extra: Last beacon: 177ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'tobias' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"tobias"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009722812cff
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'UPC Wi-Free' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c827371d
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'UPC Wi-Free' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000097228136ad
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'UPC1826327' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UPC1826327"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000017c359a995
                    Extra: Last beacon: 238ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'T-E542C0' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"T-E542C0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038b1bf4b2b
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'UPC Wi-Free' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=3200007285f36f04
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 09 - Address: <MAC 'UPC7786961' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC7786961"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007285f234c0
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'UPC1275231' [AC10]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"UPC1275231"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048b334c198
                    Extra: Last beacon: 25703ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'UPC6245610' [AC11]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"UPC6245610"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a8dee9833
                    Extra: Last beacon: 587ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'UPC Wi-Free' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000048b334ca4e
                    Extra: Last beacon: 25702ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC 'UPC Wi-Free' [AC13]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC Wi-Free"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a8deed316
                    Extra: Last beacon: 585ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC 'UPC3162537' [AC14]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"UPC3162537"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000971a40418a
                    Extra: Last beacon: 300ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     4B2FFE4B90A21C08ABE6873
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     AE9B4BBC6D82855B9265054
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/4.2.0-18-lowlatency/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     6DF74A7EF5817B6F27A5CB0
depends:        
intree:         Y
vermagic:       4.2.0-18-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        41:DD:E1:54:B9:3A:9A:87:43:F7:FD:9F:F9:43:64:CA:9C:25:98:9B
sig_hashalgo:   sha512

##### module parameters #################

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
blacklist b43
blacklist ssb

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   10.705896] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   10.705931] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   10.705973] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   10.706038] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   10.718730] bcma: bus0: Bus registered
[   12.391299] brcmsmac bcma0:1: mfg 4bf core 812 rev 24 class 0 irq 17
[   12.604731] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 499
[   12.696021] brcmsmac bcma0:1 wlp2s0b1: renamed from wlan0
[   26.735397] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   27.050534] brcmsmac bcma0:1: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   27.050545] brcmsmac bcma0:1: brcms_ops_config: change power-save mode: false (implement)
[   27.051223] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready
[   27.052776] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.204051] r8169 0000:03:00.0 enp3s0: link down
[   27.204099] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   27.364037] IPv6: ADDRCONF(NETDEV_UP): wlp2s0b1: link is not ready (repeated 3 times)

########## wireless info END ############


```

---

### Post by Hadaka on 2015-11-17
Hi, your first post says..
"At the moment, we can see wifi networks and can connect to them, but websites, email etc fail to load"
that should have been cleared by the removal of the b43 modules. followed by the configuration adjustment.
again..what wifi signal are you trying to attach to??? what ssid??? that should have the BSSID you need
also ubuntu 15.10 can be difficult with some wifi drivers, and it is a short term os, meaning it will no longer be
supported in just a few months. where 14.04 LTS AND 15.04 LTS have long term...years...of support. you "may"
want to condiser loading one of those instead. also...is this a university network and have you worked with the
school IT guys to help get you going?? They also can tell you the mac addressed...BSSID of each connection.

---

### Post by Hyenaz on 2015-11-17
Alright, thanks a lot for your help. So far, the problems persist despite the changes.

We will consider downgrading to 14.04.

All the best,

HYENAZ

---

### Post by Hyenaz on 2015-11-25
Hi Hadaka,

We downgraded to 14.04 and, as you predicted, wifi works fine now. So I guess there are some problems still with 15.10.

Thanks for working through this with us.

All the best,

HYENAZ.

---

### Post by Hadaka on 2015-11-25
Hi, glad you are up and running ! I dont consider 14.04 a downgrade,
it should be a nice stable solid long term os for you and other than keeping up with the updates, hassel free.
please take the time to sign back in to your post, click TOOLS upper right and then mark SOLVED
thanks.

---

