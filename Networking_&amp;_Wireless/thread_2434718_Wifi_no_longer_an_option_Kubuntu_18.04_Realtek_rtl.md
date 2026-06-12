---
title: "Wifi no longer an option Kubuntu 18.04 Realtek rtl8812au driver"
date: 2020-01-09
forum: Networking &amp; Wireless
---

### Post by chcis on 2020-01-09
I've been using this wifi adapter for about 6 months.  Dkms doesn't work very well with kernel upgrades but reinstalling the driver isn't that much of an issue.  However, this morning I had no option for wifi.  The adapter shows up in lsusb and works in another computer but not in this one.  Lshw -C network only shows my wired interface. I've been googling all morning and have tried the stuff on [this page]("https://askubuntu.com/questions/1038242/no-wifi-option-on-ubuntu-18-04-and-16-04") but no joy.  Wireless-info below.  Any ideas?

```


########## wireless info START ##########


Report from: 09 Jan 2020 14:58 EST -0500


Booted last: 09 Jan 2020 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, recovery, nomodeset


##### desktop ###########################


Plasma


##### lspci #############################


libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '“options'


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7596]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04d9:fa56 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


cfg80211              675840  0
compat                 20480  1 cfg80211
wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof


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
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.1.17/24 brd 192.168.1.255 scope global dynamic noprefixroute enp2s0
       valid_lft 85232sec preferred_lft 85232sec
    inet6 fe80::209e:13f7:ddf:f877/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


default via 192.168.1.1 dev enp2s0 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.1.0/24 dev enp2s0 proto kernel scope link src 192.168.1.17 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1263     1  0 14:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       2fb6b7df-77ec-317b-8320-a9ed69a4f64e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.17/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_ntp_servers = 1
DHCP4.OPTION[3]:                        requested_domain_search = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       expiry = 1578685137
DHCP4.OPTION[11]:                       next_server = 0.0.0.0
DHCP4.OPTION[12]:                       requested_wpad = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_lease_time = 86400
DHCP4.OPTION[17]:                       requested_subnet_mask = 1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       ip_address = 192.168.1.17
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::209e:13f7:ddf:f877/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2fb6b7df-77ec-317b-8320-a9ed69a4f64e | Wired connection 1


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


[[/etc/NetworkManager/system-connections/Moto G (5) Plus 8613]] (600 root)
[connection] id=Moto G (5) Plus 8613 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Moto G (5) Plus 8613
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR00]] (600 root)
[connection] id=NETGEAR00 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR00
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005-e2bcd796-56e5-4638-b174-b15db1547a55]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
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


enp2s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.15.0-74-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:master:8324:9176b151
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     85C762B91466B7F2749B25C
depends:        compat
retpoline:      Y
name:           cfg80211
vermagic:       4.15.0-74-generic SMP mod_unload 
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
“options iwlwifi disable_msix=1”


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   24.437638] iwlwifi-stack-public:master:8324:9176b151
[   24.958980] 8812au: version magic '4.15.0-72-generic SMP mod_unload ' should be '4.15.0-74-generic SMP mod_unload '
[   86.263029] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   86.436204] r8169 0000:02:00.0 enp2s0: link down (repeated 2 times)
[   86.436325] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   89.649439] r8169 0000:02:00.0 enp2s0: link up
[   89.649455] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2020-01-09
It looks like you installed backport-iwlwifi or backport-iwlwifi-dkms and that is part of the problem, you also have had a kernel update since you last reinstalled rtl8812au-dkms.  After getting rid of backport-iwlwifi and reinstalling rtl8812au-dkms do
```
gedit admin:///usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

Change the line that begins with MAKE to
```
MAKE="'make' all KVER=${kernelver}"
```
Save and exit and it should work for kernel updates again

---

### Post by chcis on 2020-01-09
Thanks for the help. Despite having used kubuntu for 12 years, I don't really understand a lot of the behind the scenes stuff.  So I think I've done what you suggested, but I'm not sure.  It's still not working so I did a new wireless-info. I appreciate any further suggestions.

