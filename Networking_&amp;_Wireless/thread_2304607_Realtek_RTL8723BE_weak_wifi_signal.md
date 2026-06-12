---
title: "Realtek RTL8723BE weak wifi signal"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by jinsujais on 2015-11-28
Hi,

I installed Xubuntu 15.10 on my HP Laptop, that has a Realtek RTL8723BE wifi adapter. With Windows, the wifi works pretty well, having good signal strength. But after installing xubuntu, the signal is extremely weak, works when sitting next to modem.
Please help me to solve this issue.
Here is the result of wireless-info script.

```


########## wireless info START ##########

Report from: 30 Nov 2015 09:26 IST +0530

Booted last: 30 Nov 2015 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily

##### kernel ############################

Linux 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
	Subsystem: Hewlett-Packard Company Device [103c:804c]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
	DeviceName: Realtek PCIe FE Family Controller
	Subsystem: Hewlett-Packard Company Device [103c:8096]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0bda:57c4 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723be             135168  0
btcoexist             184320  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               102400  3 btcoexist,rtl_pci,rtl8723be
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              733184  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              548864  2 mac80211,rtlwifi
mxm_wmi                16384  1 nouveau
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eno1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43416764 (43.4 MB)  TX bytes:3191932 (3.1 MB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1280  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:187778 (187.7 KB)  TX bytes:19228 (19.2 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"D-Link"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'D-Link' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eno1
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1

##### resolv.conf #######################

nameserver 127.0.1.1
search domain.name

##### network managers ##################

Installed:

	NetworkManager

Running:

root       754     1  0 09:10 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       0885c1bb-d55d-4c63-b007-d8db0384b9d9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   0885c1bb-d55d-4c63-b007-d8db0384b9d9 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.2/24
IP4.GATEWAY:                            192.168.1.1
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1448941345
DHCP4.OPTION[9]:                        domain_name = domain.name
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.2
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'eno1' [IF]>/64
IP6.GATEWAY:                            fe80::56b8:aff:fe47:7dc4

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.2.0-16-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     D-Link
GENERAL.CON-UUID:                       083e68f1-6590-4ca6-9a40-4932d3ec7317
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   083e68f1-6590-4ca6-9a40-4932d3ec7317 | D-Link
IP4.ADDRESS[1]:                         192.168.1.7/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          domain.name
DHCP4.OPTION[1]:                        network_number = 192.168.1.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1448941273
DHCP4.OPTION[9]:                        domain_name = domain.name
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.1.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.1.7
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            fe80::56b8:aff:fe47:7dc4

SSID    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
D-Link  <MAC 'D-Link' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2      yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/D-Link]] (600 root)
[connection] id=D-Link | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=D-Link
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

wlo1      13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'D-Link' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"D-Link"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000360a94ad
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-16-generic/updates/dkms/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     1A35907BCCEF84FE28F988D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/4.2.0-16-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     1BFD9F9E9693CB93908149A
depends:        mac80211,rtlwifi
vermagic:       4.2.0-16-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.2.0-16-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     9A94C1A2CE5E02B2F239836
depends:        mac80211,cfg80211
vermagic:       4.2.0-16-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-16-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-16-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        6A:1C:9C:21:F0:4A:B8:6F:D1:D7:CE:D6:CA:11:35:40:FC:8E:35:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: N
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   13.839597] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   13.839600] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   13.921244] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   14.494860] Using firmware rtlwifi/rtl8723befw.bin
[   14.526478] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.526673] rtlwifi: wireless switch is on
[   14.560532] rtl8723be 0000:08:00.0 wlo1: renamed from wlan0
[   28.188399] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   28.261144] r8169 0000:09:00.0 eno1: link down
[   28.261193] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   28.263387] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)
[   56.913764] wlo1: authenticate with <MAC 'D-Link' [AC1]>
[   56.925700] wlo1: send auth to <MAC 'D-Link' [AC1]> (try 1/3)
[   56.928347] wlo1: authenticated
[   56.931108] wlo1: associate with <MAC 'D-Link' [AC1]> (try 1/3)
[   56.936273] wlo1: RX AssocResp from <MAC 'D-Link' [AC1]> (capab=0x411 status=0 aid=1)
[   56.937319] wlo1: associated
[   56.937328] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[  131.077221] r8169 0000:09:00.0 eno1: link up
[  131.077231] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready

########## wireless info END ############


```

---

### Post by praseodym on 2015-11-28
Try these module parameters:

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
echo 'KERNEL=="wlo1", RUN+="/sbin/iwconfig wlo1 txpower 18"' | sudo tee -a /etc/udev/rules.d/75-wlan.rules 

