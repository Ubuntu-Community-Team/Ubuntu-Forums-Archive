---
title: "Lenovo G580 &amp; ubuntu 18.04 LTS no wifi :("
date: 2018-06-07
forum: Networking &amp; Wireless
---

### Post by koza2 on 2018-06-07
Hello, recently I decided to enrich my laptop with ubuntu, my choice is Ubuntu 18.04 LTS. Unfortunately, I have the message No wifi adapters found.

I watch
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
and
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)
unfortunately, nothing else works :(

Information from "wireless-info"

```

########## wireless info START ##########

Report from: 07 Jun 2018 18:00 CEST +0200

Booted last: 07 Jun 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Lenovo AR8162 Fast Ethernet [17aa:3979]
    Kernel driver in use: alx

03:00.0 Network controller [0280]: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter [14e4:0587]
    Kernel modules: bcma, wl

##### lsusb #############################

Bus 002 Device 003: ID 5986:0295 Acer, Inc 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 0489:e032 Foxconn / Hon Hai Broadcom BCM20702 Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 03f0:a407 Hewlett-Packard 
Bus 003 Device 002: ID 13fe:3e00 Kingston Technology Company Inc. Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ideapad_laptop         32768  0
cfg80211              622592  0
sparse_keymap          16384  1 ideapad_laptop
mxm_wmi                16384  1 nouveau
wmi                    24576  3 mxm_wmi,nouveau,ideapad_laptop
video                  40960  3 nouveau,i915,ideapad_laptop

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.0.164/24 brd 192.168.0.255 scope global dynamic noprefixroute enp2s0
       valid_lft 3536sec preferred_lft 3536sec
    inet6 fe80::c388:9016:b52c:aed1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

##### route #############################

default via 192.168.0.1 dev enp2s0 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.0.0/24 dev enp2s0 proto kernel scope link src 192.168.0.164 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       799     1  0 17:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8162 Fast Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       ed8395f2-1e5c-3551-b942-fea15f5e2307
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.164/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             62.179.1.61
IP4.DNS[2]:                             62.179.1.63
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        domain_name = home
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        host_name = koza-Lenovo-G580
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       expiry = 1528390753
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_interface_mtu = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.164
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 3600
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       domain_name_servers = 62.179.1.61 62.179.1.63
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_routers = 1
DHCP4.OPTION[26]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       requested_host_name = 1
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[30]:                       default_ip_ttl = 64
IP6.ADDRESS[1]:                         fe80::c388:9016:b52c:aed1/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ed8395f2-1e5c-3551-b942-fea15f5e2307 | Wired connection 1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/skankolor]] (600 root)
[connection] id=skankolor | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=skankolor
[ipv4] method=auto
[ipv6] method=auto

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
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp2s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp2s0    Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.15.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-22-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
blacklist b43
blacklist ssb

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   24.865748] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   28.912945] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0489-e032.hcd failed with error -2
[   28.912948] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0489-e032.hcd not found
[   39.314761] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready (repeated 2 times)
[  222.432670] alx 0000:02:00.0 enp2s0: NIC Up: 100 Mbps Full
[  222.433344] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

########## wireless info END ############


```

Thanks


EDIT: Found solution need to remove this package
```
bcmwl-kernel-source
```

---

