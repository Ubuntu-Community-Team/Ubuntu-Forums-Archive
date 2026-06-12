---
title: "Yoga C740: WiFi works with LiveCD / LiveUSB, does not work installed"
date: 2020-03-02
forum: Networking &amp; Wireless
---

### Post by ajtoth on 2020-03-02
What's crazy to me is that everything worked fine with the LiveCD, but now that it's installed it doesn't. I tested with both Ubuntu 19.04 and Ubuntu 18.04LTS. The network card is Intel(R) Wireless-AC 9560. I've tried installing sudo apt install backport-iwlwifi-dkms and it doesn't work either. 
```
cat wireless-info.txt 

########## wireless info START ##########

Report from: 02 Mar 2020 17:11 EST -0500

Booted last: 02 Mar 2020 00:00 EST -0500

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 5.3.0-40-generic #32~18.04.1-Ubuntu SMP Mon Feb 3 14:05:59 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

00:14.3 Network controller [0280]: Intel Corporation Device [8086:02f0]
    Subsystem: Intel Corporation Device [8086:0034]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 005: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 13d3:56b2 IMC Networks 
Bus 001 Device 002: ID 06cb:00be Synaptics, Inc. 
Bus 001 Device 004: ID 8087:0aaa Intel Corp. 
Bus 001 Device 006: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

intel_wmi_thunderbolt    20480  0
wmi_bmof               16384  0
iwlmvm                397312  0
mac80211              847872  1 iwlmvm
libarc4                16384  1 mac80211
ideapad_laptop         20480  0
sparse_keymap          16384  1 ideapad_laptop
iwlwifi               348160  1 iwlmvm
cfg80211              704512  3 iwlmvm,iwlwifi,mac80211
wmi                    32768  3 intel_wmi_thunderbolt,wmi_bmof,ideapad_laptop
video                  49152  2 ideapad_laptop,i915

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
3: enx<IF from MAC [IF1]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
    inet 192.168.0.22/24 brd 192.168.0.255 scope global dynamic noprefixroute enx<IF from MAC [IF1]>
       valid_lft 3501sec preferred_lft 3501sec
    inet6 2601:140:8300:c9d0::12/128 scope global dynamic noprefixroute 
       valid_lft 3505sec preferred_lft 1705sec
    inet6 2601:140:8300:c9d0:aca3:88c:a474:4deb/64 scope global temporary dynamic 
       valid_lft 345597sec preferred_lft 86203sec
    inet6 2601:140:8300:c9d0:8a09:9254:805b:3088/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 345597sec preferred_lft 345597sec
    inet6 fe80::38ca:38b1:5a5:eb6a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enx<IF from MAC [IF1]>  no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enx<IF from MAC [IF1]> proto dhcp metric 100 
169.254.0.0/16 dev enx<IF from MAC [IF1]> scope link metric 1000 
192.168.0.0/24 dev enx<IF from MAC [IF1]> proto kernel scope link src 192.168.0.22 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0
search hsd1.va.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       784     1  0 Mar01 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx<IF from MAC [IF1]>
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        USB 10/100/1000 LAN
GENERAL.DRIVER:                         r8152
GENERAL.DRIVER-VERSION:                 v1.09.10
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enx<IF from MAC [IF1]>' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-4/2-4.3/2-4.3:1.0/net/enx<IF from MAC [IF1]>
GENERAL.IP-IFACE:                       enx<IF from MAC [IF1]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       992d69c4-3767-3067-a9df-2d95ae5a4e58
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.22/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             75.75.75.75
IP4.DNS[2]:                             75.75.76.76
IP4.DOMAIN[1]:                          hsd1.va.comcast.net
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 75.75.75.75 75.75.76.76
DHCP4.OPTION[5]:                        ip_address = 192.168.0.22
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        default_ip_ttl = 64
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       time_offset = 0
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[16]:                       requested_broadcast_address = 1
DHCP4.OPTION[17]:                       routers = 192.168.0.1
DHCP4.OPTION[18]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[19]:                       requested_domain_name = 1
DHCP4.OPTION[20]:                       domain_name = hsd1.va.comcast.net.
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       expiry = 1583190572
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_netbios_scope = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.0.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       next_server = 192.168.0.1
DHCP4.OPTION[30]:                       requested_ntp_servers = 1
DHCP4.OPTION[31]:                       requested_host_name = 1
DHCP4.OPTION[32]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         2601:140:8300:c9d0::12/128
IP6.ADDRESS[2]:                         2601:140:8300:c9d0:aca3:88c:a474:4deb/64
IP6.ADDRESS[3]:                         2601:140:8300:c9d0:8a09:9254:805b:3088/64
IP6.ADDRESS[4]:                         fe80::38ca:38b1:5a5:eb6a/64
IP6.GATEWAY:                            fe80::be2e:48ff:fe00:75c3
IP6.ROUTE[1]:                           dst = 2601:140:8300:c9d0::/60, nh = fe80::be2e:48ff:fe00:75c3, mt = 100
IP6.ROUTE[2]:                           dst = 2601:140:8300:c9d0::/64, nh = ::, mt = 100
IP6.ROUTE[3]:                           dst = ::/0, nh = fe80::be2e:48ff:fe00:75c3, mt = 100
IP6.ROUTE[4]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[5]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[6]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[7]:                           dst = 2601:140:8300:c9d0::12/128, nh = ::, mt = 100
IP6.DNS[1]:                             2001:558:feed::1
IP6.DNS[2]:                             2001:558:feed::2
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:4e:4c:ba:c2:45:a6:e0:82:ae:da:b1:a7:f:92:c2:5b
DHCP6.OPTION[2]:                        dhcp6_name_servers = 2001:558:feed::1 2001:558:feed::2
DHCP6.OPTION[3]:                        requested_dhcp6_name_servers = 1
DHCP6.OPTION[4]:                        rebind = 1350
DHCP6.OPTION[5]:                        max_life = 3600
DHCP6.OPTION[6]:                        preferred_life = 1800
DHCP6.OPTION[7]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[8]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[9]:                        life_starts = 1583186975
DHCP6.OPTION[10]:                       ip6_address = 2601:140:8300:c9d0::12
DHCP6.OPTION[11]:                       ip6_prefixlen = 64
DHCP6.OPTION[12]:                       renew = 900
DHCP6.OPTION[13]:                       dhcp6_server_id = 0:3:0:1:bc:2e:48:0:75:c3
DHCP6.OPTION[14]:                       iaid = 1e:70:0c:e9
DHCP6.OPTION[15]:                       starts = 1583186975
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   992d69c4-3767-3067-a9df-2d95ae5a4e58 | Wired connection 1

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

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

[[/etc/NetworkManager/system-connections/Tothnet]] (600 root)
[connection] id=Tothnet | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Tothnet
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

enx<IF from MAC [IF1]>  no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enx<IF from MAC [IF1]>  Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/5.3.0-40-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     2C84FD44C3B5F1C7E065DBC
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       5.3.0-40-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/5.3.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B74C319077A9D20B0ECE3D6
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.3.0-40-generic SMP mod_unload 
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
filename:       /lib/modules/5.3.0-40-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-9260-th-b0-jf-b0-46.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-46.ucode
firmware:       iwlwifi-ty-a0-gf-a0-48.ucode
firmware:       iwlwifi-so-a0-gf-a0-48.ucode
firmware:       iwlwifi-so-a0-hr-b0-48.ucode
firmware:       iwlwifi-so-a0-jf-b0-48.ucode
firmware:       iwlwifi-cc-a0-48.ucode
firmware:       iwlwifi-QuQnj-b0-jf-b0-48.ucode
firmware:       iwlwifi-QuZ-a0-jf-b0-48.ucode
firmware:       iwlwifi-QuZ-a0-hr-b0-48.ucode
firmware:       iwlwifi-Qu-b0-jf-b0-48.ucode
firmware:       iwlwifi-Qu-c0-hr-b0-48.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-48.ucode
firmware:       iwlwifi-QuQnj-b0-hr-b0-48.ucode
firmware:       iwlwifi-Qu-b0-hr-b0-48.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-48.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-48.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-48.ucode
srcversion:     263DD85C748F2F7EFAE8CF0
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       5.3.0-40-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for 22560 devices, 4K for other devices 1:4K 2:8K 3:12K 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: 0 (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/5.3.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7A4BDDDDFBDE4DDDB63AAE3
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.3.0-40-generic SMP mod_unload 
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
disable_11ax: N
enable_ini: N
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

[/etc/modprobe.d/libopenni-sensor-pointclouds0.conf]
blacklist gspca_kinect

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   96.111858] r8152 2-4.3:1.0 eth0: v1.09.10
[   96.116441] r8152 2-4.3:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[   99.020135] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF1]>: link becomes ready
[   99.021605] r8152 2-4.3:1.0 enx<IF from MAC [IF1]>: carrier on
[85844.376587] r8152 2-4.3:1.0 eth0: v1.09.10
[85844.393419] r8152 2-4.3:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[85847.314713] IPv6: ADDRCONF(NETDEV_CHANGE): enx<IF from MAC [IF1]>: link becomes ready
[85847.315298] r8152 2-4.3:1.0 enx<IF from MAC [IF1]>: carrier on

########## wireless info END ############


```