```Reboot

---

### Post by jinsujais on 2015-11-28
Tried those parameters. Still, signal strength is weak, and I'm not able to get the wifi when I move away from modem. 
Please help.

It seems, HP use Realtek adapter for both WiFi and Bluetooth, and by default, Bluetooth is working perfectly well in my laptop. I tried to disable Bluetooth using the method showed in: [http://itsfoss.com/turn-off-bluetooth-by-default-in-ubuntu-14-04/](http://itsfoss.com/turn-off-bluetooth-by-default-in-ubuntu-14-04/)
But when I restart the laptop, Bluetooth is automatically enabled by default.
I don't know what is happening, but I assume that Bluetooth overrides WiFi.

_rtl8723befw.bin_ is already there in */lib/firmware/rtlwifi/*, and I tried *echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf*

What to do to make WiFi working, just like when it was on Windows?

---

### Post by Geoffrey_Arndt on 2015-11-30
An alternative solution would be just to try a known, and tested Linux compatible wifi adapter.   Panda provides several of these - - starting at about $10 usd for the nano size dongle and slightly more for the full stick with high gain antenna.    Works very well in all versions of Ubuntu that I've tried, just "plug & play".     The one I'm using now in my Acer Laptop is the Panda Ultra 150n.

I've built wireless modules from source . . . but then they require recompiling upon kernel updates, so I prefer the simplest fix.

Here's a link to Panda (but can pick these up at Amazon, NewEgg etc.)    [http://www.pandawireless.com/](http://www.pandawireless.com/)

---

### Post by chili555 on 2015-11-30
I suggest you try updating the driver:```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```Also, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Reboot and tell us if the performance is improved.

---

### Post by jinsujais on 2015-11-30
Did as per the instructions. Set IN instead of IS, for India.
But issue still exists. Able to connect wifi only when I keep laptop close to modem.

---

### Post by Hadaka on 2015-11-30
Hi, since your wifi does not function correctly on 15.10
i recommend you try the stable LTS long term support 14.04
15.10 is only supported another 6 ..9 months
14.04 is supported until almost 2019.
beyond that you could try a usb type wifi.
good luck

---

### Post by Geoffrey_Arndt on 2015-11-30
Just to verify, you did the install as listed by Chili555?  Including the _reboot_ so system uses mod'd kernel?

The LTS solution seems worth trying also.

Finally, you can build the driver from source:   see post#2   [http://ubuntuforums.org/showthread.php?t=2299578](http://ubuntuforums.org/showthread.php?t=2299578)

---

### Post by Jerry_Gorland on 2015-11-30
I have exactly the same problem on an HP Stream 11-r010 Cloudbook with an RTL8723BE chipset.  I reported my problem in the wrong forum ([http://ubuntuforums.org/showthread.php?t=2304461&p=13397470#post13397470](http://ubuntuforums.org/showthread.php?t=2304461&p=13397470#post13397470)) only to discover that I should have posted here.  Also, I was unaware that the problem I am having is the "reduced range problem".  I, too, need to sit next to the WiFi antenna to get any reception at all!  By the way, I started testing with Mint 17.2 (equivalent to Ubuntu 14.04) but just installed Xubuntu 15.10.  I am using a D-Link DUB-E100 USB to ethernet converter to get connectivity to do some debug.  Previously (with Mint 17.2) I tried downloading the rtlwifi_new files and recompiling, etc., but still I can't see beyond a few feet.  There must be an answer to this...

By the way, with a fresh install of Xubuntu 15.10, I execute the wifi script, and my results are pasted at:  [http://paste.ubuntu.com/13588280/](http://paste.ubuntu.com/13588280/)  (pretty cool feature!).

---

### Post by jinsujais on 2015-11-30
yes, i did exactly as what is told by Chili555 and Praseodym instructed.
do i need to change my OS to 14.04, as i installed 15.10, hoping to install when 16.04 LTS is released. when i googled, kernel 4.2 is updated with realtek drivers by default.

*lspci* shows this as the device of laptop :
Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
Subsystem: Hewlett-Packard Company Device [103c:804c]

**Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter** means, wifi and bluetooth together, right?
Bluetooth is working perfectly well in the system, and i can't find out what happened to wifi. 

please please help me.

---

### Post by Jerry_Gorland on 2015-12-01
Jinsujais, I started with Mint 17.2 (equivalent to Ubuntu 14.04) but noticed no difference.  I also tried the rtlwifi_new driver and recompiled.  Yes, BT 4.0 means Bluetooth.  I disabled bluetooth and tried various other things recommended on various posts.  No improvement.

---

### Post by jinsujais on 2015-12-01
I reverted to Windows. :confused::(

Tried 14.04 with all previous solution, which didn't help to get wifi on the laptop.
Anyway, Thanks to all who spend the time for giving some tips.

Kindly inform the developers to find a solution for users having realtek RLT8723BE as the wifi adapter, in the next 16.04LTS.

---

### Post by Jerry_Gorland on 2015-12-01
Sad, indeed, but I understand.  I went ahead an ordered a Panda USB adapter as recommended by Geoffrey_Arndt ([http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG](http://www.amazon.com/Panda-150Mbps-Wireless-N-2-4GHz-Adapter/dp/B00762YNMG)) while the RTL8723be bugs are worked-out.  I'll see if it works as expected.  The RTL8723be is a big pain for Linux users so hopefully its drivers will get some attention by someone with skill and interest in it.  I'd be interested in doing some debug work, but it's probably a huge learning curve.

---

### Post by jeremy31 on 2015-12-01
Jerry_Gorland

Can you try this [http://ubuntuforums.org/showthread.php?t=2304946&p=13400164#post13400164](http://ubuntuforums.org/showthread.php?t=2304946&p=13400164#post13400164)

I am not sure if it will work but none of the normal fixes seem to work anymore

---

### Post by Jerry_Gorland on 2015-12-01
Thanks, Jeremy.  However, no luck with that one.  It remains a mystery.

---

### Post by Geoffrey_Arndt on 2015-12-04
Jerry,   I am keeping a spreadsheet on wireless adaptor compatibility with various versions of the "Buntu" family.

When your Panda usb-wireless dongle arrives and you test it, I would appreciate an update here as I have't yet tested it on Xubuntu 15.10.   Thanks much in advance , , , , as this would be an easy way for most folks to avoid going back to windows, and all that overhead expense at later times.

PS:   I have tested it from Ubuntu 12.04 thru and including 15.04 (with full compatibility) . . . but haven't had chance to do just yet with 15.10 as that lappie is out of town just now.

---

### Post by Jerry_Gorland on 2015-12-04
I will definitely update this thread, Geoffrey.  I lifted the lid on my laptop expecting to possibly replace the wi-fi card with another one I know works with Linux, but I see that an the card is an M.2 form factor PCIe card (not like the HMC "half height PCIe" card that I have).  Plus, I've learned that HP whitelists specific WiFi cards in the BIOS so replacing it with a card not on the whitelist may fail at boot.  However, I noticed that the laptop only has one antenna connected (the other is empty).  Perhaps I should try moving the antenna over to the other connector...

SOLUTION for my particular case (HP Stream 11-r010 Cloudbook with N3050 Celeron and HP Model No. 792204-001 30x22mm M.2 Wi-Fi card):  Moving the single antenna cable from one connector to the other (as shown in the attached diagram) solved the problem.  This would explain why the laptop worked only when sitting right next to the Wi-Fi router:  With Linux the card is configured to use the other connector compared to Windows.  Now I am two floors up from my router and connected well with Xubuntu 14.04.  With Xubuntu, all the hotkeys work.  I tried Mint 17.2, but I was unable to adjust the display brightness.  I am still going to test out the Panda Wi-Fi dongle when I get it.

---

### Post by chili555 on 2015-12-06
Great information and thanks for sharing it. 

I have been looking at driver parameters to try to force the driver to use one antenna or the other, but haven't found the solution...yet!

---

### Post by Jerry_Gorland on 2015-12-07
You bet. You would think that the WiFi controller would automatically switch to the antenna that has the highest power... that is the whole point of two antennas!

---

### Post by chili555 on 2015-12-07
> **Jerry_Gorland said:**
> You bet. You would think that the WiFi controller would automatically switch to the antenna that has the highest power... that is the whole point of two antennas!May I assume you tried the *rtlwifi_new* that I recommended above? I notice on the git page:> 	rtlwifi_new: Add "fix" for single-antenna RTL8723BEIf you did try it and there is no improvement, then I suggest you register and file an issue: [https://github.com/lwfinger/rtlwifi_new/issues](https://github.com/lwfinger/rtlwifi_new/issues)

---

### Post by Jerry_Gorland on 2015-12-07
Yes, I originally tried a build with rtlwifi_new (at least once, I'm thinking twice on two different OS variants). With this laptop there is no copper ethernet (only Wi-Fi) so I needed to sit close to the Wi-Fi base station, or (as I later did) use a USB-RJ45 dongle for Internet access. To be sure I would need to move the antenna back to the original coax connector and re-try rtlwifi_new and run the debug script, etc. Without doing that I wouldn't want to file an issue since I have already moved the target.

However, I have rebuilt using rtlwifi_new with my new antenna setup and Xubuntu 14.04 (per [http://askubuntu.com/questions/623001/how-to-install-realtek-rtl8723be-wifi-pcie-wireless-network-adapter](http://askubuntu.com/questions/623001/how-to-install-realtek-rtl8723be-wifi-pcie-wireless-network-adapter)) and I've noticed that the TX speed has gone up about 10-fold when two stories up (RX speed was always good).  So, I think using the new driver is a good thing in this case!

By the way, to stop Wi-Fi from periodically dropping with the pre-rtlwifi_new driver, I executed echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf per [http://ubuntuforums.org/showthread.php?t=2243978](http://ubuntuforums.org/showthread.php?t=2243978) and used network manager to set IPV6 to "ignore".  Whether I still needed those commands now is not known.

---

### Post by titoose on 2015-12-13
> **Jerry_Gorland said:**
> SOLUTION for my particular case (HP Stream 11-r010 Cloudbook with N3050 Celeron and HP Model No. 792204-001 30x22mm M.2 Wi-Fi card):  Moving the single antenna cable from one connector to the other (as shown in the attached diagram) solved the problem.  This would explain why the laptop worked only when sitting right next to the Wi-Fi router:  With Linux the card is configured to use the other connector compared to Windows.  Now I am two floors up from my router and connected well with Xubuntu 14.04.  With Xubuntu, all the hotkeys work.  I tried Mint 17.2, but I was unable to adjust the display brightness.  I am still going to test out the Panda Wi-Fi dongle when I get it.

Perfect! Many thanks Jerry for that clue. Now my HP 250 G4 is working flawless after plugging the antenna cable from outer connector to the inner one. Before of this I only could connect if I were very close to an AP (the disconnected connector was acting as antenna) but now I can use the notebook without restrictions.

---

### Post by Jerry_Gorland on 2015-12-13
That is terrific, titoose!  I wonder how many cases of "weak RX signals" would be addressed by this?  It appears that HP has resorted to using only one antenna to keep costs down (not that I've found one antenna on my box to create a range issue), but then subjects users to this problem.  Having to open the lid on a laptop is a pain.

---

### Post by titoose on 2015-12-14
> **Jerry_Gorland said:**
> That is terrific, titoose!  I wonder how many cases of "weak RX signals" would be addressed by this?  It appears that HP has resorted to using only one antenna to keep costs down (not that I've found one antenna on my box to create a range issue), but then subjects users to this problem.  Having to open the lid on a laptop is a pain.

I think almost all cases with weak signal can be addressed by this but, as chili555 said, the best solution would be the driver being able to select the correct antenna (as Windows driver does).

Said so, I think this is not a cost cutting thing, simply Linux driver developers have not information enough about this type of hardware (in contrast with Realtek own developers who made the Windows driver).

---

### Post by Jerry_Gorland on 2015-12-14
> **Geoffrey_Arndt said:**
> Jerry,   I am keeping a spreadsheet on wireless adaptor compatibility with various versions of the "Buntu" family.

When your Panda usb-wireless dongle arrives and you test it, I would appreciate an update here as I have't yet tested it on Xubuntu 15.10.   Thanks much in advance , , , , as this would be an easy way for most folks to avoid going back to windows, and all that overhead expense at later times.

PS:   I have tested it from Ubuntu 12.04 thru and including 15.04 (with full compatibility) . . . but haven't had chance to do just yet with 15.10 as that lappie is out of town just now.

Update: I just received the Panda PAU03 mini-Wi-Fi dongle, and [COLOR=#d3d3d3]it works great when I boot from a Mint 17.2 Live USB stick.  It is very sensitive, even more so than the built-in RTL8723BE Wi-Fi card with single antenna.  It is definitely a good option for someone who wants something that "just works"!  [/COLOR][COLOR=#000000]well, see below:[/COLOR]

---

### Post by jeremy31 on 2015-12-14
> **Jerry_Gorland said:**
> Update: I just received the Panda PAU03 mini-Wi-Fi dongle, and it works great when I boot from a Mint 17.2 Live USB stick.  It is very sensitive, even more so than the built-in RTL8723BE Wi-Fi card with single antenna.  It is definitely a good option for someone who wants something that "just works"!

How are you judging sensitivity?  By the number of wireless access points or by download speed as I wouldn't trust a lot of reported signal strength indicators

---

### Post by Jerry_Gorland on 2015-12-15
Umm, er, I take that back.  There were a lot of access points, but it seems that I cannot log into my own.  The circle just keeps rotating.  I might need to dig further (e.g., disable the existing NIC).  Sorry for the confusion.

---

### Post by chili555 on 2015-12-16
> I might need to dig further (e.g., **disable the existing NIC**).Yes, indeed! Let us know if you need guidance to do so.

---

### Post by Kevin_Gormley on 2015-12-23
I suspect this may solve my problem. The big problem appears to be that it's only just connecting, and moving even a little from the router drops the signal. No similar problems when the laptop had Windows. Need to pick up a #000 Phillips (#00 won't remove the screws by the cd drive) to give this a shot, but an edit to the driver would certainly be preferable. 

Once I manage to get the laptop open, I'll update with my experience.

Kevin

---

### Post by chili555 on 2015-12-23
I would love to find the software solution. So far, it is unavailable. 

Here is more information on the subject: [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)

---

### Post by nmlferreira on 2015-12-23
Guys, I have been following this thread for since I purchased my HP Stream 11-r-010nr. Just to make sure I understand, your solution for this issue is to open the laptop and connect the antenna cable from connection 1 to connection 2, correct?

---

### Post by chili555 on 2015-12-23
> **nmlferreira said:**
> Guys, I have been following this thread for since I purchased my HP Stream 11-r-010nr. Just to make sure I understand, your solution for this issue is to open the laptop and connect the antenna cable from connection 1 to connection 2, correct?That is a probable solution.

Please follow all the safety precautions listed in the service manual I am certain is available on line. You know, grounding, unplugging, hazmat suit, clean room, no spouses allowed to spectate, etc.; all that stuff.

[http://ecx.images-amazon.com/images/I/41ZJpoCxkCL.jpg](http://ecx.images-amazon.com/images/I/41ZJpoCxkCL.jpg)

---

### Post by Jerry_Gorland on 2015-12-27
Haha, that hazmat suit doesn't look conductive!  This is what fixed the Wi-FI issues on my Stream 11. I didn't wear a grounding strap (or hazmat suit), but made sure I was discharged to a metal ground point (screw on the AC outlet) before I did anything. Then I didn't walk over a carpet in my wool sweater.  Note that taking apart the laptop may/probably void the warranty.

Refer to Chpater 5 in the maintenance manual at [http://h10032.www1.hp.com/ctg/Manual/c04795670](http://h10032.www1.hp.com/ctg/Manual/c04795670). 

There are 11 screws to take off on the bottom (note four under the rubber feet and two under small rubber covers). Carefully use a thin blade/knife to help lift off the rubber feet. Use a thin plastic tool to separate the keyboard cover from the bottom body. If you use a metal screwdriver you will leave a lot of little indentations and it won't be pretty. I used a plastic tool meant for paint edging, but you can purchase the proper ones online for $2. Get some courage and pry the two apart... they do separate and the keyboard cover comes away, but be careful of the wires attached to the keyboard. The Wi-Fi card is located near the back. Pry the Wi-Fi connector off the Wi-Fi board with your fingers/nails by lifting straight up. Then, carefully position it over the other connector and press down. You will feel it click into place. 

By the way, I needed to also install the rtlwifi_new driver to make the connection stable (per [http://askubuntu.com/questions/623001/how-to-install-realtek-rtl8723be-wifi-pcie-wireless-network-adapter](http://askubuntu.com/questions/623001/how-to-install-realtek-rtl8723be-wifi-pcie-wireless-network-adapter)).  More details at this post: [http://ubuntuforums.org/showthread.php?t=1543006&page=165&p=13403380#post13403380](http://ubuntuforums.org/showthread.php?t=1543006&page=165&p=13403380#post13403380).

Good luck!

> **chili555 said:**
> Yes, indeed! Let us know if you need guidance to do so.

I finally got around for a 2nd look at the Panda USB Wi-Fi dongle, and tried the following:
sudo modprobe -r rtl8723ae  (i.e., the existing internal NIC)
sudo service network-manager restart

The Panda still won't connect. Attached is the wireless-info.txt if it is informative at all.  Hmmm.

---

### Post by chili555 on 2015-12-28
> **Jerry_Gorland said:**
> I finally got around for a 2nd look at the Panda USB Wi-Fi dongle, and tried the following:
sudo modprobe -r rtl8723ae  (i.e., the existing internal NIC)
sudo service network-manager restart

The Panda still won't connect. Attached is the wireless-info.txt if it is informative at all.  Hmmm.I suggest you start a new thread about your Panda USB. Otherwise, it will get lost and largely ignored in this RTL8723BE thread.

---

### Post by Keith_Henderson on 2015-12-28
I own a HP Stream 11 with the RTL8723be, and I saw absolutely no wireless signal whatsoever until I opened up the laptop and switched the antenna to the other connector.  

THANK YOU for posting that solution.  It was nerve wracking, but worth it.  

I have also updated to the rtlwifi_new driver and hope it'll be stable as well as functional. :)

---

### Post by chili555 on 2015-12-28
> **Keith_Henderson said:**
> I own a HP Stream 11 with the RTL8723be, and I saw absolutely no wireless signal whatsoever until I opened up the laptop and switched the antenna to the other connector.  

THANK YOU for posting that solution.  It was nerve wracking, but worth it.  

I have also updated to the rtlwifi_new driver and **hope it'll be stable as well as functional.** :)We will look forward to your report.

---

### Post by inigoD on 2015-12-28
Same problem here....

And the laptop stills in warranty so I can't open it... I rather prefer to get my money back....

Here:

[https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)

The main maintainer of the driver asks for help to fix this problem...

I would like to help but... well, my C skills are not so good....

Anyway I'll try it tomorrow if I get some help from him about where can I find the antenna selection...

---

### Post by Jerry_Gorland on 2015-12-29
> **inigoD said:**
> Same problem here....

And the laptop stills in warranty so I can't open it... I rather prefer to get my money back....
...
[https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)
...
The main maintainer of the driver asks for help to fix this problem...
...

Certainly a reasonable thing to do since a warranty is generally a nice thing to have.  It's hard to get a Linux-friendly/inexpensive laptop.  For those willing to throw caution to the wind, the Stream 11 is pretty sweet.  I feel for the maintainer of rtlwifi_new.  He can't fix what he can't observe.  I wonder if Realtek's tech support would be of any help in locating that one register write that is needed somewhere?

---

### Post by jeremy31 on 2015-12-29
Actually, as of 4 hours ago, it seems he has something available in the 'test' branch and is looking for people to try it

---

### Post by chili555 on 2015-12-29
When one of you is ready to test:```
sudo apt-get update
sudo apt-get install build-essential linux-headers-generic
wget https://github.com/lwfinger/rtlwifi_new/archive/test.zip
unzip test.zip
cd rtlwifi_new-test
make
sudo make install
```Now reboot and test:```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=1

