---
title: "Wifi adapter suddenly disappears"
date: 2020-08-31
forum: Networking &amp; Wireless
---

### Post by alv1234 on 2020-08-31
After couple of minutes / sometimes an hour or so, the Wifi suddenly disappears. I need to reboot to have the wifi available again. I'm not aware of any changes to the system, still it happens. 

Posting the content of *wireless-info* from the script from this forum. Any ideas?

```



########## wireless info START ##########


Report from: 31 Aug 2020 09:28 CEST +0200


Booted last: 31 Aug 2020 00:00 CEST +0200


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:    20.04
Codename:    focal


##### kernel ############################


Linux 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (4) I219-LM [8086:15d7] (rev 21)
    Subsystem: Lenovo Ethernet Connection (4) I219-LM [17aa:506a]
    Kernel driver in use: e1000e


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:2113 Acer, Inc Integrated Camera
Bus 001 Device 005: ID 0bda:b023 Realtek Semiconductor Corp. Bluetooth Radio 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


mac80211              843776  2 rtwpci,rtw88
cfg80211              704512  2 mac80211,rtw88
wmi_bmof               16384  0
intel_wmi_thunderbolt    20480  0
libarc4                16384  1 mac80211
wmi                    32768  2 intel_wmi_thunderbolt,wmi_bmof


##### interfaces ########################


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.0.200/24 brd 192.168.0.255 scope global dynamic noprefixroute enp0s31f6
       valid_lft 3580sec preferred_lft 3580sec
    inet6 fe80::a820:bdf9:daac:9461/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp6s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp6s0' [IF2]> brd <MAC address>
4: vmnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'vmnet1' [IF3]> brd <MAC address>
    inet 172.16.1.1/24 brd 172.16.1.255 scope global vmnet1
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'vmnet1' [IF3]>/64 scope link 
       valid_lft forever preferred_lft forever
5: vmnet8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN group default qlen 1000
    link/ether <MAC 'vmnet8' [IF4]> brd <MAC address>
    inet 192.168.88.1/24 brd 192.168.88.255 scope global vmnet8
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'vmnet8' [IF4]>/64 scope link 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


vmnet8    no wireless extensions.


lo        no wireless extensions.


enp0s31f6  no wireless extensions.


vmnet1    no wireless extensions.


wlp6s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


default via 192.168.0.1 dev enp0s31f6 proto dhcp metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
172.16.1.0/24 dev vmnet1 proto kernel scope link src 172.16.1.1 
192.168.0.0/24 dev enp0s31f6 proto kernel scope link src 192.168.0.200 metric 100 
192.168.88.0/24 dev vmnet8 proto kernel scope link src 192.168.88.1 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53
options edns0
search home


##### network managers ##################


Installed:


    NetworkManager


Running:


root         906       1  0 08:36 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (4) I219-LM
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.1-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Kabelgebundene Verbindung 1
GENERAL.CON-UUID:                       777c14e4-0662-31b6-9176-71e15d9b7c72
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.200/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        dhcp_lease_time = 3600
DHCP4.OPTION[2]:                        domain_name = home
DHCP4.OPTION[3]:                        domain_name_servers = 192.168.0.1
DHCP4.OPTION[4]:                        expiry = 1598862478
DHCP4.OPTION[5]:                        host_name = PC19084
DHCP4.OPTION[6]:                        ip_address = 192.168.0.200
DHCP4.OPTION[7]:                        next_server = 192.168.0.1
DHCP4.OPTION[8]:                        requested_broadcast_address = 1
DHCP4.OPTION[9]:                        requested_domain_name = 1
DHCP4.OPTION[10]:                       requested_domain_name_servers = 1
DHCP4.OPTION[11]:                       requested_domain_search = 1
DHCP4.OPTION[12]:                       requested_host_name = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[15]:                       requested_nis_domain = 1
DHCP4.OPTION[16]:                       requested_nis_servers = 1
DHCP4.OPTION[17]:                       requested_ntp_servers = 1
DHCP4.OPTION[18]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_root_path = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_static_routes = 1
DHCP4.OPTION[22]:                       requested_subnet_mask = 1
DHCP4.OPTION[23]:                       requested_time_offset = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       routers = 192.168.0.1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::a820:bdf9:daac:9461/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/4
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   777c14e4-0662-31b6-9176-71e15d9b7c72 | Kabelgebundene Verbindung 1


GENERAL.DEVICE:                         wlp6s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8822BE 802.11a/b/g/n/ac WiFi adapter (ThinkPad E595)
GENERAL.DRIVER:                         rtw_pci
GENERAL.DRIVER-VERSION:                 5.4.0-42-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp6s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.2/0000:06:00.0/net/wlp6s0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         vmnet1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'vmnet1' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet1
GENERAL.IP-IFACE:                       vmnet1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         172.16.1.1/24
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 172.16.1.0/24, nh = 0.0.0.0, mt = 0
IP6.ADDRESS[1]:                         fe80::<IP6 'vmnet1' [IF3]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         vmnet8
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/5
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         unknown
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'vmnet8' [IF4]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               0 (unknown)
GENERAL.IP6-CONNECTIVITY:               0 (unknown)
GENERAL.UDI:                            /sys/devices/virtual/net/vmnet8
GENERAL.IP-IFACE:                       vmnet8
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     no
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.88.1/24
IP4.GATEWAY:                            --
IP4.ROUTE[1]:                           dst = 192.168.88.0/24, nh = 0.0.0.0, mt = 0
IP6.ADDRESS[1]:                         fe80::<IP6 'vmnet8' [IF4]>/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
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


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/AndroidAPEAD8.nmconnection]] (600 root)
[connection] id=AndroidAPEAD8 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=AndroidAPEAD8
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC314CFBC_5GEXT.nmconnection]] (600 root)
[connection] id=UPC314CFBC_5GEXT | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=UPC314CFBC_5GEXT
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/UPC314CFBC_5GEXT 1.nmconnection]] (600 root)
[connection] id=UPC314CFBC_5GEXT 1 | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=UPC314CFBC_5GEXT
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager


##### iw reg get ########################


Region: Europe/Vienna (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


vmnet8    no frequency information.


lo        no frequency information.


enp0s31f6  no frequency information.


vmnet1    no frequency information.


wlp6s0    32 channels in total; available frequencies :
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


vmnet8    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


enp0s31f6  Interface doesn't support scanning.


vmnet1    Interface doesn't support scanning.


wlp6s0    No scan results


##### module infos ######################


[mac80211]
filename:       /lib/modules/5.4.0-42-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     085335B68C989451CD4CC8A
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.4.0-42-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        02:B6:04:06:D9:82:F4:38:95:E4:6F:84:9F:1D:B4:8E:C5:85:90:8B
sig_hashalgo:   sha512
signature:      A1:89:14:B4:66:69:72:F4:70:9A:C4:D9:7D:DF:A8:0E:A5:20:C8:9E:
        A1:F6:23:B4:15:B6:A3:1B:EC:B1:57:80:10:C0:E3:0B:9F:5A:91:B9:
        56:55:6B:71:57:FE:0F:D1:90:E9:B4:D8:0E:14:1B:E4:16:D6:5E:94:
        A5:88:FC:4E:96:29:01:DB:01:16:88:96:66:95:22:25:74:21:D5:E0:
        D4:CF:19:5C:73:B1:E6:DF:96:8D:65:F7:05:00:77:0B:55:B4:DA:E0:
        FE:EC:69:F4:AB:1E:39:15:BD:F9:D7:50:94:74:C1:87:7A:64:D1:2E:
        F7:6C:15:96:F5:E5:E5:E6:01:F6:0B:77:E6:E1:51:AD:55:5B:FF:E5:
        2A:AD:A2:AD:EF:A1:74:C3:12:B6:16:20:83:B1:64:83:0B:0D:6D:B1:
        E1:A6:2C:A8:C4:FE:AC:97:F3:7E:DF:55:38:B1:A0:F2:7F:91:69:8C:
        F1:9B:DF:86:15:42:40:BE:76:21:2D:14:55:AB:6B:3E:1F:FA:C4:62:
        A1:6B:E7:50:CA:29:B7:31:B0:07:70:EB:A0:24:F5:6D:9D:FB:EE:10:
        1C:CD:53:56:5B:46:29:3F:F1:33:47:90:7E:0C:56:D7:77:A4:B3:AE:
        AD:2B:61:DB:34:01:B4:0D:03:6A:72:0A:7B:73:4F:B3:6A:B9:BF:35:
        8E:71:E5:C8:F6:D6:57:43:3C:B1:55:B3:05:22:22:CA:6C:8E:CC:19:
        FD:63:B4:11:74:43:41:7D:95:20:F2:E2:6C:BE:0C:1A:0A:81:DB:84:
        04:90:5B:12:50:BD:95:2B:DC:BD:C9:8B:D5:49:DC:2B:71:57:A5:CA:
        07:DB:08:4F:C9:F5:B2:51:70:18:C0:67:70:DF:7D:F2:5F:58:BB:D3:
        13:06:F2:0B:CC:B5:AA:6E:90:F8:A4:08:24:C9:14:93:46:B9:64:55:
        16:E4:24:EE:6B:1A:00:CC:EA:7C:2A:48:FE:6F:1A:5D:9A:F3:CC:C7:
        C4:66:0D:0E:E5:94:A4:E9:82:E4:AF:A7:FC:CA:6A:0D:78:AE:CD:49:
        EA:D4:4E:96:E6:A9:9C:8F:A1:08:EC:8A:A0:0D:44:D4:12:29:9D:81:
        2F:90:E4:16:69:93:7C:24:D7:8E:05:62:52:BD:AA:82:A0:B1:02:29:
        16:89:1A:98:D0:6E:96:D6:71:3C:C6:0A:D2:1A:1E:82:08:49:5C:87:
        C2:DD:B3:A8:1D:07:50:34:BA:2F:C4:B4:62:21:EA:E8:69:16:D5:DD:
        47:D3:45:3D:9B:D9:E0:8B:C9:B9:9C:3C:BC:B3:AC:1D:74:58:8B:BC:
        46:B8:8A:04:55:E5:B8:1F:2E:FA:B2:EB
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/5.4.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2369BA84B34843FE73A01F4
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-42-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        02:B6:04:06:D9:82:F4:38:95:E4:6F:84:9F:1D:B4:8E:C5:85:90:8B
sig_hashalgo:   sha512
signature:      11:09:20:94:BE:F4:40:A6:FA:D0:3E:51:A8:D4:D2:61:63:79:98:EB:
        10:58:65:0E:8E:46:FF:83:C3:09:4D:0D:4E:43:FF:34:22:F3:75:27:
        0C:0C:C2:CC:1D:94:31:F0:20:B9:61:67:C9:7C:B4:64:FD:F6:76:2F:
        90:66:77:66:E4:CD:48:E9:0A:AA:2D:4C:AB:65:64:6C:0E:B8:FE:80:
        29:21:79:61:2D:DE:8B:C2:7F:A5:6D:DD:B8:22:E7:4C:5E:DB:36:17:
        98:BE:79:AC:F2:32:15:A4:1A:A5:F3:7D:53:27:44:66:05:C1:4D:9E:
        B4:42:CF:CF:B6:D3:5E:76:51:CD:FE:49:CB:88:40:18:05:12:03:3B:
        C7:00:6A:E2:C2:67:CF:BD:42:FF:1D:7A:22:73:6B:13:85:1C:40:E3:
        2E:66:00:D2:99:A3:DC:1F:21:AB:2F:E4:DB:02:74:83:5B:6D:B7:AE:
        D8:35:05:4D:8F:99:27:08:8D:7A:C8:F3:E8:70:7B:B2:C3:0F:59:B6:
        4F:8F:F4:FE:02:1C:10:A5:60:27:F0:B4:9D:49:00:47:55:BB:14:73:
        4F:25:B1:41:AC:F3:E7:C7:C9:0E:3A:2A:B1:8E:81:B9:8D:29:C9:4E:
        58:BA:82:AC:EB:D2:EA:30:BB:90:F0:72:A4:38:8A:D2:81:65:1B:FB:
        D3:D8:C9:F5:41:3F:5B:9F:AB:76:C0:F4:3D:44:C1:B4:1D:7B:75:0B:
        C6:70:E0:E9:83:D8:33:A7:FE:DB:A0:B1:97:B1:12:26:F7:22:CB:99:
        A8:77:A3:EA:3A:DF:A8:8C:82:64:9F:5B:CD:34:E2:1F:79:09:03:C8:
        3B:F5:A7:20:CA:B2:8C:EF:C6:50:1F:A2:1F:11:21:91:50:6E:6F:A9:
        89:00:5C:4D:84:9D:07:09:BC:A9:2E:B5:F0:1E:BB:75:D7:8E:9C:20:
        8A:6F:40:DD:7E:40:54:38:09:A3:8B:C2:3C:7B:0A:0F:7E:7E:F3:86:
        33:CE:FF:D7:54:5F:89:E4:FE:BB:0F:A2:46:65:20:CE:CC:88:5B:53:
        CF:C9:AD:14:9C:FD:0C:6C:F2:A6:2E:DF:B0:E5:7D:A5:28:B1:9F:ED:
        12:31:4C:BD:DD:15:F3:A3:13:61:5A:FD:51:3C:7B:3F:5B:9F:D5:C9:
        74:B4:2B:F3:6D:6B:96:48:06:29:63:50:1C:6A:3F:F8:C5:43:D4:B1:
        A6:D8:00:1D:D8:A1:BF:B4:66:05:36:3A:E5:9F:BC:8E:F9:A4:F1:31:
        E1:8D:1C:DF:F5:27:19:95:38:73:DE:FF:D1:81:D5:B7:37:D2:B1:81:
        F9:0C:71:F5:5C:30:FF:47:DB:F2:A6:7D
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


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 3097.988432] e1000e: enp0s31f6 NIC Link is Down
[ 3102.122042] e1000e: enp0s31f6 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 3102.122046] e1000e 0000:00:1f.6 enp0s31f6: 10/100 speed: disabling TSO
[ 3149.311013] CPU: 2 PID: 8323 Comm: iwlist Tainted: G        W  OE     5.4.0-42-generic #46-Ubuntu


########## wireless info END ############



```

