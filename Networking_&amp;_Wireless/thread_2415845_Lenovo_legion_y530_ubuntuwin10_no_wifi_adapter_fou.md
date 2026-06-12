---
title: "Lenovo legion y530 ubuntu/win10 no wifi adapter found"
date: 2019-04-01
forum: Networking &amp; Wireless
---

### Post by festyn on 2019-04-01
Hello,

I have installed ubuntu 18.04 to my preinstalled windows 10. Everything is fine on windows, but when I change to Ubuntu I cant reach internet (no wifi adapter found). 

Tried commands from some of the topics like: 
[https://ubuntuforums.org/showthread.php?t=2415678](https://ubuntuforums.org/showthread.php?t=2415678)

Below report which I get from your main post:

Thx for every help :)

```
 
########## wireless info START ##########
 
Report from: 01 Apr 2019 20:40 CEST +0200
 
Booted last: 01 Apr 2019 00:00 CEST +0200
 
Script from: 22 Oct 2018 03:34 UTC +0000
 
##### release ###########################
 
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:   bionic
 
##### kernel ############################
 
Linux 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
 
Parameters: ro, quiet, splash, vt.handoff=1
 
##### desktop ###########################
 
Ubuntu
 
##### lspci #############################
 
07:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:3166] (rev 99)
    Subsystem: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:4210]
    Kernel driver in use: iwlwifi
 
08:00.0 Ethernet controller [0200]: Realtek  Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet  Controller [10ec:8168] (rev 15)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:38c2]
    Kernel driver in use: r8169
 
##### lsusb #############################
 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04ca:7070 Lite-On Technology Corp. 
Bus 001 Device 003: ID 145f:01d9 Trust 
Bus 001 Device 008: ID 04e8:6864 Samsung Electronics Co., Ltd GT-I9070 (network tethering, USB debugging enabled)
Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
##### PCMCIA card info ##################
 
##### rfkill ############################
 
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
 
##### secure boot #######################
 
SecureBoot disabled
 
##### lsmod #############################
 
intel_wmi_thunderbolt    16384  0
wmi_bmof               16384  0
iwlmvm                376832  0
mac80211              802816  1 iwlmvm
iwlwifi               299008  1 iwlmvm
mxm_wmi                16384  1 nouveau
cfg80211              667648  3 iwlmvm,iwlwifi,mac80211
ideapad_laptop         32768  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    24576  5 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop,mxm_wmi,nouveau
video                  45056  3 ideapad_laptop,i915,nouveau
 
##### interfaces ########################
 
[/etc/network/interfaces]
auto lo
iface lo inet loopback
 
##### ifconfig ##########################
 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
4: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>
5: enp0s20f0u2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20f0u2' [IF3]> brd <MAC address>
    inet 192.168.42.199/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20f0u2
       valid_lft 3288sec preferred_lft 3288sec
    inet6 fe80::aac4:aa19:35fd:fc00/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
 
##### iwconfig ##########################
 
lo        no wireless extensions.
 
enp0s20f0u2  no wireless extensions.
 
enp8s0    no wireless extensions.
 
wlp7s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
 
##### route #############################
 
default via 192.168.42.129 dev enp0s20f0u2 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20f0u2 scope link metric 1000 
192.168.42.0/24 dev enp0s20f0u2 proto kernel scope link src 192.168.42.199 metric 100 
 
##### resolv.conf #######################
 
[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']
 
nameserver 127.0.0.53
options edns0
 
##### network managers ##################
 
Installed:
 
    NetworkManager
 
Running:
 
root       948     1  0 20:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
 
##### NetworkManager info ###############
 
GENERAL.DEVICE:                         enp0s20f0u2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u2' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enp0s20f0u2
GENERAL.IP-IFACE:                       enp0s20f0u2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       93801bf1-4d63-3b76-b4be-d9a8a01e217c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.199/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.199
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
DHCP4.OPTION[19]:                       expiry = 1554147294
DHCP4.OPTION[20]:                       host_name = patryk-Lenovo-Legion-Y530-15ICH-1060
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_host_name = 1
IP6.ADDRESS[1]:                         fe80::aac4:aa19:35fd:fc00/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   93801bf1-4d63-3b76-b4be-d9a8a01e217c | Wired connection 1
 
GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.5/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
 
GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Dual Band Wireless-AC 3165 Plus Bluetooth
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.18.0-16-generic
GENERAL.FIRMWARE-VERSION:               29.1044073957.0
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.4/0000:07:00.0/net/wlp7s0
GENERAL.IP-IFACE:                       --
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
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
 
SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
 
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
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no
 
[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved
 
[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:wwan
 
[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/
 
[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve
 
##### NetworkManager profiles ###########
 
##### Netplan config ####################
 
[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager
 
##### iw reg get ########################
 
Region: Europe/Warsaw (based on set time zone)
 
global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
 
##### iwlist channels ###################
 
lo        no frequency information.
 
enp0s20f0u2  no frequency information.
 
enp8s0    no frequency information.
 
wlp7s0    32 channels in total; available frequencies :
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
 
lo        Interface doesn't support scanning.
 
enp0s20f0u2  Interface doesn't support scanning.
 
enp8s0    Interface doesn't support scanning.
 
wlp7s0    Interface doesn't support scanning : Network is down
 
##### module infos ######################
 
[iwlmvm]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4DAD4F3B58FCA15965D5AC4
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)
 
[mac80211]
filename:       /lib/modules/4.18.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
 
[iwlwifi]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-38.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-38.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-38.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-38.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-38.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-38.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-38.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-38.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-38.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-38.ucode
srcversion:     1F6BE15A46F5E4E4DE83078
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality,  bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX  (uint)
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
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
 
[cfg80211]
filename:       /lib/modules/4.18.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-16-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3
 
[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00
 
##### /etc/modules ######################
 
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
 
[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
 
##### rc.local ##########################
 
grep: /etc/rc.local: No such file or directory
 
##### pm-utils ##########################
 
##### udev rules ########################
 
##### dmesg #############################
 
[    6.101630] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2: link is not ready
[    6.115570] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[    6.182642] r8169 0000:08:00.0 enp8s0: link down
[    6.182821] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[    6.193470] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   40.902478] rndis_host 1-2:1.0 enp0s20f0u2: unregister 'rndis_host' usb-0000:00:14.0-2, RNDIS device
[   44.825332] rndis_host 1-2:1.0 enp0s20f0u2: renamed from usb0
[   44.866995] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2: link is not ready
 
########## wireless info END ############


```