```


########## wireless info START ##########


Report from: 09 Jan 2020 20:00 EST -0500


Booted last: 09 Jan 2020 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Plasma


##### lspci #############################


libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 8: ignoring bad line starting with '“options'


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7596]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04d9:fa56 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


cfg80211              622592  0
wmi_bmof               16384  0
wmi                    24576  1 wmi_bmof


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
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
    inet 192.168.1.17/24 brd 192.168.1.255 scope global dynamic noprefixroute enp2s0
       valid_lft 86122sec preferred_lft 86122sec
    inet6 fe80::209e:13f7:ddf:f877/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


enp2s0    no wireless extensions.


##### route #############################


default via 192.168.1.1 dev enp2s0 proto dhcp metric 100 
169.254.0.0/16 dev enp2s0 scope link metric 1000 
192.168.1.0/24 dev enp2s0 proto kernel scope link src 192.168.1.17 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


    NetworkManager


Running:


root       889     1  0 19:53 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       2fb6b7df-77ec-317b-8320-a9ed69a4f64e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.17/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        expiry = 1578704162
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       ip_address = 192.168.1.17
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::209e:13f7:ddf:f877/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2fb6b7df-77ec-317b-8320-a9ed69a4f64e | Wired connection 1


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


[[/etc/NetworkManager/system-connections/Moto G (5) Plus 8613]] (600 root)
[connection] id=Moto G (5) Plus 8613 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Moto G (5) Plus 8613
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR00]] (600 root)
[connection] id=NETGEAR00 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR00
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005-e2bcd796-56e5-4638-b174-b15db1547a55]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
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


enp2s0    no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp2s0    Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.15.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8074B69894BD60D7367507A
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-74-generic SMP mod_unload 
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
“options iwlwifi disable_msix=1”


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   24.985869] 8812au: version magic '4.15.0-72-generic SMP mod_unload ' should be '4.15.0-74-generic SMP mod_unload '
[   37.118823] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   37.356104] r8169 0000:02:00.0 enp2s0: link down
[   37.356222] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  193.541666] r8169 0000:02:00.0 enp2s0: link up
[  193.541680] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


########## wireless info END ############



```

---

### Post by jeremy31 on 2020-01-10
Edit /etc/modprobe.d/iwlwifi.conf and remove the line in quotes.  Then do ```
sudo dkms reinstall rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
```
Reboot

---

### Post by chcis on 2020-01-10
Didn't work.  I removed that line in [COLOR=#000000]iwlwifi.conf[/COLOR] and copy and pasted the command and got the following result.

```
[FONT=monospace][COLOR=#000000]Warning: I do not know how to handle rtl8812au/4.3.8.12175.20140902+dfsg.[/COLOR]
Usage: /usr/sbin/dkms [action] [options]
  [action]  = { add | remove | build | install | uninstall | match | autoinstall
               | mkdriverdisk | mktarball | ldtarball | mkrpm | mkkmp | mkdeb | mkbmdeb | status }
  [options] = [-m module] [-v module-version] [-k kernel-version] [-a arch]
              [-d distro] [-c dkms.conf-location] [-q] [--force] [--force-version-override] [--all]
              [--templatekernel=kernel] [--directive='cli-directive=cli-value']
              [--config=kernel-.config-location] [--archive=tarball-location]
              [--kernelsourcedir=source-location] [--no-prepare-kernel] [--no-initrd]
              [--binaries-only] [--source-only] [-r release (SuSE)] [--verbose]
              [--size] [--spec=specfile] [--media=floppy|iso|tar] [--legacy-postinst=0|1]
              [--no-depmod]
              [-j number]
Error! No action was specified.
[/FONT]
```

---

### Post by jeremy31 on 2020-01-10
Ok try
```
sudo dkms uninstall rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
sudo dkms install rtl8812au/4.3.8.12175.20140902+dfsg -k $(uname -r)
```
Then reboot

