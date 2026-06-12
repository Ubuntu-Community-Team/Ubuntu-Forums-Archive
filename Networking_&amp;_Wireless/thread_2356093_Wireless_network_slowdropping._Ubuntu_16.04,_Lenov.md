---
title: "Wireless network slow/dropping. Ubuntu 16.04, Lenovo ideapad"
date: 2017-03-19
forum: Networking &amp; Wireless
---

### Post by physicsjason on 2017-03-19
I know this is an extremely overposted topic - I've spent the better part of my day attempting many solutions, none of which work.

I have a fresh install of Ubuntu 16.04 on a Lenovo ideapad, which is also brand now - i'm also dual booting windows 10. The ubuntu install is "proper", as in **not wubi**, it's on its own partition and all that. I can connect to my home wireless in ubuntu just fine, but it's extremely slow - and after a while just drops completely, and won't reconnect until i reboot. 

Useful facts (hopefully):
[LIST]
[*]if i boot into windows everything works fast and normally
[*]i have a windows 8.1 machine, and a chrome book on the same network, both of which have no issues whatsoever
[*]i have "ignored" IPv6 in ubuntu's wireless interface
[*]i turned off power handling at the suggestion of a forum post elsewhere
[*]i ran the suggested updates/steps listed in the sticky for this forum
[*]The wireless adapters are not "blocked", or otherwise ubuntu doesn't think they're blocked.
[/LIST]

Also worth noting i'm not completely new to ubuntu - i use it on a work computer, so i'm at least a little familiar with CLI, but only at a basic level (on the work machine i basically don't change anything, it's just a data-gathering computer). Just to be clear, this issue is happening on **my home computer/home network.**

Here's the output from what the sticky requested i run. Just to note, the network i'm attempting to connect to is called "SherlockHolmies" and is nothing special or complicated - just a generic centrylink home network (no servers, or anything special going on).

If someone sees the magic fix for me, i'll be extremely excited - Ubuntu has been a huge pain to install (mostly lenovo's fault), and i have a ton of work i need to be doing, instead of fighting with what is supposed to be a better OS. Thanks.

