---
title: "No visible Wifi Networks"
date: 2020-07-18
forum: Networking &amp; Wireless
---

### Post by SBFree on 2020-07-18
A new install fails to discover wifi networks. Turning networking and wireless off then on sometimes lets SSIDs become visible. Thanks in advance for any thoughts.
Scott
The debug script output is:
```


########## wireless info START ##########

Report from: 18 Jul 2020 05:19 EDT -0400

Booted last: 18 Jul 2020 00:00 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal

##### kernel ############################

Linux 5.4.0-40-generic #44-Ubuntu SMP Tue Jun 23 00:01:04 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

MATE

##### lspci #############################

08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: Toshiba Corporation AR8161 Gigabit Ethernet [1179:ff1e]
	Kernel driver in use: alx

09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:0181]
	Kernel driver in use: rtl8188ee

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a4f Importek 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:07b2 Microsoft Corp. 2.4GHz Transceiver v8.0 used by mouse Wireless Desktop 900
Bus 003 Device 003: ID 125f:0000 A-DATA Technology Co., Ltd. USB Flash Drive
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rtl8188ee             102400  0
rtl_pci                28672  1 rtl8188ee
rtlwifi                90112  2 rtl_pci,rtl8188ee
mac80211              843776  3 rtl_pci,rtl8188ee,rtlwifi
cfg80211              704512  2 rtlwifi,mac80211
libarc4                16384  1 mac80211
wmi                    32768  0

##### interfaces ########################

[/etc/network/interfaces]
source-directory /etc/network/interfaces.d

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp8s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
3: wlp9s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp9s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

wlp9s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0

##### network managers ##################

Installed:

	NetworkManager

Running:

root         731       1  0 05:05 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp9s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 5.4.0-40-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp9s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:09:00.0/net/wlp9s0
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
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         p2p-dev-wlp9s0
GENERAL.TYPE:                           wifi-p2p
GENERAL.NM-TYPE:                        NMDeviceWifiP2P
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/4
GENERAL.VENDOR:                         --
GENERAL.PRODUCT:                        --
GENERAL.DRIVER:                         (unknown)
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /virtual/device/placeholder/0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8161 Gigabit Ethernet
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp8s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:08:00.0/net/enp8s0
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
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIRED-PROPERTIES.CARRIER:               off
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

enp8s0    no frequency information.

wlp9s0    13 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

wlp9s0    No scan results

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/5.4.0-40-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     23DD123075FCCEAB135BFA9
depends:        rtlwifi,rtl_pci,mac80211
retpoline:      Y
intree:         Y
name:           rtl8188ee
vermagic:       5.4.0-40-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4B:23:A5:59:0D:2F:CD:21:25:92:F9:B4:83:84:A3:01:81:3E:5C:19
sig_hashalgo:   sha512
signature:      28:1C:B4:2F:23:45:4D:B5:CC:2A:C9:09:AD:AD:0C:12:90:3F:F6:35:
		8B:11:48:AA:82:B9:E5:0B:B8:87:33:0B:D3:C9:13:57:9B:DF:C0:35:
		E1:2B:EB:D9:DF:2E:1F:58:55:F9:0E:BC:A4:BB:F0:C9:1C:4E:D6:37:
		E2:8E:FA:41:14:39:FD:E0:A3:30:84:1D:5F:6B:D1:B3:4E:0B:EA:91:
		94:78:4D:36:AC:BE:43:9D:8D:04:D7:C1:81:F2:C6:9E:AF:27:3D:84:
		60:FA:30:C7:00:8B:6C:41:62:D6:82:F8:04:85:EE:57:E9:70:39:63:
		5D:C2:52:7A:3D:27:97:40:06:1C:8B:44:06:D1:D5:6B:35:68:FA:0C:
		08:13:1C:41:02:2B:C6:88:D3:01:1E:41:79:A3:C5:57:9D:18:49:A7:
		78:D4:87:A2:7A:B9:23:0E:17:01:AA:C8:A6:54:05:70:8C:01:B3:FA:
		A1:36:E0:26:59:4B:E1:DE:97:E0:CC:BC:F3:04:2B:98:AC:E1:65:3A:
		FE:B2:A4:BE:E5:16:F6:00:B3:1F:72:69:80:13:BF:2A:B5:F3:F6:44:
		CA:B6:04:16:E7:2E:FB:C2:4A:BF:A0:FB:D8:E9:72:42:04:49:BE:6A:
		BD:AD:3A:F8:53:A5:36:8F:A9:44:A7:9E:D2:14:9F:BE:9C:DB:54:F6:
		A4:9F:DA:54:33:9E:9C:32:DB:79:40:C0:35:EB:D8:02:43:95:B9:6C:
		62:1A:AC:E8:0B:8C:0D:65:F9:FA:87:6D:E0:5D:5E:85:56:62:8B:3F:
		C6:F5:3D:1F:AB:D6:C7:5E:28:0E:A6:0C:33:1C:03:F3:AE:7D:FD:83:
		2C:A8:D7:16:A9:7E:A0:62:AE:6C:B1:C0:12:DB:05:F6:3B:ED:33:F5:
		8C:17:AB:B0:4B:DC:67:A3:22:13:7C:49:5F:8D:9D:01:33:96:94:93:
		89:D8:80:92:47:8A:1C:B7:50:FE:C9:8D:87:7A:2B:8A:2B:9A:94:23:
		D8:66:72:D9:A6:A3:88:7C:B0:CC:A8:4D:38:63:CB:A1:27:EE:B5:AB:
		47:69:AC:80:95:43:92:44:4B:2E:24:7E:9D:33:67:D1:92:6B:53:0A:
		76:97:38:24:64:01:85:D8:6B:7C:09:98:57:06:56:09:65:6C:D0:7B:
		A4:2A:65:1B:47:15:45:6E:5C:A7:67:82:3D:94:9A:6D:BC:83:99:26:
		F5:35:29:D3:FA:05:9D:CF:36:81:B4:4C:05:8C:AB:30:30:F2:79:48:
		DB:0B:48:81:02:E6:D3:B6:26:48:6D:96:E9:7E:C2:AB:62:1D:53:9B:
		FA:55:76:6A:F6:37:4A:7B:18:50:57:E5
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/5.4.0-40-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     359AF533CEBD24E6328F94E
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_pci
vermagic:       5.4.0-40-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4B:23:A5:59:0D:2F:CD:21:25:92:F9:B4:83:84:A3:01:81:3E:5C:19
sig_hashalgo:   sha512
signature:      22:13:60:53:FA:81:CE:90:2B:82:FF:9B:31:24:DD:D8:14:7B:8C:CC:
		74:C7:CE:D3:53:A3:88:AB:73:2F:37:BA:E2:9F:8F:2E:DC:58:90:19:
		B8:1E:C4:B7:D8:55:7F:59:AB:31:1A:1E:A0:24:FC:2D:B0:5E:DB:DC:
		37:E5:B9:99:BB:0F:BE:F8:86:BB:E6:BB:4F:17:65:54:57:3A:12:5D:
		A9:CB:03:3B:42:9B:44:79:5C:93:C7:7A:E1:AE:28:8F:53:25:A9:D6:
		AF:57:9C:CC:95:D8:03:DE:03:8D:49:97:A8:8E:2B:BD:A3:BA:F0:4D:
		91:33:48:7E:BF:6F:77:EB:0C:BE:E6:D1:6E:E0:BE:E3:58:83:19:B1:
		03:B9:42:67:BB:F9:37:24:C0:6B:CE:EA:C4:EC:74:60:59:B8:FD:40:
		A1:2F:5F:41:B1:E7:30:CE:AA:E5:90:46:B8:B1:0D:95:E0:70:6D:EC:
		23:62:35:EA:90:18:8A:73:40:F7:33:D0:A0:58:1B:89:5B:15:7E:7E:
		D6:13:C8:84:D3:9C:81:19:7B:AC:2B:D8:47:5E:A9:2C:2D:7C:B3:7F:
		B1:74:05:75:08:15:A9:B4:B1:60:16:A2:B2:E2:09:35:70:62:AF:21:
		47:14:F4:16:E2:20:4E:F5:78:89:80:80:65:C5:C8:D7:B4:AE:7F:27:
		08:A9:52:95:71:DF:B2:FE:0C:67:4E:BE:0C:02:8C:DA:0A:01:96:DE:
		62:03:91:16:D3:E9:65:F1:EE:51:7A:9D:D7:86:0B:A4:1D:B5:D1:91:
		04:E7:1F:89:81:CA:CC:5D:76:83:9B:D8:D9:BC:45:24:7D:E2:31:F4:
		1D:68:02:FB:AD:F6:3A:2A:FE:CC:57:46:0A:AC:2C:0E:16:BC:60:0A:
		DD:50:88:D0:E4:F4:AD:13:5F:9B:0A:54:53:B2:6C:C0:11:0D:F2:FB:
		4A:0B:75:13:5D:53:D5:FA:0C:4B:A2:5C:67:7E:BF:F8:2B:A1:F6:74:
		00:5A:66:FA:12:1E:10:A2:CD:C6:9C:A0:1D:BC:DC:E0:A2:AA:01:BA:
		BD:92:24:9D:26:AB:C3:F6:F5:C0:A4:0F:DF:23:2E:18:33:7F:4A:F1:
		03:59:0B:49:2C:FB:0D:90:77:F0:73:AA:7E:0C:E1:36:AD:43:C5:A1:
		C4:5B:3F:98:5B:88:29:CC:55:D2:9A:16:86:BA:4C:21:F0:53:5D:32:
		01:B8:DF:44:60:28:97:E8:0D:D2:6B:49:86:27:AF:80:18:C7:F8:19:
		8F:2E:0E:D0:C5:1D:AF:69:67:49:75:E2:5D:D8:4F:1B:09:B9:7A:FC:
		A0:A6:E2:03:A3:EE:05:DA:F9:02:FA:5E

[rtlwifi]
filename:       /lib/modules/5.4.0-40-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     02A494ECA51AA6F5AA385C3
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       5.4.0-40-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4B:23:A5:59:0D:2F:CD:21:25:92:F9:B4:83:84:A3:01:81:3E:5C:19
sig_hashalgo:   sha512
signature:      8D:EA:C0:E3:1D:56:AA:B8:DA:20:D9:DE:AF:BF:2F:A3:E3:2A:26:4A:
		F5:89:85:1D:8D:01:26:86:E9:CB:01:DA:C0:A6:D6:0F:CF:A7:9E:A9:
		20:AC:DD:A2:56:32:47:33:F7:71:35:1D:DE:AC:09:4D:96:54:CB:B7:
		16:BE:C4:60:7F:16:BD:60:2E:9B:52:6A:C9:10:0F:C8:2A:19:46:9B:
		CB:1B:65:C3:7E:29:C4:DF:BA:C5:0D:A4:52:21:B9:ED:02:DE:BF:70:
		63:18:54:96:93:51:45:58:EF:0C:57:FD:BC:52:84:69:E8:A9:F6:75:
		98:AA:21:48:0A:62:72:96:1A:1A:A4:64:C1:8A:E6:2B:4D:7B:18:B3:
		1F:06:B6:9E:9D:BD:03:4C:0D:3C:A7:F0:CA:BB:AB:9D:1D:93:C9:44:
		6F:CE:F8:F7:A0:1A:42:F1:2C:04:BE:AC:08:E9:1C:71:35:65:0B:51:
		5E:7E:EB:0A:56:82:E6:FB:C9:DE:C7:7C:D4:63:A6:60:37:70:DC:A2:
		16:52:42:EC:5D:13:96:FA:80:D0:C8:DB:B1:E8:36:08:BF:B7:99:8E:
		F4:BD:65:C2:09:0A:E7:4C:99:9B:5A:5E:3A:A0:29:BE:82:F3:46:E0:
		D0:2D:1F:B5:BC:D2:27:FA:1D:01:4A:8C:E7:8A:E6:6F:B0:F0:A0:E3:
		D8:EB:FE:BB:79:31:F7:EA:AF:5F:10:D3:E8:B7:01:61:A3:10:83:E8:
		86:F2:40:87:C0:29:E3:77:9F:82:85:5C:7D:E1:45:EF:47:2D:E5:8A:
		2C:AF:36:35:4C:F3:CE:43:F3:02:BF:73:06:F3:8D:10:EE:3D:77:E2:
		6F:BD:FB:F2:BF:2E:5D:BF:38:D6:A7:DA:63:96:66:A9:FB:AB:7B:D0:
		A4:71:98:CD:ED:53:6C:0F:1A:E2:23:E1:50:FF:BE:69:6C:CD:E4:BC:
		7F:79:79:B4:67:43:96:C6:AB:48:AE:4A:C2:0B:56:86:D7:07:3F:AD:
		84:64:9E:5A:9D:2E:2D:F0:B6:8E:E2:21:CB:97:10:0A:FB:FE:A8:2D:
		9A:75:C8:F9:06:97:AF:5D:A2:B3:82:2C:49:F7:9F:35:1D:B6:09:F8:
		92:5D:D5:AC:A5:C1:42:EC:EA:12:61:1C:7D:43:47:4D:4F:16:22:66:
		FD:66:A6:7D:15:2C:0B:E7:99:89:18:FC:72:42:AA:7A:BD:C9:2F:BB:
		5F:92:CF:35:9C:B5:5A:AB:58:A9:2A:C5:65:44:FA:DA:A9:25:41:90:
		AB:02:69:81:DD:73:90:B7:DC:94:A1:66:37:CF:CD:FC:55:46:6E:72:
		31:4E:17:2F:EB:05:6C:8E:97:22:EF:FF

[mac80211]
filename:       /lib/modules/5.4.0-40-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     085335B68C989451CD4CC8A
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.4.0-40-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4B:23:A5:59:0D:2F:CD:21:25:92:F9:B4:83:84:A3:01:81:3E:5C:19
sig_hashalgo:   sha512
signature:      5D:44:B3:E3:A9:C2:59:58:C9:21:C8:63:CA:23:83:54:26:41:81:31:
		C8:B1:06:BE:02:2E:6F:A1:FF:D9:18:53:9F:1F:12:63:2A:CF:4D:93:
		D5:49:19:C8:72:C5:2F:18:5E:78:77:04:9D:42:BC:65:D9:F3:68:64:
		58:58:E0:6D:CF:7F:58:11:32:4D:3A:CE:6B:F4:4E:D7:A2:82:A6:FF:
		C2:99:63:E2:D2:53:72:5A:1F:BD:D4:D3:E3:48:09:71:B1:DF:BE:3A:
		F4:D6:13:0F:43:E1:46:C7:DD:2F:CC:75:E6:9F:5A:A2:C5:1B:0C:DE:
		03:03:D6:7D:21:96:7B:72:4F:C4:E6:D0:21:FB:94:B1:98:D1:37:09:
		41:2C:6D:90:43:27:0D:06:7D:4D:97:6B:E0:9B:09:3A:FF:7A:50:6F:
		6C:3E:82:19:0D:78:57:05:6C:82:E2:24:FD:A6:57:D3:B3:5B:C6:C7:
		5A:00:94:E4:13:E4:0B:FA:67:42:CD:AF:12:EF:B1:28:36:CC:A3:86:
		7D:D5:AA:EE:A3:64:99:3C:1F:A1:D1:46:E0:BC:DC:95:6D:66:50:0E:
		35:86:3D:1A:B2:A6:24:CD:C1:32:0F:45:34:CB:A0:81:EC:C5:53:45:
		29:FB:55:07:47:EF:80:E9:13:FD:F5:7D:A9:E4:C5:C8:D1:74:72:86:
		74:67:40:7E:CF:E2:6F:61:61:AE:AB:00:B3:D4:1D:A9:D0:7D:4A:34:
		D8:8B:93:44:0A:87:89:16:C6:D6:52:37:5B:EC:9C:D6:06:04:D0:D7:
		12:80:F4:DD:C4:B6:51:53:61:A4:0A:6F:82:64:D8:08:4C:52:3B:22:
		CA:AC:3F:BE:A4:A8:92:B1:FA:2B:0B:DA:6D:EA:C5:0E:4C:19:32:E5:
		2B:26:0E:76:B5:17:78:4F:0D:34:C0:49:8D:AB:62:1B:4A:E0:4F:3D:
		D9:A4:1E:18:03:C3:34:E6:9D:8A:6C:8C:C0:10:87:08:14:D9:E6:A2:
		41:46:58:ED:E7:BC:23:11:17:E7:1A:FC:0C:D9:EE:70:08:37:29:6C:
		AB:71:BA:AE:4C:9A:32:10:71:12:88:8B:8F:F5:24:29:07:FD:20:9E:
		8B:82:50:AF:20:98:99:DE:FE:80:4C:90:E8:80:9C:D1:19:0E:E5:4E:
		0C:51:B6:7F:11:96:68:6C:B3:31:70:FC:49:63:44:63:3D:E5:2A:F6:
		2D:C1:23:C9:3C:EE:EE:CE:35:26:D9:69:3A:5C:79:E0:21:DB:A0:71:
		CA:9D:EF:B6:19:6F:64:93:52:B6:7F:67:7B:C2:FF:08:BB:34:7E:58:
		39:26:D2:EF:E2:BB:46:A8:CE:90:5D:B6
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.4.0-40-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2369BA84B34843FE73A01F4
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.4.0-40-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         Build time autogenerated kernel key
sig_key:        4B:23:A5:59:0D:2F:CD:21:25:92:F9:B4:83:84:A3:01:81:3E:5C:19
sig_hashalgo:   sha512
signature:      2A:8D:4A:AD:DB:25:CF:97:6B:7E:3C:71:C9:F5:27:F9:DF:E4:3A:A8:
		72:60:E5:15:24:11:46:92:D5:83:07:14:AC:0B:10:02:D8:E3:21:7E:
		B3:86:A7:00:88:1C:08:B4:AA:68:A3:88:3A:EF:5D:22:32:1C:2C:39:
		E4:32:37:33:C6:E6:92:73:E1:F1:CE:42:95:35:92:17:2A:63:0D:C1:
		2B:D2:3D:15:2C:79:2D:39:BE:72:94:60:EC:5C:CB:99:0C:D2:80:0E:
		5A:AA:14:F8:C2:11:17:9C:5E:0E:99:6B:BC:7C:79:8D:45:07:B0:DD:
		0C:1E:F5:B7:D1:E4:3F:12:13:0C:44:80:55:97:BC:05:AB:2E:5A:DF:
		58:29:57:44:7C:E7:8E:C2:A1:DE:77:03:0B:D8:0C:74:7B:B9:80:DE:
		66:92:91:1A:76:44:9B:B9:65:02:40:87:0A:C8:F8:09:AF:C5:60:6B:
		34:2B:59:3F:5B:1D:70:65:03:C8:9D:A5:45:48:4B:4E:A3:AE:7E:38:
		6A:35:2A:CD:17:21:7A:53:8B:A5:92:D5:E0:90:C2:3E:07:51:3B:A7:
		7B:9B:49:B3:25:63:30:6A:2A:54:6E:C9:C9:A2:27:64:EB:84:D5:97:
		AF:26:49:29:70:5E:B0:FC:5E:B7:F5:13:98:5B:C2:D7:58:28:5F:E9:
		57:B7:A2:2D:F1:0A:15:D5:DE:48:6B:FF:F2:4B:5E:EA:C5:D9:73:B7:
		A2:48:F9:EB:A4:F8:0C:E1:19:8D:D4:D4:CE:7C:E1:A7:6E:D6:D8:3B:
		F7:03:27:7F:F8:A8:38:2C:16:B2:F7:19:86:F5:C3:65:8B:23:8F:B2:
		52:4F:C1:A5:CE:54:58:96:B4:9B:F4:BC:0E:2B:56:FC:BD:06:40:7F:
		BD:C0:43:FB:B7:12:C0:DE:9F:F6:A1:75:DF:D6:47:72:59:B6:5F:B2:
		98:AA:CB:0D:68:3A:F9:78:43:6C:80:AD:F0:6A:CB:E6:69:7C:38:E2:
		33:53:54:86:9B:93:20:21:66:C8:8F:2F:05:10:E1:CC:4C:40:77:0A:
		83:A3:3F:B6:E9:3E:21:BF:3F:CD:56:28:65:C9:5E:BE:F8:C4:E9:80:
		85:B3:34:4B:93:C7:50:48:01:49:C5:A6:D4:5B:F9:0E:76:E7:1D:BA:
		39:E4:BA:B2:97:4D:BA:73:24:9D:76:18:EF:7A:F2:89:DF:B2:E9:8D:
		5A:33:7B:76:F3:CC:05:87:FE:D3:EF:5C:56:02:99:AC:6B:D4:45:E4:
		72:C2:29:90:DD:2F:03:41:45:34:9E:58:14:2A:F7:50:52:9D:01:67:
		C2:B7:5B:AA:67:CB:CE:34:8D:2F:58:01
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: N
ips: Y
msi: Y
swenc: N
swlps: N

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    7.836137] rtl8188ee: rtl8188ee: FW Power Save off (module option)
[    8.000068] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[    8.011363] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.027576] rtlwifi: rtlwifi: wireless switch is on
[    8.594978] rtl8188ee 0000:09:00.0 wlp9s0: renamed from wlan0

########## wireless info END ############


```

---

