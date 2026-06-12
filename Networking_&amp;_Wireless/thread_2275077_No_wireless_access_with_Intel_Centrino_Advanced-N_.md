---
title: "No wireless access with Intel Centrino Advanced-N 6205 after upgrade to 15.04"
date: 2015-04-24
forum: Networking &amp; Wireless
---

### Post by salvatore-8 on 2015-04-24
```



########## wireless info START ##########


Report from: 24 Apr 2015 11:16 EEST +0300


Booted last: 24 Apr 2015 10:57 EEST +0300


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid


##### kernel ############################


Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 96)
	Subsystem: Intel Corporation Device [8086:c220]
	Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 004 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 5986:0266 Acer, Inc 
Bus 003 Device 003: ID 1004:61f9 LG Electronics, Inc. 
Bus 003 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 0eef:790a D-WAV Scientific Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


4: phy4: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


iwldvm                237568  0 
iwlwifi               196608  1 iwldvm
mac80211              720896  1 iwldvm
cfg80211              540672  3 iwlwifi,mac80211,iwldvm
wmi                    20480  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.43.197  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::863a:4bff:feca:a390/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3342 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:478067 (478.0 KB)  TX bytes:764942 (764.9 KB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"Salva"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Salva' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-29 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:84   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     0      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6205 [Taylor Peak]
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 3.19.0-15-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Salva
GENERAL.CON-UUID:                       1e8f1fbc-dc2d-485d-9d54-b280a311f03a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/13
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1e8f1fbc-dc2d-485d-9d54-b280a311f03a | Salva
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   8e8a80ae-38f3-4eae-9b4d-d07f6e6c5adb | salva_bridge
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.43.197/24, gw = 192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.197
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 6300
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 3600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1429870274
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = x1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 7200
IP6.ADDRESS[1]:                         ip = fe80::863a:4bff:feca:a390/64, gw = ::


SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
NETGEAR97     <MAC 'NETGEAR97' [AC5]>  Infra  6     2437 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2       no        
001601AF2C7C  <MAC '001601AF2C7C' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1       no        
Koti_ED3C     <MAC 'Koti_ED3C' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
Kotiverkko    <MAC 'Kotiverkko' [AC4]>  Infra  2     2417 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
salva_bridge  <MAC 'salva_bridge' [AC6]>  Infra  11    2462 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2       no        
Salva         <MAC 'Salva' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  86      &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 


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


[[/etc/NetworkManager/system-connections/salva 1]] (600 root)
[connection] id=salva 1 | type=802-11-wireless
[802-11-wireless] ssid=salva | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Salva]] (600 root)
[connection] id=Salva | type=802-11-wireless
[802-11-wireless] ssid=Salva | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/salva]] (600 root)
[connection] id=salva | type=802-11-wireless
[802-11-wireless] ssid=salva | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/salva_bridge]] (600 root)
[connection] id=salva_bridge | type=wifi
[wifi] ssid=salva_bridge | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/tanja]] (600 root)
[connection] id=tanja | type=802-11-wireless
[802-11-wireless] ssid=tanja | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Helsinki (based on set time zone)


country FI: DFS-ETSI
	(2402 - 2482 @ 40), (N/A, 20), (N/A)
	(5170 - 5250 @ 40), (N/A, 20), (N/A)
	(5250 - 5330 @ 40), (N/A, 20), (0 ms), DFS
	(5490 - 5710 @ 40), (N/A, 27), (0 ms), DFS
	(57240 - 65880 @ 2160), (N/A, 40), (N/A), NO-OUTDOOR


##### iwlist channels ###################


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Salva' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Salva"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000099407d3c
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '001601AF2C7C' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"001601AF2C7C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006cd8fa5054
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Koti_ED3C' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Koti_ED3C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004c163b19
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Kotiverkko' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"Kotiverkko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003c131b5594e
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'NETGEAR97' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR97"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000050978d95c97
                    Extra: Last beacon: 52ms ago
    lo        Interface doesn't support scanning.


                IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'salva_bridge' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"salva_bridge"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f3eadbc22
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwldvm]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     259D494A97B601F302CD790
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[iwlwifi]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
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


[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwldvm]
force_cam: Y


[iwlwifi]
11n_disable: 8
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
options iwlwifi 11n_disable=8


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x0085 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (asix)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[  778.976810] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[  778.981196] iwlwifi 0000:03:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[  778.989629] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[  778.989634] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[  778.989636] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[  778.989639] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205S AGN, REV=0xB0
[  779.016032] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  779.034221] ieee80211 phy4: Selected rate control algorithm 'iwl-agn-rs'
[  779.052563] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  779.059596] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  779.331028] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[  779.338037] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  782.136142] wlan0: authenticate with <MAC 'Salva' [AC1]>
[  782.138957] wlan0: send auth to <MAC 'Salva' [AC1]> (try 1/3)
[  782.141735] wlan0: authenticated
[  782.143999] wlan0: associate with <MAC 'Salva' [AC1]> (try 1/3)
[  782.147400] wlan0: RX AssocResp from <MAC 'Salva' [AC1]> (capab=0x411 status=0 aid=1)
[  782.149548] wlan0: associated
[  783.766799] wlan0: deauthenticating from <MAC 'Salva' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  786.466452] wlan0: authenticate with <MAC 'salva_bridge' [AC6]>
[  786.468358] wlan0: send auth to <MAC 'salva_bridge' [AC6]> (try 1/3)
[  786.470197] wlan0: authenticated
[  786.473733] wlan0: associate with <MAC 'salva_bridge' [AC6]> (try 1/3)
[  786.476533] wlan0: RX AssocResp from <MAC 'salva_bridge' [AC6]> (capab=0x411 status=0 aid=4)
[  786.478390] wlan0: associated
[  796.471960] wlan0: deauthenticating from <MAC 'salva_bridge' [AC6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  796.474904] wlan0: authenticate with <MAC 'salva_bridge' [AC6]>
[  796.475496] wlan0: send auth to <MAC 'salva_bridge' [AC6]> (try 1/3)
[  796.477311] wlan0: authenticated
[  796.478067] wlan0: associate with <MAC 'salva_bridge' [AC6]> (try 1/3)
[  796.480854] wlan0: RX AssocResp from <MAC 'salva_bridge' [AC6]> (capab=0x411 status=0 aid=4)
[  796.482580] wlan0: associated
[  799.071464] wlan0: deauthenticating from <MAC 'salva_bridge' [AC6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  802.356951] wlan0: authenticate with <MAC 'Salva' [AC1]>
[  802.358119] wlan0: send auth to <MAC 'Salva' [AC1]> (try 1/3)
[  802.359995] wlan0: authenticated
[  802.360188] wlan0: associate with <MAC 'Salva' [AC1]> (try 1/3)
[  802.364758] wlan0: RX AssocResp from <MAC 'Salva' [AC1]> (capab=0x411 status=0 aid=1)
[  802.366546] wlan0: associated


########## wireless info END ############



```