```
Test the results. Then

```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=2
```

Test again. Is one or the other better? If so then do the following:

```
sudo -i
echo "options rtl8723be ant_sel=Y" > /etc/modprobe.d/50-rtl8723be.conf
exit
```

where Y is 1 or 2 depending on which works better.

---

### Post by Alamri on 2015-12-29
Ok i went through the hard way.. Replacing the connector... It was very difficult (maybe for me) as i couldn't recognize the driver and it was very small hidden beside the board covered with a small sticker. Altho it has small numbers 1 and 2..it was connected in 1.. A very small tiny wire.. I managed to switch it to port 2 i will include a photo of how it looks in HP pavilion x360 13-s100nx..

Btw that fixed everything i installed Ubuntu 15.10 again ( fresh install ) it seems that Ubuntu recognize it perfectly.. No need to blacklist anything or to change any configurations or install any drivers it just worked directly like it worked on windows..

Here how it looks ( red dot is connector 1. Green is 2)
[http://i.imgur.com/DBIkUwm.jpg](http://i.imgur.com/DBIkUwm.jpg)

Happy to lose my warranty just the second day of the laptop age :)

---

### Post by Jerry_Gorland on 2015-12-31
Great to hear, Alamri.  Now, chilli555, those are great step-by-step instructions.  I am a bit hesitant to take my laptop apart to test it out, but am thinking about it.  Hopefully another volunteer with a fresh machine will test it out.  As long as a person can be co-located with their router (within a few feet, max) they should be able to get the files on their PC and do the build.
Update:  Looks like *lwfinger* is in touch with a Realtek engineer.  Cool.  However, *inigodm* does not report success ([https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)).

---

### Post by jeremy31 on 2015-12-31
> **Jerry_Gorland said:**
> Great to hear, Alamri.  Now, chilli555, those are great step-by-step instructions.  I am a bit hesitant to take my laptop apart to test it out, but am thinking about it.  Hopefully another volunteer with a fresh machine will test it out.  As long as a person can be co-located with their router (within a few feet, max) they should be able to get the files on their PC and do the build.

You wouldn't need to take it apart.  If the test works, one parameter setting should have the same results as moving the antenna wire to the other connector and if the test module doesn't work at all, remove it by changing into the rtlwifi_new-test directory and ```
sudo make uninstall
```

---

### Post by Jerry_Gorland on 2016-01-02
Unfortunately the fix doesn't work and lwfinger is waiting on a driver fix from Realtek:   [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28)

---

### Post by chili555 on 2016-01-02
From the link:> The Realtek engineer says that their group is working on code that will detect which connector has the antenna. **Until that is ready, switching the connector is the only option **as long as your vendor is not matching the connected pin to the EEPROM on the card.

---

### Post by marco-zamana1 on 2016-01-05
> **Jerry_Gorland said:**
> SOLUTION for my particular case (HP Stream 11-r010 Cloudbook with N3050 Celeron and HP Model No. 792204-001 30x22mm M.2 Wi-Fi card):  Moving the single antenna cable from one connector to the other (as shown in the attached diagram) solved the problem.  This would explain why the laptop worked only when sitting right next to the Wi-Fi router:  With Linux the card is configured to use the other connector compared to Windows.  Now I am two floors up from my router and connected well with Xubuntu 14.04.  With Xubuntu, all the hotkeys work.  I tried Mint 17.2, but I was unable to adjust the display brightness.  I am still going to test out the Panda Wi-Fi dongle when I get it.

I bought yesterday this notebook hp 255 G4 and i've spent a lot of time for understand how i can solve this "bug".
After a day i solved. I solved moving the antenna cable from one to other like Jerry explain before... Yes i opened my notebook for do that, but now it works perfectly.
Hope this helps.

---

### Post by kraestal on 2016-01-06
Thank you.

Now WiFi work on my HP Stream 2015 11-r010, i writed a guide with some images (italian):
[http://www.osside.net/?p=15640](http://www.osside.net/?p=15640)

---

### Post by pchokola on 2016-01-06
> **kraestal said:**
> Thank you.

Now WiFi work on my HP Stream 2015 11-r010, i writed a guide with some images (italian):
[http://www.osside.net/?p=15640](http://www.osside.net/?p=15640)

I just bought the same exact laptop a couple of weeks ago.  I am using an external USB network adapter (Atheros) to bypass the internal wifi card (Realtek) while running Linux for the time being.  I will wait a while for an updated Realtek driver, but I might get antsy and rip apart the laptop eventually so I can free up that USB port for my mouse transmitter (The only other USB port holds my Linux boot up flash drive), so thanks for the write-up.

---

### Post by Jerry_Gorland on 2016-01-08
> **kraestal said:**
> Thank you.

Now WiFi work on my HP Stream 2015 11-r010, i writed a guide with some images (italian):
[http://www.osside.net/?p=15640](http://www.osside.net/?p=15640)

Very nice!  I like the pictures.  Here is an English translation:  [https://translate.google.ca/translate?sl=auto&tl=en&js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.osside.net%2F%3Fp%3D15640&edit-text=](https://translate.google.ca/translate?sl=auto&tl=en&js=y&prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.osside.net%2F%3Fp%3D15640&edit-text=)   I am glad it worked out.  Using the pizza cutter is a novel idea.

---

### Post by lwta08 on 2016-01-17
Thank you all for the valuable hints.

Got my WiFi working on **HP X360 13-S-0130ng** by changing the WiFi antenna to input #2.

For instructions to open the case etc. refer to the service manual for HP X360 13-s which can be found here:
[http://h10032.www1.hp.com/ctg/Manual/c04582281](http://h10032.www1.hp.com/ctg/Manual/c04582281)


I also had to blacklist the acer_wmi module in /etc/modprobe.d/blacklist.conf:

```
sudo -i
modprobe -r acer_wmi
echo "blacklist acer_wmi"  >>  /etc/modprobe.d/blacklist.conf
exit
```

Details here:
[https://wiki.ubuntuusers.de/rfkill/](https://wiki.ubuntuusers.de/rfkill/)


Now everything works perfectly.

---

### Post by Jerry_Gorland on 2016-01-18
Looks like there might be some ground-breaking progress on this one with a s/w fix:  [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28).

---

### Post by lwta08 on 2016-01-19
> **Jerry_Gorland said:**
> Looks like there might be some ground-breaking progress on this one with a s/w fix:  [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28).

I tried the driver from rock.the new_btcoex branch and it is working fine on my HP x360 13-s laptop.

Here is what I did:

I downloaded the code from [https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex) , unzipped it and then:

```

$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
sudo ip link set wlp2s0 up
sudo iw dev wlp2s0 scan

```

The scan then showed all networks with expected signal strength.

To make the settings permanent:

```

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf

```

Note:
I had to use the parameter** ant_sel=2** even though my antenna is connected to antenna** input #1** !
Using ant_sel=1 (what I tried first) did not work.

---

### Post by Jerry_Gorland on 2016-01-19
That's awesome.  This is a much better solution than having to take the box apart.  I'm going to leave mine as-is, though.  The downside is that you need to co-locate your laptop initially right next to the Wi-Fi router (within about 3 to 5 feet) in order to download the new driver, but it is a portable laptop after all!

---

### Post by pchokola on 2016-01-24
> **Jerry_Gorland said:**
> Looks like there might be some ground-breaking progress on this one with a s/w fix:  [https://github.com/lwfinger/rtlwifi_new/issues/28](https://github.com/lwfinger/rtlwifi_new/issues/28).

This worked for my HP Stream 11.  I selected ant # 2 and now I have excellent reception and range using Linux Mint 17.3.  Best part is I didn't have to rip apart the laptop.

---

### Post by muzbox2 on 2016-01-28
> **Jerry_Gorland said:**
>  SOLUTION for my particular case (HP Stream 11-r010 Cloudbook with N3050 Celeron and HP Model No. 792204-001 30x22mm M.2 Wi-Fi card):  Moving the single antenna cable from one connector to the other (as shown in the attached diagram) solved the problem.  This would explain why the laptop worked only when sitting right next to the Wi-Fi router:  With Linux the card is configured to use the other connector compared to Windows.  Now I am two floors up from my router and connected well with Xubuntu 14.04.  With Xubuntu, all the hotkeys work.  I tried Mint 17.2, but I was unable to adjust the display brightness.  I am still going to test out the Panda Wi-Fi dongle when I get it.

Awesome! My Wi-fi now working fine on my HP Notebook 14-af105AX - thanks for the help, pic and follow up instructions!

---

### Post by ErmenegildoRos on 2016-01-28
Hello guys.
I have the same problem but this post is a bit confusing, I don't really get what I have to do to fix the problem.
I already tried post #52.
Can you please help me with this?

Thank you!

---

### Post by chili555 on 2016-01-28
> **ErmenegildoRos said:**
> Hello guys.
I have the same problem but this post is a bit confusing, I don't really get what I have to do to fix the problem.
I already tried post #52.
Can you please help me with this?

Thank you!Please replay the steps you took following post #52 above. If it isn't working, then I suspect one of the steps ended in an error. Please post any errors and we'll try to help you fix them.

If you are having trouble remembering, you can see the last (1000? many??) commands you issued in the terminal with:```
history
```

---

### Post by manurss on 2016-01-30
[SIZE=2][FONT=arial][COLOR=#000000]ErmenegildoRos r[/COLOR][/FONT][FONT=arial]emember to take the correct name for your computer. The post #52 say [COLOR=#000000]wlp2s0, you can look what is yours with the ifconfig command (discard eth and lo).

By the way, I try it in a hp stream 11 2015 ([/COLOR][r000ns]("http://store.hp.com/SpainStore/Merch/product.aspx?sel=NTB&id=P0F28EA&opt=ABE")[COLOR=#000000]) with no result. May this is a fix just for some computers...[/COLOR][/FONT][/SIZE]

---

### Post by chili555 on 2016-01-30
> **manurss said:**
> [SIZE=2][FONT=arial][COLOR=#000000]ErmenegildoRos r[/COLOR][/FONT][FONT=arial]emember to take the correct name for your computer. The post #52 say [COLOR=#000000]wlp2s0, you can look what is yours with the ifconfig command (discard eth and lo).

By the way, I try it in a hp stream 11 2015 ([/COLOR][r000ns]("http://store.hp.com/SpainStore/Merch/product.aspx?sel=NTB&id=P0F28EA&opt=ABE")[COLOR=#000000]) with no result. May this is a fix just for some computers...[/COLOR][/FONT][/SIZE]I suggest you start a new thread and post the wireless script mentioned in the stickie at the top of this forum and we'll be glad to help.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by Avirup_Das on 2016-02-06
Hi,

I have successfully installed rock.new_btcoex.zip on my system and changed the antenna to 2. Now I can see all the available WiFi networks around and also the signal strengths are good, However, for some reason I am unable to connect to my network. It simply fails to connect.

I am using HP-15 AU006Ax

---

### Post by chili555 on 2016-02-06
> **Avirup_Das said:**
> Hi,

I have successfully installed rock.new_btcoex.zip on my system and changed the antenna to 2. Now I can see all the available WiFi networks around and also the signal strengths are good, However, for some reason I am unable to connect to my network. It simply fails to connect.I suggest you start a new thread and include the information requested in the sticky: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by i-mebonia on 2016-03-03
This works like a charm, thank you for posting this solution, I've been suffering since November and it seemed there was no solution...

---

### Post by anu_di on 2016-03-15
Hello,

Have you started new thread on this  :

[COLOR=#000000][I]" I have successfully installed rock.new_btcoex.zip on my system and changed the antenna to 2. Now I can see all the available WiFi networks around and also the signal strengths are good, However, for some reason I am unable to connect to my network. It simply fails to connect. "

because i am also facing the same problem.

I am able to discover the networks after following #52 post but unable to connect.[/I][/COLOR]

---

### Post by jeremy31 on 2016-03-15
> **anu_di said:**
> Hello,

Have you started new thread on this  :

[COLOR=#000000][I]" I have successfully installed rock.new_btcoex.zip on my system and changed the antenna to 2. Now I can see all the available WiFi networks around and also the signal strengths are good, However, for some reason I am unable to connect to my network. It simply fails to connect. "

because i am also facing the same problem.

I am able to discover the networks after following #52 post but unable to connect.[/I][/COLOR]

If you can, follow chili555's link(post #61) and post the info after running the wireless script command, the file will be named wireless-info.txt

---

### Post by anu_di on 2016-03-16
> **jeremy31 said:**
> If you can, follow chili555's link(post #61) and post the info after running the wireless script command, the file will be named wireless-info.txt


Hello i have run the script mentioned there and ("wireless-info.tar.gz") is attached herewith. Actually i haven't applied those change permanently (because i first want to see weather this procedure is working or not ) i.e this command haven`t been used : 

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf

hence these settings are not permanent so when i restart my system wi-fi get connected within 1ft of router with less signal strength but i want to use it in 10ft range with improved signal strength.

---

### Post by chili555 on 2016-03-16
> i.e this command haven`t been used :

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
I'm confused.

First of all, the command you've shown is incorrect. It ought to be:```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```Or you might even do:```
sudo -i
echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf"
exit
```But you said you did *NOT* use the command. However, your wireless script shows:> [rtl8723be]
[COLOR="#FF0000"]ant_sel: 2[/COLOR]
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: NAnd it also shows:> Cell 03 - Address: <MAC 'pradeep HI-SPEED 8750586440 ' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    [COLOR="#FF0000"]Quality=70/70[/COLOR]  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"pradeep HI-SPEED 8750586440 "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000bbd535c4
                    Extra: Last beacon: 0ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSKSo how did *ant_sel=2* get there if you didn't put it there?

I'm confused.

By the way, I have worked on more than one case here where spaces in the name have caused difficulties connecting. I suggest you go to the administration pages of your router and change the name from pradeep HI-SPEED 8750586440 to pradeep_HI-SPEED_8750586440 or pradeep6440 or something without spaces and see if you can then properly connect.

---

### Post by anu_di on 2016-03-17
> **chili555 said:**
> I'm confused.

First of all, the command you've shown is incorrect. It ought to be:```
echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf
```Or you might even do:```
sudo -i
echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf"
exit
```But you said you did *NOT* use the command. However, your wireless script shows:And it also shows:So how did *ant_sel=2* get there if you didn't put it there?


Hello,
 I have said that i have not used following command :

echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf

as the above command said that it is to make settings permanently and i just wanted to check first before applying permanently so i have used these commands :

$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
sudo ip link set wlp2s0 up
sudo iw dev wlp2s0 scan

and after these command i got the proper signal strength but unable to connect.

---

### Post by chili555 on 2016-03-17
In addition to this suggestion:> By the way, I have worked on more than one case here where spaces in the name have caused difficulties connecting. I suggest you go to the administration pages of your router and change the name from pradeep HI-SPEED 8750586440 to pradeep_HI-SPEED_8750586440 or pradeep6440 or something without spaces and see if you can then properly connect. I also suggest that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Now can you connect?

---

### Post by SATANoiD on 2016-04-02
> **lwta08 said:**
> I tried the driver from rock.the new_btcoex branch and it is working fine on my HP x360 13-s laptop.

Here is what I did:

I downloaded the code from [https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex) , unzipped it and then:

```

$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
sudo ip link set wlp2s0 up
sudo iw dev wlp2s0 scan

```

The scan then showed all networks with expected signal strength.

To make the settings permanent:

```

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf

```

Note:
I had to use the parameter** ant_sel=2** even though my antenna is connected to antenna** input #1** !
Using ant_sel=1 (what I tried first) did not work.

facing the same issue .. so I am here on this thread. BTW, I am totally new to ubuntu, installed last night and had difficulties to connect to wifi. 
yet, I gave a try to this method but I get error below whenever I try to run a command: 


on : $ make
```

make -C /lib/modules/4.2.0-34-generic/build M=/media/pawan/Softwares/Driver/wifi driver fix Ubuntu/rtlwifi_new-rock.new_btcoex modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-34-generic'
arch/x86/Makefile:138: CONFIG_X86_X32 enabled but no binutils support
Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
make[1]: *** No rule to make target 'driver'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-34-generic'
Makefile:58: recipe for target 'all' failed
make: *** [all] Error 2

```


on : $ sudo make install
```

make -C /lib/modules/4.2.0-34-generic/build M=/media/pawan/Softwares/Driver/wifi driver fix Ubuntu/rtlwifi_new-rock.new_btcoex modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-34-generic'
arch/x86/Makefile:138: CONFIG_X86_X32 enabled but no binutils support
Makefile:669: Cannot use CONFIG_CC_STACKPROTECTOR_STRONG: -fstack-protector-strong not supported by compiler
make[1]: *** No rule to make target 'driver'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-34-generic'
Makefile:58: recipe for target 'all' failed
make: *** [all] Error 2

```


on : $ sudo modprobe -rv rtl8723be
```

rmmod rtl8723be
rmmod rtl_pci
rmmod rtlwifi
rmmod rtl8723_common
rmmod btcoexist

```

on : $ sudo modprobe -v rtl8723be ant_sel=2
```

insmod /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko 
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/btcoexist/btcoexist.ko 
insmod /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko ant_sel=2

```


on : $ sudo ip link set wlp2s0 up
```

Cannot find device "wlp2s0"

```

Please Help ! :(

---

### Post by Bucky Ball on 2016-04-02
@SATANoiD: You do yourself no favours posting this deep with a new problem. The original problem was a while ago. You know for sure you are using the same wireless card as in the title of the thread?

Welcome. I advise you run the wirelessinfo script in my signature at the bottom of this post and post the output in a new thread with a descriptive title for the best chance of support. 

Good luck.

---

### Post by jeremy31 on 2016-04-02
Need to change the name of the folder that contains the source code to something without spaces like ```
wifi-driver-fix-Ubuntu
```

---

### Post by SATANoiD on 2016-04-02
> **Bucky Ball said:**
> @SATANoiD: You do yourself no favours posting this deep with a new problem. The original problem was a while ago. You know for sure you are using the same wireless card as in the title of the thread?

Welcome. I advise you run the wirelessinfo script in my signature at the bottom of this post and post the output in a new thread with a descriptive title for the best chance of support. 

Good luck.


Thanks for quick reply Bucky. Yeah, I was pretty sure that my wifi adapter is RTL8723BE .. you can find same in the info you asked to fetch. 

I don't understand why I get errors (mentioned in last post) when running those commands, where other people had success in fixing problem. 

like I mentioned I am new to ubuntu and linux, so may be I am doing something wrong. I am not sure where to place these driver files and run commands. 

```


