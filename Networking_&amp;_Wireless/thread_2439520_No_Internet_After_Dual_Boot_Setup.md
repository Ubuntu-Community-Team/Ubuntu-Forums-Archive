---
title: "No Internet After Dual Boot Setup"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by wewantutopia on 2020-03-28
Hello. 

Until yesterday morning I had a perfectly working 16.04 dual boot install.  Needing to use some Windows software for work I replaced a long unused W7 install on a separate partition with W10. After some excellent help from OLDFRED fixing a bootflag and grub issue they are both up and running. Except... 

I have no internet. I can connect to wifi, connect to my router and other devices in my network but no internet. All other devices on the network work fine and the W10 install also has internet. I can ping the dns server fine but host [www.google.com](www.google.com) gives me connection timed out; no servers could be reached.

I ran the wireless-info script and below is the output. 

Anyone notice any problems? 

Any help is greatly appreciated!! 

```

########## wireless info START ##########

Report from: 28 Mar 2020 13:57 CDT -0500

Booted last: 28 Mar 2020 00:00 CDT -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-176-generic #206-Ubuntu SMP Fri Feb 28 05:02:04 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak] [8086:0091] (rev 34)
	Subsystem: Intel Corporation Centrino Advanced-N 6230 AGN [8086:5201]
	Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Samsung Electronics Co Ltd RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [144d:c0b3]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1018 Silicon Motion 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: samsung-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: samsung-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

iwldvm                233472  0
mac80211              737280  1 iwldvm
iwlwifi               200704  1 iwldvm
cfg80211              565248  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>
    inet 192.168.1.235/24 brd 192.168.1.255 scope global dynamic wlp2s0
       valid_lft 85270sec preferred_lft 85270sec
    inet6 fe80::2e0c:1e32:b88a:82e3/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"wewantutopia1"  
          Mode:Managed  Frequency:5.24 GHz  Access Point: <MAC 'wewantutopia1' [AC1]>   
          Bit Rate=216 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:218   Missed beacon:0

##### route #############################

default via 192.168.1.1 dev wlp2s0  proto static  metric 600 
169.254.0.0/16 dev wlp2s0  scope link  metric 1000 
192.168.1.0/24 dev wlp2s0  proto kernel  scope link  src 192.168.1.235  metric 600 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1113     1  0 13:02 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6230 [Rainbow Peak] (Centrino Advanced-N 6230 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-176-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     wewantutopia1
GENERAL.CON-UUID:                       8a1c8ae7-8747-4b1f-b680-46adf64c8d5d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     135 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,11,15,0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   56e522fc-943c-410a-9c77-2dad2a474725 | Chromecast7090
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   483741ba-f753-4ae2-96ac-e1b61001e052 | wewantutopia
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   ce43afef-d62c-4b30-8a92-4bf6e0762a2d | wewantutopia2
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   8a1c8ae7-8747-4b1f-b680-46adf64c8d5d | wewantutopia1
IP4.ADDRESS[1]:                         192.168.1.235/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.235
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
DHCP4.OPTION[20]:                       expiry = 1585507129
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dk
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::2e0c:1e32:b88a:82e3/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_F8_95_C7_17_A5_D2
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{24}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   79b25038-b298-4091-b989-734fac4921a3 | Dave's LG G4  Network

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/enp3s0
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
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
wewantutopia    <MAC 'wewantutopia' [AC2]>  Infra  9     2452 MHz  54 Mbit/s  97      &#9602;&#9604;&#9606;&#9608;  WPA2      no        
wewantutopia2   <MAC 'wewantutopia2' [AC5]>  Infra  161   5805 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2      no        
wewantutopia1   <MAC 'wewantutopia1' [AC1]>  Infra  48    5240 MHz  54 Mbit/s  76      &#9602;&#9604;&#9606;_  WPA2      yes     * 
Chromecast7090  <MAC '' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --        no        
ATT8N58wnt      <MAC 'ATT8N58wnt' [AC3]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2      no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/ATTp4jZsFi]] (600 root)
[connection] id=ATTp4jZsFi | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ATTp4jZsFi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Awesome Repeater]] (600 root)
[connection] id=Awesome Repeater | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Awesome Repeater
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Howard]] (600 root)
[connection] id=Howard | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Howard
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/sammy5G2]] (600 root)
[connection] id=sammy5G2 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=sammy5G2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Howard1-guest]] (600 root)
[connection] id=Howard1-guest | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Howard1-guest
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FoxFi32]] (600 root)
[connection] id=FoxFi32 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=FoxFi32
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-Ny-V20]] (600 root)
[connection] id=DIRECT-Ny-V20 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=DIRECT-Ny-V20
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ATT2K8h7b3]] (600 root)
[connection] id=ATT2K8h7b3 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=ATT2K8h7b3
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=xfinitywifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/v20]] (600 root)
[connection] id=v20 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=v20
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Chromecast7090]] (600 root)
[connection] id=Chromecast7090 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Chromecast7090
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Howard1]] (600 root)
[connection] id=Howard1 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=Howard1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CBCI-35F4-2.4]] (600 root)
[connection] id=CBCI-35F4-2.4 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=CBCI-35F4-2.4
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/landconservancy]] (600 root)
[connection] id=landconservancy | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=landconservancy
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/dd]] (600 root)
[connection] id=dd | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=dd
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/repeater]] (600 root)
[connection] id=repeater | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=repeater
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CBCI-35F4-5]] (600 root)
[connection] id=CBCI-35F4-5 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=CBCI-35F4-5
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wewantutopia1]] (600 root)
[connection] id=wewantutopia1 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=wewantutopia1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bearpaw]] (600 root)
[connection] id=bearpaw | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=bearpaw
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wewantutopia2]] (600 root)
[connection] id=wewantutopia2 | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=wewantutopia2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CBCI-35F4-2.4_2GEXT]] (600 root)
[connection] id=CBCI-35F4-2.4_2GEXT | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=CBCI-35F4-2.4_2GEXT
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/that wifi]] (600 root)
[connection] id=that wifi | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=that wifi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/wewantutopia]] (600 root)
[connection] id=wewantutopia | type=wifi | permissions=user:david:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=wewantutopia
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:5.24 GHz (Channel 48)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.805 GHz

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'wewantutopia1' [AC1]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"wewantutopia1"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f6cf5a37d
                    Extra: Last beacon: 300ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'wewantutopia' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"wewantutopia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f6cc7ed08
                    Extra: Last beacon: 3156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'ATT8N58wnt' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"ATT8N58wnt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000046a65f951d
                    Extra: Last beacon: 3176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f6cc85142
                    Extra: Last beacon: 3164ms ago
          Cell 05 - Address: <MAC 'wewantutopia2' [AC5]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"wewantutopia2"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007f6cbd63fb
                    Extra: Last beacon: 136ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.4.0-176-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     58FF645F7DE3DD061B613D8
depends:        mac80211,iwlwifi,cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-176-generic SMP mod_unload modversions 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.4.0-176-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     CD58AC927E26FDA6A73F559
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-176-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-176-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     CB5AC244E1344F14798FC7E
depends:        cfg80211
retpoline:      Y
intree:         Y
vermagic:       4.4.0-176-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.4.0-176-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     649B1B8B37AC928F18974F4
depends:        
retpoline:      Y
intree:         Y
vermagic:       4.4.0-176-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

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
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

coretemp

coretemp

coretemp

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

[/etc/modprobe.d/intel_powerclamp.conf]
install intel_powerclamp /bin/true

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

[  114.131817] iwlwifi 0000:02:00.0: Not sending command - RF KILL
[  114.131821] wlp2s0: failed to remove key (2, <MAC address>) from hardware (-5)
[  114.132105] iwlwifi 0000:02:00.0: Not sending command - RF KILL (repeated 2 times)
[  135.744805] r8169 0000:03:00.0 enp3s0: link up
[  135.744817] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  192.807649] r8169 0000:03:00.0 enp3s0: link down
[ 2183.322203] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 2183.322493] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[ 2183.329227] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[ 2183.604254] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled (repeated 2 times)
[ 2183.610955] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[ 2183.695256] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[ 2189.909693] wlp2s0: authenticate with <MAC 'wewantutopia1' [AC1]>
[ 2189.911907] wlp2s0: send auth to <MAC 'wewantutopia1' [AC1]> (try 1/3)
[ 2189.930345] wlp2s0: authenticated
[ 2189.931877] wlp2s0: associate with <MAC 'wewantutopia1' [AC1]> (try 1/3)
[ 2189.932703] wlp2s0: RX AssocResp from <MAC 'wewantutopia1' [AC1]> (capab=0x1011 status=0 aid=1)
[ 2189.935028] wlp2s0: associated
[ 2189.935075] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[ 2190.032149] wlp2s0: Limiting TX power to 30 (30 - 0) dBm as advertised by <MAC 'wewantutopia1' [AC1]>

########## wireless info END ############


   
```