The message in dmesg says:

```

[  796.474904] wlan0: authenticate with 00:90:4c:60:04:02
[  796.475496] wlan0: send auth to 00:90:4c:60:04:02 (try 1/3)
[  796.477311] wlan0: authenticated
[  796.478067] wlan0: associate with 00:90:4c:60:04:02 (try 1/3)
[  796.480238] cfg80211: World regulatory domain updated:
[  796.480242] cfg80211:  DFS Master region: unset
[  796.480243] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  796.480245] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  796.480246] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  796.480248] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  796.480249] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  796.480250] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  796.480266] cfg80211: Calling CRDA for country: FI
[  796.480854] wlan0: RX AssocResp from 00:90:4c:60:04:02 (capab=0x411 status=0 aid=4)
[  796.482580] wlan0: associated
[  796.482948] cfg80211: Regulatory domain changed to country: FI
[  796.482950] cfg80211:  DFS Master region: ETSI
[  796.482951] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  796.482954] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  796.482955] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[  796.482956] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm), (0 s)
[  796.482958] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm), (0 s)
[  796.482959] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[  799.071464] wlan0: deauthenticating from 00:90:4c:60:04:02 by local choice (Reason: 3=DEAUTH_LEAVING)

```

This happens only on my home wifi. If I create a wireless hotspot from my phone, it connects just fine.

---

### Post by prince_niceguy on 2015-04-24
I too face similar issue on the 5Ghz band. Works fine with 2.4Ghz band though. Try using 2.4G instead of 5G.

---

### Post by salvatore-8 on 2015-04-24
Aren't I on 2..4 GHz already?

Extract from the log above:

```
[COLOR=#000000][FONT=Ubuntu Mono]Current Frequency:2.462 GHz (Channel 11)
```[/FONT][/COLOR]

---

### Post by salvatore-8 on 2015-04-24
Uh funny, rebooted the AP and things worked. It's an extraordinary coincidence that this happened exactly as I upgraded Ubuntu!

---

