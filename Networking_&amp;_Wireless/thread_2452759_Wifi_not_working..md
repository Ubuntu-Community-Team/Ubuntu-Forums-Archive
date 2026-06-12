---
title: "Wifi not working."
date: 2020-10-28
forum: Networking &amp; Wireless
---

### Post by smcdaid on 2020-10-28
I'm new to Linux so understand if you think I'm missing something small, I am. I've tried several things to get my WiFi to work. I've searched in this forum and done google searches but keep coming up empty. I'll post some info that the terminal spit out. Any help is really appreciated. 
```

########## wireless info START ##########

Report from: 28 Oct 2020 00:02 EDT -0400

Booted last: 28 Oct 2020 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-52-generic #57-Ubuntu SMP Thu Oct 15 10:57:00 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '“options'

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8125 2.5GbE Controller [10ec:8125] (rev 05)
    Subsystem: ASRock Incorporation RTL8125 2.5GbE Controller [1849:8168]
    Kernel modules: r8169

##### lsusb #############################

Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 008: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC
Bus 003 Device 007: ID 0408:7090 Quanta Computer, Inc. ASM107x
Bus 003 Device 006: ID 0408:7a10 Quanta Computer, Inc. 
Bus 003 Device 005: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 004: ID 04d9:fc4d Holtek Semiconductor, Inc. 802.11ac NIC
Bus 003 Device 003: ID 0bda:c820 Realtek Semiconductor Corp. ASM107x
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 26ce:01a2 ASRock LED Controller
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 062a:8508 MosArt Semiconductor Corp. USB Keyboard
Bus 001 Device 007: ID 04e8:6863 Samsung Electronics Co., Ltd Galaxy series, misc. (tethering mode)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

cfg80211              708608  0
compat                 16384  1 cfg80211
wmi_bmof               16384  0
wmi                    32768  1 wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: usb0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'usb0' [IF1]> brd <MAC address>
    inet 192.168.42.25/24 brd 192.168.42.255 scope global dynamic noprefixroute usb0
       valid_lft 3335sec preferred_lft 3335sec
    inet6 fe80::a1ac:e68:de2c:cd44/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

usb0      no wireless extensions.

##### route #############################

default via 192.168.42.129 dev usb0 proto dhcp metric 100 
169.254.0.0/16 dev usb0 scope link metric 1000 
192.168.42.0/24 dev usb0 proto kernel scope link src 192.168.42.25 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root        5744       1  0 Oct27 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Samsung Electronics Co., Ltd
GENERAL.PRODUCT:                        Galaxy series, misc. (tethering mode)
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.2/0000:02:00.0/usb1/1-1/1-1:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       bc06a0ad-df0b-34c4-bb99-60c7b6b5d22e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.42.25/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.42.129, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.42.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        dhcp_lease_time = 3600
DHCP4.OPTION[2]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[3]:                        expiry = 1603861107
DHCP4.OPTION[4]:                        host_name = stephen-desktop
DHCP4.OPTION[5]:                        ip_address = 192.168.42.25
DHCP4.OPTION[6]:                        next_server = 192.168.42.129
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_domain_name = 1
DHCP4.OPTION[9]:                        requested_domain_name_servers = 1
DHCP4.OPTION[10]:                       requested_domain_search = 1
DHCP4.OPTION[11]:                       requested_host_name = 1
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[14]:                       requested_nis_domain = 1
DHCP4.OPTION[15]:                       requested_nis_servers = 1
DHCP4.OPTION[16]:                       requested_ntp_servers = 1
DHCP4.OPTION[17]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[18]:                       requested_root_path = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_static_routes = 1
DHCP4.OPTION[21]:                       requested_subnet_mask = 1
DHCP4.OPTION[22]:                       requested_time_offset = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       routers = 192.168.42.129
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::a1ac:e68:de2c:cd44/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bc06a0ad-df0b-34c4-bb99-60c7b6b5d22e | Wired connection 1

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: Permission denied

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

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

usb0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/5.4.0-52-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:master:8794:f51dd362
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     CF490DA33510941E267022A
depends:        compat
retpoline:      Y
name:           cfg80211
vermagic:       5.4.0-52-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
“options iwlwifi disable_msix=1”

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  107.159804] rndis_host 1-1:1.0 usb0: register 'rndis_host' at usb-0000:02:00.0-1, RNDIS device, <MAC 'usb0' [IF1]>

########## wireless info END ############
```

---

### Post by morrownr on 2020-10-28
You have an adapter with a Realtek 8812bu chipset.

Go here:

[https://github.com/morrownr/88x2bu](https://github.com/morrownr/88x2bu)

Scroll down to the README. Following the installation instructions. Let us know if there is anything you don't understand or if anything goes wrong.

Good luck.

---

