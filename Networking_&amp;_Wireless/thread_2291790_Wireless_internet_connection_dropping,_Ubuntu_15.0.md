---
title: "Wireless internet connection dropping, Ubuntu 15.04"
date: 2015-08-22
forum: Networking &amp; Wireless
---

### Post by afonso2 on 2015-08-22
First of all, I want to apologize for making previous threads without reading the terms and other threads that explained how to make a proper thread.

I own an Asus-S551LN laptop and I have installed Ubuntu 15.04 alongside Windows 10. After some days of usage, I found that the wireless connection is constantly dropping. While the Wireless icon in the top bar indicates that it's connected, there seems to be no Internet connection. This happens after a couple of minutes of usage and I have to reboot the entire system to get back an Internet connection.

The problem happens most often **but not exclusively** when the laptop lid closes, the system suspends or when the battery percentage is relatively low.

How can I fix this issue and get a stable connection?

I have ran the wireless info script and here is the output:

```
########## wireless info START ##########

Report from: 23 Aug 2015 00:06 WEST +0100

Booted last: 23 Aug 2015 03:02 WEST +0100

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:32 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4160]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 004: ID 0457:1024 Silicon Integrated Systems Corp. 
Bus 001 Device 003: ID 13d3:5195 IMC Networks 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                278528  0 
mac80211              724992  1 iwlmvm
asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  1 snd_soc_rt5640
iwlwifi               196608  1 iwlmvm
snd_pcm               106496  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
mxm_wmi                16384  1 nouveau
cfg80211              540672  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  3 mxm_wmi,nouveau,asus_wmi
video                  20480  3 i915,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:463323 (463.3 KB)  TX bytes:214424 (214.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Optimus-Kanguru-C77A73"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Optimus-Kanguru-C77A73' [AC1]>   
          Bit Rate=11 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:164   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search kanguru4g.hotspot

##### network managers ##################

Installed:

    NetworkManager

Running:

root       702     1  0 00:02 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7260 (Dual Band Wireless-N 7260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-26-generic
GENERAL.FIRMWARE-VERSION:               25.17.12.0
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Optimus-Kanguru-C77A73
GENERAL.CON-UUID:                       dc62d692-5ea7-49a6-b03c-ed442b25a140
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     11 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1,0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d65b95c0-103a-4289-b15f-c724918d8b18 | WiFi_9A1F
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   dc62d692-5ea7-49a6-b03c-ed442b25a140 | Optimus-Kanguru-C77A73
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   f81da69b-9524-4ca6-aaf1-17ab498e4c72 | Cabovisao-44D0
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.1.104/24, gw = 192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          kanguru4g.hotspot
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        expiry = 1440378157
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       domain_name = kanguru4g.hotspot
DHCP4.OPTION[12]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       ip_address = 192.168.1.104
DHCP4.OPTION[17]:                       dhcp_lease_time = 86400
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[22]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.1 192.168.1.1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       requested_netbios_scope = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         ip = fe80::<IP6 'wlan0' [IF]>/64, gw = ::

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off

SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Thomson1898BE           <MAC 'Thomson1898BE' [AC6]>  Infra  9     2452 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Cabovisao-44D0          <MAC 'Cabovisao-44D0' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  WPA1 WPA2  no        
Thomson960827           <MAC 'Thomson960827' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2  no        
WiFi_9A1F               <MAC 'WiFi_9A1F' [AN4]>  Infra  5     2432 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        
WIRELESS4               <MAC 'WIRELESS4' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  --         no        
Optimus-Kanguru-C77A73  <MAC 'Optimus-Kanguru-C77A73' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA1 WPA2  yes     * 

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

[[/etc/NetworkManager/system-connections/HUAWEI-E5172-FA99]] (600 root)
[connection] id=HUAWEI-E5172-FA99 | type=wifi
[wifi] ssid=HUAWEI-E5172-FA99 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi_9A1F]] (600 root)
[connection] id=WiFi_9A1F | type=wifi
[wifi] ssid=WiFi_9A1F | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Cabovisao-44D0]] (600 root)
[connection] id=Cabovisao-44D0 | type=wifi
[wifi] ssid=Cabovisao-44D0 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Optimus-Kanguru-C77A73]] (600 root)
[connection] id=Optimus-Kanguru-C77A73 | type=wifi
[wifi] ssid=Optimus-Kanguru-C77A73 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Lisbon (based on set time zone)

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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.452 GHz (Channel 9)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Optimus-Kanguru-C77A73' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Optimus-Kanguru-C77A73"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008d4345cd3
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'WIRELESS4' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"WIRELESS4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008526b84f0
                    Extra: Last beacon: 4452ms ago
          Cell 03 - Address: <MAC 'Cabovisao-44D0' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Cabovisao-44D0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b39a7781a1
                    Extra: Last beacon: 4404ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'LOJADOPC' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:off
                    ESSID:"LOJADOPC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000200cff928b
                    Extra: Last beacon: 20ms ago
          Cell 05 - Address: <MAC 'Thomson960827' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Thomson960827"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c110f4b138
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Thomson1898BE' [AC6]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Thomson1898BE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c81f62098f
                    Extra: Last beacon: 20ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     03499C43751395EB809E042
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:BF:A7:5C:65:57:07:FD:5A:4B:C3:A9:A6:CB:49:E0:1A:16:E1:F5
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:BF:A7:5C:65:57:07:FD:5A:4B:C3:A9:A6:CB:49:E0:1A:16:E1:F5
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     19A5C735A79087003D53D6A
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:BF:A7:5C:65:57:07:FD:5A:4B:C3:A9:A6:CB:49:E0:1A:16:E1:F5
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
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E2:BF:A7:5C:65:57:07:FD:5A:4B:C3:A9:A6:CB:49:E0:1A:16:E1:F5
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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   10.860788] iwlwifi 0000:03:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm
[   11.139955] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[   11.140276] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   11.413065] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   26.230752] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   30.276515] wlan0: authenticate with <MAC 'Optimus-Kanguru-C77A73' [AC1]>
[   30.283922] wlan0: send auth to <MAC 'Optimus-Kanguru-C77A73' [AC1]> (try 1/3)
[   30.289629] wlan0: authenticated
[   30.289776] wlan0: AP has invalid WMM params (AIFSN=1 for ACI 0), disabling WMM
[   30.293319] wlan0: associate with <MAC 'Optimus-Kanguru-C77A73' [AC1]> (try 1/3)
[   30.296002] wlan0: RX AssocResp from <MAC 'Optimus-Kanguru-C77A73' [AC1]> (capab=0x411 status=0 aid=2)
[   30.297039] wlan0: associated

########## wireless info END ############

```