########## wireless info START ##########

Report from: 02 Apr 2016 14:01 IST +0530

Booted last: 02 Apr 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
    Subsystem: Hewlett-Packard Company Device [103c:804c]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company Device [103c:8099]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd Wireless keyboard/mouse
Bus 001 Device 002: ID 05c8:0379 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              77824  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              471040  2 ath9k_common,ath9k_htc
ath                    32768  3 ath9k_common,ath9k_htc,ath9k_hw
rtl8723be              86016  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              733184  4 rtl_pci,rtlwifi,ath9k_htc,rtl8723be
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  5 ath,ath9k_common,mac80211,rtlwifi,ath9k_htc
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:508 (508.0 B)  TX bytes:7041 (7.0 KB)

wlxe8de270fab4c Link encap:Ethernet  HWaddr <MAC 'wlxe8de270fab4c' [IF]>  
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlxe8de270fab4c' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3617321 (3.6 MB)  TX bytes:267229 (267.2 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
wlxe8de270fab4c  IEEE 802.11bgn  ESSID:"negi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'negi' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:28   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlxe8de270fab4c
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlxe8de270fab4c
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlxe8de270fab4c

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       607     1  0 13:56 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlxe8de270fab4c
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         ATHEROS
GENERAL.PRODUCT:                        USB2.0 WLAN
GENERAL.DRIVER:                         ath9k_htc
GENERAL.DRIVER-VERSION:                 4.2.0-34-generic
GENERAL.FIRMWARE-VERSION:               1.3
GENERAL.HWADDR:                         <MAC 'wlxe8de270fab4c' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/wlxe8de270fab4c
GENERAL.IP-IFACE:                       wlxe8de270fab4c
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     negi 1
GENERAL.CON-UUID:                       7c77c1e1-c797-4270-81ab-e7aabf76bf08
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   7c77c1e1-c797-4270-81ab-e7aabf76bf08 | negi 1
IP4.ADDRESS[1]:                         192.168.0.108/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1459589826
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.108
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlxe8de270fab4c' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.2.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
negi     <MAC 'negi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       yes     * 
karthik  <MAC 'karthik' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Belkin.354B]] (600 root)
[connection] id=Belkin.354B | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=Belkin.354B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/negi 1]] (600 root)
[connection] id=negi 1 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlxe8de270fab4c' [IF]> | mac-address-blacklist= | ssid=negi
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/negi]] (600 root)
[connection] id=negi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=negi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

wlo1      11 channels in total; available frequencies :
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
wlxe8de270fab4c  11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      No scan results

wlxe8de270fab4c  Scan completed :
          Cell 01 - Address: <MAC 'negi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"negi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000096227d60b
                    Extra: Last beacon: 380ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'karthik' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"karthik"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f756b3179
                    Extra: Last beacon: 6396ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Hunter' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"Hunter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008896214bb8
                    Extra: Last beacon: 9580ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     56ECCCF5270ED7B9AD6E283
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           blink:Enable LED blink on activity (int)

[ath9k_common]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     619327754B562F78060585E
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F987BF2735D3EF13C4E4E3D
depends:        ath
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     F1417AD8012BEEF1598B307
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[rtl8723be]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     F4CACC5FCAEBE7C22930A24
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
blink: 1
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   20.125550] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 2 times)
[   20.708167] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   20.740218] r8169 0000:09:00.0 eno1: link down
[   20.740262] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   20.805494] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[   25.327843] wlo1: authenticate with <MAC 'negi' [AC1]>
[   25.340251] wlo1: send auth to <MAC 'negi' [AC1]> (try 1/3)
[   25.443963] wlo1: send auth to <MAC 'negi' [AC1]> (try 2/3)
[   25.447459] wlo1: authenticated
[   25.447943] wlo1: associate with <MAC 'negi' [AC1]> (try 1/3)
[   25.551997] wlo1: associate with <MAC 'negi' [AC1]> (try 2/3)
[   25.656053] wlo1: associate with <MAC 'negi' [AC1]> (try 3/3)
[   25.661001] wlo1: RX AssocResp from <MAC 'negi' [AC1]> (capab=0x431 status=0 aid=4)
[   25.661381] wlo1: associated
[   25.661408] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[   54.540720] wlo1: Connection to AP <MAC 'negi' [AC1]> lost
[   55.515901] wlo1: authenticate with <MAC 'negi' [AC1]>
[   55.539110] wlo1: send auth to <MAC 'negi' [AC1]> (try 1/3)
[   55.639574] wlo1: send auth to <MAC 'negi' [AC1]> (try 2/3)
[   55.743628] wlo1: send auth to <MAC 'negi' [AC1]> (try 3/3)
[   55.847681] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[   72.065651] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 6 times)
[  204.120130] usb 1-2: ath9k_htc: Firmware htc_9271.fw requested
[  204.120243] usbcore: registered new interface driver ath9k_htc
[  204.416203] usb 1-2: ath9k_htc: Transferred FW: htc_9271.fw, size: 50980
[  204.656443] ath9k_htc 1-2:1.0: ath9k_htc: HTC initialized with 33 credits
[  205.717961] ath9k_htc 1-2:1.0: ath9k_htc: FW Version: 1.3
[  205.717964] ath9k_htc 1-2:1.0: FW RMW support: Off
[  205.717966] ath: EEPROM regdomain: 0x809c
[  205.717967] ath: EEPROM indicates we should expect a country code
[  205.717968] ath: doing EEPROM country->regdmn map search
[  205.717969] ath: country maps to regdmn code: 0x52
[  205.717970] ath: Country alpha2 being used: CN
[  205.717971] ath: Regpair used: 0x52
[  205.726798] ath9k_htc 1-2:1.0 wlxe8de270fab4c: renamed from wlan0
[  205.750499] IPv6: ADDRCONF(NETDEV_UP): wlxe8de270fab4c: link is not ready (repeated 3 times)
[  207.561990] wlxe8de270fab4c: authenticate with <MAC 'negi' [AC1]>
[  207.961527] wlxe8de270fab4c: send auth to <MAC 'negi' [AC1]> (try 1/3)
[  207.963753] wlxe8de270fab4c: authenticated
[  207.966026] wlxe8de270fab4c: associate with <MAC 'negi' [AC1]> (try 1/3)
[  207.970018] wlxe8de270fab4c: RX AssocResp from <MAC 'negi' [AC1]> (capab=0x431 status=0 aid=3)
[  207.980172] wlxe8de270fab4c: associated
[  207.980209] IPv6: ADDRCONF(NETDEV_CHANGE): wlxe8de270fab4c: link becomes ready

########## wireless info END ############



```

---

### Post by jeremy31 on 2016-04-02
Copy the rtlwifi_new.rock.new_btcoex folder to your desktop, then
```
cd ~/Desktop/rtlwifi_new.rock.new_btcoex
```

Then try the make and sudo make install commands

make doesn't work with directory names that have spaces

---

### Post by SATANoiD on 2016-04-02
> **jeremy31 said:**
> Need to change the name of the folder that contains the source code to something without spaces like ```
wifi-driver-fix-Ubuntu
```

THAT WORKED !! now I have working wifi like Windows :) 

Thanks Jeremy, spaces in the folder name were causing the errors. I changed like you suggested .. and it worked jst fine. 
1. $ make
2. $ sudo make install
3. $ sudo modprobe -rv rtl8723be
4. $ sudo modprobe -v rtl8723be ant_sel=2
5. $ echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf


as soon as I hit the 4th command, It started detecting the available networks, and I was able to connect to my wifi network as well.
5th Command I used to make settings permanent, otherwise on the next boot you'll have to repeat the commands again. 

Many thanks to everyone for help !!

---

### Post by SATANoiD on 2016-04-02
Well, I was able to connect to the my Wifi Network and Internet earlier like I mentioned . But suddenly its **not able to connect anymore**. It jst keeps on connecting to network. Something's broken in the code I guess. 
I installed the driver again from step 1 to 4

1. $ make
2. $ sudo make install
3. $ sudo modprobe -rv rtl8723be
4. $ sudo modprobe -v rtl8723be ant_sel=2

and again successfully able to connect to the Network .. but now there is no more Internet access :(

I've mailed the Realtek WLAN Tech Team to look into the matter .. but not sure when will they take action on it. :?

here's is my **wireless-info** when I was **unable to connect** to Network

```


########## wireless info START ##########

Report from: 02 Apr 2016 18:44 IST +0530

Booted last: 02 Apr 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
    Subsystem: Hewlett-Packard Company Device [103c:804c]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company Device [103c:8099]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05c8:0379 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 007: ID 05c6:9024 Qualcomm, Inc. 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0
btcoexist             425984  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              733184  3 rtl_pci,rtlwifi,rtl8723be
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
cfg80211              548864  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx0254040a3738 Link encap:Ethernet  HWaddr <MAC 'enx0254040a3738' [IF]>  
          inet addr:192.168.42.215  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx0254040a3738' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31406 errors:11 dropped:0 overruns:0 frame:0
          TX packets:19726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41024621 (41.0 MB)  TX bytes:2638106 (2.6 MB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34486 (34.4 KB)  TX bytes:18724 (18.7 KB)

##### iwconfig ##########################

eno1      no wireless extensions.

lo        no wireless extensions.

enx0254040a3738  no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx0254040a3738
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enx0254040a3738
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx0254040a3738

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       607     1  0 18:06 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx0254040a3738
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         YU
GENERAL.PRODUCT:                        YU5010
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx0254040a3738' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enx0254040a3738
GENERAL.IP-IFACE:                       enx0254040a3738
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       23ab7d48-1aa3-4aa9-8b40-9498e2a2a152
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/22
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   23ab7d48-1aa3-4aa9-8b40-9498e2a2a152 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.215/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.215
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1459605178
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = pawan-HP-Pavilion-Notebook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx0254040a3738' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.2.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cbd6ade1-a1ca-42fc-9d24-3e710964545e | negi

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
karthik       <MAC 'karthik' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
negi          <MAC 'negi' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
OrinocoDLink  <MAC 'OrinocoDLink' [AC4]>  Infra  8     2447 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        
Hunter        <MAC 'Hunter' [AC2]>  Infra  11    2462 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Belkin.354B]] (600 root)
[connection] id=Belkin.354B | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=Belkin.354B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/negi]] (600 root)
[connection] id=negi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=negi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

