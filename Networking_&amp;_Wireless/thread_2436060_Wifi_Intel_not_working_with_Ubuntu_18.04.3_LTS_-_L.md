---
title: "Wifi Intel not working with Ubuntu 18.04.3 LTS - Lenovo Ideapad 730S"
date: 2020-01-30
forum: Networking &amp; Wireless
---

### Post by aafgarci on 2020-01-30
Hi,

I have a new Lenovo Ideapad 730S and my wifi is not working (it was when I installed Ubuntu a few days ago).

Some information:

Network controller [0280]: Intel Corporation Wireless-AC 9260 [8086:2526] (rev 29)
Subsystem: Intel Corporation Device [8086:0014]
Kernel modules: iwlwifi

Linux 5.3.0-28-generic

Any suggestion? Many thanks in advance

---

### Post by jeremy31 on 2020-01-30
See the wireless script link in my signature and post results

---

### Post by aafgarci on 2020-01-30
########## wireless info START ##########


Report from: 30 Jan 2020 13:38 EST -0500


Booted last: 30 Jan 2020 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


73:00.0 Network controller [0280]: Intel Corporation Wireless-AC 9260 [8086:2526] (rev 29)
	Subsystem: Intel Corporation Device [8086:0014]
	Kernel modules: iwlwifi


##### lsusb #############################


Bus 004 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. 
Bus 004 Device 003: ID 058f:8468 Alcor Micro Corp. 
Bus 004 Device 002: ID 2109:0817 VIA Labs, Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 27c6:5584  
Bus 001 Device 004: ID 8087:0025 Intel Corp. 
Bus 001 Device 003: ID 04f2:b61e Chicony Electronics Co., Ltd 
Bus 001 Device 008: ID 2109:8888 VIA Labs, Inc. 
Bus 001 Device 009: ID 0c76:153f JMTek, LLC. 
Bus 001 Device 007: ID 1a40:0801 Terminus Technology Inc. 
Bus 001 Device 005: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 002: ID 2109:2817 VIA Labs, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


asus_wmi               32768  0
sparse_keymap          16384  1 asus_wmi
wmi_bmof               16384  0
intel_wmi_thunderbolt    20480  0
iwlwifi               372736  0
cfg80211              688128  1 iwlwifi
compat                 16384  2 iwlwifi,cfg80211
wmi                    32768  3 intel_wmi_thunderbolt,asus_wmi,wmi_bmof
video                  49152  2 asus_wmi,i915


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
2: enx<IF from MAC [IF1]>: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enx<IF from MAC [IF1]>' [IF1]> brd <MAC address>
3: enp0s20f0u2u1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'enp0s20f0u2u1' [IF2]> brd <MAC address>
    inet 192.168.42.211/24 brd 192.168.42.255 scope global dynamic noprefixroute enp0s20f0u2u1
       valid_lft 3367sec preferred_lft 3367sec
    inet6 fe80::4d3b:a87f:61b9:c264/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


enp0s20f0u2u1  no wireless extensions.


enx<IF from MAC [IF1]>  no wireless extensions.


##### route #############################


default via 192.168.42.129 dev enp0s20f0u2u1 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20f0u2u1 scope link metric 1000 
192.168.42.0/24 dev enp0s20f0u2u1 proto kernel scope link src 192.168.42.211 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


	NetworkManager


Running:


root       837     1  0 13:34 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s20f0u2u1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u2u1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2.1/1-2.1:1.0/net/enp0s20f0u2u1
GENERAL.IP-IFACE:                       enp0s20f0u2u1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6c7e05e0-52ff-363b-b31a-ad6c1b6a3879
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.211/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.211
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
DHCP4.OPTION[19]:                       expiry = 1580412868
DHCP4.OPTION[20]:                       host_name = wolfpack
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       next_server = 192.168.42.129
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::4d3b:a87f:61b9:c264/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6c7e05e0-52ff-363b-b31a-ad6c1b6a3879 | Wired connection 1


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_68_7D_6B_50_16_14
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
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   39240d1e-c2cf-42d4-9d90-dba7849decae | Ludwig Network


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
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:02:00.0/0000:03:02.0/0000:3b:00.0/usb4/4-1/4-1.3/4-1.3:1.0/net/enx<IF from MAC [IF1]>
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


[[/etc/NetworkManager/system-connections/ncsu]] (600 root)
[connection] id=ncsu | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=ncsu
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


enp0s20f0u2u1  no frequency information.


enx<IF from MAC [IF1]>  no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp0s20f0u2u1  Interface doesn't support scanning.


enx<IF from MAC [IF1]>  Interface doesn't support scanning.


##### module infos ######################


[iwlwifi]
filename:       /lib/modules/5.3.0-28-generic/updates/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
version:        iwlwifi-stack-public:master:8324:9176b151
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-36.ucode
firmware:       iwlwifi-8000C-36.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-46.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-46.ucode
firmware:       iwlwifi-SoSnj-a0-gf-a0-55.ucode
firmware:       iwlwifi-SoSnj-a0-gf4-a0-55.ucode
firmware:       iwlwifi-ty-a0-gf-a0-55.ucode
firmware:       iwlwifi-so-a0-gf-a0-55.ucode
firmware:       iwlwifi-so-a0-hr-b0-55.ucode
firmware:       iwlwifi-so-a0-jf-b0-55.ucode
firmware:       iwlwifi-cc-a0-55.ucode
firmware:       iwlwifi-QuQnj-b0-jf-b0-55.ucode
firmware:       iwlwifi-QuZ-a0-jf-b0-55.ucode
firmware:       iwlwifi-QuZ-a0-hr-b0-55.ucode
firmware:       iwlwifi-Qu-b0-jf-b0-55.ucode
firmware:       iwlwifi-Qu-c0-hr-b0-55.ucode
firmware:       iwlwifi-QuQnj-b0-hr-b0-55.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-55.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-55.ucode
srcversion:     429405ECF8888645E7117B9
depends:        compat,cfg80211
retpoline:      Y
name:           iwlwifi
vermagic:       5.3.0-28-generic SMP mod_unload 
parm:           debug:debug output mask (uint)
parm:           xvt_default_mode:xVT is the default operation mode (default: false) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 2K for AX210 devices, 4K for other devices 1:4K 2:8K 3:12K 4: 2K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           enable_ini:Enable debug INI TLV FW debug infrastructure (default: true (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)
parm:           disable_11ax:Disable HE capabilities (default: false) (bool)
parm:           disable_msix:Disable MSI-X and use MSI instead (default: false) (bool)
parm:           remove_when_gone:Remove dev from PCIe bus if it is deemed inaccessible (default: false) (bool)


[cfg80211]
filename:       /lib/modules/5.3.0-28-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:master:8324:9176b151
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     85C762B91466B7F2749B25C
depends:        compat
retpoline:      Y
name:           cfg80211
vermagic:       5.3.0-28-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
debug: 0
disable_11ac: N
disable_11ax: N
disable_msix: N
enable_ini: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
remove_when_gone: N
swcrypto: 0
uapsd_disable: 3
xvt_default_mode: N


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


[/etc/modprobe.d/blacklist-ideapad.conf]
blacklist ideapad_laptop


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


[    6.017773] r8152 4-1.3:1.0 enx<IF from MAC [IF1]>: renamed from eth0
[    6.060998] rndis_host 1-2.1:1.0 enp0s20f0u2u1: renamed from usb0


########## wireless info END ############

---

