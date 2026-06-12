---
title: "Typical Broadcom BCM43142 802.11b/g/n [14e4:4365] (rev 01) in Ubuntu 20.04"
date: 2020-06-21
forum: Networking &amp; Wireless
---

### Post by kyorosuke on 2020-06-21
Well, tha same problem in Ubuntu 20.04, i need help...

This the output of lspci

 ```

07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)

```

This is the output of wireless-info.txt

```

########## wireless info START ##########

Report from: 21 Jun 2020 01:16 -03 -0300

Booted last: 21 Jun 2020 00:00 -03 -0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
    Kernel driver in use: wl

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Toshiba Corporation RTL810xE PCI Express Fast Ethernet controller [1179:f840]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd TOSHIBA Web Camera - HD
Bus 002 Device 002: ID 0930:0225 Toshiba Corp. BCM43142A0
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wl                   6455296  0
wmi_bmof               16384  0
cfg80211              704512  1 wl
wmi                    32768  2 toshiba_acpi,wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
    inet 192.168.0.94/24 brd 192.168.0.255 scope global dynamic noprefixroute enp8s0
       valid_lft 84270sec preferred_lft 84270sec
    inet6 2804:14d:8084:93c6::1008/128 scope global dynamic noprefixroute 
       valid_lft 84275sec preferred_lft 84275sec
    inet6 2804:14d:8084:93c6:85d5:91e4:acaf:72d7/64 scope global temporary dynamic 
       valid_lft 86373sec preferred_lft 71973sec
    inet6 2804:14d:8084:93c6:70be:4d8b:1f50:fd1e/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 86373sec preferred_lft 71973sec
    inet6 fe80::ded9:bfbd:274d:9415/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp8s0    no wireless extensions.

lo        no wireless extensions.

wlp7s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.0.1 dev enp8s0 proto dhcp metric 100 
169.254.0.0/16 dev enp8s0 scope link metric 1000 
192.168.0.0/24 dev enp8s0 proto kernel scope link src 192.168.0.94 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

    NetworkManager

Running:

root         703       1  0 00:40 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       7e6a2163-028a-32af-8543-a9ba19ac0bd6
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.94/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             189.7.80.22
IP4.DNS[2]:                             189.7.80.42
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        domain_name_servers = 189.7.80.22 189.7.80.42
DHCP4.OPTION[3]:                        expiry = 1592797260
DHCP4.OPTION[4]:                        ip_address = 192.168.0.94
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_domain_name_servers = 1
DHCP4.OPTION[8]:                        requested_domain_search = 1
DHCP4.OPTION[9]:                        requested_host_name = 1
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[12]:                       requested_nis_domain = 1
DHCP4.OPTION[13]:                       requested_nis_servers = 1
DHCP4.OPTION[14]:                       requested_ntp_servers = 1
DHCP4.OPTION[15]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_root_path = 1
DHCP4.OPTION[17]:                       requested_routers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_subnet_mask = 1
DHCP4.OPTION[20]:                       requested_time_offset = 1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       routers = 192.168.0.1
DHCP4.OPTION[23]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2804:14d:8084:93c6::1008/128
IP6.ADDRESS[2]:                         2804:14d:8084:93c6:85d5:91e4:acaf:72d7/64
IP6.ADDRESS[3]:                         2804:14d:8084:93c6:70be:4d8b:1f50:fd1e/64
IP6.ADDRESS[4]:                         fe80::ded9:bfbd:274d:9415/64
IP6.GATEWAY:                            fe80::966a:77ff:fe25:70f9
IP6.ROUTE[1]:                           dst = 2804:14d:8084:93c6::/64, nh = fe80::966a:77ff:fe25:70f9, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::966a:77ff:fe25:70f9, mt = 20100
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = 2804:14d:8084:93c6::1008/128, nh = ::, mt = 100
IP6.DNS[1]:                             2804:14d:1:0:181:213:132:2
IP6.DNS[2]:                             2804:14d:1:0:181:213:132:3
DHCP6.OPTION[1]:                        dhcp6_name_servers = 2804:14d:1:0:181:213:132:2 2804:14d:1:0:181:213:132:3
DHCP6.OPTION[2]:                        ip6_address = 2804:14d:8084:93c6::1008
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7e6a2163-028a-32af-8543-a9ba19ac0bd6 | Conexión cableada 1

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Broadcom Inc. and subsidiaries
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/wlp7s0
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
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Sao_Paulo (based on set time zone)

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

enp8s0    no frequency information.

lo        no frequency information.

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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

enp8s0    Interface doesn't support scanning.

wlp7s0    Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/5.4.0-37-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
license:        MIXED/Proprietary
srcversion:     6F850B860170BC76E1ADCC3
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.4.0-37-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         ubuntu Secure Boot Module Signature key
sig_key:        75:43:C0:AE:00:EC:FB:7D:2B:06:1D:D4:EF:14:48:AC:E0:42:57:D1
sig_hashalgo:   sha512
signature:      2A:2C:10:74:01:54:50:1E:7A:17:E1:B4:B3:75:77:4C:D8:DA:A5:5D:
        40:BC:8A:B2:7F:83:33:23:E7:E2:01:F0:EB:11:E5:06:C3:63:F5:99:
        8D:17:97:FC:EB:4D:8E:51:B5:73:3E:4B:97:09:C0:91:82:75:C7:8F:
        FE:A6:0B:1A:92:7C:B4:75:52:77:60:94:77:EF:2E:6A:06:0E:0D:93:
        66:57:D0:62:AE:7E:53:8C:E4:8F:EB:9C:4A:EA:1E:5C:84:7F:BF:BE:
        58:B5:68:15:40:F9:30:41:9E:1B:3B:88:4F:5D:B2:0A:82:F8:60:54:
        CE:47:B9:53:CC:BB:1B:B9:9E:62:D8:CD:26:DF:3C:34:3F:77:76:CC:
        84:40:33:24:92:E1:9D:D5:A7:66:07:BD:FE:ED:DD:85:09:30:33:00:
        DF:EF:8A:47:2E:2F:CA:7E:EF:84:70:41:24:A4:16:3F:0F:B6:C2:2E:
        AC:9E:45:A7:31:77:24:D9:A0:1E:92:FE:97:A8:5C:FD:47:7A:FE:23:
        58:65:19:A1:25:7E:67:EA:5A:68:DE:8E:C5:D5:EF:EA:68:F0:36:D7:
        32:7E:86:EE:2A:85:8A:2E:55:AE:15:D4:E6:90:F2:74:03:01:F7:EF:
        F3:29:60:62:49:60:EB:0E:C6:2F:26:DC:9D:87:02:C8
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/5.4.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C806D0B3412B28507AE57E5
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-37-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        28:76:AD:92:E9:CE:4F:50:32:F3:D4:3E:98:97:7B:B4:F1:F8:92
sig_hashalgo:   sha512
signature:      61:52:83:66:E4:26:43:39:5E:73:B1:A6:9D:7F:70:05:51:F3:0C:2E:
        69:B4:17:79:9C:9E:E8:33:0B:FE:09:0F:A0:4B:3A:DE:91:D9:E4:78:
        FF:C5:A2:71:9B:A4:88:AF:E4:48:94:9E:15:A1:1B:AD:E0:7E:6C:D5:
        05:FE:75:9E:F3:21:88:B5:23:97:2C:AF:09:05:4B:1B:DC:92:9F:35:
        0C:14:2A:6B:79:58:7B:EA:F9:C7:4E:05:6C:14:31:CD:3C:21:75:F7:
        D7:CA:C4:05:EE:5D:04:F2:AC:11:D4:62:C4:31:05:F7:8A:B8:4B:C4:
        51:0B:11:CD:AA:68:1F:87:A7:19:57:CF:E7:F9:E2:28:B7:02:E7:67:
        5A:3E:72:24:50:ED:BA:61:81:55:E6:BB:BE:6B:DD:9D:70:55:56:A2:
        35:89:FE:8F:C2:96:97:4D:2F:E0:5A:D6:74:FF:23:43:92:99:77:69:
        94:0E:12:E3:34:4F:03:0B:35:8B:29:57:48:CD:6B:B2:12:D4:3F:0E:
        51:0B:58:9D:A1:98:8F:1D:D6:FA:69:3C:99:4C:DF:C5:86:DB:17:F2:
        78:8B:D7:74:67:EC:1B:B9:63:B2:DD:6F:1D:E1:BA:D9:E0:D2:C7:E9:
        F9:BF:6C:09:E2:1E:6D:B7:F0:CB:07:2D:4B:FF:9E:A2:8B:79:9D:F3:
        8C:A9:81:1B:48:4C:17:7B:54:62:0D:3E:AF:54:F3:43:DD:84:5F:EE:
        40:5D:95:79:EA:27:B8:AF:12:11:4E:24:D1:20:4B:44:48:1B:6D:CA:
        C9:5F:51:23:58:13:17:A2:32:81:DB:DA:1B:3E:59:16:2C:D4:1C:C6:
        AF:93:FC:68:E3:52:35:8C:17:DE:8D:10:EF:AF:FB:BB:97:C0:07:D8:
        C1:C6:68:89:D0:06:2E:20:95:C8:35:42:71:5B:3B:8B:52:DE:D8:FB:
        08:99:0C:D6:29:D3:BE:63:C4:07:B7:F2:EB:08:1C:94:7D:4E:75:2F:
        7B:6F:56:A9:55:39:05:1B:9D:2C:10:12:DE:57:AC:84:17:0B:2E:8A:
        3A:82:65:6F:01:BA:83:F5:29:69:D7:D4:F0:78:5F:7E:AA:75:76:07:
        27:D8:2F:73:D3:3A:B6:CD:17:D0:38:93:ED:11:65:E8:08:8F:E0:EB:
        F4:B9:C1:6D:58:F7:10:DC:95:9B:E7:19:7D:F1:59:57:41:2B:36:EF:
        51:A1:06:3C:1B:9F:BB:AB:96:7D:52:CD:BC:4D:69:26:76:4A:90:7E:
        F7:59:44:2D:01:6B:7F:5F:0E:29:56:46:6C:51:AE:3A:3E:7A:9C:36:
        54:0C:51:6A:8E:09:2F:84:73:96:7C:32
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

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

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

[   10.236013] wl: loading out-of-tree module taints kernel.
[   10.236018] wl: module license 'MIXED/Proprietary' taints kernel.
[   10.239752] wl: module verification failed: signature and/or required key missing - tainting kernel
[   10.272099] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.271 (r587334)
[   10.353577] wl 0000:07:00.0 wlp7s0: renamed from wlan0
[   10.984794] bluetooth hci0: Direct firmware load for brcm/BCM43142A0-0930-0225.hcd failed with error -2
[   10.984797] Bluetooth: hci0: BCM: Patch brcm/BCM43142A0-0930-0225.hcd not found
[   27.054937] r8169 0000:08:00.0 enp8s0: Link is Down
[   28.715000] r8169 0000:08:00.0 enp8s0: Link is Up - 100Mbps/Full - flow control rx/tx
[   28.715012] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready

########## wireless info END ############
```

