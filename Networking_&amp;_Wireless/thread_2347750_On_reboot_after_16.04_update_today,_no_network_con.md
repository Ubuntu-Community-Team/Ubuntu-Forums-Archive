---
title: "On reboot after 16.04 update today, no network connection or network indicator"
date: 2016-12-28
forum: Networking &amp; Wireless
---

### Post by yeshua-1 on 2016-12-28
Updated 16.04 MATE today. 
Update proceeded smoothly and requested reboot.
On reboot, the network indicator is no longer on task bar, and no network connection can be established.
Rebooted several times and have noticed that the network indicator does load for a very brief moment, then disappears and for a very brief moment a slash screen says something like network registration required before disappearing.

Suggestions in how to assess and fix this problem?

---

### Post by praseodym on 2016-12-28
Please run the wireless script from the sticky thread and show the outputs

---

### Post by yeshua-1 on 2016-12-28
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs

how is this done? everytime I paste in the script, which contains no images, I get an error message stating you have included more than 10 images?

---

### Post by wildmanne39 on 2016-12-28
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by yeshua-1 on 2016-12-28
```

   ########## wireless info START ##########

Report from: 28 Dec 2016 21:00 MMT +0630

Booted last: 28 Dec 2016 00:00 MMT +0630

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Wistron NeWeb Corp. BCM4313 802.11bgn Wireless Network Adapter [185f:051a]
    Kernel driver in use: wl

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
    Subsystem: Samsung Electronics Co Ltd 88E8040 PCI-E Fast Ethernet Controller [144d:c08c]
    Kernel driver in use: sky2

##### lsusb #############################

Bus 001 Device 004: ID 2232:1005 Silicon Motion WebCam SCB-0385N
Bus 001 Device 007: ID 04e8:6864 Samsung Electronics Co., Ltd GT-I9070 (network tethering, USB debugging enabled)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0a5c:219c Broadcom Corp. 
Bus 003 Device 002: ID 1d57:f833 Xenta 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6365184  0
cfg80211              565248  1 wl

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s29f7u7 Link encap:Ethernet  HWaddr <MAC 'enp0s29f7u7' [IF1]>  
          inet addr:192.168.42.84  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::12d2:c931:5a4e:e1de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1661222 (1.6 MB)  TX bytes:574935 (574.9 KB)

enp9s0    Link encap:Ethernet  HWaddr <MAC 'enp9s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

wlp5s0    Link encap:Ethernet  HWaddr <MAC 'wlp5s0' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:748 errors:0 dropped:0 overruns:0 frame:26274
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84524 (84.5 KB)  TX bytes:1144 (1.1 KB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

enp0s29f7u7  no wireless extensions.

enp9s0    no wireless extensions.

wlp5s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s29f7u7
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s29f7u7
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s29f7u7

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       965     1  0 20:48 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s29f7u7
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s29f7u7' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/net/enp0s29f7u7
GENERAL.IP-IFACE:                       enp0s29f7u7
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       afaa9c52-6f78-3657-bcfa-3b630c66c749
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{31}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   afaa9c52-6f78-3657-bcfa-3b630c66c749 | Wired connection 2
IP4.ADDRESS[1]:                         192.168.42.84/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.84
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
DHCP4.OPTION[19]:                       expiry = 1482938401
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = ympnote
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::12d2:c931:5a4e:e1de/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.248 (r487574)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:05:00.0/net/wlp5s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{20}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d36a747a-3e36-4d68-ad38-f8762ce9f147 | GL 6R

GENERAL.DEVICE:                         enp9s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8040 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp9s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:09:00.0/net/enp9s0
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

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
GL4R                <MAC 'GL4R' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Technomation Guest  <MAC 'Technomation Guest' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2  no        
HUAWEI-4180         <MAC 'HUAWEI-4180' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
Technomation        <MAC 'Technomation' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2       no        
GL 5L               <MAC 'GL 5L' [AC3]>  Infra  9     2452 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA2       no        
GL 6R               <MAC 'GL 6R' [AC2]>  Infra  10    2457 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
GL 7R               <MAC 'GL 7R' [AN7]>  Infra  9     2452 MHz  54 Mbit/s  15      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/YangonBakehouse]] (600 root)
[connection] id=YangonBakehouse | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=YangonBakehouse
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tamri]] (600 root)
[connection] id=Tamri | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Tamri
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/#TELUS]] (600 root)
[connection] id=#TELUS | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=#TELUS
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GL 6R]] (600 root)
[connection] id=GL 6R | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=GL 6R
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/963C14]] (600 root)
[connection] id=963C14 | type=wifi | permissions=user:ubuntu-mate:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=963C14
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DQQ-54442_2GEXT]] (600 root)
[connection] id=DQQ-54442_2GEXT | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=DQQ-54442_2GEXT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/earthnet]] (600 root)
[connection] id=earthnet | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=earthnet
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ShawOpen]] (600 root)
[connection] id=ShawOpen | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=ShawOpen
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UNOG-Public-WiFi]] (600 root)
[connection] id=UNOG-Public-WiFi | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=UNOG-Public-WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wmo-public]] (600 root)
[connection] id=wmo-public | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=wmo-public
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/81D503]] (600 root)
[connection] id=81D503 | type=wifi | permissions=user:ubuntu-mate:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=81D503
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_YUL Wi-Fi]] (600 root)
[connection] id=.YUL Wi-Fi | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=.YUL Wi-Fi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wireless-N]] (600 root)
[connection] id=Wireless-N | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Wireless-N
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/gdbyia]] (600 root)
[connection] id=gdbyia | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=gdbyia
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tamri_2.4GHz]] (600 root)
[connection] id=Tamri_2.4GHz | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Tamri_2.4GHz
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SHAW-E6B260]] (600 root)
[connection] id=SHAW-E6B260 | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SHAW-E6B260
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GL 6L]] (600 root)
[connection] id=GL 6L | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=GL 6L
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wireless-N 1]] (600 root)
[connection] id=Wireless-N 1 | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Wireless-N
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Jomon]] (600 root)
[connection] id=Jomon | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Jomon
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/   .@  TRUEWIFI]] (600 root)
[connection] id=\s\s\s.@  TRUEWIFI | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=\s\s\s.@  TRUEWIFI
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GVPL]] (600 root)
[connection] id=GVPL | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=GVPL
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AFKLM_Sky_Lounge]] (600 root)
[connection] id=AFKLM_Sky_Lounge | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=AFKLM_Sky_Lounge
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Campground-EXT]] (600 root)
[connection] id=Campground-EXT | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Campground-EXT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BC Ferries]] (600 root)
[connection] id=BC Ferries | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=BC Ferries
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/@yvrairport]] (600 root)
[connection] id=@yvrairport | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=@yvrairport
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 2]] (600 root)
[connection] id=Wi-Fi connection 2 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=SHAW-E6B260
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Free Airport WIFI]] (600 root)
[connection] id=Free Airport WIFI | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=Free Airport WIFI
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/@Hyatt_WiFi]] (600 root)
[connection] id=@Hyatt_WiFi | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=@Hyatt_WiFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=E6B260
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/SHAW-68AB60]] (600 root)
[connection] id=SHAW-68AB60 | type=wifi | permissions=user:ymp:;
[wifi] mac-address=<MAC 'wlp5s0' [IF3]> | mac-address-blacklist= | ssid=SHAW-68AB60
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Rangoon (based on set time zone)

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

enp0s29f7u7  no frequency information.

enp9s0    no frequency information.

wlp5s0    32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s29f7u7  Interface doesn't support scanning.

enp9s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp5s0    Scan completed :
          Cell 01 - Address: <MAC 'GL4R' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"GL4R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'GL 6R' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"GL 6R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'GL 5L' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"GL 5L"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Technomation' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Technomation"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Technomation Guest' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Technomation Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-57-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     4DDC5FCDB1E30F7DFDCA530
depends:        cfg80211
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

##### dmesg #############################

[  726.712603] CPU: 0 PID: 554 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-57-generic #78-Ubuntu
[  726.712946]  [<ffffffffc0540955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  726.713103]  [<ffffffffc053ffb0>] wl_event_handler+0x60/0x1d0 [wl]
[  726.713259]  [<ffffffffc053ff50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  730.092623] CPU: 0 PID: 554 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-57-generic #78-Ubuntu
[  730.092966]  [<ffffffffc0540955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  730.093123]  [<ffffffffc053ffb0>] wl_event_handler+0x60/0x1d0 [wl]
[  730.093279]  [<ffffffffc053ff50>] ? wl_notify_scan_status+0x320/0x320 [wl]
[  732.734420] ERROR @wl_dev_intvar_get : error (-1)
[  733.368796] CPU: 2 PID: 554 Comm: wl_event_handle Tainted: P        W  OE   4.4.0-57-generic #78-Ubuntu
[  733.369284]  [<ffffffffc0540955>] wl_notify_roaming_status+0xc5/0x140 [wl]
[  733.369494]  [<ffffffffc053ffb0>] wl_event_handler+0x60/0x1d0 [wl]
[  733.369703]  [<ffffffffc053ff50>] ? wl_notify_scan_status+0x320/0x320 [wl]

########## wireless info END ############


```
OK, figured that out by searching insert code

---

### Post by wildmanne39 on 2016-12-28
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
```
sudo sed -i '/blacklist bcma/ d' /etc/modprobe.d/blacklist.conf
```
```
sudo sed -i '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by yeshua-1 on 2016-12-28
Done, but still no joy.

---

### Post by wildmanne39 on 2016-12-28
We need to also do:
```
sudo apt-get install --reinstall network-manager-gnome
```
if wifi does not work after doing the above command please run the wireless script again and post the new file created so we can make sure the changes stuck.
Thanks

---

