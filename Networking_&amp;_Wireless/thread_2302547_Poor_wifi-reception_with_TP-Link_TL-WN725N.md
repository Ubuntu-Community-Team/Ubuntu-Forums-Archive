---
title: "Poor wifi-reception with TP-Link TL-WN725N"
date: 2015-11-11
forum: Networking &amp; Wireless
---

### Post by damien14 on 2015-11-11
Hi,

I've recently bought a second-hand Lenovo Ideapad U310 laptop, which is known to have issues with non-functioning internal wireless card, and installed Xubuntu 15.10 (which works like a charm).
I knew that and thought I would just buy a little usb wifi adapter, in my case a TP-Link TL-WN725N. 
The problem is, for some reason, it shows the same symptoms as the defective integrated chip. The adapter actually works, but the signal is very low.
You have to be very close to the Internet box, literally one meter away, to be able to browse the Web. I thought maybe my network was the issue, but I tried to connect to other wireless networks like at my university and it's the same problem. I can actually see all the available networks and connect to them, but the signal is so poor that I can't go online.
First I thought there was some sort of conflict between the usb adapter and the internal chip, so I disabled the internal one in the bios. This did not have any effect whatsoever.

Here is the output of the wireless-info script (I'm not sure what to include so here's the whole file) :

```

########## wireless info START ##########

Report from: 11 Nov 2015 12:41 CET +0100

Booted last: 11 Nov 2015 00:00 CET +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-16-lowlatency #19-Ubuntu SMP PREEMPT Thu Oct 8 16:19:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 04f3:003f Elan Microelectronics Corp. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 5986:0295 Acer, Inc 
Bus 001 Device 005: ID 0bda:8179 Realtek Semiconductor Corp. RTL8188EUS 802.11n Wireless Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              557056  0
r8188eu               458752  0
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  0
video                  36864  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1420  Metric:1
          RX packets:13858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11397 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12916570 (12.9 MB)  TX bytes:1479515 (1.4 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1420  Metric:1
          RX packets:2387 errors:0 dropped:105 overruns:0 frame:0
          TX packets:1871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:833458 (833.4 KB)  TX bytes:308794 (308.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"Bbox-E7EC6960"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Bbox-E7EC6960' [AC1]>   
          Bit Rate:72.2 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=5/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlan1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       745     1  0 11:57 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n NIC
GENERAL.DRIVER:                         r8188eu
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlan1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/wlan1
GENERAL.IP-IFACE:                       wlan1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Bbox-E7EC6960 1
GENERAL.CON-UUID:                       2ed4fd96-a84f-4161-a937-a90f2f96b361
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2ed4fd96-a84f-4161-a937-a90f2f96b361 | Bbox-E7EC6960 1
IP4.ADDRESS[1]:                         192.168.1.82/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[5]:                        ip_address = 192.168.1.82
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.254
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1447327432
DHCP4.OPTION[21]:                       host_name = damien-laptop-001
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       interface_mtu = 1420
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.1.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.254
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       requested_host_name = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::<IP6 'wlan1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1420
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         40 (Carrier/link changed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/eth0
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
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Bbox-E7EC6960           <MAC 'Bbox-E7EC6960' [AC1]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  WPA1 WPA2    no        
FreeWifi_secure         <MAC 'FreeWifi_secure' [AC6]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA1 802.1X  no        
freebox_Ouhim           <MAC 'freebox_Ouhim' [AC3]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA1         no        
--                      <MAC '' [AC4]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  WPA2         no        
FreeWifi                <MAC 'FreeWifi' [AC5]>  Infra  11    2462 MHz  44 Mbit/s  0       ____  --           no        
--                      <MAC '--' [AN6]>  Infra  8     2447 MHz  44 Mbit/s  0       ____  WPA2         no        
freebox_JCALLS1         <MAC 'freebox_JCALLS1' [AN7]>  Infra  8     2447 MHz  44 Mbit/s  0       ____  WPA1         no        
SFR_EE80                <MAC 'SFR_EE80' [AC7]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  WPA1         no        
SFR WiFi Mobile         <MAC 'SFR WiFi Mobile' [AC9]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  WPA2 802.1X  no        
FreeWifi                <MAC 'FreeWifi' [AN10]>  Infra  8     2447 MHz  44 Mbit/s  0       ____  --           no        
Bouygues Telecom Wi-Fi  <MAC 'Bouygues Telecom Wi-Fi' [AC2]>  Infra  6     2437 MHz  16 Mbit/s  0       ____  --           no        
SFR WiFi FON            <MAC 'SFR WiFi FON' [AC8]>  Infra  11    2462 MHz  16 Mbit/s  0       ____  --           no        

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

[[/etc/NetworkManager/system-connections/UPPAWIFI]] (600 root)
[connection] id=UPPAWIFI | type=wifi
[wifi] ssid=UPPAWIFI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Bbox-E7EC6960 1]] (600 root)
[connection] id=Bbox-E7EC6960 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlan1' [IF]> | mac-address-blacklist= | ssid=Bbox-E7EC6960
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UPPAWIFI 1]] (600 root)
[connection] id=UPPAWIFI 1 | type=wifi
[wifi] ssid=UPPAWIFI | mac-address=<MAC 'wlan1' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Bbox-E7EC6960]] (600 root)
[connection] id=Bbox-E7EC6960 | type=wifi | autoconnect=false
[wifi] ssid=Bbox-E7EC6960 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

wlan1     13 channels in total; available frequencies :
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

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.437 GHz (Channel 6)
      7   APs on   Frequency:2.462 GHz (Channel 11)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'Bbox-E7EC6960' [AC1]>
                    ESSID:"Bbox-E7EC6960"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality=0/100  Signal level=4/100  
          Cell 02 - Address: <MAC 'Bouygues Telecom Wi-Fi' [AC2]>
                    ESSID:"Bouygues Telecom Wi-Fi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 03 - Address: <MAC 'freebox_Ouhim' [AC3]>
                    ESSID:"freebox_Ouhim"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 04 - Address: <MAC '' [AC4]>
                    ESSID:""
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 05 - Address: <MAC 'FreeWifi' [AC5]>
                    ESSID:"FreeWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:300 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 06 - Address: <MAC 'FreeWifi_secure' [AC6]>
                    ESSID:"FreeWifi_secure"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f201
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality:0  Signal level:0  Noise level:0
          Cell 07 - Address: <MAC 'SFR_EE80' [AC7]>
                    ESSID:"SFR_EE80"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Quality:0  Signal level:0  Noise level:0
          Cell 08 - Address: <MAC 'SFR WiFi FON' [AC8]>
                    ESSID:"SFR WiFi FON"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:144 Mb/s
                    Quality:0  Signal level:0  Noise level:0
          Cell 09 - Address: <MAC 'SFR WiFi Mobile' [AC9]>
                    ESSID:"SFR WiFi Mobile"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac010c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Quality:0  Signal level:0  Noise level:0

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.2.0-16-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CC:B0:C2:67:C5:A8:96:ED:12:3A:F6:B9:45:E8:10:D6:1E:B1:07:AA
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8188eu]
filename:       /lib/modules/4.2.0-16-lowlatency/kernel/drivers/staging/rtl8188eu/r8188eu.ko
version:        v4.1.4_6773.20130222
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     1BBF69F35CA1904D717B487
depends:        
staging:        Y
intree:         Y
vermagic:       4.2.0-16-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        CC:B0:C2:67:C5:A8:96:ED:12:3A:F6:B9:45:E8:10:D6:1E:B1:07:AA
sig_hashalgo:   sha512
parm:           rtw_ips_mode:The default IPS mode (int)
parm:           ifname:The default name to allocate for first interface (charp)
parm:           if2name:The default name to allocate for second interface (charp)
parm:           rtw_initmac:charp
parm:           rtw_channel_plan:int
parm:           rtw_chip_version:int
parm:           rtw_rfintfs:int
parm:           rtw_lbkmode:int
parm:           rtw_network_mode:int
parm:           rtw_channel:int
parm:           rtw_wmm_enable:int
parm:           rtw_vrtl_carrier_sense:int
parm:           rtw_vcs_type:int
parm:           rtw_busy_thresh:int
parm:           rtw_ht_enable:int
parm:           rtw_cbw40_enable:int
parm:           rtw_ampdu_enable:int
parm:           rtw_rx_stbc:int
parm:           rtw_ampdu_amsdu:int
parm:           rtw_lowrate_two_xmit:int
parm:           rtw_rf_config:int
parm:           rtw_power_mgnt:int
parm:           rtw_smart_ps:int
parm:           rtw_low_power:int
parm:           rtw_wifi_spec:int
parm:           rtw_antdiv_cfg:int
parm:           rtw_antdiv_type:int
parm:           rtw_enusbss:int
parm:           rtw_hwpdn_mode:int
parm:           rtw_hwpwrp_detect:int
parm:           rtw_hw_wps_pbc:int
parm:           rtw_max_roaming_times:The max roaming times to try (uint)
parm:           rtw_fw_iol:FW IOL (int)
parm:           rtw_mc2u_disable:int
parm:           rtw_80211d:Enable 802.11d mechanism (int)
parm:           rtw_notch_filter:0:Disable, 1:Enable, 2:Enable only for P2P (uint)
parm:           debug:Set debug level (1-9) (default 1) (int)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8188eu]
debug: 1
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_antdiv_type: 0
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 66
rtw_chip_version: 0
rtw_enusbss: 0
rtw_fw_iol: 1
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_smart_ps: 2
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

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

##### rc.local ##########################

sudo ifconfig wlan0 down

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0888 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (r8188eu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    5.043392] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.240475] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[    5.240526] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.828171] r8169 0000:02:00.0 eth0: link up
[    6.828185] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1469.128684] r8169 0000:02:00.0 eth0: link down
[ 1487.985095] r8188eu: module is from the staging directory, the quality is unknown, you have been warned.
[ 1488.019566] r8188eu 1-1:1.0 wlan1: renamed from wlan0
[ 1534.110842] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1534.299190] r8169 0000:02:00.0 eth0: link down
[ 1534.299231] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1561.980399] r8188eu 1-1:1.0 wlan1: renamed from wlan0
[ 1562.016816] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 4 times)
[ 1566.967035] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1569.552067] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1571.266393] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 1900.204791] r8169 0000:02:00.0 eth0: link up
[ 1900.204813] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 2057.523724] r8169 0000:02:00.0 eth0: link down

########## wireless info END ############


```

I would really appreciate any help on this topic as I really need the wifi to work properly at my university.
Thanks a lot in advance for your answers,
D.

---