---

### Post by alv1234 on 2020-09-03
Nobody got any ideas? It is a really annoying problem. I found that the adapter is still there, but it is down. However it does not display any access points anymore and thus cannot connect to them. Not sure if this info is of any help:

```

$ dmesg | grep -e b43 -e wl
[   15.840203] rtw_pci 0000:06:00.0 wlp6s0: renamed from wlan0
[   22.194029] wlp6s0: authenticate with 2c:30:33:4c:f5:ea
[   22.780528] wlp6s0: send auth to 2c:30:33:4c:f5:ea (try 1/3)
[   22.781100] wlp6s0: authenticated
[   22.784041] wlp6s0: associate with 2c:30:33:4c:f5:ea (try 1/3)
[   22.785830] wlp6s0: RX AssocResp from 2c:30:33:4c:f5:ea (capab=0x911 status=0 aid=1)
[   22.786582] wlp6s0: associated
[   22.831242] wlp6s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 2c:30:33:4c:f5:ea
[   23.019507] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready
[ 2302.104166] wlp6s0: deauthenticating from 2c:30:33:4c:f5:ea by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2309.249977] wlp6s0: authenticate with 2c:30:33:4c:f5:ea
[ 2309.812426] wlp6s0: send auth to 2c:30:33:4c:f5:ea (try 1/3)
[ 2309.812922] wlp6s0: authenticated
[ 2309.816413] wlp6s0: associate with 2c:30:33:4c:f5:ea (try 1/3)
[ 2309.817574] wlp6s0: RX AssocResp from 2c:30:33:4c:f5:ea (capab=0x911 status=0 aid=2)
[ 2309.818289] wlp6s0: associated
[ 2309.911392] wlp6s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 2c:30:33:4c:f5:ea
[ 2310.031307] IPv6: ADDRCONF(NETDEV_CHANGE): wlp6s0: link becomes ready

```