I'm currently running Ubuntu 18.04 and intend to continue because of support for ROS Melodic.

---

### Post by ajtoth on 2020-03-02
Extra info that I would imagine is much more useful is the output of dmesg:

```
dmesg | grep iwlwifi
[    5.160816] iwlwifi 0000:00:14.3: TLV_FW_FSEQ_VERSION: FSEQ Version: 43.2.23.17
[    5.160822] iwlwifi 0000:00:14.3: Found debug destination: EXTERNAL_DRAM
[    5.160825] iwlwifi 0000:00:14.3: Found debug configuration: 0
[    5.161227] iwlwifi 0000:00:14.3: loaded firmware version 48.13675109.0 op_mode iwlmvm
[    5.225396] iwlwifi 0000:00:14.3: Detected Intel(R) Wireless-AC 9560, REV=0x354
[    5.233405] iwlwifi 0000:00:14.3: Applying debug destination EXTERNAL_DRAM
[    5.235025] iwlwifi 0000:00:14.3: Allocated 0x00400000 bytes for firmware monitor.
[    6.251270] iwlwifi 0000:00:14.3: Collecting data: trigger 15 fired.
[    6.251354] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[    6.251358] iwlwifi 0000:00:14.3: Status: 0x00000000, count: -1236499254
[    6.251360] iwlwifi 0000:00:14.3: Loaded firmware version: 48.13675109.0
[    6.251363] iwlwifi 0000:00:14.3: 0x5FC03815 | ADVANCED_SYSASSERT          
[    6.251365] iwlwifi 0000:00:14.3: 0x56003899 | trm_hw_status0
[    6.251367] iwlwifi 0000:00:14.3: 0x01E423B8 | trm_hw_status1
[    6.251369] iwlwifi 0000:00:14.3: 0xA6B756A9 | branchlink2
[    6.251370] iwlwifi 0000:00:14.3: 0xE328D71C | interruptlink1
[    6.251372] iwlwifi 0000:00:14.3: 0x30FAE5C9 | interruptlink2
[    6.251374] iwlwifi 0000:00:14.3: 0x5C8EB565 | data1
[    6.251375] iwlwifi 0000:00:14.3: 0x3D2FDD0B | data2
[    6.251377] iwlwifi 0000:00:14.3: 0x4ECFDDAF | data3
[    6.251379] iwlwifi 0000:00:14.3: 0xE0689EE8 | beacon time
[    6.251380] iwlwifi 0000:00:14.3: 0x06191069 | tsf low
[    6.251382] iwlwifi 0000:00:14.3: 0x7DBBFEDD | tsf hi
[    6.251384] iwlwifi 0000:00:14.3: 0x1BEA870A | time gp1
[    6.251385] iwlwifi 0000:00:14.3: 0x32EF9E49 | time gp2
[    6.251387] iwlwifi 0000:00:14.3: 0xB4E8CFB0 | uCode revision type
[    6.251389] iwlwifi 0000:00:14.3: 0xFC1576D9 | uCode version major
[    6.251391] iwlwifi 0000:00:14.3: 0xB26D9E2B | uCode version minor
[    6.251392] iwlwifi 0000:00:14.3: 0x70242BE0 | hw version
[    6.251394] iwlwifi 0000:00:14.3: 0x406545E2 | board version
[    6.251396] iwlwifi 0000:00:14.3: 0xFE4691FB | hcmd
[    6.251397] iwlwifi 0000:00:14.3: 0x27E6FF4D | isr0
[    6.251399] iwlwifi 0000:00:14.3: 0x4777F7D9 | isr1
[    6.251401] iwlwifi 0000:00:14.3: 0xAB80A9A1 | isr2
[    6.251402] iwlwifi 0000:00:14.3: 0xB89EE9B0 | isr3
[    6.251404] iwlwifi 0000:00:14.3: 0xD7C7DFFA | isr4
[    6.251406] iwlwifi 0000:00:14.3: 0xFD91FF76 | last cmd Id
[    6.251407] iwlwifi 0000:00:14.3: 0x963C88E0 | wait_event
[    6.251409] iwlwifi 0000:00:14.3: 0x96B0CCE2 | l2p_control
[    6.251411] iwlwifi 0000:00:14.3: 0xEEFF6CB9 | l2p_duration
[    6.251412] iwlwifi 0000:00:14.3: 0x5E8664CE | l2p_mhvalid
[    6.251414] iwlwifi 0000:00:14.3: 0x12D1399E | l2p_addr_match
[    6.251416] iwlwifi 0000:00:14.3: 0x7C02F17C | lmpm_pmg_sel
[    6.251417] iwlwifi 0000:00:14.3: 0xDAA5E8C3 | timestamp
[    6.251419] iwlwifi 0000:00:14.3: 0xF9074764 | flow_handler
[    6.251454] iwlwifi 0000:00:14.3: Start IWL Error Log Dump:
[    6.251456] iwlwifi 0000:00:14.3: Status: 0x00000000, count: 7
[    6.251458] iwlwifi 0000:00:14.3: 0x201013F1 | ADVANCED_SYSASSERT
[    6.251460] iwlwifi 0000:00:14.3: 0x00000000 | umac branchlink1
[    6.251462] iwlwifi 0000:00:14.3: 0xC008CF5C | umac branchlink2
[    6.251464] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink1
[    6.251465] iwlwifi 0000:00:14.3: 0x00000000 | umac interruptlink2
[    6.251467] iwlwifi 0000:00:14.3: 0x00000003 | umac data1
[    6.251469] iwlwifi 0000:00:14.3: 0x20000302 | umac data2
[    6.251470] iwlwifi 0000:00:14.3: 0x01300202 | umac data3
[    6.251472] iwlwifi 0000:00:14.3: 0x00000030 | umac major
[    6.251474] iwlwifi 0000:00:14.3: 0x13675109 | umac minor
[    6.251475] iwlwifi 0000:00:14.3: 0x00005CD8 | frame pointer
[    6.251477] iwlwifi 0000:00:14.3: 0xC0887F58 | stack pointer
[    6.251479] iwlwifi 0000:00:14.3: 0x00000000 | last host cmd
[    6.251481] iwlwifi 0000:00:14.3: 0x00000000 | isr status reg
[    6.251498] iwlwifi 0000:00:14.3: Fseq Registers:
[    6.251501] iwlwifi 0000:00:14.3: 0x00000003 | FSEQ_ERROR_CODE
[    6.251522] iwlwifi 0000:00:14.3: 0x00000000 | FSEQ_TOP_INIT_VERSION
[    6.251525] iwlwifi 0000:00:14.3: 0x6FE72EAC | FSEQ_CNVIO_INIT_VERSION
[    6.251546] iwlwifi 0000:00:14.3: 0x0000A384 | FSEQ_OTP_VERSION
[    6.251549] iwlwifi 0000:00:14.3: 0x5DA66B83 | FSEQ_TOP_CONTENT_VERSION
[    6.251569] iwlwifi 0000:00:14.3: 0xD26DA623 | FSEQ_ALIVE_TOKEN
[    6.251573] iwlwifi 0000:00:14.3: 0x1A1E5C66 | FSEQ_CNVI_ID
[    6.251593] iwlwifi 0000:00:14.3: 0x50A53FD0 | FSEQ_CNVR_ID
[    6.251596] iwlwifi 0000:00:14.3: 0x20000302 | CNVI_AUX_MISC_CHIP
[    6.251619] iwlwifi 0000:00:14.3: 0x01300202 | CNVR_AUX_MISC_CHIP
[    6.251624] iwlwifi 0000:00:14.3: 0x0000485B | CNVR_SCU_SD_REGS_SD_REG_DIG_DCDC_VTRIM
[    6.251677] iwlwifi 0000:00:14.3: 0xA5A5A5A2 | CNVR_SCU_SD_REGS_SD_REG_ACTIVE_VDIG_MIRROR
[    6.251712] iwlwifi 0000:00:14.3: SecBoot CPU1 Status: 0x5c4a, CPU2 Status: 0x3
[    6.251714] iwlwifi 0000:00:14.3: Failed to start RT ucode: -110
[    6.251718] iwlwifi 0000:00:14.3: Firmware not running - cannot dump error
[    6.263333] iwlwifi 0000:00:14.3: Failed to run INIT ucode: -110

```