Thanks in advance...

[UPDATE] I reinstalled Ubuntu 20.04, i have the same problem, this is my wireless-info.txt in a clean installation...

```

########## wireless info START ##########

Report from: 21 Jun 2020 16:36 -03 -0300

Booted last: 21 Jun 2020 00:00 -03 -0300

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal

##### kernel ############################

Linux 5.4.0-37-generic #41-Ubuntu SMP Wed Jun 3 18:57:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
	Kernel driver in use: wl

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Toshiba Corporation RTL810xE PCI Express Fast Ethernet controller [1179:f840]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 04f2:b446 Chicony Electronics Co., Ltd TOSHIBA Web Camera - HD
Bus 002 Device 002: ID 0930:0225 Toshiba Corp. BCM43142A0
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

wl                   6455296  0
cfg80211              704512  1 wl
wmi_bmof               16384  0
wmi                    32768  2 toshiba_acpi,wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
    inet 192.168.0.94/24 brd 192.168.0.255 scope global dynamic noprefixroute enp8s0
       valid_lft 86330sec preferred_lft 86330sec
    inet6 2804:14d:8084:93c6::100b/128 scope global dynamic noprefixroute 
       valid_lft 86331sec preferred_lft 86331sec
    inet6 2804:14d:8084:93c6:4d:669f:c6e2:5f71/64 scope global temporary dynamic 
       valid_lft 86380sec preferred_lft 71980sec
    inet6 2804:14d:8084:93c6:1da1:8d8d:abce:57a2/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 86380sec preferred_lft 71980sec
    inet6 2804:14d:8084:93c6:cc9b:fcd2:919f:6ac3/64 scope global temporary dynamic 
       valid_lft 86312sec preferred_lft 71912sec
    inet6 2804:14d:8084:93c6:cc7:e5d5:b16f:c7c4/64 scope global temporary dynamic 
       valid_lft 86311sec preferred_lft 71911sec
    inet6 fe80::f2ce:bd0b:f916:384d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether <MAC 'wlp7s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp8s0    no wireless extensions.

lo        no wireless extensions.

wlp7s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.0.1 dev enp8s0 proto dhcp metric 100 
169.254.0.0/16 dev enp8s0 scope link metric 1000 
192.168.0.0/24 dev enp8s0 proto kernel scope link src 192.168.0.94 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root       12982       1  0 16:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Conexión cableada 1
GENERAL.CON-UUID:                       4577df30-2221-34a7-bf5a-6f75b19c294d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.94/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.ROUTE[3]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.DNS[1]:                             189.7.80.22
IP4.DNS[2]:                             189.7.80.42
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        domain_name_servers = 189.7.80.22 189.7.80.42
DHCP4.OPTION[3]:                        expiry = 1592854531
DHCP4.OPTION[4]:                        ip_address = 192.168.0.94
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        requested_domain_name_servers = 1
DHCP4.OPTION[8]:                        requested_domain_search = 1
DHCP4.OPTION[9]:                        requested_host_name = 1
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[12]:                       requested_nis_domain = 1
DHCP4.OPTION[13]:                       requested_nis_servers = 1
DHCP4.OPTION[14]:                       requested_ntp_servers = 1
DHCP4.OPTION[15]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[16]:                       requested_root_path = 1
DHCP4.OPTION[17]:                       requested_routers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_subnet_mask = 1
DHCP4.OPTION[20]:                       requested_time_offset = 1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       routers = 192.168.0.1
DHCP4.OPTION[23]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         2804:14d:8084:93c6::100b/128
IP6.ADDRESS[2]:                         2804:14d:8084:93c6:4d:669f:c6e2:5f71/64
IP6.ADDRESS[3]:                         2804:14d:8084:93c6:cc7:e5d5:b16f:c7c4/64
IP6.ADDRESS[4]:                         2804:14d:8084:93c6:cc9b:fcd2:919f:6ac3/64
IP6.ADDRESS[5]:                         2804:14d:8084:93c6:1da1:8d8d:abce:57a2/64
IP6.ADDRESS[6]:                         fe80::f2ce:bd0b:f916:384d/64
IP6.GATEWAY:                            fe80::966a:77ff:fe25:70f9
IP6.ROUTE[1]:                           dst = 2804:14d:8084:93c6::/64, nh = fe80::966a:77ff:fe25:70f9, mt = 100
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::966a:77ff:fe25:70f9, mt = 20100
IP6.ROUTE[3]:                           dst = 2804:14d:8084:93c6::100b/128, nh = ::, mt = 100
IP6.ROUTE[4]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[5]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             2804:14d:1:0:181:213:132:2
IP6.DNS[2]:                             2804:14d:1:0:181:213:132:3
DHCP6.OPTION[1]:                        dhcp6_name_servers = 2804:14d:1:0:181:213:132:2 2804:14d:1:0:181:213:132:3
DHCP6.OPTION[2]:                        ip6_address = 2804:14d:8084:93c6::100b
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4577df30-2221-34a7-bf5a-6f75b19c294d | Conexión cableada 1

GENERAL.DEVICE:                         wlp7s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Broadcom Inc. and subsidiaries
GENERAL.PRODUCT:                        BCM43142 802.11b/g/n
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'wlp7s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/wlp7s0
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
INTERFACE-FLAGS.UP:                     no
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
WIFI-PROPERTIES.MESH:                   no
WIFI-PROPERTIES.IBSS-RSN:               no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 

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
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: America/Sao_Paulo (based on set time zone)

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

enp8s0    no frequency information.

lo        no frequency information.

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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

enp8s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp7s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[wl]
filename:       /lib/modules/5.4.0-37-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       5.4.0-37-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         ubuntu Secure Boot Module Signature key
sig_key:        79:72:DF:B8:6D:C6:4E:94:77:69:5E:E1:7F:FB:51:9B:30:7F:7D:79
sig_hashalgo:   sha512
signature:      AB:48:BD:CA:B5:2D:A7:10:06:66:74:89:E9:FC:DA:30:56:DF:27:25:
		F0:DC:E3:C6:98:23:5C:BF:F8:07:92:92:BA:3A:86:B1:B5:E1:1A:30:
		2C:15:AD:1C:0E:AB:9A:4B:62:38:7E:0D:39:1B:4B:F6:F7:AC:0B:9C:
		0E:D0:BA:3A:C4:E2:8F:FD:C2:9C:F0:41:35:28:FB:12:38:99:F2:66:
		B3:5D:EC:1E:54:C2:7C:2F:8D:A7:C5:35:D8:C3:20:87:A7:1F:AF:FE:
		55:BC:32:FC:D8:F8:2B:71:97:97:42:58:21:8D:BE:27:09:46:51:6B:
		E4:A7:3C:5E:72:21:2C:F3:F2:14:40:89:50:09:50:D0:55:58:34:CB:
		C4:B6:AF:72:F9:27:FE:0B:A1:69:BB:17:A9:03:62:54:71:90:99:34:
		5A:EE:1B:82:94:82:03:82:72:B5:79:CE:B8:05:A6:F2:05:07:F3:35:
		62:0A:67:4B:98:3C:53:59:AE:0A:05:0A:46:FC:8B:9C:75:A2:F7:FD:
		6A:FB:5F:D0:0E:E5:E0:43:24:F3:EE:D0:4D:52:E5:A5:4A:36:FD:53:
		AA:B0:6F:64:BE:61:4B:3C:38:9D:99:4E:9D:7B:E2:95:77:6A:59:4C:
		FC:D5:78:83:C0:61:F9:9C:5D:B6:53:BD:CF:17:43:E3
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/5.4.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C806D0B3412B28507AE57E5
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-37-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        28:76:AD:92:E9:CE:4F:50:32:F3:D4:3E:98:97:7B:B4:F1:F8:92
sig_hashalgo:   sha512
signature:      61:52:83:66:E4:26:43:39:5E:73:B1:A6:9D:7F:70:05:51:F3:0C:2E:
		69:B4:17:79:9C:9E:E8:33:0B:FE:09:0F:A0:4B:3A:DE:91:D9:E4:78:
		FF:C5:A2:71:9B:A4:88:AF:E4:48:94:9E:15:A1:1B:AD:E0:7E:6C:D5:
		05:FE:75:9E:F3:21:88:B5:23:97:2C:AF:09:05:4B:1B:DC:92:9F:35:
		0C:14:2A:6B:79:58:7B:EA:F9:C7:4E:05:6C:14:31:CD:3C:21:75:F7:
		D7:CA:C4:05:EE:5D:04:F2:AC:11:D4:62:C4:31:05:F7:8A:B8:4B:C4:
		51:0B:11:CD:AA:68:1F:87:A7:19:57:CF:E7:F9:E2:28:B7:02:E7:67:
		5A:3E:72:24:50:ED:BA:61:81:55:E6:BB:BE:6B:DD:9D:70:55:56:A2:
		35:89:FE:8F:C2:96:97:4D:2F:E0:5A:D6:74:FF:23:43:92:99:77:69:
		94:0E:12:E3:34:4F:03:0B:35:8B:29:57:48:CD:6B:B2:12:D4:3F:0E:
		51:0B:58:9D:A1:98:8F:1D:D6:FA:69:3C:99:4C:DF:C5:86:DB:17:F2:
		78:8B:D7:74:67:EC:1B:B9:63:B2:DD:6F:1D:E1:BA:D9:E0:D2:C7:E9:
		F9:BF:6C:09:E2:1E:6D:B7:F0:CB:07:2D:4B:FF:9E:A2:8B:79:9D:F3:
		8C:A9:81:1B:48:4C:17:7B:54:62:0D:3E:AF:54:F3:43:DD:84:5F:EE:
		40:5D:95:79:EA:27:B8:AF:12:11:4E:24:D1:20:4B:44:48:1B:6D:CA:
		C9:5F:51:23:58:13:17:A2:32:81:DB:DA:1B:3E:59:16:2C:D4:1C:C6:
		AF:93:FC:68:E3:52:35:8C:17:DE:8D:10:EF:AF:FB:BB:97:C0:07:D8:
		C1:C6:68:89:D0:06:2E:20:95:C8:35:42:71:5B:3B:8B:52:DE:D8:FB:
		08:99:0C:D6:29:D3:BE:63:C4:07:B7:F2:EB:08:1C:94:7D:4E:75:2F:
		7B:6F:56:A9:55:39:05:1B:9D:2C:10:12:DE:57:AC:84:17:0B:2E:8A:
		3A:82:65:6F:01:BA:83:F5:29:69:D7:D4:F0:78:5F:7E:AA:75:76:07:
		27:D8:2F:73:D3:3A:B6:CD:17:D0:38:93:ED:11:65:E8:08:8F:E0:EB:
		F4:B9:C1:6D:58:F7:10:DC:95:9B:E7:19:7D:F1:59:57:41:2B:36:EF:
		51:A1:06:3C:1B:9F:BB:AB:96:7D:52:CD:BC:4D:69:26:76:4A:90:7E:
		F7:59:44:2D:01:6B:7F:5F:0E:29:56:46:6C:51:AE:3A:3E:7A:9C:36:
		54:0C:51:6A:8E:09:2F:84:73:96:7C:32
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

[   27.534959] r8169 0000:08:00.0 enp8s0: Link is Down
[   29.193195] r8169 0000:08:00.0 enp8s0: Link is Up - 100Mbps/Full - flow control rx/tx
[   29.193217] IPv6: ADDRCONF(NETDEV_CHANGE): enp8s0: link becomes ready
[   96.035440] ERROR @wl_dev_intvar_get :  (repeated 2 times)

########## wireless info END ############
```

