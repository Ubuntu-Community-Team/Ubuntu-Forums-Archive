---
title: "Ubuntu 16.04, broken internal wifi adapter on laptop, unable to connect w/usb"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by dravenlj on 2018-08-31
Hi, I'm having some trouble with my networking capabilities. I had to remove a damaged wifi adapter from inside my laptop (Intel chip) and installed an LB-LINK USB adapter that was supposed to be compatible with pre-installed drivers (rtl8192cu). After update and upgrade, it still is not able to display networks, citing that they are all out of range. Here's the output from wireless-info:

```


########## wireless info START ##########


Report from: 31 Aug 2018 13:06 PDT -0700


Booted last: 31 Aug 2018 00:00 PDT -0700


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.15.0-33-generic #36~16.04.1-Ubuntu SMP Wed Aug 15 17:21:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
    Subsystem: Hewlett-Packard Company 82579V Gigabit Network Connection [103c:161d]
    Kernel driver in use: e1000e


24:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    DeviceName: WLAN
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]


##### lsusb #############################


Bus 002 Device 004: ID 1bcf:2888 Sunplus Innovation Technology Inc. HP Universal Camera
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8xxxu              122880  0
rtl8192cu              73728  0
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        57344  1 rtl8192cu
rtlwifi                77824  3 rtl_usb,rtl8192c_common,rtl8192cu
iwldvm                229376  0
mac80211              778240  5 rtl_usb,rtlwifi,rtl8192cu,iwldvm,rtl8xxxu
hp_wmi                 16384  0
iwlwifi               282624  1 iwldvm
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              622592  4 iwlwifi,mac80211,rtlwifi,iwldvm
wmi                    24576  2 wmi_bmof,hp_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback
iface wlan0 inet manual


##### ifconfig ##########################


enp0s25   Link encap:Ethernet  HWaddr <MAC 'enp0s25' [IF1]>  
          inet addr:192.168.44.55  Bcast:192.168.44.255  Mask:255.255.255.0
          inet6 addr: fe80::7f62:6f6b:11ec:4554/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:34560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22890 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29979436 (29.9 MB)  TX bytes:3014839 (3.0 MB)
          Interrupt:20 Memory:d4700000-d4720000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1527 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139199 (139.1 KB)  TX bytes:139199 (139.1 KB)


wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF3]>' [IF3]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


enp0s25   no wireless extensions.


wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlx<IF from MAC [IF3]>  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.44.1    0.0.0.0         UG    100    0        0 enp0s25
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s25
192.168.44.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s25


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      8014     1  0 12:51 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp0s25
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82579V Gigabit Network Connection
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.13-4
GENERAL.HWADDR:                         <MAC 'enp0s25' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:19.0/net/enp0s25
GENERAL.IP-IFACE:                       enp0s25
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a415f5b3-61a6-3172-a8b7-a67dc6e741ca
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a415f5b3-61a6-3172-a8b7-a67dc6e741ca | Wired connection 1
IP4.ADDRESS[1]:                         192.168.44.55/24
IP4.GATEWAY:                            192.168.44.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.44.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = dravenlj-HP-ProBook-6460b
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.44.1
DHCP4.OPTION[11]:                       expiry = 1535831541
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.44.1
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.44.55
DHCP4.OPTION[17]:                       broadcast_address = 192.168.44.255
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_routers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.44.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       dhcp_lease_time = 86400
DHCP4.OPTION[25]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[28]:                       network_number = 192.168.44.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.44.1
IP6.ADDRESS[1]:                         fe80::7f62:6f6b:11ec:4554/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Centrino Advanced-N 6205 [Taylor Peak] (Centrino Advanced-N 6205 AGN)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               18.168.6.1
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:24:00.0/net/wlo1
GENERAL.IP-IFACE:                       
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


GENERAL.DEVICE:                         wlx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8192cu
GENERAL.DRIVER-VERSION:                 4.15.0-33-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/net/wlx<IF from MAC [IF3]>
GENERAL.IP-IFACE:                       
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/THENEST]] (600 root)
[connection] id=THENEST | type=wifi | permissions=user:dravenlj:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=THENEST
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MySpectrumWiFi78-5G]] (600 root)
[connection] id=MySpectrumWiFi78-5G | type=wifi | permissions=user:dravenlj:;
[wifi] mac-address=<MAC 'wlo1' [IF2]> | mac-address-blacklist= | ssid=MySpectrumWiFi78-5G
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp0s25   no frequency information.


wlo1      32 channels in total; available frequencies :
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
wlx<IF from MAC [IF3]>  13 channels in total; available frequencies :
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


wlo1      Interface doesn't support scanning : Network is down


enp0s25   Interface doesn't support scanning.


wlx<IF from MAC [IF3]>  Interface doesn't support scanning : Network is down


##### module infos ######################


[rtl8xxxu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
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
srcversion:     E7E78FAA920143C9B0CB35A
depends:        mac80211
retpoline:      Y
intree:         Y
name:           rtl8xxxu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)


[rtl8192cu]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     EAA386ED8A1CEA0A4C4DCE8
depends:        mac80211,rtlwifi,rtl8192c-common,rtl_usb
retpoline:      Y
intree:         Y
name:           rtl8192cu
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)


[rtl_usb]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D64350FFC4FB84A34CE3C02
depends:        mac80211,rtlwifi
retpoline:      Y
intree:         Y
name:           rtl_usb
vermagic:       4.15.0-33-generic SMP mod_unload 


[rtl8192c_common]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F6DAD9E9BD83515DCFF3382
depends:        rtlwifi
retpoline:      Y
intree:         Y
name:           rtl8192c_common
vermagic:       4.15.0-33-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     12BDF0F9FFC2ACFD3465C5A
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rtlwifi
vermagic:       4.15.0-33-generic SMP mod_unload 


[iwldvm]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     5144A889CD9311D5F87BAC3
depends:        mac80211,iwlwifi,cfg80211
retpoline:      Y
intree:         Y
name:           iwldvm
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)


[mac80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     6BA065AF04F0DFDB8D91DBF
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)


[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     AFB624FD5B16A8AA59A9CF7
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
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


[iwldvm]
force_cam: Y


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   47.323824] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF3]>: link is not ready
[   47.326372] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   47.329710] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[   50.542129] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   50.542164] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[  518.882061] e1000e: enp0s25 NIC Link is Down
[  590.295537] rtl8192cu: Chip version 0x10
[  590.374787] rtl8192cu: Board Type 0
[  590.375024] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  590.375107] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  590.375363] ieee80211 phy2: Selected rate control algorithm 'rtl_rc'
[  591.405740] rtl8192cu 1-1.5:1.0 wlx<IF from MAC [IF3]>: renamed from wlan0
[  591.433420] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF3]>: link is not ready
[  625.765737] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5098.828511] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF3]>: link is not ready
[ 5098.831658] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 5112.421418] e1000e: enp0s25 NIC Link is Down
[ 5117.831778] IPv6: ADDRCONF(NETDEV_UP): enp0s25: link is not ready (repeated 2 times)
[ 5118.063894] IPv6: ADDRCONF(NETDEV_UP): wlx<IF from MAC [IF3]>: link is not ready
[ 5118.065182] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 5120.854775] e1000e: enp0s25 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 5120.854830] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready


########## wireless info END ############



```

I'm hoping this is something easy and my kids didn't completely destroy the hardware.



Edit: Since I can't delete it, this thread'll be good for a laugh. The physical wifi button switch was turned off. I pushed the button, and voila! (It's been a long week.)

---

### Post by chili555 on 2018-08-31
> 24:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0085] (rev 34)
    DeviceName: WLAN
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
It looks like the inernal device is still there. Surgery was unsuccessful.

Let's try a few things. From the terminal:```
sudo -i
echo "blacklist iwlwifi"  >>  /etc/modprobe.d/blacklist.conf
echo "blacklist rtl8192cu"  >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us if there is any improvement.

---

### Post by jeremy31 on 2018-08-31
chili555, I think this is solved, see the last line > Edit: Since I can't delete it, this thread'll be good for a laugh. The physical wifi button switch was turned off. I pushed the button, and voila! (It's been a long week.)

It isn't the first time it has happened and likely won't be the last

---