---

### Post by pcfan1234 on 2020-03-30
Show the output of
```

systemd-resolve --status
ls -la /etc/resolv.conf
ping 9.9.9.9 -c 4
nslookup google.de 9.9.9.9
nslookup google.de

```

---

### Post by wewantutopia on 2020-03-30
Thanks for the reply!

Output:  systemd-resolve: unrecognized option '--status"

---

### Post by pcfan1234 on 2020-03-30
Please show the output of the other commands too.
Also explain (if you can) why 127.0.0.53 is in your resolv.conf.
That is normal only in 18.04, in 16.04 dnsmasq-base is installed and runs on 127.0.0.1:53
Please also show ```
dpkg -l |grep dnsmasq
dpkg -l |grep resolvconf
```

---

### Post by wewantutopia on 2020-03-30
Here is the output:   ```
  
david@dk:~$ ls -la /etc/resolv.conf
-rw-r--r-- 1 root root 715 Mar 27 15:32 /etc/resolv.conf


david@dk:~$ ping 9.9.9.9 -c 4
PING 9.9.9.9 (9.9.9.9) 56(84) bytes of data.
64 bytes from 9.9.9.9: icmp_seq=1 ttl=57 time=15.0 ms
64 bytes from 9.9.9.9: icmp_seq=2 ttl=57 time=15.5 ms
64 bytes from 9.9.9.9: icmp_seq=3 ttl=57 time=22.4 ms
64 bytes from 9.9.9.9: icmp_seq=4 ttl=57 time=12.8 ms

--- 9.9.9.9 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 12.813/16.477/22.487/3.619 ms

david@dk:~$ nslookup google.de 9.9.9.9
Server:		9.9.9.9
Address:	9.9.9.9#53

Non-authoritative answer:
Name:	google.de
Address: 172.217.4.227

david@dk:~$ nslookup google.de
;; connection timed out; no servers could be reached

david@dk:~$ dpkg -l |grep dnsmasq
ii  dnsmasq-base                                  2.75-1ubuntu0.16.04.5                           amd64        Small caching DNS proxy and DHCP/TFTP server

david@dk:~$ dpkg -l |grep resolvconf
ii  resolvconf                                    1.78ubuntu7                                     all          name server information handler



  
```