```
[COLOR=#000000][FONT=&amp]########## wireless info START ##########[/FONT][/COLOR]
Report from: 19 Mar 2017 18:36 CDT -0500

Booted last: 19 Mar 2017 00:00 CDT -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
    Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3855]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 04f2:b579 Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              761856  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              581632  2 mac80211,rtlwifi
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          inet addr:192.168.0.16  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:224505 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:328743217 (328.7 MB)  TX bytes:10373892 (10.3 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:"SherlockHolmies"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'SherlockHolmies' [AN4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2267   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager
    Wicd

Running:

root       904     1  0 18:13 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.8.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     SherlockHolmies
GENERAL.CON-UUID:                       bbeade9c-692d-4304-81f4-4b2d6c52cd42
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bbeade9c-692d-4304-81f4-4b2d6c52cd42 | SherlockHolmies
IP4.ADDRESS[1]:                         192.168.0.16/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             205.171.2.25
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1490051625
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.16
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1 205.171.2.25
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/enp2s0
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

SSID                             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Galactic Empire                  <MAC 'Galactic Empire' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
--                               <MAC '--' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
xfinitywifi                      <MAC 'xfinitywifi' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  --           no        
SherlockHolmies                  <MAC 'SherlockHolmies' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  88      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    yes     * 
xfinitywifi                      <MAC 'xfinitywifi' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  --           no        
--                               <MAC '--' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2         no        
MD-LT01549-Wireless              <MAC 'MD-LT01549-Wireless' [AN7]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
xfinitywifi                      <MAC 'xfinitywifi' [AN8]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  --           no        
HOME-6FFD                        <MAC 'HOME-6FFD' [AN9]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
--                               <MAC '--' [AN10]>  Infra  1     2412 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2         no        
Dr. Awesome                      <MAC 'Dr. Awesome' [AN11]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
USI-FIBER_2E73-2                 <MAC 'USI-FIBER_2E73-2' [AN12]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2         no        
EatShitAndDie                    <MAC 'EatShitAndDie' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
--                               <MAC '--' [AN14]>  Infra  149   5745 MHz  0 Mbit/s   55      &#9602;&#9604;__  WEP          no        
USI-FIBER_4DBB-2                 <MAC 'USI-FIBER_4DBB-2' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2         no        
VesperCity                       <MAC 'VesperCity' [AN16]>  Infra  9     2452 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2         no        
NETGEAR69                        <MAC 'NETGEAR69' [AN17]>  Infra  9     2452 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2         no        
finks                            <MAC 'finks' [AN18]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
USI_FIBER_209D_2                 <MAC 'USI_FIBER_209D_2' [AN19]>  Infra  10    2457 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
City of Minneapolis Public WiFi  <MAC 'City of Minneapolis Public WiFi' [AN20]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  --           no        
CenturyLink1975                  <MAC 'CenturyLink1975' [AN21]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1         no        
WadesWorld-2                     <MAC 'WadesWorld-2' [AN22]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2         no        
Linksys11144                     <MAC 'Linksys11144' [AN23]>  Infra  3     2422 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
USI-FIBER_4D53-2                 <MAC 'USI-FIBER_4D53-2' [AN24]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
NSA VAN                          <MAC 'NSA VAN' [AN25]>  Infra  9     2452 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2         no        
DropItLikeItsHotSpot             <MAC 'DropItLikeItsHotSpot' [AN26]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
USI Wireless                     <MAC 'USI Wireless' [AN27]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  --           no        
usiw_secure_S21N130T1            <MAC 'usiw_secure_S21N130T1' [AN28]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X  no        
usiw_secure                      <MAC 'usiw_secure' [AN29]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2 802.1X  no        
CenturyLink1978                  <MAC 'CenturyLink1978' [AN30]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
HOME-1AE2                        <MAC 'HOME-1AE2' [AN31]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
--                               <MAC '--' [AN32]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2         no        
FinnCity                         <MAC 'FinnCity' [AN33]>  Infra  40    5200 MHz  54 Mbit/s  45      &#9602;&#9604;__  WPA2         no        
NETGEAR35                        <MAC 'NETGEAR35' [AN34]>  Infra  2     2417 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
Kattegat                         <MAC 'Kattegat' [AN35]>  Infra  3     2422 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
Linksys11144-guest               <MAC 'Linksys11144-guest' [AN36]>  Infra  3     2422 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
USI-FIBER_3313-2                 <MAC 'USI-FIBER_3313-2' [AN37]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
USIW Free WiFi                   <MAC 'USIW Free WiFi' [AN38]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
xfinitywifi                      <MAC 'xfinitywifi' [AN39]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  --           no        
!!!                              <MAC '!!!' [AN40]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
Kattegat-guest                   <MAC 'Kattegat-guest' [AN41]>  Infra  3     2422 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
--                               <MAC '--' [AN42]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  --           no        
NETGEAR89                        <MAC 'NETGEAR89' [AN43]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
USI-FIBER_4DBB-5                 <MAC 'USI-FIBER_4DBB-5' [AN44]>  Infra  157   5785 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
SLWIFI24                         <MAC 'SLWIFI24' [AN45]>  Infra  4     2427 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        

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

[[/etc/NetworkManager/system-connections/SherlockHolmies]] (600 root)
[connection] id=SherlockHolmies | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=SherlockHolmies
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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

wlp1s0    Interface doesn't support scanning : Device or resource busy

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     3205DD813E27A789613A4C3
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
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
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7AD0477B303BCC50CCDBB66
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     27201DE455FACC68E425C86
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
msi: Y
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
blacklist ideapad-laptop
blacklist acer_wmi

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt2800pci.conf]
options rt2800pci nohwcrypt=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   12.015149] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   12.015153] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   12.469495] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[   12.483074] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   12.483081] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   12.608332] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.608782] rtlwifi: rtlwifi: wireless switch is on
[   13.644869] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   27.706446] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[   27.938310] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.078371] r8169 0000:02:00.0 enp2s0: link down
[   28.078446] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.925618] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   31.526984] wlp1s0: authenticate with <MAC 'SherlockHolmies' [AN4]>
[   31.529384] wlp1s0: send auth to <MAC 'SherlockHolmies' [AN4]> (try 1/3)
[   31.532780] wlp1s0: authenticated
[   31.536105] wlp1s0: associate with <MAC 'SherlockHolmies' [AN4]> (try 1/3)
[   31.540501] wlp1s0: RX AssocResp from <MAC 'SherlockHolmies' [AN4]> (capab=0x411 status=0 aid=3)
[   31.610249] wlp1s0: associated
[   31.610265] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
 [COLOR=#000000][FONT=&amp]########## wireless info END ############[/FONT][/COLOR]
```