Thanks...

---

### Post by CelticWarrior on 2020-06-21
```
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    **Hard blocked: yes**
```

This means it's switched off. Either a dedicated switch, a Function key (F...) or a a key combo, typically FN+F...

---

### Post by kyorosuke on 2020-06-21
Thanks for response, It is a Toshiba Satellite, there is a function key for an "Airplane mode" but I tried switching off/on but nothing happens...

---

### Post by CelticWarrior on 2020-06-21
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Check whether the correct driver is installed.

---

### Post by kyorosuke on 2020-06-21
Mine is #special case 2. but only i found responses for Ubuntu 12

---

### Post by CelticWarrior on 2020-06-21
> **kyorosuke said:**
> Mine is #special case 2. but only i found responses for Ubuntu 12

No, it isn't (it was in Ubuntu 12.04).

In any subsequent release you need "bcmwl-kernel-source".

---

### Post by kyorosuke on 2020-06-21
I'll tried this, but it does't works...

---

### Post by kyorosuke on 2020-06-21
I tried this, but it doesn't works...

---

### Post by kyorosuke on 2020-06-21
I installed Ubuntu 20.04 again and clean all, it still not working... I updated the POST with the wireless-info.txt

---

### Post by CelticWarrior on 2020-06-21
Really, nothing else to add.

