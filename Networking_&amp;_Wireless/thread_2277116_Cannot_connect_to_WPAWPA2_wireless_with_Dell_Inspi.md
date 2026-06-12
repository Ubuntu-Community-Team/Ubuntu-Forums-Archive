---
title: "Cannot connect to WPA/WPA2 wireless with Dell Inspiron running Ubuntu 15.04"
date: 2015-05-06
forum: Networking &amp; Wireless
---

### Post by dab10a on 2015-05-06
Hey all,
I've been looking around, but can't seem to find an answer to this question. I recently updated to 15.04 from 14.04 LTS and everything works fine, except that I suddenly cannot connect to certain WiFi networks (I think they are specifically WPA/WPA2 networks). Other networks, like my university network (which isn't password protected) seem to work fine, and I have access to ethernet/wired connections. Has anybody been able to fix this issue or can somebody get me in the right direction?
```

########## wireless info START ##########

Report from: 07 May 2015 07:49 CDT -0500

Booted last: 06 May 2015 16:24 CDT -0500

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-16-generic #16-Ubuntu SMP Thu Apr 30 16:09:58 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Dell Device [1028:063e]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8470]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 006: ID 064e:c231 Suyin Corp. 
Bus 003 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 004: ID 04f3:2020 Elan Microelectronics Corp. 
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                278528  0 
mac80211              720896  1 iwlmvm
dell_wmi               16384  0 
snd_soc_rt5640         94208  0 
sparse_keymap          16384  1 dell_wmi
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
snd_pcm               106496  9 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
iwlwifi               196608  1 iwlmvm
dell_laptop            16384  0 
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
dcdbas                 16384  1 dell_laptop
wmi                    20480  2 dell_led,dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:150.252.114.130  Bcast:150.252.115.255  Mask:255.255.254.0
          inet6 addr: fe80::3617:ebff:fe6f:f0a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:362386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:214837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:417398819 (417.3 MB)  TX bytes:24276928 (24.2 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         150.252.114.1   0.0.0.0         UG    1024   0        0 eth0
150.252.114.0   0.0.0.0         255.255.254.0   U     0      0        0 eth0
150.252.128.107 150.252.114.1   255.255.255.255 UGH   1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search acu.local

##### NetworkManager info ###############

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       425e1c37-aaf3-42d9-888b-944b3aa4a8c6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{48}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   425e1c37-aaf3-42d9-888b-944b3aa4a8c6 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 150.252.114.130/23, gw = 150.252.114.1
IP4.ROUTE[1]:                           dst = 150.252.128.107/32, nh = 150.252.114.1, mt = 1
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             150.252.134.249
IP4.DNS[2]:                             150.252.134.8
IP4.DNS[3]:                             150.252.134.159
IP4.DOMAIN[1]:                          acu.local
DHCP4.OPTION[1]:                        network_number = 150.252.114.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1431607262
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       domain_name = acu.local
DHCP4.OPTION[12]:                       broadcast_address = 150.252.115.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 150.252.114.1
DHCP4.OPTION[16]:                       ip_address = 150.252.114.130
DHCP4.OPTION[17]:                       dhcp_lease_time = 604800
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.254.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[23]:                       domain_name_servers = 150.252.134.249 150.252.134.8 150.252.134.159
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 150.252.128.107
IP6.ADDRESS[1]:                         ip = fe80::3617:ebff:fe6f:f0a0/64, gw = ::

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-16-generic
GENERAL.FIRMWARE-VERSION:               25.15.12.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.0/net/wlan0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes

SSID                        BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR43-5G                <MAC 'NETGEAR43-5G' [AC2]>  Infra  153   5765 MHz  54 Mbit/s  95      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
dlink-8D4C-5GHz             <MAC 'dlink-8D4C-5GHz' [AC1]>  Infra  44    5220 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
dlink-8D4C                  <MAC 'dlink-8D4C' [AC3]>  Infra  3     2422 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Lucian4ever.media           <MAC 'Lucian4ever.media' [AC5]>  Infra  36    5180 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2       no        
Lucian4ever                 <MAC 'Lucian4ever' [AC7]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
GoNetflixOrGoToSleep.media  <MAC 'GoNetflixOrGoToSleep.media' [AC6]>  Infra  149   5745 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
jkm414                      <MAC 'jkm414' [AN7]>  Infra  36    5180 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
belkin.704.guests           <MAC 'belkin.704.guests' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  --         no        

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

[[/etc/NetworkManager/system-connections/HIX Topeka North]] (600 root)
[connection] id=HIX Topeka North | type=802-11-wireless
[802-11-wireless] ssid=HIX Topeka North | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/lemley-guest]] (600 root)
[connection] id=lemley-guest | type=802-11-wireless
[802-11-wireless] ssid=lemley-guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Guest]] (600 root)
[connection] id=Guest | type=802-11-wireless
[802-11-wireless] ssid=Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Mokah Public]] (600 root)
[connection] id=Mokah Public | type=802-11-wireless
[802-11-wireless] ssid=Mokah Public | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ACUwireless]] (600 root)
[connection] id=ACUwireless | type=802-11-wireless
[802-11-wireless] ssid=ACUwireless | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WWUwireless]] (600 root)
[connection] id=WWUwireless | type=802-11-wireless
[802-11-wireless] ssid=WWUwireless | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WiFiRSU_9420e]] (600 root)
[connection] id=WiFiRSU_9420e | type=802-11-wireless
[802-11-wireless] ssid=WiFiRSU_9420e | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/tehintertubez 1]] (600 root)
[connection] id=tehintertubez 1 | type=wifi
[wifi] ssid=tehintertubez | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WashburnGuest]] (600 root)
[connection] id=WashburnGuest | type=802-11-wireless
[802-11-wireless] ssid=WashburnGuest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Grand Lodge]] (600 root)
[connection] id=Grand Lodge | type=802-11-wireless
[802-11-wireless] ssid=Grand Lodge | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Guest-Open]] (600 root)
[connection] id=Guest-Open | type=802-11-wireless
[802-11-wireless] ssid=Guest-Open | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/The Lab]] (600 root)
[connection] id=The Lab | type=802-11-wireless
[802-11-wireless] ssid=The Lab | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/slcairport.wifi]] (600 root)
[connection] id=slcairport.wifi | type=802-11-wireless
[802-11-wireless] ssid=slcairport.wifi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Hyatt]] (600 root)
[connection] id=Hyatt | type=802-11-wireless
[802-11-wireless] ssid=Hyatt | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/boots'peoples]] (600 root)
[connection] id=boots'peoples | type=802-11-wireless
[802-11-wireless] ssid=boots'peoples | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/HORIZON-PC_Network]] (600 root)
[connection] id=HORIZON-PC_Network | type=802-11-wireless
[802-11-wireless] ssid=HORIZON-PC_Network | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dylan Brugman’s iPhone]] (600 root)
[connection] id=Dylan Brugman’s iPhone | type=802-11-wireless
[802-11-wireless] ssid=68;121;108;97;110;32;66;114;117;103;109;97;110;226;128;153;115;32;105;80;104;111;110;101; | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JewellSecure]] (600 root)
[ipv6] method=auto
[connection] id=JewellSecure | type=802-11-wireless
[802-11-wireless] ssid=JewellSecure | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ATT6ucMiea]] (600 root)
[connection] id=ATT6ucMiea | type=802-11-wireless
[802-11-wireless] ssid=ATT6ucMiea | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KCKCC-WiFi]] (600 root)
[connection] id=KCKCC-WiFi | type=802-11-wireless
[802-11-wireless] ssid=KCKCC-WiFi | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Washburn]] (600 root)
[connection] id=Washburn | type=802-11-wireless
[802-11-wireless] ssid=Washburn | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Ramada]] (600 root)
[connection] id=Ramada | type=802-11-wireless
[802-11-wireless] ssid=Ramada | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/sfbakeshop]] (600 root)
[connection] id=sfbakeshop | type=802-11-wireless
[802-11-wireless] ssid=sfbakeshop | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Chrisanne]] (600 root)
[connection] id=Chrisanne | type=802-11-wireless
[802-11-wireless] ssid=Chrisanne | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE976]] (600 root)
[connection] id=2WIRE976 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE976 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UNITE-AE03]] (600 root)
[connection] id=UNITE-AE03 | type=802-11-wireless
[802-11-wireless] ssid=UNITE-AE03 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CU Wireless Network]] (600 root)
[connection] id=CU Wireless Network | type=802-11-wireless
[802-11-wireless] ssid=CU Wireless Network | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/tehintertubez]] (600 root)
[connection] id=tehintertubez | type=wifi
[wifi] ssid=tehintertubez | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/kci]] (600 root)
[connection] id=kci | type=802-11-wireless
[802-11-wireless] ssid=kci | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/lemley]] (600 root)
[connection] id=lemley | type=802-11-wireless
[802-11-wireless] ssid=lemley | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/oakview1]] (600 root)
[connection] id=oakview1 | type=802-11-wireless
[802-11-wireless] ssid=oakview1 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/RedLion]] (600 root)
[connection] id=RedLion | type=802-11-wireless
[802-11-wireless] ssid=RedLion | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/The Flat]] (600 root)
[connection] id=The Flat | type=802-11-wireless
[802-11-wireless] ssid=The Flat | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATTsYWttxi]] (600 root)
[connection] id=ATTsYWttxi | type=802-11-wireless
[802-11-wireless] ssid=ATTsYWttxi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Grand Hyatt Denver]] (600 root)
[connection] id=Grand Hyatt Denver | type=802-11-wireless
[802-11-wireless] ssid=Grand Hyatt Denver | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/TTUguest]] (600 root)
[connection] id=TTUguest | type=802-11-wireless
[802-11-wireless] ssid=TTUguest | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UGuest]] (600 root)
[connection] id=UGuest | type=802-11-wireless
[802-11-wireless] ssid=UGuest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR43]] (600 root)
[connection] id=NETGEAR43 | type=wifi
[wifi] ssid=NETGEAR43 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/williamson]] (600 root)
[connection] id=williamson | type=802-11-wireless
[802-11-wireless] ssid=williamson | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/forensics]] (600 root)
[connection] id=forensics | type=802-11-wireless
[802-11-wireless] ssid=forensics | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Zola]] (600 root)
[connection] id=Zola | type=802-11-wireless
[802-11-wireless] ssid=Zola | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Dena Counts IPhone]] (600 root)
[connection] id=Dena Counts IPhone | type=802-11-wireless
[802-11-wireless] ssid=Dena Counts IPhone | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Spokane_Int'l_Guest]] (600 root)
[connection] id=Spokane_Int'l_Guest | type=802-11-wireless
[802-11-wireless] ssid=Spokane_Int'l_Guest | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/williamson 1]] (600 root)
[connection] id=williamson 1 | type=802-11-wireless
[802-11-wireless] ssid=williamson | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UNITE-AE03 1]] (600 root)
[connection] id=UNITE-AE03 1 | type=802-11-wireless
[802-11-wireless] ssid=UNITE-AE03 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.447 GHz (Channel 8)
      3   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.22 GHz (Channel 44)
      1   APs on   Frequency:5.745 GHz
      1   APs on   Frequency:5.765 GHz
      1   APs on   Frequency:5.785 GHz

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'dlink-8D4C-5GHz' [AC1]>
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"dlink-8D4C-5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000159c63bb67d
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'NETGEAR43-5G' [AC2]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR43-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002333d0f014b
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'dlink-8D4C' [AC3]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"dlink-8D4C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023a7216fa19
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'belkin.704.guests' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"belkin.704.guests"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019d0ee83f2
                    Extra: Last beacon: 2728ms ago
          Cell 05 - Address: <MAC 'Lucian4ever.media' [AC5]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Lucian4ever.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f2cfdb980
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'GoNetflixOrGoToSleep.media' [AC6]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"GoNetflixOrGoToSleep.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000229b3c860e
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Lucian4ever' [AC7]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Lucian4ever"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000019f0217670
                    Extra: Last beacon: 2780ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'NETGEAR84' [AC8]>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR84"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000042156090947
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'NETGEAR43' [AC9]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR43"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002339b70c159
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'belkin.f37' [AC10]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"belkin.f37"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003ec8dfe38
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'jkm414-guest' [AC11]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:off
                    ESSID:"jkm414-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000015541ec4b4c4
                    Extra: Last beacon: 80ms ago
          Cell 12 - Address: <MAC 'jkm414' [AC12]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"jkm414"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Mastlo        Interface doesn't support scanning.

er
                    Extra:tsf=000015541ec586a3
                    Extra: Last beacon: 2852ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'belkin.39d' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"belkin.39d"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002952fd5417
                    Extra: Last beacon: 80ms ago
          Cell 14 - Address: <MAC 'belkin.4bb.media' [AC14]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"belkin.4bb.media"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002a2d666041

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     88D1E879FA8C28657F76FF4
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.19.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     ADFD966DF2A9D56EE93BE48
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
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
minstrel_vht_only: Y
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b3 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 9693.027663] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 9693.844691] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.2.3.d.bseq
[ 9694.053855] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[ 9694.191214] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 2 times)

########## wireless info END ############

```

---

### Post by dab10a on 2015-05-09
bump

---

### Post by Shaurya_Chaturvedi on 2015-06-01
I have a similar problem too. I have Dell Inspiron 5547. Please help.

---

### Post by hamlet32 on 2015-06-02
try running this command (atleast it solved a similar problem with me) - dont forget to reboot at the end
*sudo mv /lib/firmware/iwlwifi-3160-12.ucode /lib/firmware/iwlwifi-3160-10.ucode*

---

