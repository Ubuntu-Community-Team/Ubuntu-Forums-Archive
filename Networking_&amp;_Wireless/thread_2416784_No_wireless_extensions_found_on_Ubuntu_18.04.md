---
title: "No wireless extensions found on Ubuntu 18.04"
date: 2019-04-15
forum: Networking &amp; Wireless
---

### Post by bacebogo on 2019-04-15
Hi team,


I'm new to Ubuntu and I can't get my wireless connection work. None of the suggestions I found in another threads helped me. 


My version of Ubuntu is: 18.04.2 LTS


```



########## wireless info START ##########




Report from: 15 Apr 2019 18:48 EEST +0300




Booted last: 15 Apr 2019 00:00 EEST +0300




Script from: 22 Oct 2018 03:34 UTC +0000




##### release ###########################




Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic




##### kernel ############################




Linux 4.18.0-17-generic #18~18.04.1-Ubuntu SMP Fri Mar 15 15:27:12 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux




Parameters: ro, quiet, splash, vt.handoff=1




##### desktop ###########################




Plasma




##### lspci #############################




07:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:3166] (rev 99)
    Subsystem: Intel Corporation Dual Band Wireless-AC 3165 Plus Bluetooth [8086:4210]
    Kernel driver in use: iwlwifi




08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:38aa]
    Kernel driver in use: r8169




##### lsusb #############################




Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 174f:241a Syntek 
Bus 001 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120
Bus 001 Device 005: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 04d9:a0d6 Holtek Semiconductor, Inc. 
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




'mokutil' is not installed (package "mokutil").




##### lsmod #############################




wl                   6447104  0
iwlmvm                376832  0
mac80211              802816  1 iwlmvm
intel_wmi_thunderbolt    16384  0
wmi_bmof               16384  0
iwlwifi               299008  1 iwlmvm
cfg80211              667648  4 wl,iwlmvm,iwlwifi,mac80211
ideapad_laptop         32768  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    24576  3 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop
video                  45056  2 ideapad_laptop,i915




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
2: enp8s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
    inet 192.168.196.156/24 brd 192.168.196.255 scope global dynamic noprefixroute enp8s0
       valid_lft 380sec preferred_lft 380sec
    inet6 fe80::a7ef:eaff:b9f7:50b2/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>




##### iwconfig ##########################




lo        no wireless extensions.




enp8s0    no wireless extensions.




wlp7s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




##### route #############################




default via 192.168.196.1 dev enp8s0 proto dhcp metric 100 
169.254.0.0/16 dev enp8s0 scope link metric 1000 
192.168.196.0/24 dev enp8s0 proto kernel scope link src 192.168.196.156 metric 100 




##### resolv.conf #######################




[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']




nameserver 127.0.0.53
options edns0




##### network managers ##################




Installed:




    NetworkManager




Running:




root       992     1  0 18:30 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon




##### NetworkManager info ###############




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
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.5/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       cc19554c-726b-3857-9e39-6a0c8b78b3ad
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.196.156/24
IP4.GATEWAY:                            192.168.196.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.196.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.196.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.196.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        ntp_servers = 77.70.122.201 212.70.148.11
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1555343671
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.196.1
DHCP4.OPTION[11]:                       broadcast_address = 192.168.196.255
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 600
DHCP4.OPTION[15]:                       routers = 192.168.196.1
DHCP4.OPTION[16]:                       ip_address = 192.168.196.156
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.196.1
DHCP4.OPTION[25]:                       dhcp_message_type = 5
DHCP4.OPTION[26]:                       network_number = 192.168.196.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.196.1
IP6.ADDRESS[1]:                         fe80::a7ef:eaff:b9f7:50b2/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cc19554c-726b-3857-9e39-6a0c8b78b3ad | Wired connection 1




GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Dual Band Wireless-AC 3165 Plus Bluetooth
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.18.0-17-generic
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




Region: Europe/Sofia (based on set time zone)




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




Sorry, try again.
wlp7s0    Interface doesn't support scanning : Network is down




lo        Interface doesn't support scanning.




enp8s0    Interface doesn't support scanning.




##### module infos ######################




[wl]
filename:       /lib/modules/4.18.0-17-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.18.0-17-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string




[iwlmvm]
filename:       /lib/modules/4.18.0-17-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     4DAD4F3B58FCA15965D5AC4
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       4.18.0-17-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)




[mac80211]
filename:       /lib/modules/4.18.0-17-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-17-generic SMP mod_unload 
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
filename:       /lib/modules/4.18.0-17-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
vermagic:       4.18.0-17-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)




[cfg80211]
filename:       /lib/modules/4.18.0-17-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-17-generic SMP mod_unload 
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




[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma




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




[   47.705096] iwlwifi 0000:07:00.0: loaded firmware version 29.1044073957.0 op_mode iwlmvm
[   47.717352] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 3165, REV=0x210
[   47.744788] iwlwifi 0000:07:00.0: base HW address: <MAC 'wlp7s0' [IF2]>
[   48.443531] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   48.812647] iwlwifi 0000:07:00.0 wlp7s0: renamed from wlan0
[   65.797201] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   65.986128] r8169 0000:08:00.0 enp8s0: link down (repeated 2 times)
[   65.986298] IPv6: ADDRCONF(NETDEV_UP): enp8s0: link is not ready
[   65.998754] IPv6: ADDRCONF(NETDEV_UP): wlp7s0: link is not ready
[   68.650248] r8169 0000:08:00.0 enp8s0: link up
[   68.650264] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready




########## wireless info END ############





```