If you reinstalled and didn't go on doing random stuff, i.e., if the wireless report was obtained right after a fresh installation, the problem is exactly the same as before, the wireless is switched off **by hardware**.

So, knowing that there's only an handful of cases where some weird module gets installed that blocks the WiFi and wrongly reports it hardware blocked -and- there's no evidence of such module in your report, ergo your WiFi is actually blocked by hardware. If the aforementioned "airplane" key doesn't work (more on that later) maybe there's another switch somewhere, but thinking about it, such key is usually one of the function keys (F12 in some models, F2 in others, etc.) but, also usually,  not its main function/attribute, it often needs FN+F12 (example); or in some case it's the other way around. Have you tried both combo (FN+...) AND the key alone?

---

### Post by kyorosuke on 2020-06-21
Yes, i tried all, there is no switch 
This is my keyboard... the wifi button F12 is for activate the Airplane Mode
[https://photos.google.com/share/AF1QipN-B9Ks0RC80UFffaHcdhJLD4e_OA8Z3mWOFOT1qcf2lL0ZflmLX7EZZxIlgbUaHQ?key=VS1fVXExR1ZZY1VJdVpkTDRVZ1lSOFY2RWUzTVR3](https://photos.google.com/share/AF1QipN-B9Ks0RC80UFffaHcdhJLD4e_OA8Z3mWOFOT1qcf2lL0ZflmLX7EZZxIlgbUaHQ?key=VS1fVXExR1ZZY1VJdVpkTDRVZ1lSOFY2RWUzTVR3)

---

### Post by kyorosuke on 2020-06-21
I tried all, but nothing happens, this is my keyboard...

[https://photos.google.com/share/AF1QipN-B9Ks0RC80UFffaHcdhJLD4e_OA8Z3mWOFOT1qcf2lL0ZflmLX7EZZxIlgbUaHQ?key=VS1fVXExR1ZZY1VJdVpkTDRVZ1lSOFY2RWUzTVR3](https://photos.google.com/share/AF1QipN-B9Ks0RC80UFffaHcdhJLD4e_OA8Z3mWOFOT1qcf2lL0ZflmLX7EZZxIlgbUaHQ?key=VS1fVXExR1ZZY1VJdVpkTDRVZ1lSOFY2RWUzTVR3)

there is no external switch

The model is Toshiba Satellite C55-C5222W

---

### Post by kyorosuke on 2020-06-21
The F12 key is for On/Off the Airplane Mode but nothing happens with the Wifi

---

### Post by CelticWarrior on 2020-06-22
Please, there's no need for multiple posts saying the same.
And, again I have to ask, have you tried also with FN+F12?

---

### Post by kyorosuke on 2020-06-22
Yes, i tried and the window shows the HTML code of this page... with only F12 is for Airplane Mode

---