---

### Post by chcis on 2020-01-10
Okay, did that, still got nothing.  Still shows no options if it's not plugged in.

```


########## wireless info START ##########


Report from: 10 Jan 2020 19:51 EST -0500


Booted last: 10 Jan 2020 00:00 EST -0500


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.3 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Plasma


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7596]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 1058:0748 Western Digital Technologies, Inc. My Passport (WDBKXH, WDBY8L)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 04d9:fa56 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


'mokutil' is not installed (package "mokutil").


##### lsmod #############################


wmi_bmof               16384  0
cfg80211              622592  0
wmi                    24576  1 wmi_bmof


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
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0


##### network managers ##################


Installed:


	NetworkManager


Running:


root       894     1  0 19:47 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:05.0/0000:02:00.0/net/enp2s0
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


[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Moto G (5) Plus 8613]] (600 root)
[connection] id=Moto G (5) Plus 8613 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Moto G (5) Plus 8613
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR00]] (600 root)
[connection] id=NETGEAR00 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR00
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/NETGEAR005-e2bcd796-56e5-4638-b174-b15db1547a55]] (600 root)
[connection] id=NETGEAR005 | type=wifi | permissions=user:primary:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR005
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


enp2s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/4.15.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8074B69894BD60D7367507A
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-74-generic SMP mod_unload 
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


[   23.345418] 8812au: version magic '4.15.0-72-generic SMP mod_unload ' should be '4.15.0-74-generic SMP mod_unload '
[   35.851460] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   36.152155] r8169 0000:02:00.0 enp2s0: link down
[   36.152291] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready


########## wireless info END ############



```

---

### Post by SeijiSensei on 2020-01-11
Any chance you accidentally turned off the wifi with a keystroke command? I've done that on my HP laptop from time to time.

---

### Post by jeremy31 on 2020-01-11
See if it works after ```
sudo modprobe -f 8812au
```

---

### Post by chcis on 2020-01-11
I'm on a desktop and I'm not aware of any f keys to turn off wifi.  Do you know of one?

> **jeremy31 said:**
> See if it works after ```
sudo modprobe -f 8812au
```

Results:

```
[FONT=monospace][COLOR=#000000]sudo modprobe -f 8812au[/COLOR]
[sudo] password for main:  
modprobe: ERROR: could not insert '8812au': Exec format error
[/FONT]
```

---

### Post by jeremy31 on 2020-01-11
```
sudo sed -i 's/4.15.0-72-generic/4.15.0-74-generic/' /lib/modules/4.15.0-74-generic/updates/dkms/8812au.ko
```
Reboot

---

### Post by chcis on 2020-01-11
Hit all the function keys, no joy.

---

### Post by chcis on 2020-01-11
> **jeremy31 said:**
> ```
sudo sed -i 's/4.15.0-72-generic/4.15.0-74-generic/' /lib/modules/4.15.0-74-generic/updates/dkms/8812au.ko
```
Reboot

YOU ARE A GENIUS!  Thank you so much!

---

### Post by jeremy31 on 2020-01-11
Post result for ```
cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

---

### Post by chcis on 2020-01-11
> **jeremy31 said:**
> Post result for ```
cat /usr/src/rtl8812au-4.3.8.12175.20140902+dfsg/dkms.conf
```

I think we cross posted but just in case...

```
[FONT=monospace][COLOR=#000000]PACKAGE_NAME="rtl8812au"[/COLOR]
PACKAGE_VERSION="4.3.8.12175.20140902+dfsg"
BUILT_MODULE_NAME[0]="8812au"
MAKE="'make' all KVER=${kernelver}"
CLEAN="'make' clean"
DEST_MODULE_LOCATION[0]="/updates/dkms"
AUTOINSTALL="YES"

[/FONT]
```

---

### Post by jeremy31 on 2020-01-11
You should be good for the next kernel update

---

### Post by chcis on 2020-01-11
I really appreciate your help.

---