---

### Post by Bucky Ball on 2017-03-20
Welcome. [Give this a crack]("https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa#.ppgc4r1z3") if you haven't already. It is known to have worked for others with this and other Realtek wireless cards.

You may need to reboot to see changes take effect. When you've run the 'fix', please post the output of:

```
sudo lshw -C network
```

... so we can see which driver you now have in there. Good luck. :)

PS: Just noticed; you have Network Manager *and* WICD installed. Might even be your problem or have something to do with it. Uninstall one of them. They do not play together.

---

### Post by physicsjason on 2017-03-20
Thank you so much for your reply: Firstly, here's the output from ```
sudo lshw -C network
``` after i followed that link and tried the fix described there.

```
  *-network       description: Wireless interface
       product: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 00
       serial: c8:3d:d4:7f:17:75
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8821ae driverversion=4.8.0-41-generic firmware=N/A ip=192.168.0.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:41 ioport:2000(size=256) memory:f0b00000-f0b03fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: c8:5b:76:c5:08:a7
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:34 ioport:1000(size=256) memory:f0a04000-f0a04fff memory:f0a00000-f0a03fff
~                                                                                                          
```  

And about WICD, I did have it installed (it was recommended as a fix, that did not work). I had thought i un-installed using softerware manager, and indeed if i try from terminal i get this 

```
Reading package lists...Building dependency tree...
Reading state information...
Package 'wicd' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  gksu libgksu2-0 libglade2-0 python-cairo python-dbus python-gi python-glade2
  python-gobject python-gobject-2 python-gtk2 python-notify python-wicd
  wicd-daemon
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

At first glance it seems my wireless is holding up - After posting this I'll try to download something large, like the python IDE i use and see what happens. I'll come back and post either way, and if it's fixed i'll flag as solved.

---

### Post by physicsjason on 2017-03-20
Alas, it did not take long - after probably around 5 minutes the wireless dropped again, and could not reconnect until I rebooted.

---

### Post by physicsjason on 2017-03-21
bump - still no solution.

---

### Post by kurt18947 on 2017-03-24
If you really need to get networking on a particular machine, have you considered buying a known-to-work-out-of-the-box USB adapter as an interim solution? No, that's not a permanent solution but some hardware requires months after its release to have proper support on Linux. Having a surplus router with something like DD-WRT installed and configured as a wireless bridge might be another possibility.

---

### Post by physicsjason on 2017-03-24
Well sure, i could buy USB adapter, but that defeats the whole purpose of fixing the thing. Furthermore, nothing i'm running is new - the laptop is actually a model that's a year old, so if there's a solution, it must exist at this point.

---

### Post by jeremy31 on 2017-03-24
You can try disabling the power save function of the wifi module with
```
echo "options rtl8821ae ips=N " | sudo tee /etc/modprobe.d/rtl8821ae.conf
```
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

I would also change some wifi settings on the router, change it to channel 10 and change encryption to WPA2-AES without TKIP or WEP.  We might as well set the country code
```

sudo iw reg set US
```
```
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

Reboot

---

### Post by physicsjason on 2017-03-24
Jeremy,

Thanks for your reply, but it did not work. I was able to run those commands with no errors, etc, but literally 3 or 4 minutes later the wifi was dropped again. I've tried two reboots as well, same story.

---

### Post by jeremy31 on 2017-03-24
Did you change the router settings?  The script results showed your access point was on a very crowded channel using mixed mode encryption that isn't recommended in Ubuntu

---

### Post by physicsjason on 2017-03-24
No, i haven't changed the router settings - partly because i don't know how (with this particular router). 

One question though, i have several other machines on this network - changing those router settings won't disturb them, correct (win 10, chrome os, win 8.1)

---

### Post by physicsjason on 2017-03-24
I should also point out - that it is not just my home network that is the problem - the same things happen on all networks.

---

### Post by jeremy31 on 2017-03-24
I can change channel and encryption on my router and my devices always find it.  I have also set it to not broadcast SSID and all devices find it

I would guess that entering 192.168.0.1 in your browser should take you to a login page for the router

---