---

### Post by alv1234 on 2020-09-03
I'm not sure if it is relevant, but apparently the kernel always ouputs this lines when the wifi stops:

```

[  120.033618] rtw_pci 0000:06:00.0: failed to read ASPM, ret=-5
[  122.336826] rtw_pci 0000:06:00.0: failed to poll offset=0x5 mask=0x2 value=0x0
[  122.336838] rtw_pci 0000:06:00.0: mac power on failed
[  122.336839] rtw_pci 0000:06:00.0: failed to power on mac
[  122.336840] rtw_pci 0000:06:00.0: leave idle state failed
[  122.336992] rtw_pci 0000:06:00.0: failed to leave ips state
[  122.336994] rtw_pci 0000:06:00.0: failed to leave idle state
 
```

---

### Post by Yellow Pasque on 2020-09-05
> failed to read ASPM, ret=-5
Based on that, I would try this:
```
echo "options rtw_pci disable_aspm=1" | sudo tee -a rtwfix.conf
```
See if it works after rebooting. If it doesn't help, you can remove the created file:
```
sudo rm /etc/modprobe.d/rtwfix.conf
```

---

### Post by Yellow Pasque on 2020-09-05
Hmm. My previous post may not be effective as disable_aspm option got added after 5.4 kernel.
[https://bugzilla.kernel.org/show_bug.cgi?id=206411](https://bugzilla.kernel.org/show_bug.cgi?id=206411)

---

### Post by alv1234 on 2020-09-07
Power management indeed seems to be the problem. I followed the suggestion from another board and switched off the power management. Since then I did not experience the problem anymore. 

```

sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

```

---