```

description: Notebook
    product: 81FK (LENOVO_MT_81FK_BU_idea_FM_ideapad 330-15ICH)
    vendor: LENOVO
    version: Lenovo ideapad 330-15ICH
    serial: PF166CMR
    width: 64 bits
    capabilities: smbios-3.0 dmi-3.0 smp vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ideapad 330-15ICH frontpanel_password=disabled keyboard_password=disabled power-on_password=disabled sku=LENOVO_MT_81FK_BU_idea_FM_ideapad 330-15ICH uuid=09AB07AA-0D9D-E811-B5F5-8C1645E9E4D8
  *-core
       description: Motherboard
       product: LNVNB161216
       vendor: LENOVO
       physical id: 0
       version: NO DPK
       serial: PF166CMR
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7ZCN28WW
          date: 07/17/2018
          size: 128KiB
          capacity: 10176KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: U3E1
          size: 3941MHz
          capacity: 4100MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp flush_l1d cpufreq
          configuration: cores=6 enabledcores=6 threads=12
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 384KiB
             capacity: 384KiB
             capabilities: synchronous internal write-back unified
             configuration: level=1
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 1536KiB
             capacity: 1536KiB
             capabilities: synchronous internal write-back unified
             configuration: level=2
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 9MiB
             capacity: 9MiB
             capabilities: synchronous internal write-back unified
             configuration: level=3
     *-memory
          description: System Memory
          physical id: 25
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous 2400 MHz (0,4 ns)
             product: M471A5244CB0-CTD
             vendor: Samsung
             physical id: 0
             serial: 00000000
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous 2400 MHz (0,4 ns)
             product: HMA851S6CJR6N-VK
             vendor: SK Hynix
             physical id: 1
             serial: 823B4560
             slot: ChannelB-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 2400MHz (0.4ns)
     *-pci
          description: Host bridge
          product: 8th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16)
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 ioport:4000(size=4096) memory:a3000000-a3ffffff ioport:90000000(size=301989888)
           *-display
                description: 3D controller
                product: GP107M [GeForce GTX 1050 Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:150 memory:a3000000-a3ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:4000(size=128)
        *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:130 memory:a2000000-a2ffffff memory:b0000000-bfffffff ioport:5000(size=64) memory:c0000-dffff
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
             vendor: Intel Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:a4418000-a4418fff
        *-generic:1
             description: Signal processing controller
             product: Cannon Lake PCH Thermal Controller
             vendor: Intel Corporation
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:16 memory:a4419000-a4419fff
        *-usb
             description: USB controller
             product: Cannon Lake PCH USB 3.1 xHCI Host Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:a4400000-a440ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.18.0-17-generic xhci-hcd
                physical id: 0
                bus info: usb@1
                logical name: usb1
                version: 4.18
                capabilities: usb-2.00
                configuration: driver=hub slots=16 speed=480Mbit/s
              *-usb:0
                   description: Mouse
                   product: USB Gaming Mouse
                   vendor: E-Signal/A-One
                   physical id: 1
                   bus info: usb@1:1
                   version: 1.05
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usb:1
                   description: Keyboard
                   product: USB Keyboard
                   vendor: Logitech
                   physical id: 3
                   bus info: usb@1:3
                   version: 64.00
                   capabilities: usb-1.10
                   configuration: driver=usbhid maxpower=90mA speed=1Mbit/s
              *-usb:2
                   description: Video
                   product: EasyCamera
                   vendor: M180511j3935
                   physical id: 8
                   bus info: usb@1:8
                   version: 0.13
                   capabilities: usb-2.00
                   configuration: driver=uvcvideo maxpower=500mA speed=480Mbit/s
              *-usb:3
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: e
                   bus info: usb@1:e
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.18.0-17-generic xhci-hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 4.18
                capabilities: usb-3.10
                configuration: driver=hub slots=8 speed=10000Mbit/s
        *-memory UNCLAIMED
             description: RAM memory
             product: Cannon Lake PCH Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 10
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:a4414000-a4415fff memory:a441a000-a441afff
        *-serial:0
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:8f800000-8f800fff
        *-serial:1
             description: Serial bus controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:8f801000-8f801fff
        *-communication:0
             description: Communication controller
             product: Cannon Lake PCH HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:151 memory:a441d000-a441dfff
        *-storage
             description: SATA controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 17
             bus info: pci@0000:00:17.0
             version: 10
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:127 memory:a4416000-a4417fff memory:a4422000-a44220ff ioport:5080(size=8) ioport:5088(size=4) ioport:5060(size=32) memory:a4421000-a44217ff
        *-pci:1
             description: PCI bridge
             product: Cannon Lake PCH PCI Express Root Port 9
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:a4300000-a43fffff
           *-storage
                description: Non-Volatile memory controller
                product: NVMe SSD Controller SM981/PM981
                vendor: Samsung Electronics Co Ltd
                physical id: 0
                bus info: pci@0000:06:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:16 memory:a4300000-a4303fff
        *-pci:2
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.4
             bus info: pci@0000:00:1d.4
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:a4200000-a42fffff
           *-network DISABLED
                description: Wireless interface
                product: Dual Band Wireless-AC 3165 Plus Bluetooth
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wlp7s0
                version: 99
                serial: 34:e1:2d:fb:3f:0b
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.18.0-17-generic firmware=29.1044073957.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
                resources: irq:143 memory:a4200000-a4201fff
        *-pci:3
             description: PCI bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1d.5
             bus info: pci@0000:00:1d.5
             version: f0
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:125 ioport:3000(size=4096) memory:a4100000-a41fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: enp8s0
                version: 10
                serial: 8c:16:45:e9:e4:d8
                size: 1Gbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.196.156 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
                resources: irq:17 ioport:3000(size=256) memory:a4104000-a4104fff memory:a4100000-a4103fff
        *-communication:1
             description: Communication controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:20 memory:8f802000-8f802fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-multimedia
             description: Audio device
             product: Cannon Lake PCH cAVS
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 10
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:152 memory:a4410000-a4413fff memory:a4000000-a40fffff
        *-serial:2 UNCLAIMED
             description: SMBus
             product: Cannon Lake PCH SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@0000:00:1f.4
             version: 10
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a441f000-a441f0ff ioport:5040(size=32)
        *-serial:3 UNCLAIMED
             description: Serial bus controller
             product: Cannon Lake PCH SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
             resources: memory:fe010000-fe010fff
     *-scsi
          physical id: 1
          logical name: scsi4
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10SPZX-24Z
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sda
             version: 1A04
             serial: WD-WXS1A684KEE5
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096 signature=d9fa2484
           *-volume:0
                description: Extended partition
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sda1
                size: 469GiB
                capacity: 469GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Windows NTFS volume
                   physical id: 5
                   logical name: /dev/sda5
                   version: 3.1
                   serial: 520a55d7-437a-aa42-8b27-aedd6ece132b
                   size: 469GiB
                   capacity: 469GiB
                   capabilities: ntfs initialized
                   configuration: clustersize=4096 created=2010-05-04 06:24:57 filesystem=ntfs label=DATA modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: EXT4 volume
                vendor: Linux
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sda2
                logical name: /
                version: 1.0
                serial: c9d31935-6f61-4164-8a9b-4b2816b0cf95
                size: 462GiB
                capacity: 462GiB
                capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover 64bit extents ext4 ext2 initialized
                configuration: created=2019-04-01 10:45:50 filesystem=ext4 lastmountpoint=/ modified=2019-04-15 18:29:32 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro mounted=2019-04-15 18:29:40 state=mounted
  *-battery
       description: Zinc Air Battery
       product: CRB Battery 0
       vendor: -Virtual Battery 0-
       physical id: 1
       version: 08/08/2010
       serial: Battery 0
       slot: Fake
  *-power UNCLAIMED
       description: OEM Define 1
       product: OEM Define 5
       vendor: OEM Define 2
       physical id: 2
       version: OEM Define 6
       serial: OEM Define 3
       capacity: 75mWh





```

---

### Post by jeremy31 on 2019-04-15
Please see [https://askubuntu.com/questions/1104218/no-wifi-adapter-found-on-new-lenovo-yoga-c930-with-ubuntu-18-10/1104240#1104240](https://askubuntu.com/questions/1104218/no-wifi-adapter-found-on-new-lenovo-yoga-c930-with-ubuntu-18-10/1104240#1104240)

---

### Post by bacebogo on 2019-04-16
Hi Mate,

following the steps from that thread worked for me.

Many thanks,

Cheers

---

