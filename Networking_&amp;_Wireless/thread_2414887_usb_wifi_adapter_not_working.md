---
title: "usb wifi adapter not working"
date: 2019-03-16
forum: Networking &amp; Wireless
---

### Post by ProDigit on 2019-03-16
hi'
total noob here,
i have 3 wifi adapters, usb dongles, and none of them work.
i had to borrow one that did to upload this report, but that adaptor isnt available to me for long.
how can i install the other ones?

see wireless info:

```

########## wireless info START ##########

Report from: 16 Mar 2019 16:50 EDT -0400

Booted last: 16 Mar 2019 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 18.10
Release:	18.10
Codename:	cosmic

##### kernel ############################

Linux 4.18.0-16-generic #17-Ubuntu SMP Fri Feb 8 00:06:57 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7b80]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 007: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 003: ID 0e8f:2517 GreenAsia Inc. 
Bus 001 Device 005: ID 0bda:0811 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled
Platform is in Setup Mode

##### lsmod #############################

rtl8xxxu              122880  0
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        57344  1 rtl8192cu
rtlwifi                90112  3 rtl8192c_common,rtl_usb,rtl8192cu
mac80211              794624  4 rtl_usb,rtl8192cu,rtlwifi,rtl8xxxu
cfg80211              663552  2 rtlwifi,mac80211
wmi_bmof               16384  0
mxm_wmi                16384  0
wmi                    24576  2 wmi_bmof,mxm_wmi

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
4: wlx<IF from MAC [IF2]>: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlx<IF from MAC [IF2]>' [IF2]> brd <MAC address>
    inet 192.168.1.21/24 brd 192.168.1.255 scope global dynamic noprefixroute wlx<IF from MAC [IF2]>
       valid_lft 86332sec preferred_lft 86332sec
    inet6 fe80::87b6:b7ce:e805:a9f1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp1s0    no wireless extensions.

wlx<IF from MAC [IF2]>  IEEE 802.11  ESSID:"Hemano"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Hemano' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=12/70  Signal level=-98 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:95   Missed beacon:0

##### route #############################

default via 192.168.1.1 dev wlx<IF from MAC [IF2]> proto dhcp metric 600 
192.168.1.0/24 dev wlx<IF from MAC [IF2]> proto kernel scope link src 192.168.1.21 metric 600 

##### resolv.conf #######################

[644 root '/etc/resolv.conf']
nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root       562     1  0 16:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlx<IF from MAC [IF2]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Corp.
GENERAL.PRODUCT:                        RTL8192CU 802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.18.0-16-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF2]>' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-8/1-8:1.0/net/wlx<IF from MAC [IF2]>
GENERAL.IP-IFACE:                       wlx<IF from MAC [IF2]>
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Hemano
GENERAL.CON-UUID:                       3ca1d40c-f062-44dd-9dd9-2f3e86ff569f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
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
WIFI-PROPERTIES.5GHZ:                   no
IP4.ADDRESS[1]:                         192.168.1.21/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 600
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 600
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[6]:                        expiry = 1552855761
DHCP4.OPTION[7]:                        ip_address = 192.168.1.21
DHCP4.OPTION[8]:                        network_number = 192.168.1.0
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       requested_broadcast_address = 1
DHCP4.OPTION[11]:                       requested_domain_name = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       requested_domain_search = 1
DHCP4.OPTION[14]:                       requested_host_name = 1
DHCP4.OPTION[15]:                       requested_interface_mtu = 1
DHCP4.OPTION[16]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[17]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[18]:                       requested_netbios_scope = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       requested_static_routes = 1
DHCP4.OPTION[23]:                       requested_subnet_mask = 1
DHCP4.OPTION[24]:                       requested_time_offset = 1
DHCP4.OPTION[25]:                       requested_wpad = 1
DHCP4.OPTION[26]:                       routers = 192.168.1.1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
IP6.ADDRESS[1]:                         fe80::87b6:b7ce:e805:a9f1/64
IP6.GATEWAY:                            fe80::224e:7fff:fe57:d85e
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 600
IP6.ROUTE[2]:                           dst = ::/0, nh = fe80::224e:7fff:fe57:d85e, mt = 600
IP6.ROUTE[3]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.DNS[1]:                             fe80::224e:7fff:fe57:d85e
DHCP6.OPTION[1]:                        dhcp6_client_id = 0:4:1e:40:ae:af:83:6d:fa:96:ce:79:79:1a:2:15:e0:3a
DHCP6.OPTION[2]:                        dhcp6_name_servers = fe80::224e:7fff:fe57:d85e
DHCP6.OPTION[3]:                        dhcp6_server_id = 0:3:0:1:<MAC 'Hemano' [AC1]>
DHCP6.OPTION[4]:                        requested_dhcp6_client_id = 1
DHCP6.OPTION[5]:                        requested_dhcp6_domain_search = 1
DHCP6.OPTION[6]:                        requested_dhcp6_name_servers = 1
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3ca1d40c-f062-44dd-9dd9-2f3e86ff569f | Hemano

GENERAL.DEVICE:                         enp1s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp1s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1d.0/0000:01:00.0/net/enp1s0
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

SSID       BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
corallina  <MAC 'corallina' [AC2]>  Infra  2     2417 MHz  270 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA2      no             
2Wire24    <MAC '2Wire24' [AC3]>  Infra  9     2452 MHz  130 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA2      no             
Hemano     <MAC 'Hemano' [AC1]>  Infra  1     2412 MHz  135 Mbit/s  44      &#9602;&#9604;__  WPA2      yes     *      
swizzy2    <MAC 'swizzy2' [AC5]>  Infra  11    2462 MHz  195 Mbit/s  20      &#9602;___  WPA2      no             
--         <MAC '' [AC4]>  Infra  9     2452 MHz  65 Mbit/s   10      &#9602;___  --        no             

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

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no
wifi.cloned-mac-address=preserve
ethernet.cloned-mac-address=preserve

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Hemano]] (600 root)
[connection] id=Hemano | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF2]>' [IF2]> | mac-address-blacklist= | ssid=Hemano
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
country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 23), (N/A), AUTO-BW
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS, AUTO-BW
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp1s0    no frequency information.

wlx<IF from MAC [IF2]>  11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp1s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlx<IF from MAC [IF2]>  Scan completed :
          Cell 01 - Address: <MAC 'Hemano' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=12/70  Signal level=-98 dBm  
                    Encryption key:on
                    ESSID:"Hemano"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000352a8b0b48
                    Extra: Last beacon: 236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'corallina' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"corallina"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001513cb32ded
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '2Wire24' [AC3]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"2Wire24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b3618c6a59f
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC '' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000b3618c81140
                    Extra: Last beacon: 736ms ago
          Cell 05 - Address: <MAC 'swizzy2' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"swizzy2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010963d8289
                    Extra: Last beacon: 448ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@gmail.com>
srcversion:     8642492BC11C2F2196EFB0F
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.18.0-16-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:65:B9:86:1E:EF:56:31:51:4F:55:33:
		B0:86:47:FA:E0:31:F7:AB:FB:C7:DA:D8:5E:A4:35:B3:C9:FD:A7:8C:
		A1:A0:38:FC:A3:56:37:4E:EE:F7:0D:8E:B5:8C:E6:F2:AC:9B:A5:39:
		95:AC:BC:86:08:2B:72:15:52:54:50:60:9F:DC:17:5F:45:69:EE:F8:
		9C:30:B9:EA:30:87:95:0F:1A:9E:B7:0E:ED:5E:78:0C:19:68:3C:EB:
		7B:48:38:6F:C8:42:7E:4C:53:8D:6D:39:FC:6B:B8:C0:71:10:53:A6:
		C0:BD:8B:BD:04:09:C8:8A:5D:34:D8:83:44:12:E4:73:5A:E5:5A:7D:
		E9:72:50:97:89:D0:B1:E3:BD:80:15:73:03:62:F0:DF:0C:ED:2D:91:
		65:73:8F:99:AF:57:87:64:7E:42:83:13:DC:3B:BD:6B:6C:C1:CE:A8:
		82:18:DA:94:BB:91:81:50:B1:E8:3B:57:98:06:46:44:8A:5A:5E:48:
		06:14:8E:8D:B6:F0:45:13:96:49:03:96:DA:FA:9D:34:20:CF:53:63:
		21:0E:21:65:12:43:86:F5:D8:22:A7:A5:91:F3:1C:4A:24:83:88:8F:
		3C:7E:47:B5:49:DF:DC:0A:0B:D1:08:B5:2E:25:75:14:C6:F5:4F:ED:
		FD:D4:52:E8:0C:60:CE:6C:2C:2F:27:7D:39:42:3C:CA:6B:E6:C5:12:
		33:22:7E:69:26:7E:4F:06:20:3D:3B:42:AA:AB:21:52:82:73:60:2C:
		C8:F0:33:B6:7F:55:D4:55:84:6D:57:E4:EF:96:BF:1F:9F:D3:C3:71:
		92:BA:86:29:44:F4:19:C2:BE:A9:49:26:DF:84:16:7B:3F:0B:55:D0:
		28:42:C8:B8:BB:51:65:64:DC:D4:C4:C5:F1:FD:67:97:13:E8:D5:21:
		95:12:51:84:55:87:FC:32:9B:3C:9D:27:86:48:D4:DC:E8:FE:19:20:
		44:FF:B6:4E:C5:F0:AC:33:A3:F8:89:1C:C5:CB:F5:87:AD:01:A1:4B:
		FC:8D:1F:88:15:2C:A7:13:B2:75:4C:69:4A:B0:F6:57:30:C0:9E:2B:
		C2:14:3F:91:43:13:82:1D:7B:E7:07:CE:17:A6:15:61:04:72:3B:AE:
		4B:18:2A:45:84:D5:EC:10:4A:8F:BA:AD:EB:34:0B:B3:BD:CC:BD:E3:
		CB:B9:B1:EB:5B:DB:5D:AA:65:9D:2B:19:9E:BD:A0:55:5C:16:BD:EF:
		86:02:68:AE:6D:9F:CB:1B:B7:33:7F:25:2D:65:B9:43:27:88:CA:A7:
		30:57:CA:34:0E:6B:7F:B0:52:49:F5:A2:A7:9B:AC:F7:CE:0D:58:A1:
		88
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[rtl8192cu]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     F64AA1606198F16F12C616B
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
retpoline:      Y
intree:         Y
name:           rtl8192cu
vermagic:       4.18.0-16-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:38:6A:99:97:D0:EA:24:A5:DC:9F:EA:
		ED:48:B0:86:B9:CD:EE:2C:BD:F3:16:0B:0F:6D:95:92:04:0E:AB:35:
		24:F1:E4:54:EC:EA:37:9C:4E:00:5B:68:7C:C0:3C:A0:18:86:B4:C1:
		3E:61:4C:E4:7F:0A:1A:F1:45:D0:00:0D:DE:92:18:93:6A:57:B2:0B:
		C6:B8:D2:7D:F2:0F:64:14:1F:C8:AB:69:78:7A:66:EA:C0:21:62:F5:
		81:AB:0A:35:94:A2:D2:5A:6E:A3:0D:4B:AE:A2:DF:71:E3:A7:77:9F:
		72:3C:C6:5B:00:8E:52:F5:A1:5B:BC:E0:F5:55:08:76:E3:74:BA:2E:
		FC:F2:9F:72:67:14:30:D9:30:62:ED:34:FC:DE:AE:48:CE:18:05:D6:
		B4:14:82:76:8E:8F:85:7A:C5:80:A0:0F:28:B5:D3:F7:44:42:1E:AE:
		B9:1A:BA:4E:A3:9C:64:E4:59:B5:7C:6C:1B:02:C3:AD:A7:9E:E4:F1:
		3F:F1:5E:AD:DE:A1:43:FF:0F:41:C4:19:36:B7:18:A4:B5:3A:EA:7B:
		E5:B5:DF:7A:CC:3B:DD:F0:90:5D:E6:86:8B:94:45:86:89:8B:63:0A:
		9D:F4:69:92:D4:74:3E:73:8A:C2:5B:1A:71:36:B8:A9:D0:61:AE:26:
		76:F4:B0:C3:DF:13:0B:6D:6D:34:1C:A6:C9:23:F1:C4:BF:38:92:01:
		7F:46:DE:94:94:AD:59:8B:C7:17:71:85:36:06:70:76:37:CB:80:EF:
		62:36:20:98:5A:FB:5D:00:A6:D9:89:B7:5C:BB:8F:7D:BE:02:3B:ED:
		E3:28:05:16:95:2F:4A:EE:94:FF:23:2B:0D:09:6C:56:6C:1B:B0:EF:
		06:AD:D7:EA:CC:CD:A2:24:3F:12:9D:B4:82:FA:A6:18:79:FE:0B:E5:
		4A:2F:6A:FA:9A:99:3E:2A:AC:BC:C1:05:CD:99:9A:BE:0C:4B:55:EA:
		B7:6B:CB:FD:9C:A6:97:05:9B:34:F3:F5:FB:CF:D8:96:B5:B2:1A:E6:
		3D:08:B0:74:C5:F9:C7:C9:39:15:F3:08:C8:8C:88:93:44:10:EC:6F:
		1C:43:A1:90:FA:34:C2:09:AE:C0:8B:FA:E5:66:B8:58:64:C1:59:65:
		A7:6B:CE:1F:05:34:54:77:E7:00:12:00:CF:C5:EF:22:B8:0E:7C:FE:
		3A:B4:62:66:01:30:DC:EA:A5:DD:5F:35:E7:D4:E8:31:B1:3A:A4:E1:
		08:73:61:11:9B:F8:1E:99:6D:63:CE:3E:0C:59:5F:2F:2F:5D:C3:2F:
		6F:0D:4D:3E:09:71:D6:94:BB:F4:A2:AC:36:4E:B0:C6:4F:32:07:E5:
		FE
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)

[rtl_usb]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3C1A7F672BAE13FD701B28C
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_usb
vermagic:       4.18.0-16-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:68:AD:CA:57:3C:FC:E0:F8:10:20:54:
		F6:46:3F:CE:85:DA:5C:EA:2C:A6:71:F7:6E:B6:CC:00:F8:EE:A8:77:
		BE:45:97:3A:05:FE:B9:39:25:3F:2F:06:A4:57:03:65:C0:AE:17:B9:
		78:06:77:92:92:9B:C2:30:56:0D:1B:DD:DD:75:AE:03:56:71:59:A5:
		DE:75:B6:CB:39:4B:49:27:E4:C8:42:56:05:6C:D5:DD:EF:E3:52:39:
		8B:F2:2B:65:D4:7D:E7:7D:33:69:B2:48:C8:E8:F7:5F:C1:1D:B4:3F:
		75:B5:37:13:C5:EC:9E:CE:37:0C:0C:93:DE:C0:91:35:D7:FC:A4:31:
		B6:EB:84:FA:8D:C1:85:03:26:B3:DD:36:7F:1A:1A:10:E7:5D:6A:0E:
		BF:D1:7E:16:DE:89:4D:4E:59:11:F7:80:4B:74:DB:25:2B:A0:BC:39:
		2E:A5:BB:66:5F:91:0F:E0:FC:4C:FB:9B:DE:3E:AC:31:C7:DB:39:5B:
		AF:1A:B2:4F:27:ED:2D:75:31:E9:F7:09:DD:12:49:5A:79:47:47:A9:
		C9:06:AB:F6:B3:DD:EF:30:C7:7B:DA:02:93:31:32:FB:0F:48:AD:8C:
		FB:A3:29:A9:C9:87:82:AD:A6:FF:10:50:AE:F6:49:E6:96:19:ED:6F:
		94:8B:78:95:60:E3:D9:0C:32:FA:7E:A1:79:1C:80:00:67:7F:18:32:
		24:6D:B6:CB:EC:43:5F:FB:28:67:64:38:B1:33:17:33:5B:95:E8:39:
		2E:7E:FC:A7:C5:2F:42:32:02:A4:AB:D7:D0:C9:B5:C0:C7:9B:4F:41:
		8A:7C:CE:58:9E:34:B9:EB:55:F7:04:3B:E6:AA:A0:9F:AC:0C:16:1D:
		C2:2F:13:F9:7B:9B:24:68:E8:3A:F3:AB:38:C2:32:6D:4E:4D:F4:EC:
		6C:D2:DA:E7:EB:C0:E3:F8:C2:D0:EA:84:CE:DF:3C:0D:44:35:4E:98:
		E3:CF:FD:7E:44:74:16:CC:CA:88:D9:BB:C3:F3:55:5C:9B:69:F0:C7:
		4A:5A:B8:E7:07:1B:82:10:50:46:B2:A2:6E:24:FD:9F:AC:D9:12:B1:
		CE:F1:91:5B:1E:47:F7:EC:E9:D7:E1:A3:5F:03:1F:B1:1F:84:F5:A1:
		27:FC:DF:21:80:EB:EC:80:21:20:E9:38:CA:DE:C0:33:43:86:D5:58:
		93:EF:89:78:DB:1F:D0:5B:5B:53:2C:4B:83:12:7E:D1:03:53:7D:B7:
		56:CF:44:A7:22:CC:5D:E3:9B:EF:64:AF:CA:A9:DC:03:31:64:89:84:
		C9:6A:49:A5:2B:52:CD:12:74:8F:99:21:16:45:9F:96:6D:1B:58:DC:
		1B

[rtl8192c_common]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     AFC0D7DCB46D280A5A1FBFC
depends:        rtlwifi
retpoline:      Y
intree:         Y
name:           rtl8192c_common
vermagic:       4.18.0-16-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:66:68:A0:76:E9:E3:A3:63:BD:8F:73:
		E5:26:E0:4C:2E:93:D6:5F:D0:43:D0:64:73:4A:4C:DA:F2:3C:65:5C:
		D7:7F:08:52:22:17:94:BA:1E:B3:9D:1E:03:FA:2A:18:34:8C:6A:EE:
		5E:90:14:C5:83:76:16:76:27:69:58:5F:E3:FA:CD:DA:3E:14:A4:E0:
		52:1F:63:39:B7:09:A0:03:11:61:5E:7C:29:8F:EC:7D:2D:30:ED:0E:
		BA:3E:57:79:05:59:6B:F0:D7:F9:97:DE:21:21:5A:D9:AF:74:B2:2A:
		89:0E:BC:22:20:0D:E9:21:F2:56:32:F6:E7:49:B7:E9:8D:CB:18:69:
		31:B4:00:70:A2:7A:E0:38:EB:18:77:CA:AA:F4:58:61:79:75:32:7D:
		7B:EA:82:2B:23:D8:42:1A:E7:6E:39:CC:49:00:C7:79:07:06:01:65:
		40:DA:80:4E:5B:87:4D:7C:C9:1C:BD:6A:05:01:9E:03:C6:47:8B:75:
		87:16:68:A7:B7:86:42:96:BC:52:57:39:26:BD:DA:43:DA:5E:21:BE:
		47:24:97:59:DE:95:75:51:EB:7D:ED:27:AE:E5:F8:3C:7B:D9:F4:62:
		F0:C4:3F:BC:C9:BB:0A:2B:9A:C0:13:DF:53:9D:70:11:AB:93:80:EB:
		7E:D9:3E:57:DE:87:18:05:DC:0B:00:E2:85:9A:DF:99:AA:F2:2B:FA:
		E7:5A:09:26:EB:9A:11:77:8C:36:8D:2D:5E:2A:F1:7D:07:B0:7E:0C:
		EB:1C:4B:5E:99:37:04:F2:BF:59:0F:B5:8C:DF:86:2E:4C:0A:83:50:
		1E:6A:EC:72:FE:A0:3B:E5:2F:F9:FD:17:A3:D7:FF:7B:C1:78:60:E7:
		28:7B:A8:33:E0:C0:B4:B1:06:E8:A4:8F:18:0A:F7:84:FF:64:20:C2:
		3D:09:A6:E8:74:38:C8:06:E9:88:53:4A:16:C2:DC:D4:A6:85:88:DB:
		C2:AC:FF:9F:22:45:56:E0:21:75:FE:29:84:90:27:6B:B6:31:DA:77:
		7A:26:87:83:8F:6E:D3:8B:3A:4C:EC:81:C6:A5:05:3C:B1:E6:8F:09:
		CB:25:5C:87:8F:55:FD:5E:CB:1C:F9:9A:92:2D:49:CE:A2:77:5D:BB:
		C4:25:21:34:5C:C8:81:F9:06:9D:30:44:55:FD:F7:F1:FF:28:69:7A:
		3B:40:65:18:19:23:3C:19:17:04:CE:7C:A2:5D:FE:D4:76:50:F6:22:
		76:E8:C3:5C:37:E8:98:BF:DB:B8:BA:75:29:67:5C:4D:4B:80:13:FD:
		0A:0C:6D:6B:B9:C4:2C:36:78:15:48:B6:42:F3:64:43:7E:B2:AD:BB:
		75

[rtlwifi]
filename:       /lib/modules/4.18.0-16-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     BD2B6DBADE667F4F0EE035C
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       4.18.0-16-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:10:DC:5A:CD:CB:E4:BD:35:74:E2:E5:
		3B:86:3F:64:11:D1:44:AA:11:6B:48:3D:1B:A4:97:55:EA:5F:B8:F0:
		2E:D6:9B:66:D5:E9:9D:E8:53:B7:CC:7E:BE:F1:69:B1:69:79:6F:B1:
		60:B8:C3:47:BD:24:72:C8:82:F1:E5:13:EF:14:52:EC:3A:7D:AD:E8:
		09:12:AC:2B:51:41:BB:DC:90:CD:EC:55:ED:D0:E1:FF:E1:B3:A0:1F:
		2E:66:1E:AC:2F:D7:16:40:CB:27:B8:B3:47:88:FA:02:11:19:9F:FB:
		97:73:57:74:D7:55:D5:41:5E:BA:10:89:05:3A:34:B1:5F:DB:14:05:
		F3:ED:6E:C0:72:09:46:3A:F3:71:8D:79:C1:C5:1D:BD:21:3E:71:04:
		8D:D7:EE:2A:72:13:B1:95:02:ED:3B:15:33:5E:F4:ED:67:24:FC:D0:
		78:49:71:C7:CF:76:B8:D6:74:4A:72:0B:8D:66:2E:3F:B5:57:60:6B:
		82:C8:E9:0A:0E:7C:C9:BE:12:1D:18:4A:25:E6:7F:DC:17:AB:A6:A0:
		5B:AD:4B:5C:41:09:F3:E7:0C:36:86:C4:80:62:0D:07:C3:B4:64:54:
		1E:34:3B:3B:92:66:E3:F9:1F:0A:4C:E9:30:10:35:28:CC:D3:A2:5C:
		C8:FC:75:CD:7B:51:76:D3:FB:40:D9:F7:19:E0:C2:FC:DE:E7:D5:F6:
		A8:0A:EE:E6:FF:7B:F5:9E:B8:83:02:AD:6E:77:F2:FE:46:50:24:D1:
		B2:BF:B3:CA:5C:36:B1:CE:7A:11:9A:E2:65:22:2D:AD:B5:2B:88:5A:
		85:DD:A3:CE:C2:89:76:84:F4:CC:87:5E:7C:A8:CE:A7:30:FF:C9:28:
		D1:1B:BD:89:D2:DB:6A:FC:EF:93:43:0D:F5:79:D7:6B:60:61:D7:8A:
		70:74:F5:16:AB:26:94:2A:7F:3B:2C:9F:88:8F:A8:A1:2D:B9:C1:1E:
		11:D1:C0:10:A8:B7:C6:2B:4B:38:C1:F8:49:FA:EF:28:AA:D6:61:0B:
		9A:20:E7:C2:A4:E0:2D:97:34:AD:53:F9:20:69:1D:10:2A:C0:DD:3B:
		37:75:0E:75:D3:1B:FA:F6:61:3C:06:6F:C9:C8:E7:6D:DB:22:40:FF:
		75:9D:FB:06:8F:2D:0A:59:16:64:52:FC:2D:DD:B9:52:FF:13:A4:CD:
		CA:26:55:D8:8B:5B:65:9B:23:CF:27:92:73:9A:35:7F:17:EF:D9:92:
		EA:4E:DA:7A:3D:98:37:3D:AA:43:9A:4D:77:F2:2A:72:58:33:53:A5:
		DF:07:40:05:76:BF:E7:B2:7B:A6:73:AA:DE:2F:5D:7F:CE:C6:9E:C7:
		F3

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
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:42:0C:29:AD:20:1E:BD:CE:C7:E8:6C:
		89:83:FE:02:0F:22:55:38:CA:C6:02:A8:63:65:B3:0A:F4:E9:58:87:
		0A:48:43:C0:15:0E:7F:8C:FA:1C:9D:2C:1F:42:4D:CA:4A:A0:E7:5C:
		BA:B8:7C:5E:B9:01:C2:04:59:09:8C:3C:5A:F6:83:FB:21:A3:A8:D5:
		9B:81:82:0D:F0:E0:5D:19:AF:A4:9E:B5:D3:38:8A:BA:5F:87:45:D0:
		44:C7:95:4B:27:A2:F3:4A:7E:BE:6A:84:F6:1D:82:A9:B8:6F:8C:FE:
		B5:62:63:DA:68:DE:F3:76:47:E8:6B:C3:0C:2B:CB:2F:01:C9:CB:D4:
		45:82:E4:DE:D0:99:12:63:BA:CD:62:5D:22:69:AB:4D:22:D3:26:2C:
		4E:5F:14:68:A0:B1:00:8C:F7:D6:66:04:FA:80:40:13:73:DD:91:F8:
		6F:CC:89:E1:72:0A:5C:D0:30:C9:F0:E6:85:3D:42:3F:F1:09:DA:1E:
		0B:AC:FF:4D:1C:03:D0:C7:A3:72:62:2E:84:AC:37:DD:E0:D1:C9:DD:
		37:1C:0F:69:74:D1:38:19:E0:C6:E2:44:85:2F:35:88:EB:13:AF:13:
		BA:8A:3E:86:E8:E9:CE:FC:C3:C0:6E:C8:87:F0:3D:D5:12:59:5C:C2:
		9E:E7:31:6B:1A:6A:26:A3:15:06:5A:C3:11:B2:35:6F:DF:B9:96:FC:
		8E:02:79:20:F1:42:55:14:D6:D7:4C:CE:63:F9:1F:9F:0A:24:13:F7:
		8A:3D:BD:81:91:BA:91:C2:75:67:7D:A0:B6:D9:40:AD:75:15:A2:F2:
		39:86:53:BD:B7:2D:14:87:D9:15:14:FE:A2:5E:8C:73:22:62:FE:94:
		94:4F:7B:9D:CB:79:A4:AC:37:10:B4:7B:E6:DC:BC:C6:60:34:63:A4:
		A5:4F:4B:2D:45:BF:0D:20:E4:7D:53:65:01:AE:45:43:98:3A:D2:8F:
		59:0C:2E:05:C1:B1:79:D8:98:A0:F3:17:59:4D:A7:2E:70:D4:22:C8:
		F8:74:63:62:7A:C0:A4:09:81:9E:5E:34:8D:00:62:C5:78:3C:1C:C8:
		CC:86:40:2E:6F:6C:4F:0B:28:B8:65:33:E1:23:12:E6:1E:CD:1D:3F:
		A3:3B:3B:5A:C8:06:44:59:25:8B:07:A8:F9:E0:29:2A:F7:72:39:43:
		E4:85:31:FD:F6:12:E5:63:CA:12:EA:BA:C2:AB:80:E6:DB:F0:DC:46:
		28:98:F3:28:55:D3:EB:CA:2E:26:01:9E:D8:2F:11:A2:6E:A9:42:4D:
		F1:81:6D:3B:36:A8:1D:02:5E:CF:3C:F7:89:F8:B6:11:FA:86:04:47:
		43
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

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
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
		82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
		03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
		02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
		42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
		61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:3D:08:8B:
		4C:7B:71:CD:6B:AF:DD:3F:4D:A4:59:54:16:D7:0D:39:AB:30:0B:06:
		09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
		01:01:01:05:00:04:82:02:00:56:C4:7D:0A:F9:85:45:BD:D1:4F:25:
		50:2C:6F:36:0D:65:AF:E1:EA:E2:54:07:C9:0D:C9:7E:58:2F:A6:FA:
		C4:73:04:5D:ED:BB:D4:11:AB:31:49:17:D1:CA:31:1A:D4:5B:84:D8:
		9B:45:9A:03:9C:30:DB:F2:6E:8F:24:87:44:5C:31:55:32:ED:3B:CA:
		31:81:07:E1:74:CF:15:3F:C5:C6:CD:60:81:18:00:3D:6B:FF:26:0C:
		B5:CB:E0:CA:32:22:7B:B2:14:93:60:E3:DC:F2:D3:51:99:9C:A9:B7:
		08:02:53:EA:8B:22:75:3D:B7:41:88:65:07:97:39:2B:60:C0:FE:BE:
		12:2E:C4:52:CF:FE:38:6B:78:90:77:5E:3A:5D:45:2C:D0:E3:46:72:
		94:1E:F9:52:97:91:13:50:2B:D4:3D:5C:3F:D1:C4:5B:6A:44:62:99:
		E1:CF:63:13:EE:FA:BC:E0:D4:98:72:CC:D3:7E:FE:5A:04:0C:63:96:
		09:7D:E0:35:47:49:F2:38:51:F7:2C:1B:23:0A:75:C2:46:27:E0:2F:
		EC:D8:D0:73:5F:F2:75:54:79:6B:EE:88:62:F1:11:56:76:E3:4B:59:
		61:A5:A2:A5:30:E6:E6:87:BD:1E:BE:9B:A4:CC:A4:87:BF:82:53:30:
		35:E0:53:3F:1B:F6:8D:92:AC:02:6E:5B:B7:87:4D:72:05:D6:22:D6:
		01:DD:15:9D:AE:9E:38:0F:30:62:F4:87:F5:3A:4C:6D:C7:DA:E8:1F:
		5A:5B:90:DC:EB:98:94:22:8E:99:03:20:89:0E:E4:A2:D1:08:8E:E7:
		8A:58:67:B1:3D:88:0F:19:73:02:3F:E4:EF:07:97:48:3E:83:3A:93:
		30:40:F1:9B:3E:AA:F2:2C:47:C6:64:15:6D:57:22:80:D2:3E:DE:C0:
		AF:6C:77:70:DE:E3:56:B2:FE:65:21:55:95:FD:72:77:C6:14:46:51:
		A1:61:AC:19:A8:E1:0F:6E:B2:47:A4:A9:54:ED:D1:5C:D3:20:93:1C:
		1E:EE:95:7D:E2:3B:3F:21:3E:D2:2D:7F:99:E4:65:89:F3:B3:AC:E3:
		ED:AE:FC:5E:5E:A6:37:14:95:A2:74:4B:94:AD:0D:45:C8:15:48:19:
		37:0F:CB:01:E2:E9:C2:52:F0:0D:5F:60:A0:6F:26:98:80:0D:9A:FE:
		0E:8E:79:67:AC:DE:98:E6:A3:2B:9F:EB:39:33:1E:E9:07:D6:9A:15:
		61:35:E4:0D:32:55:86:2E:38:66:C7:9F:1A:38:55:D4:9A:A3:FB:83:
		16:35:D1:0F:F2:89:73:D2:E7:AE:17:6B:DF:44:4F:0F:07:C2:CB:32:
		48
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[rtl8192cu]
debug_level: 0
debug_mask: 0
swenc: N

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

########## wireless info END ############


```

thanks

---

### Post by praseodym on 2019-03-16
```
[COLOR="#FF0000"]Bus 001 Device 004: ID 0bda:0811 Realtek Semiconductor Corp.[/COLOR] 
Bus 001 Device 007: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
[COLOR="#FF0000"]Bus 001 Device 005: ID 0bda:0811 Realtek Semiconductor Corp.[/COLOR] 
```
The two red ones have the same chipset. Run
```

sudo apt-get install --reinstall build-essential dkms rtl8812au-dkms
```
For the other one, blacklist the older driver, it loads two:
```

echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by ProDigit on 2019-03-18
Thanks!
1 wifi dongle now works!

I still need help in getting the other one to work, as well as a new Wifi/bluetooth dongle that just arrived,

I've updated the wifi info, in link below.

[http://paste.ubuntu.com/p/Sz9tpYfcWx/](http://paste.ubuntu.com/p/Sz9tpYfcWx/)

---

