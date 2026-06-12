---
title: "Ubuntu 16.04 LTS wifi connected but only 1mb/s max"
date: 2016-12-31
forum: Networking &amp; Wireless
---

### Post by droidude on 2016-12-31
Hey Guys,

Like stated above I cannot get a usable internet connection.

This is the ouput when I ran ```
rfkill list all
```:

```

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

This is the output when I ran ```
iwconfig

```:

```
wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
lo        no wireless extensions.

enp0s25   no wireless extensions.
```

I hope this can help you so you can help me. I think my problem occurred after I played a bit with a virtualbox.

Appreciate your help,
droidude

---

### Post by praseodym on 2016-12-31
For the first step, please try
```

sudo iwconfig wlp3s0 power off
```
2nd step: please run the wireless scipt from the sticky thread and show the outputs.

---

### Post by kurt18947 on 2016-12-31
Does your connection **feel** like it's 1 mb/sec? In other words, pretty slow? If not, it might be worth running a speed checker to see what your connection's real rate is. Numbers from something like iwconfig may or may not be accurate.

---

### Post by droidude on 2017-01-01
So I ran the script with these results:

```

########## wireless info START ##########

Report from: 01 Jan 2017 16:08 CET +0100

Booted last: 01 Jan 2017 00:00 CET +0100

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

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
    Subsystem: Lenovo Ethernet Connection (3) I218-V [17aa:2227]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5210]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04ca:703c Lite-On Technology Corp. 
Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                311296  0
mac80211              737280  1 iwlmvm
iwlwifi               200704  1 iwlmvm
cfg80211              565248  3 iwlwifi,mac80211,iwlmvm
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:192.168.178.36  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::2089:6ba2:1169:62c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25395 errors:0 dropped:9 overruns:0 frame:0
          TX packets:17402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26542208 (26.5 MB)  TX bytes:2775423 (2.7 MB)
          Interrupt:20 Memory:f2200000-f2220000 

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.178.64  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::c626:a5ca:72d2:dfc5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2705610 (2.7 MB)  TX bytes:850994 (850.9 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s25   no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG    100    0        0 enp0s25
0.0.0.0         192.168.178.1   0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.178.0   0.0.0.0         255.255.255.0   U     100    0        0 enp0s25
192.168.178.0   0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 127.0.1.1
search fritz.box

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1010     1  0  2016 ?        00:00:28 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (3) I218-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       2b2e4a9d-8e72-410c-9215-b1f7d9b1cc6c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2b2e4a9d-8e72-410c-9215-b1f7d9b1cc6c | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.178.36/24
IP4.GATEWAY:                            192.168.178.1
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.36
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1484147190
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::2089:6ba2:1169:62c/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.4.0-57-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     FRITZ!Box 6360 Cable
GENERAL.CON-UUID:                       d827db03-22a5-4ee1-aa14-9701e1daf651
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
GENERAL.METERED:                        no (guessed)
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
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d827db03-22a5-4ee1-aa14-9701e1daf651 | FRITZ!Box 6360 Cable
IP4.ADDRESS[1]:                         192.168.178.64/24
IP4.GATEWAY:                            192.168.178.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.178.1
IP4.DOMAIN[1]:                          fritz.box
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.178.1
DHCP4.OPTION[5]:                        ip_address = 192.168.178.64
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.178.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.178.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 756000
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.178.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 432000
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = fritz.box
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1484147075
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.178.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.178.1
DHCP4.OPTION[28]:                       ntp_servers = 192.168.178.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 864000
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::c626:a5ca:72d2:dfc5/64
IP6.GATEWAY:                            

SSID                  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
FRITZ!Box 6360 Cable  <MAC 'FRITZ!Box 6360 Cable' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
o2-WLAN36             <MAC 'o2-WLAN36' [AN2]>  Infra  13    2472 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       no        
HITRON-2DB0           <MAC 'HITRON-2DB0' [AN3]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 WPA2  no        
WLAN-8B9981           <MAC 'WLAN-8B9981' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA2       no        
FRITZ!Box 7490        <MAC 'FRITZ!Box 7490' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
o2-WLAN36             <MAC 'o2-WLAN36' [AN6]>  Infra  36    5180 MHz  54 Mbit/s  19      &#9602;___  WPA2       no        
FRITZ!Box 7362 SL     <MAC 'FRITZ!Box 7362 SL' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  14      &#9602;___  WPA2       no        
FRITZ!Box 7490        <MAC 'FRITZ!Box 7490' [AN8]>  Infra  6     2437 MHz  54 Mbit/s  10      &#9602;___  WPA2       no        

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

[[/etc/NetworkManager/system-connections/FRITZ!Box 6360 Cable]] (600 root)
[connection] id=FRITZ!Box 6360 Cable | type=wifi | permissions=user:duc:;
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=FRITZ!Box 6360 Cable
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s25   no frequency information.

wlp3s0    32 channels in total; available frequencies :
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

wlp3s0    Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

enp0s25   Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     60ED6558F1225672289299A
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.4.0-57-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0B114888238BEBBE8043BC5
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.4.0-57-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     4116E844336D79483D28F6F
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-57-generic SMP mod_unload modversions 
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

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

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

[ 3597.912981] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3597.913924] wlp3s0: associated
[ 3598.205093] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3598.205107] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3601.457870] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3601.463329] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3601.466229] wlp3s0: authenticated
[ 3601.468706] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3601.474892] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3601.475807] wlp3s0: associated
[ 3601.770297] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3601.770330] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3602.520953] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3602.525679] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3602.528503] wlp3s0: authenticated
[ 3602.532675] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3602.538879] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3602.540201] wlp3s0: associated
[ 3602.832711] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3602.832755] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3603.689554] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3603.694331] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3603.708104] wlp3s0: authenticated
[ 3603.708647] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3603.715578] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3603.716522] wlp3s0: associated
[ 3604.001225] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3604.001237] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3605.292645] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3605.297682] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3605.300473] wlp3s0: authenticated
[ 3605.300640] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3605.306860] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3605.308168] wlp3s0: associated
[ 3605.604708] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3605.604723] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3608.874828] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3608.879837] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3608.882597] wlp3s0: authenticated
[ 3608.884619] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3608.891624] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3608.892761] wlp3s0: associated
[ 3609.186815] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3609.186831] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3609.927865] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3609.932751] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3609.935624] wlp3s0: authenticated
[ 3609.936616] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3609.943523] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3609.944382] wlp3s0: associated
[ 3610.239635] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3610.239651] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3610.989357] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3610.993567] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3610.996478] wlp3s0: authenticated
[ 3611.000605] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3611.007497] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3611.008802] wlp3s0: associated
[ 3611.300602] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3611.300646] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3614.556948] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3614.561995] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3614.564781] wlp3s0: authenticated
[ 3614.568616] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3614.574865] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3614.576180] wlp3s0: associated
[ 3614.869019] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3614.869062] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3615.609649] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3615.614788] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3615.631604] wlp3s0: authenticated
[ 3615.632604] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3615.638797] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3615.640469] wlp3s0: associated
[ 3615.921495] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3615.921510] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3616.772713] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3616.777199] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3616.810573] wlp3s0: authenticated
[ 3616.812623] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3616.818886] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3616.820265] wlp3s0: associated
[ 3617.084183] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3617.084198] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3617.822944] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3617.827779] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3617.830657] wlp3s0: authenticated
[ 3617.832644] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3617.838914] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3617.840193] wlp3s0: associated
[ 3618.134806] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3618.134848] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost
[ 3618.877959] wlp3s0: authenticate with <MAC 'FRITZ!Box 6360 Cable' [AN1]>
[ 3618.882644] wlp3s0: send auth to <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3618.891352] wlp3s0: authenticated
[ 3618.892642] wlp3s0: associate with <MAC 'FRITZ!Box 6360 Cable' [AN1]> (try 1/3)
[ 3618.899411] wlp3s0: RX AssocResp from <MAC 'FRITZ!Box 6360 Cable' [AN1]> (capab=0x431 status=0 aid=5)
[ 3618.900260] wlp3s0: associated
[ 3619.189584] iwlwifi 0000:03:00.0: No association and the time event is over already...
[ 3619.189610] wlp3s0: Connection to AP <MAC 'FRITZ!Box 6360 Cable' [AN1]> lost

########## wireless info END ############


```

My internet connection is really slow like i stated before 1mb/s at max. It is not really useable as websites don't load or hardly do. I have dualboot on my machine, on windows my wifi is very fast.

---

### Post by praseodym on 2017-01-01
Lets check

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi-wd.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by droidude on 2017-01-01
Unfortunately, nothing changed

Edit: I tried your commands again, and this time it worked. Let's see how it goes for the next few days. Appreciate your help, thanks so much!

PS.: What does the commands actually do, I try to understand and what went wrong in my setup?

Update: The problem reappeared. The commands dont work anymore. Can you help me out?

Greets, Droidude

---

### Post by droidude on 2017-01-07
Sorry for the push, I really need your help.

---

