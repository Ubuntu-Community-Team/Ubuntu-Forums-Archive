---
title: "Ubuntu still using blacklisted USB WiFi driver"
date: 2024-06-25
forum: Networking &amp; Wireless
---

### Post by kx92 on 2024-06-25
I have an Lubuntu installation version 22 LTS (VM) which accesses internet seamlessly on an external TP-LINK T3U ARCHER. [COLOR=#008000]driver=rtl88x2bu driverversion=5.15.0-112-generic[/COLOR]
It originally [COLOR=#ff0000]did not work[/COLOR] with this WiFi adapter, but after trying many things long back, eventually it started working fine and I now have no idea exactly what made it work right like this.

However I am planning to move over to Ubuntu version 22 LTS, but it is facing the same issues with the above mentioned WiFi adapter. [COLOR=#ff0000]driver=rtw_8822bu driverversion=6.5.0-41-generic 
[/COLOR]
I have tried installing the same [COLOR=#008000]rtl88x2bu [/COLOR](a newer version), but Ubuntu still persistently uses the [COLOR=#ff0000]rtw_8822bu[/COLOR] driver whenever this USB WiFi adapter is connected to the VM.
I blacklisted this driver, but Ubuntu still ignores the blacklist and proceeds with using it instead of [COLOR=#008000]rtl88x2bu[/COLOR] which I want.

Please help with a solution.

---

### Post by jeremy31 on 2024-06-25
See the wireless script link in my signature and post results

---

### Post by kx92 on 2024-06-25
```
########## wireless info START ##########

Report from: 25 Jun 2024 22:36 IST +0530

Booted last: 25 Jun 2024 00:00 IST +0530

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 6.5.0-41-generic #41~22.04.2-Ubuntu SMP PREEMPT_DYNAMIC Mon Jun  3 11:32:55 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

02:01.0 Ethernet controller [0200]: Intel Corporation 82545EM Gigabit Ethernet Controller (Copper) [8086:100f] (rev 01)
    DeviceName: Ethernet0
    Subsystem: VMware PRO/1000 MT Single Port Adapter [15ad:0750]

##### lsusb #############################

Bus 002 Device 002: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 003: ID 2357:012d TP-Link Archer T3U [Realtek RTL8812BU]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 001 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

EFI variables are not supported on this system

##### lsmod #############################

mac80211             1724416  2 rtw88_core,rtw88_usb
cfg80211             1323008  3 88x2bu,rtw88_core,mac80211
libarc4                12288  1 mac80211

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'ens33' [IF1]> brd <MAC address>
    altname enp2s1
    inet 192.168.2.6/24 brd 192.168.2.255 scope global dynamic noprefixroute ens33
       valid_lft 85004sec preferred_lft 85004sec
    inet6 fe80::184f:b316:ae24:bc05/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlx<IF from MAC [IF2]>: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.0.110/24 brd 192.168.0.255 scope global dynamic noprefixroute wlx<IF from MAC [IF2]>
       valid_lft 86366sec preferred_lft 86366sec
    inet6 2406:7400:56:ce94:5784:976e:729e:e883/64 scope global temporary dynamic 
       valid_lft 294sec preferred_lft 114sec
    inet6 2406:7400:56:ce94:b4d8:c2f2:1e9:7f7/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 294sec preferred_lft 114sec
    inet6 fe80::7c4c:dddf:553f:4f72/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

ens33     no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.0.1 dev wlx<IF from MAC [IF2]> proto dhcp metric 600 linkdown 
default via 192.168.2.2 dev ens33 proto dhcp metric 20100 
169.254.0.0/16 dev ens33 scope link metric 1000 
192.168.0.0/24 dev wlx<IF from MAC [IF2]> proto kernel scope link src 192.168.0.110 metric 600 linkdown 
192.168.2.0/24 dev ens33 proto kernel scope link src 192.168.2.6 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search localdomain

##### network managers ##################

Installed:

    NetworkManager

Running:

root         768       1  0 22:13 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         TP-Link
GENERAL.PRODUCT:                        Archer T3U [Realtek RTL8812BU]
GENERAL.DRIVER:                         rtw_8822bu
GENERAL.DRIVER-VERSION:                 6.5.0-41-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb2/2-1/2-1:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.PATH:                           pci-0000:02:03.0-usb-0:1:1.0
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     My_SSID
GENERAL.CON-UUID:                       a586420c-a64f-4c78-9be6-068e2fe18269
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/10
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     780 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
INTERFACE-FLAGS.PROMISC:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               no
IP4.ADDRESS[1]:                         192.168.0.110/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             49.205.72.130
IP4.DNS[2]:                             183.82.243.66
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[3]:                        domain_name_servers = 49.205.72.130 183.82.243.66
DHCP4.OPTION[4]:                        expiry = 1719421584
DHCP4.OPTION[5]:                        ip_address = 192.168.0.110
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        requested_domain_name_servers = 1
DHCP4.OPTION[9]:                        requested_domain_search = 1
DHCP4.OPTION[10]:                       requested_host_name = 1
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[13]:                       requested_nis_domain = 1
DHCP4.OPTION[14]:                       requested_nis_servers = 1
DHCP4.OPTION[15]:                       requested_ntp_servers = 1
DHCP4.OPTION[16]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_root_path = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       requested_subnet_mask = 1
DHCP4.OPTION[21]:                       requested_time_offset = 1
DHCP4.OPTION[22]:                       requested_wpad = 1
DHCP4.OPTION[23]:                       routers = 192.168.0.1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2406:7400:56:ce94:5784:976e:729e:e883/64
IP6.ADDRESS[2]:                         2406:7400:56:ce94:b4d8:c2f2:1e9:7f7/64
IP6.ADDRESS[3]:                         fe80::7c4c:dddf:553f:4f72/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = 2406:7400:56:ce94::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 1024
IP6.DNS[1]:                             2406:7400:a:10::2
IP6.DNS[2]:                             2406:7400:b0:b::2
DHCP6.OPTION[1]:                        dhcp6_name_servers = 2406:7400:a:10::2 2406:7400:b0:b::2
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a586420c-a64f-4c78-9be6-068e2fe18269 | My_SSID

GENERAL.DEVICE:                         ens33
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82545EM Gigabit Ethernet Controller (Copper) (PRO/1000 MT Single Port Adapter)
GENERAL.DRIVER:                         e1000
GENERAL.DRIVER-VERSION:                 6.5.0-41-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'ens33' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               3 (limited)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:11.0/0000:02:01.0/net/ens33
GENERAL.PATH:                           pci-0000:02:01.0
GENERAL.IP-IFACE:                       ens33
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       2040bd46-ee74-3681-8400-d5467fbb2cf9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
INTERFACE-FLAGS.PROMISC:                no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.2.6/24
IP4.GATEWAY:                            192.168.2.2
IP4.ROUTE[1]:                           dst = 192.168.2.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[2]:                           dst = 0.0.0.0/0, nh = 192.168.2.2, mt = 20100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.2
IP4.DOMAIN[1]:                          localdomain
DHCP4.OPTION[1]:                        broadcast_address = 192.168.2.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_server_identifier = 192.168.2.9
DHCP4.OPTION[4]:                        domain_name = localdomain
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.2.2
DHCP4.OPTION[6]:                        expiry = 1719420220
DHCP4.OPTION[7]:                        ip_address = 192.168.2.6
DHCP4.OPTION[8]:                        next_server = 192.168.2.9
DHCP4.OPTION[9]:                        requested_broadcast_address = 1
DHCP4.OPTION[10]:                       requested_domain_name = 1
DHCP4.OPTION[11]:                       requested_domain_name_servers = 1
DHCP4.OPTION[12]:                       requested_domain_search = 1
DHCP4.OPTION[13]:                       requested_host_name = 1
DHCP4.OPTION[14]:                       requested_interface_mtu = 1
DHCP4.OPTION[15]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_nis_domain = 1
DHCP4.OPTION[17]:                       requested_nis_servers = 1
DHCP4.OPTION[18]:                       requested_ntp_servers = 1
DHCP4.OPTION[19]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_root_path = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       requested_static_routes = 1
DHCP4.OPTION[23]:                       requested_subnet_mask = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       routers = 192.168.2.2
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::184f:b316:ae24:bc05/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 1024
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/3
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2040bd46-ee74-3681-8400-d5467fbb2cf9 | Wired connection 1

SSID               BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
My_SSID  <MAC 'My_SSID' [AN1]>  Infra  36    5180 MHz  270 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no             
My_SSID_G    <MAC 'My_SSID_G' [AN2]>  Infra  1     2412 MHz  270 Mbit/s  87      &#9602;&#9604;&#9606;&#9608;  WPA2       no             

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
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com./

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/My_SSID.nmconnection]] (600 root)
[connection] id=My_SSID | type=wifi
[wifi] ssid=My_SSID
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/My_SSID_G.nmconnection]] (600 root)
[connection] id=My_SSID_G | type=wifi
[wifi] ssid=My_SSID_G
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

lo        no frequency information.

ens33     no frequency information.

wlx<IF from MAC [IF2]>  32 channels in total; available frequencies :
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

ens33     Interface doesn't support scanning.

wlx<IF from MAC [IF2]>  Failed to read scan data : Resource temporarily unavailable

##### module infos ######################

[mac80211]
filename:       /lib/modules/6.5.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       6.5.0-41-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/6.5.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.5.0-41-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

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
blacklist rtw_8822bu

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

[  931.504548] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:b4d8:c2f2:1e9:7f7 on wlx<IF from MAC [IF2]>!
[  931.616303] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:33d7:53c2:486e:1e84 on wlx<IF from MAC [IF2]>!
[ 1044.451504] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1053.303773] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1058.316430] wlx<IF from MAC [IF2]>: aborting authentication with <MAC 'My_SSID' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1087.024734] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1095.845852] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1096.096548] wlx<IF from MAC [IF2]>: authenticated
[ 1096.100966] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1096.111721] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1096.305513] wlx<IF from MAC [IF2]>: associated
[ 1125.565381] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1134.407059] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1135.172071] wlx<IF from MAC [IF2]>: authenticated
[ 1135.180412] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1135.786718] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1135.986818] wlx<IF from MAC [IF2]>: associated
[ 1138.569587] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address fe80::7c4c:dddf:553f:4f72 on wlx<IF from MAC [IF2]>!
[ 1143.679307] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:4433:b748:8c6:b259 on wlx<IF from MAC [IF2]>!
[ 1144.377959] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:b4d8:c2f2:1e9:7f7 on wlx<IF from MAC [IF2]>!
[ 1167.783741] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1176.559101] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1177.356202] wlx<IF from MAC [IF2]>: authenticated
[ 1177.364095] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1178.436033] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 2/3)
[ 1179.460494] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 3/3)
[ 1180.421875] wlx<IF from MAC [IF2]>: association with <MAC 'My_SSID' [AN1]> timed out
[ 1201.958340] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1210.784268] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1211.004802] wlx<IF from MAC [IF2]>: authenticated
[ 1211.007210] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1211.308771] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1211.504210] wlx<IF from MAC [IF2]>: associated
[ 1226.118079] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:b4d8:c2f2:1e9:7f7 on wlx<IF from MAC [IF2]>!
[ 1226.472027] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:7ee8:94dc:9181:a0b9 on wlx<IF from MAC [IF2]>!
[ 1327.502668] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1336.282317] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1337.208040] wlx<IF from MAC [IF2]>: authenticated
[ 1337.209799] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1337.922183] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1338.116579] wlx<IF from MAC [IF2]>: associated
[ 1371.766768] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1380.558778] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1381.376742] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 2/3)
[ 1381.379303] wlx<IF from MAC [IF2]>: authenticated
[ 1381.382855] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1382.370922] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 2/3)
[ 1382.391772] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1382.656606] wlx<IF from MAC [IF2]>: associated
[ 1388.361410] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address fe80::7c4c:dddf:553f:4f72 on wlx<IF from MAC [IF2]>!
[ 1393.116866] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:b4d8:c2f2:1e9:7f7 on wlx<IF from MAC [IF2]>!
[ 1394.413337] ICMPv6: NA: <MAC 'wlx<IF from MAC [IF2]>' [IF2]> advertised our address 2406:7400:56:ce94:5784:976e:729e:e883 on wlx<IF from MAC [IF2]>!
[ 1398.440326] wlx<IF from MAC [IF2]>: deauthenticated from <MAC 'My_SSID' [AN1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[ 1399.129202] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1407.867102] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1408.142715] wlx<IF from MAC [IF2]>: authenticated
[ 1408.145273] wlx<IF from MAC [IF2]>: associate with <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1408.447553] wlx<IF from MAC [IF2]>: RX AssocResp from <MAC 'My_SSID' [AN1]> (capab=0x11 status=0 aid=3)
[ 1408.645325] wlx<IF from MAC [IF2]>: associated
[ 1434.618230] wlx<IF from MAC [IF2]>: authenticate with <MAC 'My_SSID' [AN1]>
[ 1443.610392] wlx<IF from MAC [IF2]>: send auth to <MAC 'My_SSID' [AN1]> (try 1/3)
[ 1448.614218] wlx<IF from MAC [IF2]>: aborting authentication with <MAC 'My_SSID' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############
```

---

### Post by jeremy31 on 2024-06-25
Try ```
echo "blacklist rtw88_8822bu"| sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by kx92 on 2024-06-26
Awesome! Your suggestion has resolved my issue. That driver is now blacklisted as expected and now my WiFi adapter is currently using this driver.
[COLOR=#008000]driver=rtl88x2bu driverversion=v5.13.1-20

[/COLOR]Thank you so much for the solution.
Although this is an older version than the one on Lubuntu, it initially seemed to work just as fine. However in further testing, it is observed that this is not reliable as it will not re-connect if I connect with another WiFi USB adapter, and then switch back to the TP-LINK T3U ARCHER.

Rebooting the Ubuntu OS also did not fix it.

---

### Post by kx92 on 2024-06-26
From what I recall, there were a few newer versions of [COLOR=#008000]driver=rtl88x2bu[/COLOR] already installed in this Ubuntu VM installation.

Requesting you to please share the command to list them out and then another command to force Ubuntu to use a specific driver version with this USB WiFi adapter?

---

### Post by jeremy31 on 2024-06-26
```
dkms status
```
Might show others but they should have shown in script results.  Maybe ```
modprobe -c | grep 2357 | grep -i 012d
```
Will show something more than the script did

---

