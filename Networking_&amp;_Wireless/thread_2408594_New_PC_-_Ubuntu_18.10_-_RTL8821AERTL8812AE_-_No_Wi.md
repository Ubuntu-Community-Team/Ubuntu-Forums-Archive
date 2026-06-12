---
title: "New PC - Ubuntu 18.10 - RTL8821AE/RTL8812AE - No Wireless Networks"
date: 2018-12-20
forum: Networking &amp; Wireless
---

### Post by wafitzpatrick on 2018-12-20
I've extensively searched for this topic already and exhausted all solutions suggested for similar issues.

Ordered this custom PC from PCSpecialist as Gaming laptop for my nephew - typically their line is if you want to install Linux you're on your own for support.

Card seems to be recognised and working - but no wireless networks can be found. It has 2 antennas, model no. AWP1200E.

I have already tried the github rtlwifi_new driver. I used to be fairly experienced with debugging wifi but it's been a few years since I've had to do this with Ubuntu... :(

Not sure why lspci outputs RTL8812AE but lsmod is RTL8821AE. I do have a driver installation CD - if necessary I can grab it from there.

Wifi Diagnostics:

```



########## wireless info START ##########


Report from: 20 Dec 2018 12:33 GMT +0000


Booted last: 20 Dec 2018 00:00 GMT +0000


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.10
Release:    18.10
Codename:    cosmic


##### kernel ############################


Linux 4.18.0-13-generic #14-Ubuntu SMP Wed Dec 5 09:04:24 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8812AE 802.11ac PCIe Wireless Network Adapter [10ec:8812]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0c45:7603 Microdia 
Bus 003 Device 002: ID 04d9:a088 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1e71:1711 NZXT 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


eeepc_wmi              16384  0
asus_wmi               28672  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
video                  45056  1 asus_wmi
wmi_bmof               16384  0
rtl8821ae             233472  0
btcoexist             176128  1 rtl8821ae
rtl_pci                32768  1 rtl8821ae
rtlwifi                98304  3 rtl_pci,rtl8821ae,btcoexist
mac80211              794624  3 rtl_pci,rtl8821ae,rtlwifi
cfg80211              663552  2 rtlwifi,mac80211
wmi                    24576  2 asus_wmi,wmi_bmof


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
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
    inet 192.168.1.226/24 brd 192.168.1.255 scope global dynamic noprefixroute enp3s0
       valid_lft 86286sec preferred_lft 86286sec
    inet6 fe80::e722:bc09:a8e9:462d/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp5s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp5s0' [IF2]> brd <MAC address>


##### iwconfig ##########################


enp3s0    no wireless extensions.


lo        no wireless extensions.


wlp5s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


default via 192.168.1.1 dev enp3s0 proto dhcp metric 100 
169.254.0.0/16 dev enp3s0 scope link metric 1000 
192.168.1.0/24 dev enp3s0 proto kernel scope link src 192.168.1.226 metric 100 


##### resolv.conf #######################


[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager
    Wicd


Running:


root       844     1  0 12:31 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.3/0000:01:00.2/0000:02:00.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       enp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       e705b1b4-df04-3363-b7b3-d51ca33ff60a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.226/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[2]:                        dhcp_lease_time = 86400
DHCP4.OPTION[3]:                        dhcp_message_type = 5
DHCP4.OPTION[4]:                        dhcp_rebinding_time = 75600
DHCP4.OPTION[5]:                        dhcp_renewal_time = 43200
DHCP4.OPTION[6]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[7]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[8]:                        expiry = 1545395519
DHCP4.OPTION[9]:                        host_name = gamerjim
DHCP4.OPTION[10]:                       ip_address = 192.168.1.226
DHCP4.OPTION[11]:                       network_number = 192.168.1.0
DHCP4.OPTION[12]:                       next_server = 192.168.1.1
DHCP4.OPTION[13]:                       requested_broadcast_address = 1
DHCP4.OPTION[14]:                       requested_domain_name = 1
DHCP4.OPTION[15]:                       requested_domain_name_servers = 1
DHCP4.OPTION[16]:                       requested_domain_search = 1
DHCP4.OPTION[17]:                       requested_host_name = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[20]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_static_routes = 1
DHCP4.OPTION[26]:                       requested_subnet_mask = 1
DHCP4.OPTION[27]:                       requested_time_offset = 1
DHCP4.OPTION[28]:                       requested_wpad = 1
DHCP4.OPTION[29]:                       routers = 192.168.1.1
DHCP4.OPTION[30]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[31]:                       wpad = a
IP6.ADDRESS[1]:                         fe80::e722:bc09:a8e9:462d/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e705b1b4-df04-3363-b7b3-d51ca33ff60a | Wired connection 1


GENERAL.DEVICE:                         wlp5s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8812AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.18.0-13-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp5s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         42 (The supplicant is now available)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.3/0000:01:00.2/0000:02:02.0/0000:05:00.0/net/wlp5s0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 


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


Region: Europe/London (based on set time zone)


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


enp3s0    no frequency information.


lo        no frequency information.


wlp5s0    32 channels in total; available frequencies :
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
          Channel 140 : 5.7 GHz


##### iwlist scan #######################


enp3s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlp5s0    No scan results


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.18.0-13-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw_29.bin
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     2CE28F5AC9749CAF48145E8
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
retpoline:      Y
name:           rtl8821ae
vermagic:       4.18.0-13-generic SMP mod_unload 
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
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.18.0-13-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     6081DC1832010BD0C4C8DDC
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.18.0-13-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.18.0-13-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C3D6C55583BFB4BF0EE61E2
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.18.0-13-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.18.0-13-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C5D73328CD704BB6E363074
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.18.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:40:71:35:
        68:4F:B5:09:52:A4:1C:79:66:D0:19:CB:22:FE:F8:0B:19:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:07:0F:80:14:7E:03:E2:C9:93:0C:03:
        DA:58:F6:C6:18:A3:CA:19:3C:FD:25:EF:66:E0:D8:71:C9:59:92:54:
        2E:E9:65:0C:E5:3C:85:79:17:4A:CD:CC:0E:7F:3F:51:94:0A:A0:15:
        DD:7D:79:BC:A5:05:09:67:CF:7E:A9:CC:D4:6B:CF:19:42:FE:4F:B6:
        B7:63:03:7D:98:CE:FC:90:54:C5:E6:36:7F:E1:C9:6B:B6:9B:6A:FA:
        15:41:28:32:25:FD:52:E4:02:8F:1F:E8:92:96:79:31:3C:5C:E2:CD:
        9C:5F:1C:78:54:7E:94:4C:4B:0B:B2:25:76:64:F4:41:43:C9:B4:FA:
        06:B2:F7:6C:85:BF:C2:1C:D3:81:1B:BD:0C:B8:32:A7:CF:1A:4C:E6:
        37:52:7F:A8:93:64:EC:9D:D3:E9:58:04:3E:8A:54:9B:5B:77:3A:45:
        D3:7E:61:98:40:12:FD:04:1C:D4:1D:99:B1:3B:1E:5E:89:3A:EA:F6:
        02:E5:94:6D:15:C4:8D:67:3F:A9:8E:06:BC:C8:69:EB:53:D9:01:03:
        1B:38:DC:79:FE:05:69:83:8E:80:75:0E:3C:F4:1A:D0:00:62:F2:3A:
        9D:59:6B:20:D3:35:22:C5:89:FC:34:BC:EA:CC:C3:5C:CA:1D:35:5C:
        79:38:04:97:8B:CB:CF:26:7E:D5:48:C5:4D:0C:32:47:F5:13:E8:3F:
        02:E7:7E:9A:43:29:33:D2:2E:1E:5B:35:C2:DF:D7:11:26:C4:C9:35:
        45:A4:24:1A:8F:B0:D5:FC:CB:33:F3:AC:24:19:97:0D:FB:74:7D:9A:
        F2:94:2A:19:AB:8F:57:19:53:B5:E5:33:18:DE:C7:B8:39:66:4D:DE:
        75:DC:1F:9C:74:B6:8C:E2:49:19:BC:39:AF:8C:AF:7A:11:8F:9D:EB:
        C6:2A:22:6E:D6:92:B8:A6:2F:83:7E:87:9F:34:82:C5:C0:A6:7A:66:
        A2:11:E7:93:F0:A8:CA:36:71:1C:2B:87:2F:A8:69:57:66:67:C6:FE:
        B6:36:5F:5D:4A:14:4A:FA:89:CB:7D:C5:DC:47:A0:A1:FA:4D:13:33:
        BD:12:60:9D:AD:26:B3:B5:44:0B:9E:4C:AD:B9:83:89:65:B6:52:1F:
        32:23:16:0A:89:0A:04:8A:9C:72:B7:0C:E5:77:A7:31:A4:70:BB:9D:
        85:82:33:0F:B0:F9:CA:D6:90:A4:6F:BE:0C:48:91:2F:62:EB:FF:87:
        0E:C6:E7:18:51:39:D0:1C:AB:0C:56:E8:35:11:FA:51:DC:10:B2:40:
        0F:96:78:A5:B4:13:FF:F1:A9:7A:C1:BA:55:49:D5:4B:7F:46:54:89:
        15
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.18.0-13-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BFB309EF7C6C321F605D36E
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.18.0-13-generic SMP mod_unload 
sig_id:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
signature:      30:82:02:A5:06:09:2A:86:48:86:F7:0D:01:07:02:A0:82:02:96:30:
        82:02:92:02:01:01:31:0D:30:0B:06:09:60:86:48:01:65:03:04:02:
        03:30:0B:06:09:2A:86:48:86:F7:0D:01:07:01:31:82:02:6F:30:82:
        02:6B:02:01:01:30:46:30:2E:31:2C:30:2A:06:03:55:04:03:0C:23:
        42:75:69:6C:64:20:74:69:6D:65:20:61:75:74:6F:67:65:6E:65:72:
        61:74:65:64:20:6B:65:72:6E:65:6C:20:6B:65:79:02:14:40:71:35:
        68:4F:B5:09:52:A4:1C:79:66:D0:19:CB:22:FE:F8:0B:19:30:0B:06:
        09:60:86:48:01:65:03:04:02:03:30:0D:06:09:2A:86:48:86:F7:0D:
        01:01:01:05:00:04:82:02:00:A2:45:9F:C3:36:1A:59:C6:56:E3:58:
        D7:FA:2B:2E:7D:18:C4:18:59:A5:2D:6B:02:4F:B4:B2:5A:0A:6A:B9:
        BD:43:2C:FD:B2:4C:97:A8:E3:8E:32:43:32:88:15:22:55:DF:06:B9:
        3B:96:09:30:D0:F9:1B:B4:53:8C:F6:21:B8:0A:B6:5A:20:DB:4C:D0:
        EA:BB:6C:E8:54:A6:55:E8:56:69:79:19:41:4F:E0:8A:89:C4:BC:8C:
        D7:09:C5:BE:F6:B7:9F:57:94:42:5C:41:C8:60:8A:01:5D:A4:4B:13:
        B2:AE:41:C5:03:18:E9:49:02:6C:5E:DC:E6:8A:F0:84:AC:BD:27:F3:
        78:75:5E:9A:0B:39:BA:3C:51:5E:66:03:BF:83:F6:E7:B2:27:59:0F:
        DF:8D:F5:06:7E:65:78:EB:87:97:0A:59:97:BA:E3:11:A1:21:3A:91:
        13:A5:12:6C:26:35:D4:9A:8C:A2:98:12:ED:1C:56:36:C6:52:39:1E:
        02:EF:0D:44:72:FE:49:9E:08:40:52:B4:20:AB:BF:20:C0:99:0F:F7:
        32:37:50:F0:6C:07:2F:9F:FC:B6:C7:A4:B7:BE:A7:A5:8F:4B:98:4D:
        AA:33:09:6A:E2:8E:10:BE:09:F8:84:D9:2E:0E:E8:AC:92:66:31:43:
        AA:38:E5:A8:2C:7C:FE:C0:05:44:05:A1:41:67:12:A2:AD:62:F1:3E:
        E8:B4:09:04:75:C9:CE:AD:55:86:11:37:6B:35:F5:4A:6C:DC:80:99:
        1F:BB:72:7F:A2:F7:19:AE:DC:47:55:3B:C2:20:FA:9B:27:0F:FD:4F:
        94:47:57:FC:18:0B:F4:3F:ED:AE:0B:45:B9:61:94:03:60:A7:2E:04:
        E6:96:A0:BE:BA:EB:AB:71:24:47:3D:AB:C6:08:4E:E1:02:DA:E5:FB:
        1C:49:90:25:85:6F:84:E3:37:81:85:05:ED:C2:69:D2:54:AC:DF:D3:
        2D:38:7F:D6:E2:81:DF:FB:0F:C0:D0:8F:4D:5E:DD:A6:15:FD:20:2A:
        9D:B5:46:BF:1B:42:F4:78:FC:90:1E:E7:11:0E:75:7C:70:A0:F0:4C:
        2F:4A:67:41:CE:DF:6A:DD:9B:46:46:BE:C9:97:37:DC:C0:C9:FB:2E:
        79:2B:BF:BC:E9:CE:A6:0D:BC:0A:7B:73:92:49:52:BE:CA:6D:BE:E6:
        FD:04:CE:8F:3C:C9:5D:60:F3:5F:26:63:07:29:EA:03:01:2F:69:17:
        F5:A5:5D:37:46:E7:59:2F:25:39:27:78:EB:95:85:21:98:D0:7B:84:
        AE:96:4B:82:5E:D7:41:CC:98:B1:0D:EF:9B:59:58:9B:26:91:DB:93:
        89
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: N
int_clear: Y
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


[/etc/modprobe.d/ideapad-laptop.conf]
blacklist ideapad-laptop


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/rtl8821ae.conf]
options rtl8821ae fwlps=N


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   11.483925] r8169 0000:03:00.0 enp3s0: link up
[   11.483933] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready


########## wireless info END ############



```

---

### Post by wafitzpatrick on 2018-12-20
OK well this is one of those odd solutions... I continued to troubleshoot and I just got this idea to try switching the antennas. They are both the same spec and there are no markings to indicate which belongs on which connector - but the wireless now works!

---

