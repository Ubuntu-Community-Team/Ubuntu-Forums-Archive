---
title: "Can't connect to wifi with Intel 7265AC on Ubuntu 16.04 LST"
date: 2017-02-07
forum: Networking &amp; Wireless
---

### Post by truongcan on 2017-02-07
Frist, I am sory for my english.
I have a problem with wifi on ubuntu 16.04.
My laptop is ASUS model K501UB use Intel Wireless 7265AC card. But it not working on Ubuntu 16.04.
I got these firmware-files from [https://github.com/OpenELEC/iwlwifi-firmware/tree/master/firmware](https://github.com/OpenELEC/iwlwifi-firmware/tree/master/firmware) and copied to /lib/firmware. But it not working.
```
$ ls -al /lib/firmware | grep 7265
-rw-r--r--  1 root root  736844 Th02  7 14:31 iwlwifi-7265-10.ucode
-rw-r--r--  1 root root  880604 Th02  7 14:31 iwlwifi-7265-12.ucode
-rw-r--r--  1 root root  885224 Th02  7 14:31 iwlwifi-7265-13.ucode
-rw-r--r--  1 root root 1180224 Th02  7 14:31 iwlwifi-7265-14.ucode
-rw-r--r--  1 root root 1180356 Th02  7 14:31 iwlwifi-7265-15.ucode
-rw-r--r--  1 root root 1180356 Th02  7 14:31 iwlwifi-7265-16.ucode
-rw-r--r--  1 root root 1180412 Th02  7 14:31 iwlwifi-7265-17.ucode
-rw-r--r--  1 root root  690452 Th02  7 14:31 iwlwifi-7265-8.ucode
-rw-r--r--  1 root root  697828 Th02  7 14:31 iwlwifi-7265-9.ucode
lrwxrwxrwx  1 root root      21 Th10  7 20:15 iwlwifi-7265D-10.ucode -> iwlwifi-7265-10.ucode
-rw-r--r--  1 root root 1002800 Th02  7 14:31 iwlwifi-7265D-12.ucode
-rw-r--r--  1 root root 1008692 Th02  7 14:31 iwlwifi-7265D-13.ucode
-rw-r--r--  1 root root 1384256 Th02  7 14:31 iwlwifi-7265D-14.ucode
-rw-r--r--  1 root root 1384060 Th02  7 14:31 iwlwifi-7265D-15.ucode
-rw-r--r--  1 root root 1384500 Th02  7 14:31 iwlwifi-7265D-16.ucode
-rw-r--r--  1 root root 1383604 Th02  7 14:31 iwlwifi-7265D-17.ucode
-rw-r--r--  1 root root 1375112 Th02  7 14:31 iwlwifi-7265D-18.ucode
-rw-r--r--  1 root root 1387836 Th02  7 14:31 iwlwifi-7265D-19.ucode
-rw-r--r--  1 root root 1388680 Th02  7 14:31 iwlwifi-7265D-20.ucode
-rw-r--r--  1 root root 1385368 Th02  7 14:31 iwlwifi-7265D-21.ucode -rw-r--r--  1 root root 1028316 Th02  7 14:31 iwlwifi-7265D-22.ucode
```


I try rf-kill.


```
$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes     Hard blocked: no
```

Please help me. Thanks you.

---

### Post by Hadaka on 2017-02-07
Hi please open a terminal and do..
```
sudo apt-get install linux-generic-hwe-16.04-edge
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux-firmware_1.161_all.deb

```
Thanks.

---

### Post by truongcan on 2017-02-07
> **Hadaka said:**
> Hi please open a terminal and do..
```
sudo apt-get install linux-generic-hwe-16.04-edge
wget http://mirrors.kernel.org/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.161_all.deb
sudo dpkg -i linux-firmware_1.161_all.deb

```
Thanks.

Thank you but it not working :( I can't turn on wireless :(

---

### Post by Hadaka on 2017-02-07
Hi from a hardwired working connection please do and post...
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
or
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
thanks.

---

### Post by truongcan on 2017-02-07
> **Hadaka said:**
> Hi from a hardwired working connection please do and post...
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
or
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
thanks.

This is my wireless info:

```

########## wireless info START ##########

Report from: 07 Feb 2017 19:05 ICT +0700

Booted last: 07 Feb 2017 00:00 ICT +0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-34-generic #36~16.04.1-Ubuntu SMP Wed Dec 21 18:55:08 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:205f]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095a] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5110]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:57ed Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
iwlmvm                360448  0
mac80211              761856  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              581632  3 iwlmvm,iwlwifi,mac80211
mxm_wmi                16384  1 nouveau
video                  40960  4 asus_wmi,int3406_thermal,nouveau,i915
wmi                    16384  3 asus_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.100.23  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::3d8c:64a2:b6ba:6d86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28787553 (28.7 MB)  TX bytes:3050739 (3.0 MB)

wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.1   0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.100.0   0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       908     1  0 17:37 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a3524d21-1625-335a-ab79-4e38db972c6f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a3524d21-1625-335a-ab79-4e38db972c6f | Wired connection 1
IP4.ADDRESS[1]:                         192.168.100.23/24
IP4.GATEWAY:                            192.168.100.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1486550263
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.100.23
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.100.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.100.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.100.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.100.1
IP6.ADDRESS[1]:                         fe80::3d8c:64a2:b6ba:6d86/64
IP6.GATEWAY:                            fe80::1
IP6.ROUTE[1]:                           dst = fe80::1/128, nh = ::, mt = 100
IP6.DNS[1]:                             fe80::1
DHCP6.OPTION[1]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::1
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:1:0:1:c7:92:bc:99:24:9e:ab:d4:a0:5b
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[6]:                        dhcp6_client_id = 0:4:84:d2:42:cd:24:96:ad:e9:6e:a5:f8:54:7:62:27:9c

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 7265 (Dual Band Wireless-AC 7265)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.8.0-34-generic
GENERAL.FIRMWARE-VERSION:               22.361476.0
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:03:00.0/net/wlp3s0
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
WIFI-PROPERTIES.5GHZ:                   yes
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

Region: Asia/Ho_Chi_Minh (based on set time zone)

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

enp2s0    no frequency information.

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
          Channel 14 : 2.484 GHz
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

##### iwlist scan #######################

wlp3s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.8.0-34-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     8CB024DCE8CBAD06752D324
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.8.0-34-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.8.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C63473656FCDBBDA56E12DA
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-34-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.8.0-34-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
srcversion:     E7651FD3D9AF45F96CD8B2E
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-34-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.8.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-34-generic SMP mod_unload modversions 
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

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    9.217485] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[    9.368099] iwlwifi 0000:03:00.0: loaded firmware version 22.361476.0 op_mode iwlmvm
[    9.410160] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    9.743787] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[    9.745845] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    9.860540] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   11.041297] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[   11.157302] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   28.521837] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   28.525101] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.569255] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   28.569359] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   30.153178] r8169 0000:02:00.0 enp2s0: link up
[   30.153188] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############


```
Thanks

---

### Post by chili555 on 2017-02-07
> Hard blocked: yesIs the switch or key combination set to enable wireless? Is the key combination not working as expected?

You may need to try this: [http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v/351860#351860](http://askubuntu.com/questions/351594/wireless-disabled-by-hardware-switch-on-an-asus-x550v/351860#351860)

---

