---
title: "Can only connect to original WPA network"
date: 2015-12-17
forum: Networking &amp; Wireless
---

### Post by SlidingHorn on 2015-12-17
I'm using a stripped down version of ubuntu 15.10 (technically used the xubuntu install) on my laptop (HP 15) where I removed the GUI entirely and installed X, xdm & openbox.  I cannot connect to any WPA network other than the one that was set up during installation. 

Here's the output of the wifi script:
```
########## wireless info START ##########

Report from: 17 Dec 2015 14:59 EST -0500

Booted last: 17 Dec 2015 00:00 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-19-generic #23-Ubuntu SMP Wed Nov 11 11:39:30 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

xubuntu (from ~/.dmrc)

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	DeviceName: Realtek 802.11 b/g/n w/ *2 antennas
	Subsystem: Hewlett-Packard Company Device [103c:197d]

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 08)
	Subsystem: Hewlett-Packard Company Device [103c:21de]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 0bda:0401 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05c8:022a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 003: ID 045e:07b2 Microsoft Corp. 
Bus 001 Device 002: ID 0bda:5401 Realtek Semiconductor Corp. RTL 8153 USB 3.0 hub with gigabit ethernet
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8188ee              86016  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                77824  2 rtl_pci,rtl8188ee
hp_wmi                 16384  0
mac80211              733184  3 rtl_pci,rtlwifi,rtl8188ee
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  2 mac80211,rtlwifi
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          200704  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_pcm_dmaengine,snd_hda_core
wmi                    20480  1 hp_wmi

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

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:3106:d0a0:<IP6 'wlo1' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1645 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1892766 (1.8 MB)  TX bytes:224371 (224.3 KB)

##### iwconfig ##########################

enp3s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"T 2 Wifi "  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'T 2 Wifi ' [AC1]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search attlocal.net

##### network managers ##################

Installed:

	NetworkManager

Running:

root       635     1  0 14:57 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.2.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     T 2 Wifi 
GENERAL.CON-UUID:                       243a88d2-6fab-437c-a055-4cd2b7cf13c7
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   243a88d2-6fab-437c-a055-4cd2b7cf13c7 | T 2 Wifi 
IP4.ADDRESS[1]:                         192.168.1.111/24
IP4.GATEWAY:                            192.168.1.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.254
IP4.DOMAIN[1]:                          attlocal.net
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1450486665
DHCP4.OPTION[10]:                       next_server = 192.168.1.254
DHCP4.OPTION[11]:                       domain_name = attlocal.net
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.254
DHCP4.OPTION[16]:                       ip_address = 192.168.1.111
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         2602:306:3106:d0a0:<IP6 'wlo1' [IF]>/64
IP6.ADDRESS[2]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            fe80::62c3:97ff:fe48:fa09
IP6.ROUTE[1]:                           dst = 2602:306:3106:d0a0::/64, nh = ::, mt = 600

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
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

SSID                          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
2WIRE913                      <MAC '2WIRE913' [AC2]>  Infra  3     2422 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        
ATT4K6s9T7                    <MAC 'ATT4K6s9T7' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        
ATTjIwDQgs                    <MAC 'ATTjIwDQgs' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
2WIRE139                      <MAC '2WIRE139' [AC7]>  Infra  10    2457 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1       no        
ATTJnMuHfi                    <MAC 'ATTJnMuHfi' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2  no        
DIRECT-roku-624               <MAC 'DIRECT-roku-624' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
2WIRE266                      <MAC '2WIRE266' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1       no        
Miljak                        <MAC 'Miljak' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
2WIRE700                      <MAC '2WIRE700' [AN9]>  Infra  9     2452 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
TG862G12                      <MAC 'TG862G12' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
ATT5N9c235                    <MAC 'ATT5N9c235' [AN11]>  Infra  9     2452 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
ATTeuUcmS2                    <MAC 'ATTeuUcmS2' [AC6]>  Infra  6     2437 MHz  54 Mbit/s  34      &#9602;&#9604;__  WEP        no        
HP-Print-85-Officejet 6600    <MAC 'HP-Print-85-Officejet 6600' [AC3]>  Infra  7     2442 MHz  54 Mbit/s  60      &#9602;&#9604;&#9606;_  --         no        
HP-Print-DD-ENVY 4500 series  <MAC 'HP-Print-DD-ENVY 4500 series' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  --         no        
T 2 Wifi                      <MAC 'T 2 Wifi ' [AC1]>  Infra  7     2442 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
shadow                        <MAC 'shadow' [AN16]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
2WIRE181                      <MAC '2WIRE181' [AN17]>  Infra  5     2432 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
ASUS_Guest                    <MAC 'ASUS_Guest' [AN18]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2       no        
ATTJeAuMS2                    <MAC 'ATTJeAuMS2' [AN19]>  Infra  11    2462 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/T 2 Wifi ]] (600 root)
[connection] id=T 2 Wifi  | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=T 2 Wifi 
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/2WIRE302]] (600 root)
[connection] id=2WIRE302 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=2WIRE302
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp3s0    no frequency information.

lo        no frequency information.

wlo1      11 channels in total; available frequencies :
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
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

enp3s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.422 GHz (Channel 3)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'T 2 Wifi ' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"T 2 Wifi "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000259090ea18
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '2WIRE913' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE913"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000015794beccce
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-85-Officejet 6600' [AC3]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-85-Officejet 6600"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b19d90322
                    Extra: Last beacon: 84ms ago
          Cell 04 - Address: <MAC 'ATTJnMuHfi' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"ATTJnMuHfi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b9008b58a8
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'ATT4K6s9T7' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ATT4K6s9T7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b9006dacca
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'ATTeuUcmS2' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ATTeuUcmS2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002b9005c82f5
                    Extra: Last beacon: 84ms ago
          Cell 07 - Address: <MAC '2WIRE139' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"2WIRE139"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005667475fe0
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     521127E57F4409EF9EC91CF
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
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

[rtl_pci]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A888EFDC516033207A503FA
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-19-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     065F4A11FE84275F51A59F2
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-19-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        36:C9:DD:EE:C2:96:8B:FC:DA:67:40:D7:CD:68:4B:F0:4B:70:27:94
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
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

[   13.506737] rtl8188ee: rtl8188ee: Power Save off (module option)
[   13.506743] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[   13.506765] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   13.561312] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.561666] rtlwifi: rtlwifi: wireless switch is on
[   13.715434] rtl8188ee 0000:02:00.0 wlo1: renamed from wlan0
[   23.437695] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   23.834544] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   23.919740] r8169 0000:03:00.0 enp3s0: link down
[   23.919792] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[   24.020375] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   24.909660] wlo1: authenticate with <MAC 'T 2 Wifi ' [AC1]>
[   24.919719] wlo1: send auth to <MAC 'T 2 Wifi ' [AC1]> (try 1/3)
[   24.927280] wlo1: authenticated
[   24.927624] rtl8188ee 0000:02:00.0 wlo1: disabling HT as WMM/QoS is not supported by the AP
[   24.927629] rtl8188ee 0000:02:00.0 wlo1: disabling VHT as WMM/QoS is not supported by the AP
[   24.931099] wlo1: associate with <MAC 'T 2 Wifi ' [AC1]> (try 1/3)
[   24.933081] wlo1: RX AssocResp from <MAC 'T 2 Wifi ' [AC1]> (capab=0x431 status=0 aid=1)
[   24.933362] wlo1: associated
[   24.933409] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready

########## wireless info END ############
```

This is especially difficult to troubleshoot, as when I'm at home, I don't have a "new" network to which I can try to connect, and when I'm away, well...I can't connect, lol.  Any help would be more than appreciated.

---

### Post by SlidingHorn on 2015-12-26
So, I think I may have found the issue.  Someone in the house did a factory reset on the router at home, meaning I had to add a new network, and I was able to connect.  I think what may have been the problem is that I was trying to be too explicit in my configuration in nm-connection-editor.  I was actually entering the MAC when trying to add new networks.

This time, when I went to enter the new information for the reset network, I left that field blank and it popped right on.  

I'll be able to test and post back in a few days, if anyone's interested in hearing of a solution.

---

### Post by SlidingHorn on 2016-01-03
The issue was likely a combination of up to three issues.  

1. First, I wasn't running nm-connection-editor with privileges.  I would enter the password when prompted, and I'd be prompted each time I'd log in to enter a password.

2. Second, I was definitely being too explicit in defining the network (i.e. Using the MAC address found when I'd run a scan for networks)

3. I was not using the "Save for all users" option when entering the password. 

All in all, three little things I should have noticed earlier.  Thanks for viewing & giving it any thought to those who did :)  Marking "Solved"

---