eno1      no frequency information.

lo        no frequency information.

enx0254040a3738  no frequency information.

wlo1      13 channels in total; available frequencies :
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

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enx0254040a3738  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlo1      Scan completed :
          Cell 01 - Address: <MAC 'negi' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"negi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000758dc180
                    Extra: Last beacon: 392ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Hunter' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Hunter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008c89a17180
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'karthik' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"karthik"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002e991a173
                    Extra: Last beacon: 712ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'OrinocoDLink' [AC4]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"OrinocoDLink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000f5e0867173
                    Extra: Last beacon: 412ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Hunter' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Hunter"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000007f4478180
                    Extra: Last beacon: 188ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     2DA37D00E0E770F2130B511
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl_pci]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     ACFA86E46F5F40757CBEE97
depends:        mac80211,rtlwifi
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     49A8F1B71F07B5F00344D4F
depends:        mac80211,cfg80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=2

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 1199.056410] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1199.079596] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1199.280265] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1199.484534] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1199.688710] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1204.684797] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1213.695154] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1213.718833] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1213.922776] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1214.126935] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1214.331131] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1229.707586] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1531.056681] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1531.079890] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1531.283707] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1531.487705] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1531.691700] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1542.997563] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1543.021642] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1543.225240] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1543.429447] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1543.633547] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1554.764003] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1554.943226] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1554.966689] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1555.170353] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1555.374496] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1555.578583] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1566.874627] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1566.898050] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1567.098302] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1567.302458] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1567.506545] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1579.779843] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1581.062973] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1581.086436] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1581.286634] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1581.490783] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1581.694867] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1592.993191] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1593.017762] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1593.220893] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1593.424991] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1593.629054] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1604.792099] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1604.931536] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1604.953924] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1605.154521] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1605.358609] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1605.562700] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1616.868605] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1616.891437] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1617.091688] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1617.295744] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1617.499824] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1629.803742] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1931.307871] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1931.330900] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1931.531444] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1931.735558] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1931.939669] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1949.514146] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1949.537510] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1949.737776] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1949.941869] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1950.145980] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1955.003498] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1956.277822] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1956.301716] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1956.505417] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1956.709535] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1956.913655] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1968.211956] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1968.235587] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1968.439639] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1968.643780] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1968.847811] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1980.016050] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 1982.339645] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1982.363665] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1982.566762] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1982.770813] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1982.974923] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 1994.269568] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 1994.292293] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 1994.492560] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 1994.696573] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 1994.900745] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 2005.368872] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 2006.202653] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 2006.226150] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 2006.430202] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 2006.634294] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 2006.838420] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 2024.402752] wlo1: authenticate with <MAC 'negi' [AC1]>
[ 2024.425992] wlo1: direct probe to <MAC 'negi' [AC1]> (try 1/3)
[ 2024.626518] wlo1: direct probe to <MAC 'negi' [AC1]> (try 2/3)
[ 2024.830666] wlo1: direct probe to <MAC 'negi' [AC1]> (try 3/3)
[ 2025.034722] wlo1: authentication with <MAC 'negi' [AC1]> timed out
[ 2031.040272] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready

########## wireless info END ############



```

and here is **wireless-info** after reinstalling driver and connected to network but **no Internet access**

```


########## wireless info START ##########

Report from: 02 Apr 2016 19:02 IST +0530

Booted last: 02 Apr 2016 00:00 IST +0530

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Realtek RTL8723BE 802.11b/g/n 1x1Wi-Fi + BT4.0 Combo Adapter
    Subsystem: Hewlett-Packard Company Device [103c:804c]

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    DeviceName: Realtek PCIe FE Family Controller
    Subsystem: Hewlett-Packard Company Device [103c:8099]

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05c8:0379 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 015: ID 0fce:819c Sony Ericsson Mobile Communications AB 
Bus 001 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             143360  0
btcoexist             425984  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              733184  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              548864  2 mac80211,rtlwifi
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eno1      Link encap:Ethernet  HWaddr <MAC 'eno1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enx02751b74030b Link encap:Ethernet  HWaddr <MAC 'enx02751b74030b' [IF]>  
          inet addr:192.168.42.48  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx02751b74030b' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64256 (64.2 KB)  TX bytes:56222 (56.2 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202599 (202.5 KB)  TX bytes:31025 (31.0 KB)

##### iwconfig ##########################

enx02751b74030b  no wireless extensions.

eno1      no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11bgn  ESSID:"negi"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'negi' [AN1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enx02751b74030b
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlo1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlo1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlo1
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enx02751b74030b

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       607     1  0 18:06 ?        00:00:06 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enx02751b74030b
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Sony
GENERAL.PRODUCT:                        C6833
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enx02751b74030b' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/net/enx02751b74030b
GENERAL.IP-IFACE:                       enx02751b74030b
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Auto Ethernet
GENERAL.CON-UUID:                       1c42bf49-6da7-4f03-9ecb-1314758929a2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/40
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{5}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1c42bf49-6da7-4f03-9ecb-1314758929a2 | Auto Ethernet
IP4.ADDRESS[1]:                         192.168.42.48/24
IP4.GATEWAY:                            192.168.42.129
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.48
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1459607524
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = pawan-HP-Pavilion-Notebook
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         fe80::<IP6 'enx02751b74030b' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.2.0-34-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlo1' [IF]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0/net/wlo1
GENERAL.IP-IFACE:                       wlo1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     negi
GENERAL.CON-UUID:                       cbd6ade1-a1ca-42fc-9d24-3e710964545e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/39
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     150 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   cbd6ade1-a1ca-42fc-9d24-3e710964545e | negi
IP4.ADDRESS[1]:                         192.168.0.104/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1459610399
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 7200
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       ip_address = 192.168.0.104
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlo1' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eno1' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:09:00.0/net/eno1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
negi     <MAC 'negi' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA2       yes     * 
karthik  <MAC 'karthik' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        
Hunter   <MAC 'Hunter' [AN3]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2  no        
Hunter   <MAC 'Hunter' [AN4]>  Infra  11    2462 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA1 WPA2  no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Belkin.354B]] (600 root)
[connection] id=Belkin.354B | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=Belkin.354B
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/negi]] (600 root)
[connection] id=negi | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlo1' [IF]> | mac-address-blacklist= | ssid=negi
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (N/A, 30), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enx02751b74030b  no frequency information.

eno1      no frequency information.

lo        no frequency information.

wlo1      11 channels in total; available frequencies :
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

enx02751b74030b  Interface doesn't support scanning.

wlo1      Failed to read scan data : Resource temporarily unavailable

eno1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     2DA37D00E0E770F2130B511
depends:        rtl_pci,rtlwifi,btcoexist,mac80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl_pci]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     ACFA86E46F5F40757CBEE97
depends:        mac80211,rtlwifi
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.2.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     49A8F1B71F07B5F00344D4F
depends:        mac80211,cfg80211
vermagic:       4.2.0-34-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     292BCC26A10EA884DF6B5FF
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-34-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        54:4E:45:C0:BD:E6:F7:84:07:7A:BC:A3:DE:58:E4:8F:B5:25:EE:14
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 2
debug: 1
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
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
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/50-rtl8723be.conf]
options rtl8723be ant_sel=2

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

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[ 2410.090359] wlo1: authentication with <MAC 'negi' [AN1]> timed out
[ 2421.387435] wlo1: authenticate with <MAC 'negi' [AN1]>
[ 2421.411028] wlo1: direct probe to <MAC 'negi' [AN1]> (try 1/3)
[ 2421.615006] wlo1: direct probe to <MAC 'negi' [AN1]> (try 2/3)
[ 2421.819117] wlo1: direct probe to <MAC 'negi' [AN1]> (try 3/3)
[ 2422.023200] wlo1: authentication with <MAC 'negi' [AN1]> timed out
[ 2434.194457] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 2638.565567] Using firmware rtlwifi/rtl8723befw.bin
[ 2638.566616] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 2638.567665] rtlwifi: wireless switch is on
[ 2638.570249] rtl8723be 0000:08:00.0 wlo1: renamed from wlan0
[ 2638.590755] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready (repeated 3 times)
[ 2645.514295] wlo1: authenticate with <MAC 'negi' [AN1]>
[ 2645.961039] wlo1: send auth to <MAC 'negi' [AN1]> (try 1/3)
[ 2646.063626] wlo1: send auth to <MAC 'negi' [AN1]> (try 2/3)
[ 2646.167687] wlo1: send auth to <MAC 'negi' [AN1]> (try 3/3)
[ 2646.271693] wlo1: authentication with <MAC 'negi' [AN1]> timed out
[ 2647.232681] wlo1: authenticate with <MAC 'negi' [AN1]>
[ 2647.257370] wlo1: send auth to <MAC 'negi' [AN1]> (try 1/3)
[ 2647.260764] wlo1: authenticated
[ 2647.264210] wlo1: associate with <MAC 'negi' [AN1]> (try 1/3)
[ 2647.269107] wlo1: RX AssocResp from <MAC 'negi' [AN1]> (capab=0x431 status=0 aid=4)
[ 2647.269966] wlo1: associated
[ 2647.269975] IPv6: ADDRCONF(NETDEV_CHANGE): wlo1: link becomes ready
[ 3352.951326] rndis_host 1-2:1.0 enx02751b74030b: renamed from usb0
[ 3352.978756] IPv6: ADDRCONF(NETDEV_UP): enx02751b74030b: link is not ready
[ 3355.160082] rndis_host 1-2:1.0 enx02751b74030b: unregister 'rndis_host' usb-0000:00:14.0-2, RNDIS device
[ 3362.226588] rndis_host 1-2:1.0 enx02751b74030b: renamed from usb0
[ 3362.255761] IPv6: ADDRCONF(NETDEV_UP): enx02751b74030b: link is not ready

########## wireless info END ############



