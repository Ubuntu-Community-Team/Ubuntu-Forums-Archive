---
title: "Intel AC 7265 soft blocked, no wifi, Ubuntu 16.10"
date: 2016-12-10
forum: Networking &amp; Wireless
---

### Post by bibacula on 2016-12-10
I just bought two new HP 17 laptops, and I've loaded Ubuntu 16.10. Knowing that Intel offers good linux support, I substituted Intel AC 7265 wifi cards for the built-in Realtek RTL8188EE cards. Unfortunately, wifi has never worked consistently.

I've loaded the latest drivers as follows:
```
sudo apt-get update
sudo apt-get install git
git clone https://github.com/OpenELEC/iwlwifi-firmware.git
cd iwlwifi-firmware/firmware
sudo cp iwlwifi-7265*  /lib/firmware
```

I've also confirmed that the updated drivers are in /lib/firmware.

I ran the wireless info script. Here is the output:
```

########## wireless info START ##########

Report from: 10 Dec 2016 09:36 MST -0700

Booted last: 10 Dec 2016 00:00 MST -0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

##### kernel ############################

Linux 4.8.0-30-generic #32-Ubuntu SMP Fri Dec 2 03:43:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/user/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:81ff]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 2b)
    Subsystem: Intel Corporation Wireless-N 7265 [8086:5002]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
acer_wmi               20480  0
iwlmvm                360448  0
mac80211              757760  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              581632  3 iwlmvm,iwlwifi,mac80211
sparse_keymap          16384  4 intel_hid,acer_wmi,intel_vbtn,hp_wmi
wmi                    16384  2 acer_wmi,hp_wmi
video                  40960  2 acer_wmi,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fdc5:6f31:147c:0:cc25:a7a4:fe4d:214  prefixlen 64  scopeid 0x0<global>
        inet6 fd03:2f13:1988:0:cc25:a7a4:fe4d:214  prefixlen 64  scopeid 0x0<global>
        inet6 fde2:6121:6044:4:cc25:a7a4:fe4d:214  prefixlen 64  scopeid 0x0<global>
        inet6 fe80::3c9d:1ca6:ef94:8f11  prefixlen 64  scopeid 0x20<link>
        inet6 fde2:6121:6044:4::50a  prefixlen 128  scopeid 0x0<global>
        inet6 fdc5:6f31:147c:0:d135:60e5:296a:a976  prefixlen 64  scopeid 0x0<global>
        inet6 fd03:2f13:1988:0:777a:fbb2:f7d3:5668  prefixlen 64  scopeid 0x0<global>
        inet6 fde2:6121:6044:4:2949:c0aa:7f0f:58e9  prefixlen 64  scopeid 0x0<global>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 308205  bytes 23998530 (23.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 389458  bytes 585097808 (585.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 14849  bytes 934803 (934.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14849  bytes 934803 (934.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4098<BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

enp1s0    no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 enp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 enp1s0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       706     1  0 09:25 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/enp1s0
GENERAL.IP-IFACE:                       enp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       297819e9-6c1d-3a0d-914a-ee25fa5008a1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   297819e9-6c1d-3a0d-914a-ee25fa5008a1 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.103/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.103
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1481430363
DHCP4.OPTION[21]:                       host_name = HP1
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fde2:6121:6044:4::50a/128
IP6.ADDRESS[2]:                         fd03:2f13:1988:0:cc25:a7a4:fe4d:214/64
IP6.ADDRESS[3]:                         fdc5:6f31:147c:0:cc25:a7a4:fe4d:214/64
IP6.ADDRESS[4]:                         fde2:6121:6044:4:cc25:a7a4:fe4d:214/64
IP6.ADDRESS[5]:                         fd03:2f13:1988:0:777a:fbb2:f7d3:5668/64
IP6.ADDRESS[6]:                         fdc5:6f31:147c:0:d135:60e5:296a:a976/64
IP6.ADDRESS[7]:                         fde2:6121:6044:4:2949:c0aa:7f0f:58e9/64
IP6.ADDRESS[8]:                         fe80::3c9d:1ca6:ef94:8f11/64
IP6.GATEWAY:                            
IP6.ROUTE[1]:                           dst = fde2:6121:6044:4::/62, nh = fe80::1691:82ff:fe2c:b40d, mt = 100
IP6.ROUTE[2]:                           dst = fdc5:6f31:147c::/48, nh = fe80::1691:82ff:fe2c:b40d, mt = 100
IP6.ROUTE[3]:                           dst = fd03:2f13:1988::/48, nh = fe80::1691:82ff:fe35:cbc1, mt = 100
IP6.DNS[1]:                             fe80::1691:82ff:fe35:cbc1
IP6.DNS[2]:                             fe80::1691:82ff:fe2c:b40d
IP6.DOMAIN[1]:                          lan
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:ca:4:8b:f:a2:75:89:51:22:50:ad:da:19:b6:5e:c2
DHCP6.OPTION[2]:                        dhcp6_unknown_11 = 3:1:0:58:4c:2c:9e:0:0:0:34:1:1e:7a:47:5b:f1:c6:cf:fc:9f:79:e8:18:f9:ab:cd:e9
DHCP6.OPTION[3]:                        dhcp6_name_servers = fe80::1691:82ff:fe2c:b40d
DHCP6.OPTION[4]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[5]:                        rebind = 34560
DHCP6.OPTION[6]:                        max_life = 4294967295
DHCP6.OPTION[7]:                        preferred_life = 4294967295
DHCP6.OPTION[8]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[9]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[10]:                       life_starts = 1481387166
DHCP6.OPTION[11]:                       ip6_address = fde2:6121:6044:4::50a
DHCP6.OPTION[12]:                       ip6_prefixlen = 64
DHCP6.OPTION[13]:                       dhcp6_domain_search = lan.
DHCP6.OPTION[14]:                       dhcp6_solmax_rt = 60
DHCP6.OPTION[15]:                       renew = 21600
DHCP6.OPTION[16]:                       starts = 1481387166
DHCP6.OPTION[17]:                       iaid = 71:23:9b:10
DHCP6.OPTION[18]:                       dhcp6_server_id = 0:3:0:1:14:91:82:2c:b4:d

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Wireless-N 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.8.0-30-generic
GENERAL.FIRMWARE-VERSION:               17.352738.0
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

##### iw reg get ########################

Region: America/Denver (based on set time zone)

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

enp1s0    no frequency information.

lo        no frequency information.

wlp2s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp2s0    Interface doesn't support scanning : Network is down

enp1s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     1381C923B4D543F234722C8
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-IWL6000G2B_UCODE_API_MAX.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-24.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-24.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-24.ucode
firmware:       iwlwifi-8000C--24.ucode
firmware:       iwlwifi-9260-th-a0-lc-a0--24.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--24.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--24.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--24.ucode
srcversion:     2CEF28FC677968755470332
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
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
11n_disable: 8
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    2.645310] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.2.27.d.bseq
[    2.676690] iwlwifi 0000:02:00.0: Unsupported splx structure
[    2.683545] iwlwifi 0000:02:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    2.758019] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7265, REV=0x184
[    2.760749] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    2.844718] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.852897] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    2.917028] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.253945] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   14.092627] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   14.184957] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)

########## wireless info END ############

```

It looks likes the wifi is soft-blocked, but I don't know what that means. Based on other forum articles, I ran the following:
```
user@HP1:~/Downloads$ rfkill unblock all
user@HP1:~/Downloads$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

Wifi is still blocked, I think. Anyone able to help?

---

### Post by wildmanne39 on 2016-12-10
To fix the softblock please do:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by bibacula on 2016-12-10
Thank you, wildmanne39!

After adding "blacklist acer-wmi" to blacklist.conf, the softblocks are removed, and I'm now surfing wirelessly. I did see this command on other forum threads, but I mistakenly thought it was specific to Acer computers.

Awesome work! You have done your good deed for the day!

---

### Post by wildmanne39 on 2016-12-10
Some computers that are not acer have that module loaded also, I do not know why but it they do and their is a softblock that is the issue.

Your welcome and enjoy!:)

---

