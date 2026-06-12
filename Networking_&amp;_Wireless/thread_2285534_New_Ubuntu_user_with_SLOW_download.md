---
title: "New Ubuntu user with SLOW download"
date: 2015-07-06
forum: Networking &amp; Wireless
---

### Post by barry14 on 2015-07-06
This question has been asked by others yet I haven't found a way to resolve the issue on my PC running Ubuntu 15.04.  Results of the script "wireless-info" are attached.   Note: Downloads with my other PC via the same router are very fast.

How can I resolve this?
```


########## wireless info START ##########


Report from: 06 Jul 2015 13:07 MST -0700


Booted last: 06 Jul 2015 12:35 MST -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid


##### kernel ############################


Linux 3.19.0-22-generic #22-Ubuntu SMP Tue Jun 16 17:15:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
    Kernel driver in use: r8169


05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
    Subsystem: AzureWave Device [1a3b:2161]
    Kernel driver in use: rtl8821ae


##### lsusb #############################


Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 0461:4e26 Primax Electronics, Ltd 
Bus 007 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 13d3:3414 IMC Networks 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


rtl8821ae             229376  0 
eeepc_wmi              16384  0 
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
asus_wmi               24576  1 eeepc_wmi
sparse_keymap          16384  1 asus_wmi
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              724992  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              540672  2 mac80211,rtlwifi
video                  20480  1 asus_wmi
wmi                    20480  1 asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f279:59ff:fe3a:15d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7371 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12259151 (12.2 MB)  TX bytes:587952 (587.9 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::42e2:30ff:fef6:49a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3971 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2060 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532993 (532.9 KB)  TX bytes:211923 (211.9 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"CenturyLink0012"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'CenturyLink0012' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:  off
          Power Management ff
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:263   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    1024   0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0


##### resolv.conf #######################


nameserver 192.168.0.1
nameserver 205.171.2.25
search Home


##### network managers ##################


Installed:


    NetworkManager


Running:


root       765     1  0 12:35 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.2/0000:04:00.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       88cc183d-97ed-4fa8-83b8-507fd6556ed5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   88cc183d-97ed-4fa8-83b8-507fd6556ed5 | Wired connection 1
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.0.6/24, gw = 192.168.0.1
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             205.171.2.25
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1436297772
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.0.6
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1 205.171.2.25
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::f279:59ff:fe3a:15d5/64, gw = ::


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 3.19.0-22-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.3/0000:05:00.0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     CenturyLink0012
GENERAL.CON-UUID:                       74249545-41ea-432d-a095-324275258bfa
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   74249545-41ea-432d-a095-324275258bfa | CenturyLink0012
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
IP4.ADDRESS[1]:                         ip = 192.168.0.7/24, gw = 192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DNS[2]:                             205.171.2.25
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        network_number = 192.168.0.0
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_time_offset = 1
DHCP4.OPTION[8]:                        expiry = 1436297769
DHCP4.OPTION[9]:                        domain_name = Home
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       routers = 192.168.0.1
DHCP4.OPTION[15]:                       dhcp_lease_time = 86400
DHCP4.OPTION[16]:                       ip_address = 192.168.0.7
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_interface_mtu = 1
DHCP4.OPTION[19]:                       requested_domain_name_servers = 1
DHCP4.OPTION[20]:                       domain_name_servers = 192.168.0.1 205.171.2.25
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       requested_ntp_servers = 1
DHCP4.OPTION[27]:                       requested_netbios_scope = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         ip = fe80::42e2:30ff:fef6:49a9/64, gw = ::


SSID             BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
CenturyLink0012  <MAC 'CenturyLink0012' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  63      ƒ-,ƒ-,ƒ-+_  WPA1 WPA2  yes     * 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/CenturyLink0012]] (600 root)
[connection] id=CenturyLink0012 | type=wifi
[wifi] ssid=CenturyLink0012 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Phoenix (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20), (N/A)
    (2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
    (5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'CenturyLink0012' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key n
                    ESSID:"CenturyLink0012"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004fdeff55acd
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     9200E1F9DEA4D2D3C81C455
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C74:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512
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


[rtl_pci]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A25DC6D8C53D55DA133BC49
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7: D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.19.0-22-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7:D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-22-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     88CC41451370601B0D885E4
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7: D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-22-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-22-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C7: D4:40:34:4C:0B:3A:C2:A3:CE:C2:AE:B9:72:2E:CF:6C:AE:73:91
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz   Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    8.854746] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[    8.884002] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.884236] rtlwifi: rtlwifi: wireless switch is on
[   25.882493] wlan0: authenticate with <MAC 'CenturyLink0012' [AC1]>
[   25.882843] wlan0: send auth to <MAC 'CenturyLink0012' [AC1]> (try 1/3)
[   25.884898] wlan0: authenticated
[   25.885782] wlan0: associate with <MAC 'CenturyLink0012' [AC1]> (try 1/3)
[   25.889469] wlan0: RX AssocResp from <MAC 'CenturyLink0012' [AC1]> (capab=0x411 status=0 aid=2)
[   25.889644] wlan0: associated
[   33.329649] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:42e2:30ff:fef6:49a9 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24  (repeated 2 times)
[   33.409498] [UFW BLOCK] IN=wlan0 OUT= MAC=33:33:00:00:00:01:<MAC 'eth0' [IF]>:86:dd SRC=fe80:0000:0000:0000:f279:59ff:fe3a:15d5 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=8612 DPT=8612 LEN=24  (repeated 2 times)
[   42.099233] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:10:5f:06:73:2b:50:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2  (repeated 16 times)


########## wireless info END ############
```

---

### Post by PaulW2U on 2015-07-06
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. If you are using Quick Reply then add [noparse]```
 at the beginning of the section and 
```[/noparse] at the end.

As you can see it's made your post a little easier to read. Anyway, Welcome to the Forums.

---

