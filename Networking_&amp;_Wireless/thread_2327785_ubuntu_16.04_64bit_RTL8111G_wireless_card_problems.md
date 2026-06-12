---
title: "ubuntu 16.04 64bit RTL8111G wireless card problems"
date: 2016-06-14
forum: Networking &amp; Wireless
---

### Post by yoanncooljazz on 2016-06-14
Hello everyone,


  I am running ubuntu 16.04 64bit. I have the Realtek RTL8111G wireless  card, Ubuntu is automatically using the rtl8821ae driver. I have many  problems with it because it disconnect all the time, anyone had this  problem ?

########## wireless info START ##########

Report from: 13 Jun 2016 13:38 CEST +0200

Booted last: 13 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave RTL8821AE 802.11ac PCIe Wireless Network Adapter [1a3b:2161]
    Kernel driver in use: rtl8821ae

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 002: ID 0451:8140 Texas Instruments, Inc. 
Bus 004 Device 003: ID 8564:4000 Transcend Information, Inc. RDF8
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 009: ID 13d3:3414 IMC Networks 
Bus 003 Device 012: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 011: ID 413c:a503 Dell Computer Corp. 
Bus 003 Device 010: ID 08bb:2904 Texas Instruments PCM2904 Audio Codec
Bus 003 Device 006: ID 0451:8142 Texas Instruments, Inc. TUSB8041 4-Port Hub
Bus 003 Device 004: ID 046d:0841 Logitech, Inc. 
Bus 003 Device 007: ID 062a:0000 Creative Labs Optical mouse
Bus 003 Device 008: ID 17ef:6047 Lenovo 
Bus 003 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

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
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          212992  1 snd_soc_rt5640
snd_pcm               106496  8 snd_soc_rt5640,snd_usb_audio,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp2s0    Link encap:Ethernet  HWaddr <MAC 'wlp2s0' [IF2]>  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:a03f:22f:3900:58fe:75:9fe2:7d15/64 Scope:Global
          inet6 addr: 2a02:a03f:22f:3900:c626:cb44:e9:446c/64 Scope:Global
          inet6 addr: fe80::1195:fff9:4f3b:17eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35841 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32029028 (32.0 MB)  TX bytes:4228633 (4.2 MB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11abgn  ESSID:"WiFi-5.0-DEF9"  
          Mode:Managed  Frequency:5.54 GHz  Access Point: <MAC 'WiFi-5.0-DEF9' [AN9]>   
          Bit Rate=150 Mb/s   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=10 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:174   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       874     1  0 13:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-24-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     WiFi-5.0-DEF9 1
GENERAL.CON-UUID:                       c49cd39c-a5f6-4d86-b503-a440c406b17e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,3,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   c49cd39c-a5f6-4d86-b503-a440c406b17e | WiFi-5.0-DEF9 1
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   24c0e52f-7696-4687-95a7-a3a4e6bb225f | WiFi-2.4-DEF9
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   bd129b37-e54e-459a-a93e-f985d0e59afc | WiFi-5.0-A8A2
IP4.ADDRESS[1]:                         192.168.1.35/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1465821220
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.35
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 3600
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         2a02:a03f:22f:3900:58fe:75:9fe2:7d15/64
IP6.ADDRESS[2]:                         2a02:a03f:22f:3900:c626:cb44:e9:446c/64
IP6.ADDRESS[3]:                         fe80::1195:fff9:4f3b:17eb/64
IP6.GATEWAY:                            fe80::3291:8fff:fe3e:def8
IP6.ROUTE[1]:                           dst = 2a02:a03f:22f:3900::/56, nh = fe80::3291:8fff:fe3e:def8, mt = 600
IP6.DNS[1]:                             fe80::3291:8fff:fe3e:def8
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::3291:8fff:fe3e:def8
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC address>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:d4:4b:96:54:e4:b3:0:7e:59:ea:25:b0:a1:86:27:12

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
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
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

GENERAL.DEVICE:                         hfp/org/bluez/hci0/dev_10_68_3F_58_6A_FC
GENERAL.TYPE:                           gsm
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ofono
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /hfp/org/bluez/hci0/dev_10_68_3F_58_6A_FC
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
WiFi-2.4-DEF9      <MAC 'WiFi-2.4-DEF9' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2         no        
PROXIMUS_FON       <MAC 'PROXIMUS_FON' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  --           no        
PROXIMUS_AUTO_FON  <MAC 'PROXIMUS_AUTO_FON' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
WiFi-2.4-8B97      <MAC 'WiFi-2.4-8B97' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2         no        
PROXIMUS_FON       <MAC 'PROXIMUS_FON' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  --           no        
PROXIMUS_AUTO_FON  <MAC 'PROXIMUS_AUTO_FON' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA2 802.1X  no        
WiFi-5.0-A8A2      <MAC 'WiFi-5.0-A8A2' [AN7]>  Infra  132   5660 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2         no        
WiFi-2.4-A8A2      <MAC 'WiFi-2.4-A8A2' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2         no        
WiFi-5.0-DEF9      <MAC 'WiFi-5.0-DEF9' [AN9]>  Infra  108   5540 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA2         yes     * 
WiFi-5.0-8B97      <MAC 'WiFi-5.0-8B97' [AN10]>  Infra  112   5560 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2         no        

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

[[/etc/NetworkManager/system-connections/WiFi-5.0-DEF9 1]] (600 root)
[connection] id=WiFi-5.0-DEF9 1 | type=wifi | permissions=user:yoann:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=WiFi-5.0-DEF9
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-5.0-DEF9]] (600 root)
[connection] id=WiFi-5.0-DEF9 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=WiFi-5.0-DEF9
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-5.0-A8A2]] (600 root)
[connection] id=WiFi-5.0-A8A2 | type=wifi | permissions=user:yoann:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=WiFi-5.0-A8A2
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-2.4-DEF9]] (600 root)
[connection] id=WiFi-2.4-DEF9 | type=wifi | permissions=user:yoann:;
[wifi] mac-address=<MAC 'wlp2s0' [IF2]> | mac-address-blacklist= | ssid=WiFi-2.4-DEF9
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Brussels (based on set time zone)

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
          Current Frequency:5.54 GHz (Channel 108)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

wlp2s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     CCAF123FC0D21AE93AD5A6F
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-24-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     251B17ACC83990EE9A63C56
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-24-generic SMP mod_unload modversions 
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

[   10.108681] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   10.108684] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   10.182945] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   10.182949] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   10.191216] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.191814] rtlwifi: rtlwifi: wireless switch is on
[   10.273641] rtl8821ae 0000:02:00.0 wlp2s0: renamed from wlan0
[   10.953453] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[   11.195891] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   11.238565] r8169 0000:03:00.0 enp3s0: link down
[   11.238626] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   11.375097] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   20.126571] wlp2s0: authenticate with <MAC 'WiFi-5.0-DEF9' [AN9]>
[   20.267115] wlp2s0: send auth to <MAC 'WiFi-5.0-DEF9' [AN9]> (try 1/3)
[   20.268229] wlp2s0: authenticated
[   20.271150] wlp2s0: associate with <MAC 'WiFi-5.0-DEF9' [AN9]> (try 1/3)
[   20.279351] wlp2s0: RX AssocResp from <MAC 'WiFi-5.0-DEF9' [AN9]> (capab=0x511 status=0 aid=10)
[   20.282827] wlp2s0: associated
[   20.282834] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready

########## wireless info END ############

---