```

Hope the information will help in order to find the cure for this disease ..

---

### Post by chili555 on 2016-04-02
> enx02751b74030b Link encap:Ethernet  HWaddr <MAC 'enx02751b74030b' [IF]>  
          inet addr:[COLOR="#FF0000"]192.168.42.48 [/COLOR] Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enx02751b74030b' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64256 (64.2 KB)  TX bytes:56222 (56.2 KB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF]>  
          inet addr:[COLOR="#FF0000"]192.168.0.104[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlo1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202599 (202.5 KB)  TX bytes:31025 (31.0 KB)Is the enx-whatever an ethernet device? It is very interesting that you have two devices attached to *two different networks* at the same time. I expect that the routing is a mess and that Network Manager and old Chili are very confused.

Please detach the ethernet cable and reboot. Are you able to connect now? Reach the internet??

---

### Post by SATANoiD on 2016-04-03
That's strange, its working now. 
 I had to connect Ethernet internet  (through android mobile usb tethering) to copy paste the wireless-info,  otherwise it'd be pain to copy paste to different computer and post   o.O
I am sure that I was not able to access internet though I was  connected to network, so I had to use my android device to get  internet on my laptop to make last post.

---

### Post by atharvan on 2016-04-28
:D The blog post from connectwww solved my problem. please check it. [How to solve Realtek RTL8723BE weak wifi signal problem in ubuntu]("http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/")

---

### Post by Chirath_R on 2016-05-12
Thank you chili555. your solution fixed my problem in HP Pavillion ab-028tx with the same WiFi chip.the same WiFi chip.

---

### Post by marcello8 on 2016-06-02
HELP me!!!!!
I had the weak signal problem so I made the things written in the posts above

downloaded the new drivers 

then

1. $ make
2. $ sudo make install
3. $ sudo modprobe -rv rtl8723be
4. $ sudo modprobe -v rtl8723be ant_sel=2

After the point 2 I receive the message install rtlwifi success
after the point 3 I have no message
after the point 4 I receive the message ERROR: cuold not insert 'rtl8723be': Required key not available

it seems just like.... I have non driver installed now
the wifi card now results UNCLAIMED
and modeprobe wl gives me the result
modprobe: FATAL: Module wl not found in directory /lib/modules/4.4.0-21-generic

What have I done????
What can I do?

---

### Post by wildmanne39 on 2016-06-02
We will create a key for the new driver so it can be used.
```
openssl req -new -x509 -newkey rsa:2048 -keyout MOK.priv -outform DER -out MOK.der -nodes -days 36500 -subj "/CN=Descriptive name/"
```
If you receive an error that MOK is not installed do:
```
sudo apt install mokutil
```
Then run the above command again, in my case mokutil was already installed.
Then disable secure boot:
```
sudo mokutil --disable-validation
```
Then run the above command again, in my case mokutil was already installed.
Sign the module rtl8723be is your driver, not everyone will have the same driver so where rtl8723be is seen you will need to put your wireless driver there instead.
```
sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./MOK.priv ./MOK.der $(modinfo -n rtl8723be)
```
Register the keys to Secure Boot:
```
sudo mokutil --import MOK.der
```
Type a password for later use after reboot.

Reboot and follow instructions to Enroll MOK (Machine Owner Key).
You will see a blue screen after you reboot.

If the UEFI firmware doesn't have a MOK password, mokutil will ask you to create one here. At this point, you'll need to reboot the client system. Upon reboot, you'll see the blue screen again.

The screenshots at the bottom of the screen will walk you through the process.

Click on Enroll MOK

Then the firmware gives you the option of viewing the new MOK or continuing.  

Click on continue.

It then asks you to to confirm enrollment. 

Click on yes.

Then you will need to enter the password you used when running 'mokutil --import'. 

Finally, the firmware will ask you to reboot. 

Do all of the above after you have the driver installed.

Once your computer boots the driver should load automatically.

The directions came from here:
[http://askubuntu.com/questions/760671/could-not-load-vboxdrv-after-upgrade-to-ubuntu-16-04](http://askubuntu.com/questions/760671/could-not-load-vboxdrv-after-upgrade-to-ubuntu-16-04)
[https://sourceware.org/systemtap/wiki/SecureBoot](https://sourceware.org/systemtap/wiki/SecureBoot)

I will be traveling in a few minutes so I return you to chili555.

---

### Post by chili555 on 2016-06-02
Thank you, Wild Man!

Please note that the fix he proposes is required *if and only if* you have this error:>  ERROR: could not insert 'rtl8723be': Required key not available

---

### Post by marcello8 on 2016-06-08
thanks for your interest in my problem.
I followed all the instructions.
mok was already installed.
I copied and pasted all your instructions in the terminal windows
I had no error messages.
I had to type my password... I rebooted... I had the blue screen and retyped my password but.... the driver is not automatically loaded.
What can I try?
try to reinstall the driver whit the procedure already done at the beginning?

---

### Post by marcello8 on 2016-06-08
I tried to give  again the last command in the sequence for installing the driver
I cut and copy the result:

sudo modprobe -v rtl8723be ant_sel=2
insmod /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko 
modprobe: ERROR: could not insert 'rtl8723be': Required key not available


it seems nothing changed

---

### Post by wildmanne39 on 2016-06-08
On the blue screen did you do only this >  I had to type my password... I rebooted... I had the blue screen and retyped my password but.... .
Or did you do all of this on the blue screen?
> Reboot and follow instructions to Enroll MOK (Machine Owner Key).
You will see a blue screen after you reboot.

If the UEFI firmware doesn't have a MOK password, mokutil will ask you to create one here. At this point, you'll need to reboot the client system. Upon reboot, you'll see the blue screen again.

The screenshots at the bottom of the screen will walk you through the process, you can also refer to the second link in my precious post.
Click on Enroll MOK

Then the firmware gives you the option of viewing the new MOK or continuing.

Click on continue.

It then asks you to to confirm enrollment.

Click on yes.

Then you will need to enter the password you used when running 'mokutil --import'.

Finally, the firmware will ask you to reboot.

Do all of the above after you have the driver installed.

Once your computer boots the driver should load automatically.
Did you do everything in quotes and all of it is done in the blue screen.

Yes I would recompile the driver again and if you have the same issue you can run the creating key method again and it should work.

---

### Post by simproxy3 on 2016-06-14
Please what do you mean by:

> **Wild Man said:**
> 

Do all of the above after you have the driver installed.

Once your computer boots the driver should load automatically. ?

I created the key and tried to reinstall the driver but it still returns the ERROR: could not insert 'rtl8723be': Required key not available
What next? I've done the key creating twice now. Now I no longer have wifi at all as the driver isn't installed.

---

### Post by simproxy3 on 2016-06-15
Finally got it working. Forgive my answer format as this is likely my third post here
For anyone who was in my situation (required keys missing for rtl8723be device), these are the steps I took to solve the problem:

1. Disable secure boot:: 
sudo mokutil --disable-validation

[http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-dkms-modules-in-ubuntu-16/762255#762255) 


2. Reinstall the rtlwifi driver (during installation I was reminded to remove secure boot, perhaps that was missing from the previous answer given by wild man and chili555?). ? Unless the wifi driver from lwfinger is not considered 3rd party?

[URL="http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem"]http://askubuntu.com/questions/635625/realtek-8723be-wifi-problem
[/URL]
sudo rm /etc/modprobe.d/rtl8723be.conf
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware

3. Reboot
4. Finally do this if the wifi connection is still weak

echo "options rtl8723be ant_sel=2"  | sudo tee /etc/modprobe.d/rtl8723be.conf

Thanks to everyone who contributed to this thread.

---

### Post by chili555 on 2016-06-15
Awesome! I'm very happy that it's working and grateful that you posted a step-by-step for all the searchers.

---

### Post by wildmanne39 on 2016-06-17
simproxy3 thank for that additional information, I did not need to do that step to get mine to work, I believe secure boot was already off but I added that step to my answer.

---

### Post by ambikeshwar-one on 2016-07-03
Follow the fix given on following link, it worked for me :)
[http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/](http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/)

---

### Post by artdo on 2016-07-14
Hi,

I was facing the same low range wifi problem. I am able to correct it by installing the aforementioned driver and disabling secure boot. But I want to keep secure boot, so I followed Wild Man's suggestion and created a key to sign the module.

I am still getting this error message: " modprobe: ERROR: could not insert 'rtl8723be': Required key not available "

I have checked if my module is indeed getting signed using: hexdump -C /lib/modules/4.4.0-28-generic/updates/dkms/rtl8723be.ko | tail
This displays "~Module signature appended~.

I have also checked if the key I have created is indeed getting loaded using: sudo keyctl list %:.system_keyring
This shows the key I have created.

I am totally at loss as to what is going wrong. Please help me in resolving this issue.

---

### Post by praseodym on 2016-07-15
Tried deactivating secure boot in your UEFI?

---

### Post by artdo on 2016-07-15
Yes, like I said the module gets loaded flawlessly while secure boot is disabled (in UEFI). What I want to do is keep my secure intact; hence was trying to sign the module using keys. I tried creating the keys with secure boot enabled and disabled both. Nothing has worked till now.

---

### Post by ayush1810 on 2016-09-05
> **lwta08 said:**
> I tried the driver from rock.the new_btcoex branch and it is working fine on my HP x360 13-s laptop.

Here is what I did:

I downloaded the code from [https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex) , unzipped it and then:

```

$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
sudo ip link set wlp2s0 up
sudo iw dev wlp2s0 scan

```

The scan then showed all networks with expected signal strength.

To make the settings permanent:

```

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf

```

Note:
I had to use the parameter** ant_sel=2** even though my antenna is connected to antenna** input #1** !
Using ant_sel=1 (what I tried first) did not work.

This worked quite well for me. But after a reboot, the wireless driver doesn't work again & I have to go through the same thing all the time. How do I fix that?

---

### Post by chili555 on 2016-09-05
> **ayush1810 said:**
> This worked quite well for me. But after a reboot, the wireless driver doesn't work again & I have to go through the same thing all the time. How do I fix that?Reboot. Is it working? If not, post:```
lsmod | grep rtl
dmesg | grep rtl
```

---

### Post by ayush1810 on 2016-09-05
> **chili555 said:**
> Reboot. Is it working? If not, post:```
lsmod | grep rtl
dmesg | grep rtl
```

Wait, I noticed this time that there's an issue with permissions. This is what I get:
```

~/Desktop/rtlwifi_new-rock.new_btcoex$ sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
bash: /etc/modprobe.d/50-rtl8723be.conf: Permission denied

```

---

### Post by chili555 on 2016-09-05
> **ayush1810 said:**
> Wait, I noticed this time that there's an issue with permissions. This is what I get:
```

~/Desktop/rtlwifi_new-rock.new_btcoex$ sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
bash: /etc/modprobe.d/50-rtl8723be.conf: Permission denied

```Try it this way instead:```
sudo -i
echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
exit
```
Reboot and please report your result.

---

### Post by ayush1810 on 2016-09-05
> **chili555 said:**
> Try it this way instead:```
sudo -i
echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
exit
```
Reboot and please report your result.

Hey, this worked. Thank you so much! :D

---

### Post by dirk frigne on 2016-09-05
This worekd for me. Thanks!

Dirk

---

### Post by ayush1810 on 2016-09-07
> **chili555 said:**
> Try it this way instead:```
sudo -i
echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
exit
```
Reboot and please report your result.

Looks like that reboot was just a lucky one. 
I am back with the same issue. This time it's bigger that I redid the steps, all went ok but didn't solve the issue, the wifi is no way working now:(

---

### Post by ayush1810 on 2016-09-07
> **chili555 said:**
> Reboot. Is it working? If not, post:```
lsmod | grep rtl
dmesg | grep rtl
```

This might do something I guess. 
```

    lsmod | grep rtl