---

### Post by Hadaka on 2015-08-22
Hi, please open a terminal ctrl/alt/t then COPY
and paste each command one at a time.
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```
then do...
```
sudo iw reg set PT
sed -i 's/^REG.*=$/&PT/' /etc/default/crda
``` 
thanks

---

### Post by dragan4 on 2015-08-23
Hi Hadaka 

I'm sorry to barge in but it seems that I have a similar problem ... [http://ubuntuforums.org/showthread.php?t=2291448](http://ubuntuforums.org/showthread.php?t=2291448)


if I can do and I like as you write for afonso2 

thanks very much

---

### Post by afonso2 on 2015-08-23
Thank you for the reply, here is the output:

```
afonso@afonso-ubuntu:~$ echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo] password for afonso: 
options iwlwifi 11n_disable=8
afonso@afonso-ubuntu:~$ sudo modprobe -r iwlwifi
modprobe: FATAL: Module iwlwifi is in use.
afonso@afonso-ubuntu:~$ sudo modprobe iwlwifi
afonso@afonso-ubuntu:~$ sudo iw reg set PT
afonso@afonso-ubuntu:~$ sed -i 's/^REG.*=$/&PT/' /etc/default/crda
sed: couldn't open temporary file /etc/default/sedArDT8y: Permission denied
afonso@afonso-ubuntu:~$

```

---

### Post by Hadaka on 2015-08-23
give this a try..
```
sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
```
```
sudo ifconfig wlan0 down
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
sudo ifconfig wlan0 up

```

---

### Post by afonso2 on 2015-08-24
Thanks for the reply. I have entered the commands and the wi-fi stopped working. I had to disconnect and connect again.

```
afonso@afonso-ubuntu:~$ sudo sed -i 's/^REG.*=$/&PT/' /etc/default/crda
[sudo] password for afonso: 
afonso@afonso-ubuntu:~$ sudo ifconfig wlan0 down
afonso@afonso-ubuntu:~$ sudo modprobe -r iwlwifi
modprobe: FATAL: Module iwlwifi is in use.
afonso@afonso-ubuntu:~$ sudo modprobe iwlwifi
afonso@afonso-ubuntu:~$ sudo ifconfig wlan0 up
```

---