---

### Post by praseodym on 2019-04-01
The card is turned off. Any button, switch, key or key combo?

---

### Post by festyn on 2019-04-01
Hmm I have turned on WiFi in Settings. Ofc it didnt help, but maybe you  can check if something changed. If no, then I will look for some mystery  buttons :)

 

 ```
########## wireless info START ##########

  

 Report from: 01 Apr 2019 21:18 CEST +0200
  
 Booted last: 01 Apr 2019 00:00 CEST +0200
  
 Script from: 22 Oct 2018 03:34 UTC +0000
  
 ##### release ###########################
  
 Distributor ID: Ubuntu
 Description:    Ubuntu 18.04.2 LTS
 Release:    18.04
 Codename:   bionic
  
 ##### kernel ############################
  
 Linux 4.18.0-16-generic #17~18.04.1-Ubuntu SMP Tue Feb 12 13:35:51 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
  
 Parameters: ro, quiet, splash, vt.handoff=1
  
 ##### desktop ###########################
  
 Ubuntu
  
 ##### lspci #############################
  
 07:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:3166] (rev 99)
     Subsystem: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:4210]
     Kernel driver in use: iwlwifi

  
 08:00.0 Ethernet controller [0200]: Realtek  Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet  Controller [10ec:8168] (rev 15)
     Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:38c2]

     Kernel driver in use: r8169
  
 ##### lsusb #############################
  

 Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
 Bus 001 Device 004: ID 04ca:7070 Lite-On Technology Corp. 

 Bus 001 Device 003: ID 145f:01d9 Trust 
 Bus 001 Device 008: ID 04e8:6864 Samsung Electronics Co., Ltd GT-I9070 (network tethering, USB debugging enabled)
 Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
 ##### PCMCIA card info ##################
  
 ##### rfkill ############################
  
 0: ideapad_wlan: Wireless LAN
     Soft blocked: no
     Hard blocked: yes
 1: ideapad_bluetooth: Bluetooth
     Soft blocked: yes
     Hard blocked: yes
 2: hci0: Bluetooth
     Soft blocked: yes
     Hard blocked: no
 3: phy0: Wireless LAN
     Soft blocked: no
     Hard blocked: no
  
 ##### secure boot #######################
  
 SecureBoot disabled
  
 ##### lsmod #############################
  
 intel_wmi_thunderbolt    16384  0
 wmi_bmof               16384  0
 iwlmvm                376832  0
 mac80211              802816  1 iwlmvm
 iwlwifi               299008  1 iwlmvm
 mxm_wmi                16384  1 nouveau
 cfg80211              667648  3 iwlmvm,iwlwifi,mac80211
 ideapad_laptop         32768  0
 sparse_keymap          16384  1 ideapad_laptop
 wmi                    24576  5 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop,mxm_wmi,nouveau
 video                  45056  3 ideapad_laptop,i915,nouveau
  

 ##### interfaces ########################

  
 [/etc/network/interfaces]
 auto lo
 iface lo inet loopback
  
 ##### ifconfig ##########################

  

 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
     link/loopback <MAC address> brd <MAC address>
     inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
     inet6 ::1/128 scope host 
        valid_lft forever preferred_lft forever
 2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
     link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
 4: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
     link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>
 5: enp0s20f0u2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
     link/ether <MAC 'enp0s20f0u2' [IF3]> brd <MAC address>
     inet 192.168.42.199/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20f0u2
        valid_lft 3399sec preferred_lft 3399sec
     inet6 fe80::aac4:aa19:35fd:fc00/64 scope link noprefixroute 
        valid_lft forever preferred_lft forever
  
 ##### iwconfig ##########################
  
 lo        no wireless extensions.
  
 enp0s20f0u2  no wireless extensions.
  
 enp8s0    no wireless extensions.
  
 wlp7s0    IEEE 802.11  ESSID:off/any  
           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
           Retry short limit:7   RTS thr:off   Fragment thr:off
           Power Management:on
           
  
 ##### route #############################
  
 default via 192.168.42.129 dev enp0s20f0u2 proto dhcp metric 100 
 169.254.0.0/16 dev enp0s20f0u2 scope link metric 1000 
 192.168.42.0/24 dev enp0s20f0u2 proto kernel scope link src 192.168.42.199 metric 100 
  
 ##### resolv.conf #######################

  
 [777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']
  
 nameserver 127.0.0.53
 options edns0

  
 ##### network managers ##################

  
 Installed:
  
     NetworkManager
  

 Running:
  
 root       948     1  0 20:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon
  
 ##### NetworkManager info ###############
  
 GENERAL.DEVICE:                         enp0s20f0u2
 GENERAL.TYPE:                           ethernet
 GENERAL.NM-TYPE:                        NMDeviceEthernet
 GENERAL.VENDOR:                         SAMSUNG
 GENERAL.PRODUCT:                        SAMSUNG_Android
 GENERAL.DRIVER:                         rndis_host
 GENERAL.DRIVER-VERSION:                 22-Aug-2005
 GENERAL.FIRMWARE-VERSION:               RNDIS device
 GENERAL.HWADDR:                         <MAC 'enp0s20f0u2' [IF3]>
 GENERAL.MTU:                            1500
 GENERAL.STATE:                          100 (connected)
 GENERAL.REASON:                         0 (No reason given)
 GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enp0s20f0u2
 GENERAL.IP-IFACE:                       enp0s20f0u2
 GENERAL.IS-SOFTWARE:                    no
 GENERAL.NM-MANAGED:                     yes
 GENERAL.AUTOCONNECT:                    yes
 GENERAL.FIRMWARE-MISSING:               no
 GENERAL.NM-PLUGIN-MISSING:              no
 GENERAL.PHYS-PORT-ID:                   --
 GENERAL.CONNECTION:                     Wired connection 1
 GENERAL.CON-UUID:                       93801bf1-4d63-3b76-b4be-d9a8a01e217c
 GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/3
 GENERAL.METERED:                        yes (guessed)
 CAPABILITIES.CARRIER-DETECT:            yes
 CAPABILITIES.SPEED:                     unknown
 CAPABILITIES.IS-SOFTWARE:               no
 CAPABILITIES.SRIOV:                     no

 WIRED-PROPERTIES.CARRIER:               on
 IP4.ADDRESS[1]:                         192.168.42.199/24
 IP4.GATEWAY:                            192.168.42.129
 IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
 IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
 IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
 IP4.DNS[1]:                             192.168.42.129

 DHCP4.OPTION[1]:                        requested_subnet_mask = 1
 DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1

 DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
 DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
 DHCP4.OPTION[5]:                        ip_address = 192.168.42.199
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
 DHCP4.OPTION[19]:                       expiry = 1554149708
 DHCP4.OPTION[20]:                       host_name = patryk-Lenovo-Legion-Y530-15ICH-1060
 DHCP4.OPTION[21]:                       requested_netbios_scope = 1
 DHCP4.OPTION[22]:                       requested_wpad = 1
 DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
 DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
 DHCP4.OPTION[25]:                       network_number = 192.168.42.0
 DHCP4.OPTION[26]:                       requested_domain_search = 1
 DHCP4.OPTION[27]:                       next_server = 192.168.42.129
 DHCP4.OPTION[28]:                       requested_ntp_servers = 1
 DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
 DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
 DHCP4.OPTION[31]:                       requested_host_name = 1
 IP6.ADDRESS[1]:                         fe80::aac4:aa19:35fd:fc00/64
 IP6.GATEWAY:                            --
 IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
 IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
 IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
 CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
 CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   93801bf1-4d63-3b76-b4be-d9a8a01e217c | Wired connection 1
  
 GENERAL.DEVICE:                         enp8s0

 GENERAL.TYPE:                           ethernet
 GENERAL.NM-TYPE:                        NMDeviceEthernet
 GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
 GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
 GENERAL.DRIVER:                         r8169
 GENERAL.DRIVER-VERSION:                 2.3LK-NAPI

 GENERAL.FIRMWARE-VERSION:               --
 GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
 GENERAL.MTU:                            1500
 GENERAL.STATE:                          20 (unavailable)
 GENERAL.REASON:                         2 (Device is now managed)
 GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.5/0000:08:00.0/net/enp8s0

 GENERAL.IP-IFACE:                       --
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
 CAPABILITIES.SRIOV:                     no
 WIRED-PROPERTIES.CARRIER:               off
 CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
  
 GENERAL.DEVICE:                         wlp7s0
 GENERAL.TYPE:                           wifi
 GENERAL.NM-TYPE:                        NMDeviceWifi
 GENERAL.VENDOR:                         Intel Corporation
 GENERAL.PRODUCT:                        Dual Band Wireless-AC 3165 Plus Bluetooth
 GENERAL.DRIVER:                         iwlwifi
 GENERAL.DRIVER-VERSION:                 4.18.0-16-generic
 GENERAL.FIRMWARE-VERSION:               29.1044073957.0
 GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
 GENERAL.MTU:                            1500
 GENERAL.STATE:                          20 (unavailable)
 GENERAL.REASON:                         2 (Device is now managed)
 GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.4/0000:07:00.0/net/wlp7s0
 GENERAL.IP-IFACE:                       --
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
 CAPABILITIES.SRIOV:                     no
 WIFI-PROPERTIES.WEP:                    yes
 WIFI-PROPERTIES.WPA:                    yes
 WIFI-PROPERTIES.WPA2:                   yes
 WIFI-PROPERTIES.TKIP:                   yes

 WIFI-PROPERTIES.CCMP:                   yes
 WIFI-PROPERTIES.AP:                     yes
 WIFI-PROPERTIES.ADHOC:                  yes
 WIFI-PROPERTIES.2GHZ:                   yes
 WIFI-PROPERTIES.5GHZ:                   yes
 CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --
  

 SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
  
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
 plugins=ifupdown,keyfile
 [ifupdown]
 managed=false
 [device]
 wifi.scan-rand-mac-address=no
  

 [[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
 [main]
 dns=systemd-resolved
  
 [[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
 [keyfile]
 unmanaged-devices=*,except:type:wifi,except:type:wwan

  
 [[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
 [connectivity]
 uri=http://connectivity-check.ubuntu.com/
  
 [[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
 [device-mac-addr-change-wifi]
 match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
 wifi.scan-rand-mac-address=no
 wifi.cloned-mac-address=preserve
 ethernet.cloned-mac-address=preserve
  
 ##### NetworkManager profiles ###########

  
 ##### Netplan config ####################
  
 [/etc/netplan/01-network-manager-all.yaml]
 network:
   version: 2
   renderer: NetworkManager

  
 ##### iw reg get ########################
  
 Region: Europe/Warsaw (based on set time zone)
  
 global
 country 00: DFS-UNSET
     (2402 - 2472 @ 40), (N/A, 20), (N/A)
     (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
     (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
     (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
     (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
     (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
     (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
     (57240 - 63720 @ 2160), (N/A, 0), (N/A)
  
 ##### iwlist channels ###################
  
 lo        no frequency information.

  
 enp0s20f0u2  no frequency information.
  
 enp8s0    no frequency information.
  
 wlp7s0    32 channels in total; available frequencies :
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
  
 lo        Interface doesn't support scanning.
  
 enp0s20f0u2  Interface doesn't support scanning.
  
 enp8s0    Interface doesn't support scanning.

  
 wlp7s0    Interface doesn't support scanning : Network is down
  
 ##### module infos ######################
  
 [iwlmvm]
 filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko

 license:        GPL
 author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
 description:    The new Intel(R) wireless AGN driver for Linux
 srcversion:     4DAD4F3B58FCA15965D5AC4
 depends:        iwlwifi,mac80211,cfg80211
 retpoline:      Y
 intree:         Y
 name:           iwlmvm
 vermagic:       4.18.0-16-generic SMP mod_unload 
 signat:         PKCS#7
 signer:         
 sig_key:        
 sig_hashalgo:   md4
 parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
 parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
 parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)
  
 [mac80211]
 filename:       /lib/modules/4.18.0-16-generic/kernel/net/mac80211/mac80211.ko
 license:        GPL
 description:    IEEE 802.11 subsystem

 srcversion:     C5D73328CD704BB6E363074
 depends:        cfg80211
 retpoline:      Y
 intree:         Y
 name:           mac80211
 vermagic:       4.18.0-16-generic SMP mod_unload 
 signat:         PKCS#7

 signer:         
 sig_key:        
 sig_hashalgo:   md4
 parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
 parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
 parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
 parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
 parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
 parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
  
 [iwlwifi]
 filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko

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
 firmware:       iwlwifi-6000g2b-6.ucode
 firmware:       iwlwifi-6000g2a-6.ucode
 firmware:       iwlwifi-6050-5.ucode
 firmware:       iwlwifi-6000-6.ucode
 firmware:       iwlwifi-7265D-29.ucode
 firmware:       iwlwifi-7265-17.ucode
 firmware:       iwlwifi-3168-29.ucode
 firmware:       iwlwifi-3160-17.ucode
 firmware:       iwlwifi-7260-17.ucode
 firmware:       iwlwifi-8265-36.ucode
 firmware:       iwlwifi-8000C-36.ucode
 firmware:       iwlwifi-9260-th-b0-jf-b0-38.ucode
 firmware:       iwlwifi-9260-th-a0-jf-a0-38.ucode
 firmware:       iwlwifi-9000-pu-a0-jf-b0-38.ucode
 firmware:       iwlwifi-9000-pu-b0-jf-b0-38.ucode
 firmware:       iwlwifi-9000-pu-a0-jf-a0-38.ucode
 firmware:       iwlwifi-QuQnj-a0-hr-a0-38.ucode
 firmware:       iwlwifi-QuQnj-a0-jf-b0-38.ucode
 firmware:       iwlwifi-QuQnj-f0-hr-a0-38.ucode
 firmware:       iwlwifi-Qu-a0-jf-b0-38.ucode

 firmware:       iwlwifi-Qu-a0-hr-a0-38.ucode
 srcversion:     1F6BE15A46F5E4E4DE83078
 depends:        cfg80211
 retpoline:      Y
 intree:         Y
 name:           iwlwifi
 vermagic:       4.18.0-16-generic SMP mod_unload 

 signat:         PKCS#7
 signer:         
 sig_key:        
 sig_hashalgo:   md4
 parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
 parm:           11n_disable:disable 11n functionality,  bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX  (uint)
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
 parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
  
 [cfg80211]
 filename:       /lib/modules/4.18.0-16-generic/kernel/net/wireless/cfg80211.ko
 description:    wireless configuration support
 license:        GPL
 author:         Johannes Berg
 srcversion:     BFB309EF7C6C321F605D36E
 depends:        
 retpoline:      Y
 intree:         Y
 name:           cfg80211
 vermagic:       4.18.0-16-generic SMP mod_unload 
 signat:         PKCS#7
 signer:         
 sig_key:        
 sig_hashalgo:   md4
 parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
 remove_when_gone: N
 swcrypto: 0
 uapsd_disable: 3
  
 [cfg80211]
 bss_entries_limit: 1000
 cfg80211_disable_40mhz_24ghz: N
 ieee80211_regdom: 00
  
 ##### /etc/modules ######################
  
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
  
 [/etc/modprobe.d/iwlwifi.conf]
 remove iwlwifi \
 (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
 && /sbin/modprobe -r mac80211
  
 ##### rc.local ##########################
  
 grep: /etc/rc.local: No such file or directory

  
 ##### pm-utils ##########################
  
 ##### udev rules ########################

  

 ##### dmesg #############################

  
 [    6.101630] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2: link is not ready
 [    6.115570] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
 [    6.182642] r8169 0000:08:00.0 enp8s0: link down
 [    6.182821] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
 [    6.193470] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
 [   40.902478] rndis_host 1-2:1.0 enp0s20f0u2: unregister 'rndis_host' usb-0000:00:14.0-2, RNDIS device
 [   44.825332] rndis_host 1-2:1.0 enp0s20f0u2: renamed from usb0
 [   44.866995] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u2: link is not ready
  

 ########## wireless info END ############
```

---

### Post by jeremy31 on 2019-04-01
In terminal do
```
sudo apt-get install build-essential dkms git
git clone -b 4.18 https://github.com/jeremyb31/ideapad-laptop.git
sudo dkms add ./ideapad-laptop
sudo dkms install ideapad-laptop/1.0
echo "options ideapad_laptop override_has_hw_rfkill_switch=0" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```
Then reboot

---

### Post by festyn on 2019-04-01
It works! Amazing job, thank you very much! :)

---

### Post by jeremy31 on 2019-04-01
If you happen to be on freenode or spotchat IRC and see user ryuo, thank him as he wrote the code after I asked him for some help with this.   Please use the thread tools menu near the top right of the page to mark as solved

---