btrtl                  16384  1 btusb
bluetooth             520192  31 bnep,btbcm,btrtl,btusb,rfcomm,btintel
rtl8723be             143360  0
btcoexist             421888  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               135168  3 btcoexist,rtl_pci,rtl8723be
mac80211              737280  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              565248  2 mac80211,rtlwifi

 dmesg | grep rtl
[   11.242030] rtlwifi: module verification failed: signature and/or required key missing - tainting kernel
[   11.557753] Using firmware rtlwifi/rtl8723befw.bin
[   11.609761] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.609970] rtlwifi: wireless switch is on
[   12.798466] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   12.798470] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   12.918398] rtl8723be 0000:08:00.0 wlo1: renamed from wlan0
[   34.444900] r8169 0000:09:00.0 eno1: rtl_counters_cond == 1 (loop: 1000, delay: 10).

```

---

### Post by chili555 on 2016-09-07
What is the exact response to the command:```
sudo modprobe rtl8723be
```> rtlwifi: wireless switch is onAnd also:```
rfkill list all
```

---

### Post by ayush1810 on 2016-09-12
> **chili555 said:**
> What is the exact response to the command:```
sudo modprobe rtl8723be
```And also:```
rfkill list all
```

Nothing happens. 

```
ayush@ayush-HP:~$ sudo modprobe rtl8723be
[sudo] password for ayush:
ayush@ayush-HP:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

---

### Post by ayush1810 on 2016-09-12
This time I was using Windows 10, chose Restart and entered into Ubuntu. That's why the wireless driver isn't working.
If only I'd chosen Shut Down and then started Ubuntu, it would be working for sure.

---

### Post by wildmanne39 on 2016-09-12
Chili555 is away for a couple of weeks.

This command showed nothing? 
```
sudo modprobe rtl8723be
```
if so please post the results of the wireless script in my signature if you have shutdown the computer since you ran that command run it again and watch for errors then run the script.
Thanks

---

### Post by ayush1810 on 2016-09-19
> **Wild Man said:**
> Chili555 is away for a couple of weeks.

This command showed nothing? 
```
sudo modprobe rtl8723be
```
if so please post the results of the wireless script in my signature if you have shutdown the computer since you ran that command run it again and watch for errors then run the script.
Thanks

The command didn't show anything, as I said previously. I had stopped using Windows for a while so no issues. 
An hour ago, played games in Windows, ShutDown and started Ubuntu and the issue is back! 
 
I ran the wireless script using a wired connection, the results of which are at [http://paste.ubuntu.com/23202976/](http://paste.ubuntu.com/23202976/)
[ATTACH]271262[/ATTACH]

---

### Post by ayush1810 on 2016-09-22
So somehow the issue turned permanent and now I can't use WiFi in any OS. :(

---

### Post by jeremy31 on 2016-09-22
Power off the machine, remove power cord and battery.  See if removing the wireless card and reinstalling it brings it back

---

### Post by ayush1810 on 2016-09-23
How do I remove and reinstall the wireless card?

---

### Post by prashsid on 2016-09-27
> **lwta08 said:**
> I tried the driver from rock.the new_btcoex branch and it is working fine on my HP x360 13-s laptop.

Here is what I did:

I downloaded the code from [https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex](https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex) , unzipped it and then:

```

$ make
$ sudo make install
$ sudo modprobe -rv rtl8723be
$ sudo modprobe -v rtl8723be ant_sel=2
sudo ip link set wlp2s0 up
sudo iw dev wlp2s0 scan

```

The scan then showed all networks with expected signal strength.

To make the settings permanent:

```

sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf

```

Note:
I had to use the parameter** ant_sel=2** even though my antenna is connected to antenna** input #1** !
Using ant_sel=1 (what I tried first) did not work.



Thanks for the steps. It worked on my HP Pavilion ab031TX laptop.

---

### Post by vivekjib on 2016-09-28
> **prashsid said:**
> Thanks for the steps. It worked on my HP Pavilion ab031TX laptop.

$ sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
bash: /etc/modprobe.d/50-rtl8723be.conf: Permission denied    :(

How can I make it permanent ? 
Why I am getting *Permission denied* ?

---

### Post by chili555 on 2016-09-28
> **vivekjib said:**
> $ sudo echo "options rtl8723be ant_sel=2" > /etc/modprobe.d/50-rtl8723be.conf
bash: /etc/modprobe.d/50-rtl8723be.conf: Permission denied    :(

How can I make it permanent ? 
Why I am getting *Permission denied* ?Please try this:```
sudo -i
echo "options rtl8723be ant_sel=2"  >  /etc/modprobe.d/50-rtl8723be.conf
exit
```Reboot.

---

### Post by patond on 2016-12-17
This site solved the problem for me.  [http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/](http://connectwww.com/how-to-solve-realtek-rtl8723be-weak-wifi-signal-problem-in-ubuntu/4625/)

Signal went from Weak to Excellent.  Don't forget to note the output from iwconfig and use this in the last two steps - **sudo ip link set wlp13s0 up**  and **wlp13sudo iw dev s0 scan** insteadof wlp13s0

---

### Post by anukulsaini on 2017-02-10
i have same problem i try this but no difference anyone can help me please ???

---

### Post by chili555 on 2017-02-10
> **anukulsaini said:**
> i have same problem i try this but no difference anyone can help me please ???Please start your own new thread and include the result of the wireless script in your post: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by akshatah33 on 2017-02-24
Thanx bro.. my wifi is working perfect with ur solution... i tries everything before going for the h/w solution... nothing worked except this!!!! Thanx a lot bro.!!!

---

### Post by rgups14 on 2017-03-10
Thanks a lot guys, had the same issue, [#52]("https://ubuntuforums.org/showthread.php?t=2304607&p=13425505#post13425505") solved my problem as well.:)

---

### Post by atultherajput on 2017-03-16
Trick for Realtek RTL8723BE network adapter.
First check your **wl** number by using :

[B]iwconfig

[/B]In my case it was **wlo1 **download zip file (driver) from [https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex ]("https://github.com/lwfinger/rtlwifi_new/tree/rock.new_btcoex")extract it to desktop. Then use these commands:

[B]cd Desktop

[/B]**cd rtlwifi_new-rock.new_btcoex**

**make**

**sudo make install**

**sudo modprobe -rv rtl8723be**

**sudo modprobe -v rtl8723be ant_sel=2**
[B]
sudo ip link set [/B]*[[your wl number]]*** up**

**sudo iw dev ***[[your wl number]]*** scan**

To make your setting permanent:

**echo "options rtl8723be ant_sel=2" | sudo tee /etc/modprobe.d/50-rtl8723be.conf**

---

### Post by hansaj007 on 2017-04-21
1- install new module for realtek wifi cards where they solved the constant disconnects
-install required packages
sudo apt-get install build-essential git


-git clone new realtek wifi modules
git clone [https://github.com/lwfinger/rtlwifi_new/](https://github.com/lwfinger/rtlwifi_new/)


-enter the directory
cd rtlwifi_new


-build it
make


-install
sudo make install


Now you can reboot or unload/load modules
-unload modules
sudo modprobe -r rtl8723be


-load new module
sudo modprobe rtl8723be


2- After lots of Googling, I found a recent post with new firmware.


Download rtl8723befw.bin ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1454843/+attachment/4438588/+files/rtl8723befw.bin](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1454843/+attachment/4438588/+files/rtl8723befw.bin)), copy it to /lib/firmware/rtlwifi/ and then reboot your laptop.
-Disable the sleep feature of the driver:
$ echo "options rtl8723be fwlps=0" | sudo tee /etc/modprobe.d/rtl8723be.conf


3- Antena Test
iwlist scan | egrep -i 'ssid|quality'


sudo modprobe -r rtl8723be


Check antena 1
sudo modprobe rtl8723be ant_sel=1


iwlist scan | egrep -i 'ssid|quality'


sudo modprobe -r rtl8723be


check antena 2
sudo modprobe rtl8723be ant_sel=2


iwlist scan | egrep -i 'ssid|quality'


If ant_sel=1 was the best then do
echo "options rtl8723be ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723-ant-sel.conf


4- Also, I recommend that your regulatory domain be set explicitly. Check yours:


sudo iw reg get


-Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)
Mine is IN 


sudo iw reg set IN


-To set it permanant
gksudo gedit /etc/default/crda
REGDOMAIN=IN

---

### Post by manurss on 2017-07-01
#119 works!! thank you very very much


I only have one doubt. With this commands the wifi will continue working after a kernel update? I usually make this kind of things with dkms

---

### Post by jeremy31 on 2017-07-01
If you have the 4.4 kernel or newer you don't need to download anything to use the ant_sel parameter.  You just need to find what setting works best

A lot of info is very old as Larry Fingers github has been updated with a dkms.conf- over a year ago

If you did the git clone from your home directory you should be able to use dkms by
```
cd rtlwifi
```
```
make clean
```
```
cd
```
```
sudo dkms add ./rtlwifi-new
```
```
sudo dkms install rtlwifi-new/0.6
```

---

### Post by manurss on 2017-07-01
> **jeremy31 said:**
> If you have the 4.4 kernel or newer you don't need to download anything to use the ant_sel parameter.  You just need to find what setting works best

A lot of info is very old as Larry Fingers github has been updated with a dkms.conf- over a year ago

If you did the git clone from your home directory you should be able to use dkms by
```
cd rtlwifi
```
```
make clean
```
```
cd
```
```
sudo dkms add ./rtlwifi-new
```
```
sudo dkms install rtlwifi-new/0.6
```

Thanks!! the 0.6 was my doubt, but as you say is not needed any more

---

### Post by realmg9 on 2017-09-24
#52 Great software solution!
It works for me at Ubuntu 16.04 LTS

---

### Post by mcfant on 2017-12-15
so if i dont have to download nothing how to I fix the problem with kernel 4.10?

---

### Post by praseodym on 2017-12-15
No

---

### Post by mcfant on 2017-12-15
?

---

### Post by jeremy31 on 2017-12-15
From one of chili555's posts earlier in the thread
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=1
```
```
sudo modprobe -rv rtl8723be
sudo modprobe -v rtl8723be ant_sel=2
```

Test again. Is one or the other better? If so then do the following:

```
sudo -i
echo "options rtl8723be ant_sel=Y" > /etc/modprobe.d/50-rtl8723be.conf
exit
```

where Y is 1 or 2 depending on which works better.

---

### Post by mcfant on 2017-12-15
it worked!! thank you for your time!

---