---

### Post by chili555 on 2020-03-02
We notice: > Linux 5.3.0**-40**-genericPlease check: [https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493#comment2038719_1193493](https://askubuntu.com/questions/1192531/wifi-adapter-not-found-for-dell-inspiron-5590-processor-is-i5-10th-gen-10210u/1193493#comment2038719_1193493)

Please see the last three comments.

---

### Post by ajtoth on 2020-03-12
thanks, Chili555
I was skeptical, because the link you sent was for a different driver
BUT IT WORKS.
Step-by-step:
1. At boot, the GRUB menu comes up
2. Select "Advanced Options for Ubuntu"
3. "Ubuntu, with Linux 5.3.0-28-generic"

Will I have any issues if I update my machine? *As long as I continue to boot to kernel -28?

---

### Post by chili555 on 2020-03-13
> 
Will I have any issues if I update my machine? *As long as I continue to boot to kernel -28?
Probably not. At some point, the bug will be fixed and as you find that an offered update is a newer kernel version (linux-image),  say 5.3.0-43 or some such, try booting into it to see if the wireless now works. If so, you will be safe to start using it. When that is the case, please report back as quite a few also affected users will appreciate the good news.> 
the link you sent was for a different driver
I believe it is, in fact, the same: iwlwifi.

---

### Post by ajtoth on 2020-03-13
I was confused with the rtlwifi; before I posted I saw that and I thought they were dealing with Realtek drivers.
Thanks, Chili555. I'll update with APT, not run dist-upgrade until 20.04 comes out, and I hope to remember to post back here once it starts working again.

---

### Post by chili555 on 2020-03-16
5.3.0-42 is now out. Does the wireless work properly now? 

Thanks.

---

### Post by ajtoth on 2020-03-17
[COLOR=#000000]5.3.0-42 does not fix the WiFi.

ran
sudo apt update
sudo apt install linux-image-[/COLOR][COLOR=#000000]5.3.0-42
sudo apt upgrade

upgrade also installed linux-headers-[/COLOR][COLOR=#000000]5.3.0-42

It updated GRUB2 appropriately. Ran it, no joy.
No Wi-Fi adapter found[/COLOR]

---

### Post by chili555 on 2020-03-24
Will you please try this and report back? [https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262](https://askubuntu.com/questions/1218141/dell-vostro-5490-no-wifi-in-ubuntu-18-04/1218262#1218262)

---

### Post by ajtoth on 2020-04-08
Followed the steps up to & including
```
sudo rmmod iwlmvm
sudo rmmod iwlwifi
sudo cp /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode{,.bak}
sudo cp /lib/firmware/iwlwifi-QuZ-a0-jf-b0-48.ucode /lib/firmware/iwlwifi-Qu-b0-jf-b0-48.ucode
sudo modprobe iwlwifi
```

Wifi is working successfully under kernel 5.3.0-45-generic

---

### Post by chili555 on 2020-04-09
Awesome! Glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by ajtoth on 2020-04-09
Thanks for the tips.
Both with Ubuntu & the forums

---

### Post by ajtoth on 2020-05-08
This solution is still required for linux-image-5.3.0-51

---

### Post by ajtoth on 2020-06-05
Freshly installed 20.04: This solution is no longer required. :D

---

### Post by chili555 on 2020-06-05
> **ajtoth said:**
> Freshly installed 20.04: This solution is no longer required. :DThanks for the update. Which kernel version is running?

```
uname -r
```

---