I'm not sure what is up with the 127.0.0.1:53

THANK YOU FOR YOUR HELP!!

---

### Post by pcfan1234 on 2020-03-30
Your internet is working, DNS resolving is broken.
Show
```

cat /run/resolvconf/resolv.conf

```

---

### Post by wewantutopia on 2020-03-30
I'm back, had to go to work.

Output of cat /run/resolvconf/resolv.conf:   nameserver 127.0.1.1

---

### Post by wewantutopia on 2020-03-31
So the wireless-info script is showing /etc/resolv.conf nameserver 127.0.0.53  but /run/resolvconf/resolv.conf says nameserver is 127.0.1.1 

I'm guessing that is part of the problem?

---

### Post by wewantutopia on 2020-04-02
I'm still unable to figure out a solution to this issue... Anyone have any ideas?

Thank you!!

---

### Post by wewantutopia on 2020-04-03
Ok, I finally figured it out after pouring through countless threads between here and AskUbuntu.  I followed [this]("https://askubuntu.com/questions/1062394/how-to-repair-dns-resolution-in-ubuntu-16-04") thread and [COLOR=#242729][FONT=Arial]ran:

```
[/FONT][/COLOR]sudo dpkg-reconfigure resolvconf[COLOR=#242729][FONT=Arial]
```[/FONT][/COLOR][COLOR=#242729][FONT=Arial] to repair symlink between [/FONT][/COLOR]/etc/resolv.conf[COLOR=#242729][FONT=Arial] and [/FONT][/COLOR]/run/resolvconf/resolv.conf


I have functioning web connection again!!!!!!!!!!!

---

